# Modelo de novo caso

Use este modelo sempre que precisar registrar um novo erro, processo ou tratativa na base.

---

## Template padrão

```markdown
## Título descritivo do erro

**Mensagem:**

MENSAGEM EXATA DO ERRO (se houver)

**Contexto:**
Descreva em que cenário o erro acontece. Qual sistema, qual fluxo, qual ação do usuário.

**Causa:**
Explique a causa identificada.
Se ainda não estiver validada, escreva:
"Causa em análise — padrão ainda não confirmado."

**O que fazer:**
1. Primeiro passo
2. Segundo passo
3. Terceiro passo

**Atenção:**
Inclua alertas, limitações ou situações em que a tratativa não se aplica.

**Encaminhar para:**
Indique quando escalar e para qual área — GECON, GETIC ou DevOps.
Inclua referência de chamados anteriores se houver.
```

---

## Exemplo preenchido

```markdown
## Conta financeira não configurada no Benner

**Mensagem:**

FINOBJ - Validação das contas financeiras: A conta deve ser preenchida!

**Contexto:**
Ocorre ao tentar integrar lançamentos financeiros. O sistema rejeita a integração por falta de conta financeira no CR.

**Causa:**
O CR (Centro de Responsabilidade) não tem conta financeira configurada no Benner.

**O que fazer:**
1. Identificar o CR associado ao lançamento com erro
2. Verificar no Benner se o CR possui conta financeira cadastrada
3. Encaminhar para GECON com o nome do CR

**Atenção:**
Não altere a configuração do CR sem envolver a GECON. Alterações incorretas podem impactar outros lançamentos vinculados.

**Encaminhar para:**
GECON — carolini.silveira@fiesc.com.br / marcos@fiesc.com.br
```

---

## Checklist antes de publicar

- O título está claro e descreve o erro de forma objetiva?
- O contexto está compreensível para alguém que não viveu o caso?
- A causa está validada ou sinalizada como "em análise"?
- A solução está em passos simples e ordenados?
- O escalonamento está preciso — para qual área e quando?
- O texto está curto o suficiente para leitura rápida?

---

*Última revisão: Abril 2026*
