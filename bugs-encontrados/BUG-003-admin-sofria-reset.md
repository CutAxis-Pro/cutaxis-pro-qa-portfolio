# BUG-003 — ADMIN não deveria ter os dados mensais resetados

## Descrição
A rotina mensal precisava resetar apenas os dados dos usuários comuns, preservando os dados do ADMIN CUTAXIS.

## Impacto
- Risco de apagar dados operacionais do administrador
- Regra de negócio não atendida

## Correção aplicada
Foi adicionada verificação de `role === "ADMIN"` antes do reset.

## Resultado
- Usuários comuns: reset executado
- ADMIN: reset ignorado

## Status
**Corrigido e validado**
