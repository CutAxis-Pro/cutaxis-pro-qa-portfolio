# CT-004 – Register da API via Postman

## Identificação
- ID: CT-004
- Módulo: Auth
- Tipo: Teste funcional de API
- Prioridade: Alta
- Ambiente: Production

## Objetivo
Validar se o endpoint de registro da API do CutAxis Pro cria corretamente um novo usuário em produção, utilizando o Postman.

## Pré-condições
- Collection "CutAxis Pro API Tests" criada no Postman
- Pasta "Auth" criada na collection
- Backend online em produção
- Endpoint de registro disponível
- E-mail ainda não utilizado para cadastro

## Endpoint
- Método: POST
- Rota: `/auth/register`
- URL completa: `https://cutaxis-backend.onrender.com/auth/register`

## Headers
- Content-Type: application/json

## Body utilizado
```json
{
  "name": "Teste QA Postman",
  "email": "EMAIL_NOVO_VALIDO",
  "password": "123456"
}
