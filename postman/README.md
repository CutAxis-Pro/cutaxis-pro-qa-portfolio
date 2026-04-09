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

- https://cutaxis-backend.onrender.com

Health check validado:

- GET /health

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

  
## Evidências relacionadas
Arquivos salvos em:

- `evidencias/postman-auth-login-200-ok.png`
- `evidencias/postman-auth-register-201-created.png`

  
## Status atual
Concluído:
- collection criada;
- estrutura inicial organizada;
- environment Production selecionado;
- base da API validada;
- endpoint de login testado com sucesso via Postman;
- endpoint de register testado com sucesso via Postman.

Próximos passos:
- atualizar a task CAPA-27 no Jira com a validação do register;
- salvar e reutilizar token em requests autenticados;
- iniciar validação dos endpoints de push notifications;
- continuar documentação dos resultados no GitHub.

## Observação de segurança
Tokens de autenticação não devem ser expostos em documentação pública, commits ou screenshots abertas.
