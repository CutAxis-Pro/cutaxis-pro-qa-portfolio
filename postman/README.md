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

## Teste executado
### Login da API
Endpoint testado:

- POST /auth/login

Resultado obtido:

- 200 OK
- Retorno com dados do usuário autenticado
- Retorno de token JWT

## Achado importante de QA
Durante a validação do login, foi identificado que o backend aceita corretamente o campo:

- `password`

e não:

- `senha`

Quando o payload foi enviado com `password`, a autenticação funcionou corretamente no Postman.

## Evidência relacionada
Arquivo salvo em:

- `evidencias/postman-auth-login-200-ok.png`

## Status atual
Concluído:
- collection criada;
- estrutura inicial organizada;
- environment Production selecionado;
- base da API validada;
- login testado com sucesso via Postman.

Próximos passos:
- documentar o caso de teste formal do login;
- salvar e reutilizar token em requests autenticados;
- testar endpoint de registro;
- validar endpoints de push notifications;
- continuar a documentação dos resultados no GitHub.

## Observação de segurança
Tokens de autenticação não devem ser expostos em documentação pública, commits ou screenshots abertas.
