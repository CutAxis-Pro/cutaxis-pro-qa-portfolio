# CT-007 – Endpoint Cuts da API via Postman

## Identificação
- ID: CT-007
- Módulo: Core Features
- Tipo: Teste funcional de API
- Prioridade: Alta
- Ambiente: Production

## Objetivo
Validar o endpoint de cortes da API do CutAxis Pro em produção via Postman, verificando se a rota retorna corretamente os registros de cortes cadastrados no sistema.

## Pré-condições
- Collection "CutAxis Pro API Tests" criada no Postman
- Pasta "Core Features" criada na collection
- Request "Get Cuts" salva
- Usuário válido autenticado
- Token JWT válido disponível
- Backend em produção ativo

## Endpoint
- Método: GET
- Rota: /cuts
- URL: https://cutaxis-backend.onrender.com/cuts

## Autenticação
- Tipo: Bearer Token
- Requisito: token válido obtido no login

## Body
- Não se aplica
- Requisição GET sem body

## Resultado esperado
- HTTP 200 OK
- Retorno de dados dos cortes cadastrados
- Estrutura JSON válida contendo informações relacionadas aos cortes

## Resultado obtido
- HTTP 200 OK
- Retorno de dados reais dos cortes cadastrados
- Estrutura com campos como:
  - id
  - carne.id
  - carne.nome
  - carne.categoria
  - data
  - mes
  - pesoBruto
  - pesoUtil

## Evidência
- `evidencias/postman-core-cuts-200-ok.png`

## Status do teste
- APROVADO

## Observações
- Endpoint confirmado anteriormente via aba Network do navegador.
- A rota respondeu com sucesso no Postman utilizando Bearer Token.
- Sem autenticação, endpoints protegidos do módulo Core Features podem retornar 401 Unauthorized.
