# Modelo de registro

Use este modelo sempre que for documentar um novo erro, processo ou tratativa. A ideia é manter a base padronizada sem deixar o texto duro demais.

---

## Estrutura recomendada

```markdown
## Título claro do caso

**Mensagem:**
Mensagem exata do erro, quando existir.

**Quando acontece:**
Explique em que fluxo isso aparece e qual é o contexto do caso.

**Como identificar:**
Diga o que o suporte precisa observar antes de agir.

**Causa:**
Explique a causa confirmada.
Se ainda não estiver validada, escreva:
Causa em análise — padrão ainda não confirmado.

**O que fazer:**
1. Primeiro passo.
2. Segundo passo.
3. Terceiro passo.

**Atenção:**
Liste o que pode gerar erro de análise, retrabalho ou exceção.

**Quando escalar:**
Explique quando o caso sai da alçada do suporte e para qual área ele deve ir.

**Referências:**
Inclua chamados anteriores, links ou páginas relacionadas quando isso ajudar.
```

---

## Exemplo preenchido

```markdown
## Conta financeira não configurada no Benner

**Mensagem:**
FINOBJ - Validação das contas financeiras: A conta deve ser preenchida!

**Quando acontece:**
O erro aparece ao tentar integrar um lançamento financeiro que depende de conta associada ao CR.

**Como identificar:**
Abra o protocolo, localize o CR no lançamento e confirme que o erro está relacionado à validação financeira.

**Causa:**
O CR não possui conta financeira configurada no Benner.

**O que fazer:**
1. Identificar o CR associado ao lançamento.
2. Registrar o contexto do caso.
3. Encaminhar para GECON com o CR e a evidência do erro.

**Atenção:**
Não tente tratar isso como erro técnico de integração. O ajuste depende da área financeira.

**Quando escalar:**
Escalar para GECON assim que o CR estiver identificado.

**Referências:**
Direcionamento e escalonamento, Erros do Benner.
```

---

## Checklist antes de publicar

- O título está objetivo?
- Quem não viveu o caso vai entender o contexto?
- A causa está validada ou sinalizada como ainda em análise?
- Os passos estão curtos e seguros?
- Está claro quando o suporte resolve e quando deve escalar?
- Existe alguma referência útil que vale citar?

---

*Última revisão: Abril de 2026* 
