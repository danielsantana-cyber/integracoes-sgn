# Direcionamento e Escalonamento

>Esta página ajuda o suporte a decidir para qual equipe um caso deve ser direcionado quando não puder ser resolvido no atendimento inicial.

---

## Objetivo desta página

Evitar escalonamento incorreto e reduzir retrabalho.

O foco aqui é responder:
- quando o caso ainda é do suporte
- quando deve ir para GECON
- quando deve ir para GETIC
- quando deve ir para devs

---

## Regra geral

Antes de escalar, o suporte deve sempre validar:

1. contexto do erro
2. sistema envolvido
3. mensagem de erro
4. evidências mínimas
5. se o caso já possui tratativa documentada

---

## Quando direcionar para GECON

Use este direcionamento quando o caso envolver principalmente:

- regra de negócio
- entendimento operacional do processo
- fluxo funcional do sistema
- validação de procedimento da área
- dúvida sobre como o processo deveria funcionar

> AGECOM tende a entrar quando a questão está mais ligada ao funcionamento esperado do processo do que a erro técnico puro.

---

## Quando direcionar para GETIC

Use este direcionamento quando o caso envolver principalmente:

- falha técnica de ambiente
- indisponibilidade
- erro de infraestrutura
- integração travada sem indício funcional
- problema sistêmico que afeta mais de um usuário ou operação

> GTIC tende a entrar quando o comportamento aponta para algo mais técnico, estrutural ou sistêmico.

---

## Quando direcionar para devs

Use este direcionamento quando houver indício de:

- bug de sistema
- comportamento incoerente da aplicação
- erro reproduzível sem tratativa conhecida
- falha específica do fluxo implementado
- necessidade de correção de código ou ajuste estrutural

> O suporte deve evitar acionar devs sem contexto claro ou sem evidência mínima.

---

## Como pensar rapidamente no direcionamento

| Situação predominante | Direcionamento provável |
|---|---|
| Dúvida de processo / regra / fluxo esperado | GECON |
| Erro técnico de ambiente / indisponibilidade / infraestrutura | GETIC |
| Bug, comportamento inconsistente ou ajuste de sistema | Devs |

---

## O que deve acompanhar qualquer escalonamento

Sempre enviar junto:

- número do chamado
- descrição objetiva do problema
- sistema afetado
- mensagem de erro
- evidência visual
- contexto validado pelo suporte
- o que já foi tentado antes do envio

---

## Observação importante

Os critérios exatos de cada equipe devem ser refinados com a operação real. Esta página representa a estrutura-base para padronizar o raciocínio do suporte.

---

*Página de apoio à decisão de escalonamento da equipe de suporte.*
