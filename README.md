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

📘 O que você vai encontrar aqui

| Pasta | Conteúdo |
|------|----------|
| `/casos-de-teste` | Casos de teste documentados |
| `/bugs-encontrados` | Bugs encontrados, analisados e corrigidos |
| `/evidencias` | Screenshots e provas de execução |
| `/postman` | Coleções e documentação de testes de API |
| `README.md` | Visão geral do portfólio e validações realizadas |

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

---

## ✅ Validação recente — CAPA-31 — Retorno pós-checkout do Stripe

Foi validada com sucesso a correção do fluxo de retorno pós-checkout de assinatura no CutAxis Pro.

### Cenário validado
Durante os testes, foi identificado que, após concluir o pagamento no Stripe, o usuário nem sempre era encaminhado diretamente para dentro da aplicação como assinante. Em alguns casos, o sistema retornava para a tela de trial expirado ou só refletia o status correto após novo login.

### Correção validada
Após a correção:
- o usuário retorna do checkout diretamente para dentro da aplicação;
- o status é atualizado corretamente para **Assinante**;
- não é mais necessário fazer novo login para refletir a assinatura;
- o fluxo permanece estável após refresh e após logout/login.

### Regressão executada
- fluxo principal com usuário em trial expirado;
- upgrade com usuário já autenticado dentro da aplicação;
- persistência da assinatura após refresh;
- persistência da assinatura após logout/login;
- validação do console sem erro crítico do bug original.

### Observação complementar
Durante o teste de cancelamento, foi observado que a assinatura permanece válida até o fim do período pago. Esse comportamento foi registrado como **regra de negócio a confirmar**, sem impacto na validação da CAPA-31.

### Artefatos relacionados
- [BUG-005 — CAPA-31 — Retorno pós-checkout do Stripe não promovia o usuário imediatamente para assinante](./bugs-encontrados/BUG-005-capa-31-retorno-pos-checkout-stripe.md)

### Evidências
- [Fluxo principal corrigido](./evidencias/capa-31/01-capa31-fluxo-principal-assinante.png)
- [Upgrade com usuário autenticado](./evidencias/capa-31/02-capa31-upgrade-usuario-autenticado.png)
- [Modal de cancelamento](./evidencias/capa-31/03-capa31-cancelamento-modal.png)
- [Login após cancelamento](./evidencias/capa-31/04-capa31-login-pos-cancelamento.png)
- [Validade da assinatura após cancelamento](./evidencias/capa-31/05-capa31-validade-assinatura.png)
- [Console sem erro crítico](./evidencias/capa-31/06-capa31-console-sem-erro-critico.png)

### Resultado final
**Status: PASS**  
Correção validada com sucesso em ambiente publicado, com evidências visuais e regressão funcional executada.


## 🎯 Competências demonstradas neste projeto

- Testes funcionais end-to-end
- Validação de fluxo mensal automatizado
- Teste de integração frontend + backend
- Validação de push notifications web/mobile
- Investigação de bugs em ambiente real
- Verificação de regras de negócio
- Apoio em diagnóstico técnico com logs
- Documentação de testes e bugs

## 🔜 Próximas etapas de QA e API

As próximas evoluções deste portfólio serão:

- criação e organização das collections do Postman;
- documentação dos principais endpoints da API;
- registro contínuo de bugs encontrados durante os testes;
- expansão dos casos de teste manuais e de integração;
- acompanhamento das tarefas e bugs via Jira;
- evidências adicionais de testes em ambiente real.

### Próximo foco
- autenticação
- rotas de push notifications
- validação de endpoints do backend
- documentação dos testes de API
