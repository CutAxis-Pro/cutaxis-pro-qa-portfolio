# cutaxis-pro-qa-portfolio
Portfólio de testes manuais e de API do projeto CutAxis Pro - SaaS de gestão de inventário
🧪 Portfólio QA — CutAxis Pro

Olá! Sou **Hugo Vieira**, Software Tester em transição de carreira,
com experiência prática em testes de um sistema SaaS real em produção.

 🔗 Sobre o Projeto Testado
**CutAxis Pro** é um sistema de gestão de inventário para restaurantes,
desenvolvido por mim e usado em produção real.
👉 [Acessar sistema](https://cutaxis-pro.vercel.app/)

  🛠️ Ferramentas utilizadas
- Postman (API Testing)
- Jira (gerenciamento de bugs)
- Confluence (documentação)
- Git/GitHub

  📋 O que você vai encontrar aqui
| Pasta | Conteúdo |
|---|---|
| `/plano-de-testes` | Estratégia e escopo dos testes |
| `/casos-de-teste` | Casos de teste documentados |
| `/bug-reports` | Bugs encontrados e reportados |
| `/testes-api-postman` | Coleção de testes de API |
| `/evidencias` | Screenshots de execução |

  📬 Contato
- LinkedIn: [hugo-vieira-213b38180](https://www.linkedin.com/in/hugo-vieira-213b38180/)
- Email: vieirahugo761@gmail.com

## ✅ Validação recente — Fluxo mensal de relatórios

Foi validado com sucesso o fluxo mensal do sistema CutAxis Pro, incluindo:

- envio de relatório mensal por email;
- envio de push notification após o email;
- suporte a usuários com zero dados no mês;
- envio correto para usuários com dados reais;
- reset mensal dos usuários comuns;
- preservação dos dados do ADMIN CUTAXIS.

### Resultado final
O fluxo foi executado com sucesso em teste real, com evidência de:
- email enviado;
- push recebida no dispositivo;
- reset aplicado aos usuários comuns;
- admin preservado.

### Artefatos relacionados
- [CT-002 — Relatório mensal com email, push e reset](./casos-de-teste/CT-002-relatorio-mensal-email-push-reset.md)
- [BUG-001 — Relatório mensal não era enviado](./bugs-encontrados/BUG-001-relatorio-mensal-nao-enviado.md)
- [BUG-002 — Usuários sem dados não recebiam email](./bugs-encontrados/BUG-002-usuarios-sem-dados-nao-recebiam-email.md)
- [BUG-003 — Admin sofria reset indevido](./bugs-encontrados/BUG-003-admin-sofria-reset.md)

### Evidências
- `evidencias/relatorio-mensal-terminal.png`
- `evidencias/relatorio-mensal-mobile-comprovacao.png`

## 🎯 Competências demonstradas neste projeto

- Testes funcionais end-to-end
- Validação de fluxo mensal automatizado
- Teste de integração frontend + backend
- Validação de push notifications web/mobile
- Investigação de bugs em ambiente real
- Verificação de regras de negócio
- Apoio em diagnóstico técnico com logs
- Documentação de testes e bugs
