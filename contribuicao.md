# Como registrar novos casos

Esta página orienta como manter a base atualizada sem perder consistência, clareza e confiabilidade.

---

## Quando registrar

Registre um novo caso quando:

- o erro se repete com frequência
- a tratativa foi validada e pode ajudar outras pessoas
- o fluxo ou processo precisa ficar documentado
- a situação gera dúvida recorrente na equipe
- o escalonamento para o mesmo problema se repete

---

## O que todo registro precisa ter

- O que aconteceu
- Em que contexto aconteceu
- Qual a causa identificada (se ainda não confirmada, diga isso explicitamente)
- Qual foi a solução aplicada
- Quando escalar e para qual área

Se alguma informação não estiver confirmada, registre da seguinte forma:
> Causa em análise — padrão ainda não confirmado pela equipe.

---

## Estrutura obrigatória

```markdown
## Título descritivo do erro

**Mensagem:**

MENSAGEM EXATA DO ERRO

**Causa:** Explicação do motivo.

**O que fazer:**
1. Passo 1
2. Passo 2

**Atenção:** Observações relevantes.

**Encaminhar para:** GECON / GETIC / DevOps — com informações adicionais.
```

O modelo completo está em [Modelo de novo caso](modelo-de-registro.md).

---

## Fluxo de atualização

1. Identificar o caso que merece registro
2. Escolher a categoria correta
3. Preencher o modelo padrão
4. Revisar se o texto está claro e objetivo
5. Confirmar se as informações são confiáveis
6. Publicar no repositório

---

## Onde cada tipo de caso vai

| Tipo de caso | Página |
|---|---|
| API, WSO2, serviço externo, sincronização | integracoes.md |
| ERP, faturamento, cadastro, cobrança | benner.md |
| Permissões, acessos, onboarding | acessos.md |
| Caso reincidente com histórico de chamados | problemas.md |
| Novo chamado aberto | chamados.md |

---

## O que evitar

- Publicar causas prováveis como se fossem confirmadas
- Adicionar contatos sem validação prévia
- Textos longos demais — priorize leitura rápida
- Escalonamento sem critério claro
- Passos incompletos ou ambíguos

---

*Última revisão: Abril 2026*
