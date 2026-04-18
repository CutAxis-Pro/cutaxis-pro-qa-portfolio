# BUG-006 — CAPA-32: cancelamento de assinatura não persistia corretamente após novo login

## Resumo
Ao cancelar a assinatura, o utilizador deixava de ser deslogado e mantinha o acesso até ao fim do período pago, porém o estado visual de cancelamento não persistia corretamente após novo login. Em alguns cenários, a aplicação voltava a apresentar o utilizador como "Assinante", exibindo novamente o botão de cancelamento, em vez de manter o estado "Assinatura cancelada".

## Contexto
Fluxo de cancelamento de assinatura no ambiente de produção do CutAxis Pro, com utilizador autenticado e assinatura ativa.

## Comportamento observado
- Após cancelar a assinatura, o utilizador permanecia dentro da aplicação.
- O acesso continuava ativo até ao fim do período pago.
- Em correções intermediárias, a UI passou a mostrar "Assinatura cancelada".
- Porém, ao fazer logout/login novamente, o estado voltava para "Assinante" em vez de permanecer como cancelado até à data final.

## Impacto
- Estado visual inconsistente para o utilizador
- Reexibição incorreta do botão "Cancelar Assinatura"
- Divergência entre regra de negócio e interface
- Risco de confusão sobre validade do acesso e estado real da subscrição

## Causa raiz
A persistência do estado de cancelamento estava incompleta entre frontend e backend.

### Frontend
- A UI dependia de campos como `cancelAtPeriodEnd` / `cancel_at_period_end`
- O estado era refletido logo após o cancelamento, mas não persistia corretamente após reconstrução da sessão

### Backend
- A rota de cancelamento inicialmente rebaixava o utilizador para `TRIAL` de forma imediata
- O schema não possuía o campo `cancelAtPeriodEnd`
- O webhook e o payload retornado ao frontend não expunham corretamente o estado de cancelamento pendente até o fim do período
- O formatter/retorno do utilizador autenticado precisava incluir `cancelAtPeriodEnd`, `cancel_at_period_end` e `subscriptionStatus`

## Correções aplicadas

### Frontend
- Ajuste da `cancelSubscription()` para não derrubar mais a sessão
- Atualização da `updateSubscriptionUI()` para suportar três estados:
  - assinante ativo
  - assinatura cancelada no fim do período
  - expirado/teste

### Backend
- Inclusão do campo `cancelAtPeriodEnd` no `schema.prisma`
- Sincronização do schema com o banco via Prisma
- Ajuste da rota de cancelamento para manter:
  - `plan: "PRO"`
  - `subscriptionActive: true`
  - `cancelAtPeriodEnd: true`
  - `planEnd` preservado
- Ajuste do webhook `invoice.payment_succeeded` para limpar:
  - `cancelAtPeriodEnd: false`
- Ajuste do payload retornado ao frontend para incluir:
  - `cancelAtPeriodEnd`
  - `cancel_at_period_end`
  - `subscriptionStatus`

## Validação executada

### Cenário 1 — cancelamento imediato
1. Login com utilizador assinante
2. Acesso à área Config > Minha Assinatura
3. Clique em "Cancelar Assinatura"
4. Confirmação do cancelamento

**Resultado esperado:** manter acesso e exibir estado cancelado até o fim do período  
**Resultado obtido:** PASS

### Cenário 2 — persistência após refresh
1. Recarregar a página após cancelamento

**Resultado esperado:** continuar como assinatura cancelada  
**Resultado obtido:** PASS

### Cenário 3 — persistência após logout/login
1. Fazer logout
2. Fazer login novamente com o mesmo utilizador
3. Verificar a área Minha Assinatura

**Resultado esperado:** continuar como "Assinatura cancelada", sem reexibir botão de cancelar  
**Resultado obtido:** PASS

## Resultado final
A CAPA-32 foi validada com sucesso. O utilizador mantém o acesso até ao último dia do período pago, a UI apresenta corretamente o estado "Assinatura cancelada" e esse estado persiste após novo login.

## Evidências recomendadas
- print da tela com status "Cancelada"
- print do card "Minha Assinatura" com a data final
- evidência do comportamento após novo login

## Aprendizados de QA
- Validar não apenas o fluxo imediato, mas também a persistência do estado após reconstrução de sessão
- Confirmar consistência entre regra de negócio, payload de backend e renderização de frontend
- Investigar bugs de assinatura sempre sob a ótica completa: Stripe, backend, autenticação, UI e storage
