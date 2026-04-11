# Postman – CutAxis Pro API Tests

## Objetivo
Esta pasta documenta a estrutura inicial dos testes de API do projeto CutAxis Pro no Postman, com foco em organização QA, rastreabilidade, evidências e evolução dos testes por módulo.

## Collection principal
A collection criada no Postman foi:

- CutAxis Pro API Tests

## Estrutura inicial da collection
Pastas organizadas:

- Auth
- Push
- Monthly Flow
- Core Features

## Ambiente utilizado
Environment selecionado:

- Production

Base da API validada:

- `https://cutaxis-backend.onrender.com`

Health check validado:

- [GET /health](https://cutaxis-backend.onrender.com/health)

## Testes executados

### Login da API
Endpoint testado:

- POST /auth/login

Resultado obtido:

- 200 OK
- Retorno com dados do usuário autenticado
- Retorno de token JWT

### Registro de usuário
Endpoint testado:

- POST /auth/register

Resultado obtido:

- 201 Created
- Usuário criado com sucesso
- Retorno com dados do usuário
- Resposta válida da API

### Obter VAPID Key
Endpoint testado:

- GET /push/vapid-key

Resultado obtido:

- 200 OK
- Retorno da publicKey
- Resposta válida em JSON

  
## Evidências relacionadas
Arquivos salvos em:

- `evidencias/postman-auth-login-200-ok.png`
- `evidencias/postman-auth-register-201-created.png`
- `evidencias/postman-push-vapid-key-200-ok.png`
  
## Status atual
Concluído:
- collection criada;
- estrutura inicial organizada;
- environment Production selecionado;
- base da API validada;
- endpoint de login testado com sucesso via Postman;
- endpoint de register testado com sucesso via Postman.
- endpoint GET /push/vapid-key testado com sucesso via Postman.

Próximos passos:
- continuar validação dos endpoints de push notifications;
- atualizar a task CAPA-28 no Jira com o progresso do módulo Push;
- documentar novos resultados no GitHub;
- seguir para os próximos endpoints do módulo Push.
  
## Observação de segurança
Tokens de autenticação não devem ser expostos em documentação pública, commits ou screenshots abertas.
