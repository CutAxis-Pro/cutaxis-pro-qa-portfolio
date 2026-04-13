# Mapeamento de Endpoints – CutAxis Pro API

## Objetivo
Documentar os principais endpoints identificados e/ou validados durante a fase de testes da API do CutAxis Pro, organizando a cobertura por módulo e o status atual de cada rota.

## Base da API
`https://cutaxis-backend.onrender.com`

## Legenda de status
- **Validado** = endpoint executado com sucesso e já testado
- **Identificado** = endpoint observado no sistema/frontend ou na estrutura técnica
- **Em investigação** = endpoint encontrado, mas ainda depende de validação adicional
- **Pendente** = endpoint ainda não explorado

---

## 1. Infra / Saúde da API

| Método | Endpoint | Módulo | Status | Observação |
|--------|----------|--------|--------|------------|
| GET | `/health` | Infra | Validado | Health check retornando status OK |

---

## 2. Auth

| Método | Endpoint | Módulo | Status | Observação |
|--------|----------|--------|--------|------------|
| POST | `/auth/login` | Auth | Validado | Login testado via Postman |
| POST | `/auth/register` | Auth | Validado | Registro testado via Postman |

---

## 3. Push

| Método | Endpoint | Módulo | Status | Observação |
|--------|----------|--------|--------|------------|
| GET | `/push/vapid-key` | Push | Validado | Retorna publicKey |
| POST | `/push/subscribe` | Push | Em investigação | Exige token e valida payload |
| DELETE | `/push/unsubscribe` | Push | Pendente | Ainda não validado |

---

## 4. Core / Dados observados no frontend

| Método | Endpoint | Módulo | Status | Observação |
|--------|----------|--------|--------|------------|
| GET | `/dashboard` | Core Features | Validado | Confirmado via Network e validado via Postman |
| GET | `/cuts` | Core Features | Validado | Confirmado via Network e validado via Postman |
| GET | `/meats` | Core Features | Validado | Confirmado via Network e validado via Postman |



## 5. URLs completas confirmadas via Network

- `GET https://cutaxis-backend.onrender.com/dashboard`
- `GET https://cutaxis-backend.onrender.com/cuts`
- `GET https://cutaxis-backend.onrender.com/meats`


---

## Observações gerais
- O frontend foi observado consumindo o backend em produção.
- O endpoint `/dashboard` foi confirmado via Network do navegador.
- O endpoint `/push/subscribe` permanece em investigação funcional/técnica.
- O mapeamento será atualizado conforme novos testes forem executados.

## Próximos passos
- Expandir o mapeamento para outros endpoints consumidos pelo frontend
- Continuar a validação prática de rotas da API via Postman
- Manter README, evidências e casos de teste sincronizados com os testes executados
- Revisar o módulo Push após esclarecimento técnico do fluxo de subscribe
