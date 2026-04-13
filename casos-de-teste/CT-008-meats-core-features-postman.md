# CT-008 – Endpoint Meats da API via Postman

## Identificação
- ID: CT-008
- Módulo: Core Features
- Tipo: Teste funcional de API
- Prioridade: Alta
- Ambiente: Production

## Objetivo
Validar o endpoint de carnes da API do CutAxis Pro em produção via Postman, verificando se a rota retorna corretamente os registros cadastrados no sistema.

## Pré-condições
- Collection "CutAxis Pro API Tests" criada no Postman
- Pasta "Core Features" criada na collection
- Request "Get Meats" salva
- Usuário válido autenticado
- Token JWT válido disponível
- Backend em produção ativo

## Endpoint
- Método: GET
- Rota: /meats
- URL: https://cutaxis-backend.onrender.com/meats

## Autenticação
- Tipo: Bearer Token
- Requisito: token válido obtido no login

## Body
- Não se aplica
- Requisição GET sem body

## Resultado esperado
- HTTP 200 OK
- Retorno de dados das carnes cadastradas
- Estrutura JSON válida contendo informações relacionadas às carnes

## Resultado obtido
- HTTP 200 OK
- Retorno de dados reais cadastrados
- Estrutura com campos como:
  - id
  - name
  - category
  - userId
  - createdAt

## Evidência
- `evidencias/postman-core-meats-200-ok.png`

## Status do teste
- APROVADO

## Observações
- Endpoint confirmado anteriormente via aba Network do navegador.
- A rota respondeu com sucesso no Postman utilizando Bearer Token.
- Sem autenticação, endpoints protegidos do módulo Core Features podem retornar 401 Unauthorized.
