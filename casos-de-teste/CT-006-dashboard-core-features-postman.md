# CT-006 – Dashboard da API via Postman

## Identificação
- ID: CT-006
- Módulo: Core Features
- Tipo: Teste funcional de API
- Prioridade: Alta
- Ambiente: Production

## Objetivo
Validar o endpoint de dashboard da API do CutAxis Pro em produção via Postman, verificando se a rota retorna corretamente os dados consolidados do painel.

## Pré-condições
- Collection "CutAxis Pro API Tests" criada no Postman
- Pasta "Core Features" criada na collection
- Request "Get Dashboard" salva
- Usuário válido autenticado
- Token JWT válido disponível
- Backend em produção ativo

## Endpoint
- Método: GET
- Rota: /dashboard
- URL: https://cutaxis-backend.onrender.com/dashboard

## Autenticação
- Tipo: Bearer Token
- Requisito: token válido obtido no login

## Body
- Não se aplica
- Requisição GET sem body

## Resultado esperado
- HTTP 200 OK
- Retorno de dados consolidados do dashboard
- Estrutura JSON contendo métricas do sistema

## Resultado obtido
- HTTP 200 OK
- Retorno de dados do dashboard com métricas como:
  - totalCuts
  - producaoTotal
  - pesoUtilTotal
  - desperdicioTotal
  - rendimentoMedio

## Evidência
- `evidencias/postman-core-dashboard-200-ok.png`

## Status do teste
- APROVADO

## Observações
- Sem token, o endpoint retornou 401 Unauthorized com mensagem "Token not provided".
- Com Bearer Token válido, o endpoint respondeu corretamente com 200 OK.
- Endpoint anteriormente identificado via aba Network do navegador e posteriormente validado via Postman.
