# BUG-004 — Falha no login da API identificada via Postman ao usar `senha` no payload

## Origem do registro
Este registro foi identificado durante um teste de API executado no Postman, no ambiente Production, e não durante teste funcional da interface do app.

## Tipo
Bug / achado técnico de QA identificado em teste de API

## Contexto
Durante a validação do endpoint de autenticação da API do CutAxis Pro via Postman, a requisição de login falhou quando o body foi enviado com o campo `senha`.

## Ferramenta utilizada
- Postman

## Ambiente
- Production

## Endpoint analisado
- Método: POST
- Rota: `/auth/login`
- URL completa: `https://cutaxis-backend.onrender.com/auth/login`

## Comportamento observado
Quando o payload foi enviado com:

```json
{
  "email": "EMAIL_VALIDO",
  "senha": "SENHA_VALIDA"
}
