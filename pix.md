# PIX — Tratativas de Integracao

Esta pagina reune as informacoes especificas do fluxo de integracao PIX no SGN.

---

## Quando integrar cobranças de PIX

A cobranca via PIX so deve ser integrada **depois que o PIX e cobrado e confirmado**. Nao integrar antes da confirmacao do pagamento.

---

## Aba PIX no dashboard

A aba PIX no dashboard mostra o status das integracoes relacionadas a pagamentos via PIX. E diferente das abas principais de cobranca (Matricula, Contrato, Agrupador, RPC).

Ao analisar erros na aba PIX:
1. Verificar se o pagamento PIX ja foi confirmado
2. Consultar a planilha de casos PIX antes de qualquer acao
3. Seguir as orientacoes dos grupos de integracao no Hangouts

---

## Planilhas de acompanhamento PIX

| Entidade | Link |
|---|---|
| SESI | https://docs.google.com/spreadsheets/d/1A2h2-ApqwfJOx7tHZ4TMlPgHzWu8YjeCAUSoOSRAL7c/edit |
| SENAI | https://docs.google.com/spreadsheets/d/1Mui0RQF_Yizj3exM3smGkflpdcGw4NYWu4udy4fvu8s/edit |

---

## Erro: parcela liquidada em PIX

**Mensagem:**
```
Parcela ja foi liquidada. Verifique o valor da movimentacao, pois o documento foi baixado integralmente e restou um saldo de XX,XX
```

**Como analisar:**
- Valor da parcela original
- Valor da baixa de desconto
- Valor da baixa tesouraria (= valor do PIX recebido)

A conta correta e: `valor parcela - desconto = valor tesouraria (PIX)`

Se a conta nao fechar, provavelmente o desconto foi integrado duas vezes no Benner. O SGN enviou corretamente — o problema e do lado do Benner.

**O que fazer:**
1. Confirmar os valores
2. Solicitar ao Alexandre (grupo de integracoes) a exclusao do desconto duplicado
3. Reprocessar a baixa tesouraria apos a exclusao
4. Abrir chamado na GETIC para investigar a causa raiz

---

## Erro: cobranca vinculada ao txid nao esta integrada

**Mensagem:**
```
A cobranca vinculada ao txid XXXXXXXXXXXXXXXXXX nao esta integrada com o Benner.
```

**O que fazer:**
1. Verificar a taxa de matricula na aba correspondente — ela precisa estar integrada primeiro
2. Clicar em **Consultar** na taxa
3. Apos confirmacao, reenviar

O processo sempre e: verificar se a taxa esta integrada antes de reenviar a forma de pagamento.

---

## Grupos de comunicacao

Ha dois grupos no Hangouts para acionamentos relacionados ao PIX e fechamento:
- Grupo de PIX
- Grupo de Fechamento

Acionamentos da GECON e GETIC chegam por esses grupos e por e-mail. A Rafaela pode incluir o suporte nesses grupos se necessario.

---

*Conteudo baseado no repasse operacional — Squad Integracoes, Movimentacoes Financeiras*
