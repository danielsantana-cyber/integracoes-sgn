# Direcionamento e escalonamento

Esta página ajuda a decidir para qual equipe um caso deve ser encaminhado quando não puder ser resolvido no suporte.

---

## Antes de escalar

Verifique:

1. O contexto do erro — em qual sistema e em qual fluxo aconteceu
2. A mensagem exata de erro, se houver
3. Se o caso já tem tratativa documentada em [Integrações](integracoes.md) ou [Benner](benner.md)
4. Se já existe chamado aberto para o mesmo problema em [Chamados abertos](chamados.md)

Só escale depois de validar esses quatro pontos.

---

## Quando encaminhar para GECON

Use esse direcionamento quando o caso envolver principalmente:

- regra de negócio ou processo que a equipe financeira precisa validar
- configurações no Benner que dependem da área financeira (contas, centros de custo, boletos)
- cadastros de produto, filial ou vínculos que precisam ser completados
- dúvida sobre como o processo deveria funcionar

| Tipo de problema | Contato |
|---|---|
| Configurações financeiras no Benner | carolini.silveira@fiesc.com.br, marcos@fiesc.com.br |
| Cadastros de produto e filial | otavio.l.santos@fiesc.com.br, jackson.faria@fiesc.com.br, silvana.tkaczuk@fiesc.com.br |

---

## Quando encaminhar para GETIC

Use esse direcionamento quando o caso envolver principalmente:

- falha técnica de ambiente ou infraestrutura
- integração interrompida sem causa funcional identificada
- erro sistêmico que afeta mais de um usuário ou operação
- problemas no Benner que não dependem de configuração da área de negócio

---

## Quando encaminhar para DevOps

Use esse direcionamento quando houver:

- problema de permissão em API (WSO2)
- comportamento de sistema que parece ser bug
- falha específica de fluxo que já foi descartada como configuração ou regra de negócio

---

## Tabela de decisão rápida

| Situação | Direcionamento |
|---|---|
| Configuração financeira, regra de negócio, cadastro incompleto | GECON |
| Falha técnica, infraestrutura, integração interrompida | GETIC |
| Permissão de API, bug de sistema | DevOps |

---

## O que enviar junto em qualquer escalonamento

- Número do chamado
- Descrição objetiva do problema em no máximo duas linhas
- Sistema afetado
- Mensagem exata do erro
- Print ou evidência visual
- O que já foi validado ou tentado pelo suporte

Quanto mais organizado chegar o escalonamento, mais rápido a equipe de destino consegue atuar.

---

*Última revisão: Abril 2026*
