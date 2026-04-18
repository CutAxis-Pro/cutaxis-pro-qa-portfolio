# CT-010 — BUG-006 — CAPA-32: cancelamento de assinatura persistindo até o fim do período

## Objetivo
Validar que, após o cancelamento da assinatura, o usuário permaneça com acesso ativo até o último dia do período pago, com a interface exibindo corretamente o estado de assinatura cancelada e mantendo essa informação mesmo após refresh ou novo login.

## Contexto
Foi identificado que, ao cancelar a assinatura, o sistema inicialmente apresentava comportamento inconsistente: em alguns cenários o acesso era cortado imediatamente, e em outros a interface continuava exibindo o usuário como assinante ativo, inclusive reapresentando o botão de cancelamento após logout/login.

A correção implementada passou a considerar corretamente o estado de cancelamento no frontend e no backend, garantindo persistência visual e funcional até o fim do período pago.

## Pré-condições
- Usuário autenticado na aplicação
- Usuário com assinatura ativa
- Integração com Stripe funcionando corretamente
- Backend persistindo os campos relacionados ao cancelamento da assinatura
- Frontend atualizado para interpretar o estado `cancelAtPeriodEnd`

## Massa de dados
- Usuário de teste com assinatura ativa
- Assinatura válida com período pago em andamento

## Passos para execução
1. Acessar a aplicação com um usuário assinante.
2. Navegar até a área de gerenciamento da assinatura.
3. Acionar o cancelamento da assinatura.
4. Confirmar a ação de cancelamento.
5. Validar o comportamento imediatamente após o cancelamento.
6. Verificar se a interface exibe o status de assinatura cancelada.
7. Confirmar se o acesso permanece liberado até o fim do período vigente.
8. Atualizar a página (refresh) e validar a persistência do estado.
9. Realizar logout.
10. Efetuar novo login com o mesmo usuário.
11. Validar novamente o status exibido na interface.
12. Confirmar que o botão de cancelar assinatura não reaparece indevidamente.

## Resultado esperado
Após o cancelamento da assinatura:
- o usuário não deve ser deslogado;
- o acesso deve permanecer ativo até o fim do período pago;
- a interface deve exibir o status **"Assinatura cancelada"**;
- a mensagem de validade até o fim do período deve aparecer corretamente;
- o botão de cancelar assinatura deve desaparecer;
- o estado deve persistir após refresh;
- o estado deve continuar correto após logout/login.

## Resultado obtido
Após a correção aplicada, o cancelamento da assinatura passou a se comportar corretamente. O usuário permaneceu com acesso ativo até o fim do período pago, a interface exibiu o status **"Assinatura cancelada"** com a informação de validade, o botão de cancelamento deixou de ser exibido e o estado permaneceu consistente mesmo após refresh e novo login.

## Status final
**PASS**

## Critérios validados
- [x] Cancelamento não remove o acesso imediatamente
- [x] Interface exibe "Assinatura cancelada"
- [x] Validade até o fim do período é exibida corretamente
- [x] Botão de cancelamento desaparece após a ação
- [x] Estado persiste após refresh
- [x] Estado persiste após logout/login

## Evidências
- `BUG-006-capa-32-cancelamento-imediato.png`
- `BUG-006-capa-32-persistencia-apos-refresh.png`
- `BUG-006-capa-32-status-cancelada-pos-login.png`

## Observações
A correção exigiu ajuste conjunto entre frontend e backend:
- o backend passou a persistir corretamente o estado de cancelamento ao fim do período;
- o frontend passou a interpretar e exibir esse estado corretamente;
- o retorno da sessão autenticada passou a manter os campos de assinatura consistentes após novo login.
