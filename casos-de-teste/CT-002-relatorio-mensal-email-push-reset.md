# CT-002 — Relatório mensal com email, push e reset de dados

## Objetivo
Validar o fluxo mensal automático do CutAxis Pro, garantindo que:
- o relatório mensal seja enviado por email;
- a push notification seja enviada após o email;
- usuários sem dados recebam relatório com valores zerados;
- usuários com dados recebam relatório com valores corretos;
- usuários comuns tenham os dados mensais resetados;
- o ADMIN CUTAXIS não tenha os dados resetados.

## Pré-condições
- Backend publicado no Render
- Frontend publicado no Vercel
- Push notifications previamente registradas
- Usuários com e sem dados cadastrados no mês atual
- ADMIN com role ADMIN no sistema

## Massa de teste
- Usuário admin: CutAxis
- Usuário comum sem dados: Agenor
- Usuário comum sem dados: Hugo Vieira
- Dados mensais cadastrados para o admin

## Passos executados
1. Validar deploy do backend no Render
2. Validar deploy do frontend no Vercel
3. Executar manualmente a rotina mensal
4. Verificar logs do terminal
5. Confirmar recebimento do email
6. Confirmar recebimento da push notification
7. Confirmar reset dos usuários comuns
8. Confirmar que o admin não foi resetado

## Resultado esperado
- Email mensal enviado com sucesso
- Push notification enviada com sucesso
- Usuários sem dados recebem email com totais zerados
- Usuários com dados recebem email com valores reais
- Usuários comuns têm dados mensais resetados
- ADMIN não sofre reset

## Resultado obtido
✅ Email enviado com sucesso  
✅ Push enviado com sucesso  
✅ Usuários sem dados receberam relatório com zero corretamente  
✅ Usuário admin recebeu relatório com dados reais  
✅ Reset executado para usuários normais  
✅ Reset ignorado para admin  

## Status
**APROVADO**

## Evidências
- `evidencias/relatorio-mensal-terminal.png`
- `evidencias/relatorio-mensal-mobile-comprovacao.png`

## Observações
Durante a fase de testes, o reset foi temporariamente desativado para validação segura do fluxo de email + push. Após validação, o reset real foi reativado e o teste final confirmou o comportamento esperado.
