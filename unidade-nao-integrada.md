# Unidade nao integrada ao Benner — Baixa Tesouraria

Esta pagina documenta o processo para resolver o erro de unidade sem integracao com o Benner, identificado e tratado pelo suporte em conjunto com o Squad de Integracoes.

---

## O erro

**Mensagem:**
```
O servico de baixa tesouraria retornou status diferente de 200[OK]: Bad Request. Mensagem: A unidade da cobranca nao esta integrada com o Benner. id cobranca XXXXXXX - id unidade XXX
```

**O que significa:**
Para processar a baixa tesouraria, o SGN precisa que a unidade da cobranca tenha um `id_externo` cadastrado na base do sistema. Quando esse campo nao esta preenchido, a baixa nao consegue ser enviada.

---

## Como resolver

1. Identificar o ID da unidade informado no erro
2. Localizar o **Codigo da Filial** dessa unidade no Benner — esse e o `id_externo` que precisa ser cadastrado
3. Solicitar ao DBA a insercao do registro com o comando abaixo:

```sql
INSERT INTO integracao.unidade (id_unidade, id_aplicacao, id_externo, criacao) 
VALUES (?, 8, ?, NOW());
```

Onde:
- Primeiro `?` = id_unidade (informado no erro)
- Segundo `?` = id_externo = **Codigo da Filial no Benner**

4. Apos a insercao confirmada, reprocessar a baixa tesouraria

---

## Como encontrar o Codigo da Filial no Benner

O campo que o SGN precisa e o **Codigo da Filial** no Benner — nao e o CNPJ e nao e o campo Handle do Benner Corporativo. Sao campos diferentes.

Em caso de duvida sobre qual e o valor correto, acionar o Renan ou verificar com a Rafaela qual e o Codigo da Filial para aquela unidade especifica.

---

## Importante

Esse processo nao e um chamado — e uma configuracao de banco que precisa ser feita pelos DBAs. Confirmar com a Rafaela o canal correto para solicitar essa insercao.

---

*Caso documentado a partir de ocorrencia operacional real — Squad Integracoes*
