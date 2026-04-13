# Direcionamento e escalonamento

> 📌 Página de apoio à decisão de escalonamento.

## 🧠 Decisão rápida de escalonamento

| Tipo de problema | Destino provável |
|---|---|
| Regra de negócio / cadastro funcional | GECON |
| Cadastro financeiro / centro de custo / produto x filial | GECON |
| Erro técnico de integração / indisponibilidade / dependência entre sistemas | GETIC |
| Permissão de endpoint / WSO2 / autenticação técnica | DevOps |
| Bug / comportamento incoerente / necessidade de ajuste estrutural | Devs |

## Regra geral

Antes de escalar, o suporte deve sempre validar:

1. contexto do erro
2. sistema envolvido
3. mensagem de erro
4. evidências mínimas
5. se o caso já possui tratativa documentada

## Quando direcionar para GECON

- cadastro financeiro
- centro de custo
- conta financeira
- produto x filial
- configuração funcional no Benner
- dúvidas de processo e regra de negócio

## Quando direcionar para GETIC

- falha técnica de ambiente
- indisponibilidade
- erro sistêmico
- integração travada
- divergência técnica entre sistemas
- casos recorrentes que exigem causa raiz

## Quando direcionar para DevOps

- permissão no WSO2
- endpoint não autorizado
- autenticação técnica
- API subscription validation failed

## Quando direcionar para devs

- bug claro
- comportamento incoerente
- erro reproduzível sem tratativa
- payload errado que exige análise técnica do squad

## Observação importante

Nem sempre o destino fica óbvio no primeiro olhar. O próprio Renan sinalizou que, quando não está na planilha, ainda existe lacuna de documentação. Nesses casos, o ideal é registrar o aprendizado depois da tratativa.

*Estrutura-base para padronizar o raciocínio do suporte.*
