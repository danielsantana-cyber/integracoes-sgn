# Chamados — Base de referência

Esta página reúne **problemas já ocorridos na operação**, com base em chamados reais.

O objetivo não é controlar chamados em aberto, mas sim:

- evitar abertura duplicada
- acelerar análise de novos casos
- dar contexto histórico para escalonamento

---

## Como usar esta página

1. Identifique o erro ou comportamento
2. Busque um problema semelhante abaixo
3. Utilize os chamados como referência na análise ou escalonamento
4. Se não encontrar, siga o fluxo padrão e registre novo caso na base

---

## Problemas críticos recorrentes

Esses são os problemas com maior impacto ou reincidência.

| Problema | O que significa | Ação recomendada |
|---|---|---|
| DependenciasPAISES | Falha de dependência cadastral no Benner | Escalar para GETIC |
| Out of Memory | Falha de infraestrutura / timeout | Verificar se é sistêmico e escalar |
| Pessoa não encontrada | Integração inconsistente de pessoa | Validar integração antes de escalar |
| Value cannot be null | Erro genérico de dados | Validar campos obrigatórios e contexto |

---

## Base de chamados por problema

Cada linha representa um **problema único**, com histórico consolidado.

| Problema | Chamados relacionados | Área responsável | Observação |
|---|---|---|---|
| DependenciasPAISES | TI0302721, TI0305920, TI0312689 | GETIC | Alta recorrência |
| Out of Memory | TI0252965, TI0269739, TI0281296, TI0338268 | GETIC | Possível incidente sistêmico |
| Pessoa não encontrada no Benner | TI0291818 | GETIC | Validar integração antes |
| Value cannot be null | TI0293893 | GETIC | Erro genérico, analisar contexto |
| XML inválido (codigoCentroResponsabilidade) | TI0232055, TI0271054 | GETIC | Divergência entre servidores |
| Documento duplicado no primeiro envio | TI0332905 | GETIC | Comportamento em análise |
| Filtro fParCancelada não funciona | TI0291201 | GETIC | Problema funcional |
| Erro ao integrar faturamento RPC | TI0271054 | GETIC | Validar contexto do envio |

---

##  Como registrar um novo problema

Adicionar um novo problema nesta tabela apenas quando:

- for um erro ainda não documentado
- tiver padrão claro
- já houver pelo menos um chamado relacionado

Evitar duplicidade. Se o problema já existir, apenas utilizar os chamados como referência.

---

##  Diretriz da base

- Não registrar chamados individuais
- Registrar apenas problemas consolidados
- Priorizar clareza e reutilização da informação

---

*Última revisão: Abril 2026*
