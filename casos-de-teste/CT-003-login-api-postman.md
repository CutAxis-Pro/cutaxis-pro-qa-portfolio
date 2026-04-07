# CT-003 – Login da API via Postman

## Identificação
- ID: CT-003
- Módulo: Auth
- Tipo: Teste funcional de API
- Prioridade: Alta
- Ambiente: Production

## Objetivo
Validar se o endpoint de login da API do CutAxis Pro autentica corretamente um usuário válido em produção, utilizando o Postman.

## Pré-condições
- Collection "CutAxis Pro API Tests" criada no Postman
- Pasta "Auth" criada na collection
- Environment "Production" selecionado
- Backend em produção disponível
- Usuário válido disponível para autenticação

## Endpoint
- Método: POST
- Rota: `/auth/login`
- URL completa: `https://cutaxis-backend.onrender.com/auth/login`

## Headers
- Content-Type: application/json

## Body utilizado
```json
{
  "email": "EMAIL_VALIDO",
  "password": "SENHA_VALIDA"
}
