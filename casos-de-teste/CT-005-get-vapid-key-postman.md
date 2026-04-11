# CT-005 – Obter VAPID Key via Postman

## Identificação
- ID: CT-005
- Módulo: Push
- Tipo: Teste funcional de API
- Prioridade: Alta
- Ambiente: Production

## Objetivo
Validar se o endpoint de push notifications da API do CutAxis Pro retorna corretamente a chave pública VAPID, utilizando o Postman.

## Pré-condições
- Collection "CutAxis Pro API Tests" criada no Postman
- Pasta "Push" criada na collection
- Backend online em produção
- Endpoint de VAPID Key disponível

## Endpoint
- Método: GET
- Rota: `/push/vapid-key`
- URL completa: `https://cutaxis-backend.onrender.com/push/vapid-key`

## Headers
- Não requer headers específicos para esta validação inicial

## Body utilizado
- Não se aplica

## Resultado esperado
- Retornar status HTTP 200
- Retornar a chave pública VAPID
- Resposta válida em JSON

## Resultado obtido
- Status HTTP: 200 OK
- Retorno da `publicKey`
- Resposta válida em JSON

## Evidência
- `evidencias/postman-push-vapid-key-200-ok.png`

## Status do teste
- APROVADO

## Observações
Durante a execução inicial, o request foi enviado incorretamente com método POST e retornou erro. Após correção para o método GET, o endpoint respondeu com sucesso.
