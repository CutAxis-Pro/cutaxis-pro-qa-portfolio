# BUG-002 — Usuários sem dados no mês não recebiam relatório

## Descrição
O sistema interrompia o fluxo quando o usuário não possuía cortes no mês, impedindo o envio do relatório com valores zerados.

## Impacto
- Usuários sem dados não recebiam comunicação mensal
- Regra de negócio não era cumprida

## Causa raiz
Existia um `return` após a verificação de ausência de cortes no mês.

## Correção aplicada
O `return` foi removido para permitir a continuidade do fluxo, possibilitando:
- montagem do relatório com totais zerados;
- envio do email;
- envio da push;
- continuidade da lógica mensal.

## Status
**Corrigido e validado**
