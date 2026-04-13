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

## Core Features

### Dashboard
- Endpoint validado: `GET /dashboard`
- Ambiente: Production
- Autenticação: Bearer Token
- Resultado: `200 OK`
- Observação: retorno com métricas consolidadas do dashboard.

### Cuts
- Endpoint validado: `GET /cuts`
- Ambiente: Production
- Autenticação: Bearer Token
- Resultado: `200 OK`
- Observação: retorno com dados reais de cortes cadastrados, incluindo campos como `id`, `carne.nome`, `categoria`, `data`, `mes`, `pesoBruto` e `pesoUtil`.

### Meats
- Endpoint validado: `GET /meats`
- Ambiente: Production
- Autenticação: Bearer Token
- Resultado: `200 OK`
- Observação: retorno com dados reais de carnes cadastradas, incluindo campos como `id`, `name`, `category`, `userId` e `createdAt`.

## Evidências relacionadas
Arquivos salvos em:

- `evidencias/postman-auth-login-200-ok.png`
- `evidencias/postman-auth-register-201-created.png`
- `evidencias/postman-push-vapid-key-200-ok.png`
- `evidencias/postman-core-dashboard-200-ok.png`
- `evidencias/postman-core-cuts-200-ok.png`
- `evidencias/postman-core-meats-200-ok.png`
  
## Casos de teste relacionados

- `casos-de-teste/CT-003-login-api-postman.md`
- `casos-de-teste/CT-004-register-api-postman.md`
- `casos-de-teste/CT-005-get-vapid-key-postman.md`
- `casos-de-teste/CT-006-dashboard-core-features-postman.md`
- `casos-de-teste/CT-007-cuts-core-features-postman.md`
- `casos-de-teste/CT-008-meats-core-features-postman.md`
  
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
