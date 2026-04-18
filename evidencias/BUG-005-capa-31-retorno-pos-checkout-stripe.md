# BUG-005 — CAPA-31 — Retorno pós-checkout do Stripe não promovia o usuário imediatamente para assinante

## Resumo
Ao concluir o pagamento no Stripe, o usuário não era encaminhado diretamente para dentro da aplicação como assinante.
Em vez disso, o sistema podia retornar para a tela de trial expirado ou exigir novo login para refletir o status correto.

## Projeto
**CutAxis Pro**  
SaaS de gestão de inventário / cortes

## Tipo
Bug funcional com impacto no fluxo de assinatura e experiência do usuário

## Severidade
Alta

## Prioridade
Alta

## Ambiente
Produção

## Pré-condições
- Usuário com trial expirado ou em fluxo de upgrade
- Checkout Stripe configurado e funcional
- Backend atualizando assinatura corretamente

## Passos para reproduzir
1. Acessar a aplicação com usuário elegível para assinatura
2. Iniciar o fluxo de checkout no Stripe
3. Concluir o pagamento
4. Retornar para a aplicação

## Resultado esperado
Após o retorno do checkout:
- o usuário deve entrar diretamente na aplicação
- o status deve ser atualizado para **Assinante**
- não deve ser necessário fazer novo login
- o sistema não deve voltar para a tela de trial expirado

## Resultado observado antes da correção
Após o checkout:
- o usuário podia voltar para a tela de trial expirado
- em alguns cenários o status só era refletido após novo login
- o fluxo de sincronização do frontend falhava e impedia a promoção imediata para assinante

## Causa raiz observada
Durante a investigação foi identificado um erro no frontend no fluxo de sincronização pós-checkout.
A função responsável por consultar o backend após o retorno do Stripe utilizava uma referência incorreta para a URL da API, impedindo a atualização do estado do usuário após o pagamento.

Além disso, a ordem de execução do fluxo precisou ser validada para garantir que a sincronização ocorresse antes da montagem normal da interface.

## Correção validada
- uso da constante correta da API no frontend
- sincronização do retorno do Stripe validada antes da montagem da UI
- reteste funcional completo do fluxo de assinatura

## Casos de teste de regressão executados

### CT-REG-CAPA31-01 — trial expirado → checkout → retorno como assinante
**Resultado:** PASS

### CT-REG-CAPA31-02 — usuário autenticado no app faz upgrade
**Resultado:** PASS

### CT-REG-CAPA31-03 — persistência após refresh
**Resultado:** PASS

### CT-REG-CAPA31-04 — persistência após logout/login
**Resultado:** PASS

### CT-REG-CAPA31-05 — cancelamento de assinatura
**Resultado:** comportamento observado / regra de negócio a confirmar  
**Observação:** o sistema manteve o acesso do usuário até o fim do período pago, o que pode indicar cancelamento ao final do ciclo e não revogação imediata.

### CT-REG-CAPA31-06 — console sem erro crítico do bug corrigido
**Resultado:** PASS

## Evidências sugeridas
- erro anterior no console durante a sincronização pós-checkout
- tela final com usuário dentro da aplicação e status **Assinante**
- evidência de persistência após refresh
- evidência de persistência após logout/login
- evidência do comportamento de cancelamento e validade da assinatura

## Resultado final
Bug validado como corrigido.

## Aprendizados de QA
- validar ponta a ponta é essencial em fluxos de billing
- backend correto não garante experiência correta no frontend
- erros de console podem ser decisivos para identificar causa raiz
- fluxos com Stripe exigem atenção especial ao retorno, sincronização e persistência da sessão
- testes de regressão devem cobrir refresh, logout/login e cenários de cancelamento

## Status final
**PASS — CAPA-31 validada funcionalmente**
