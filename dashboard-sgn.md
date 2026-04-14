# Como usar o Dashboard de Integracoes

Esta pagina explica como navegar e usar o Dashboard de integracoes do SGN no dia a dia do suporte. As informacoes foram consolidadas a partir do repasse operacional da equipe de desenvolvimento.

---

## Links diretos

| Tela | Link |
|---|---|
| Dashboard Integracao Faturamento | https://sgn.sesisenai.org.br/pages/administracao/integracao/faturamento/integracao-faturamento.html |
| Dashboard Integracao Pessoa | https://sgn.sesisenai.org.br/pages/administracao/integracao/pessoa/integracao-pessoa.html |
| Busca de pessoa (para reenvio) | https://sgn.sesisenai.org.br/pages/pessoa/buscar-pessoa.html |
| Abertura de chamado GETIC | https://sesuite.fiesc.com.br/softexpert/workspace?page=home |

---

## Como abrir chamado na GETIC

Ao acessar o SeSuite, usar os seguintes campos:

- **Servico:** Sistemas de Apoio
- **Item:** Sistema de Tecnologia
- **Categoria:** Integracoes - Plataforma WSO2

---

## Abas do dashboard e o que cada uma representa

O dashboard de faturamento possui varias abas. Elas se dividem em dois grupos:

**Abas de envio de cobrancas (principal atencao do suporte):**
- Matricula
- Contrato
- Agrupador
- RPC

Essas sao as abas onde a cobranca em si e enviada ao Benner. Sao as mais criticas para monitoramento diario.

**Abas de alteracao de cobrancas:**
- Desconto
- Baixa
- Cancelamento
- Pix
- Cartao

Essas abas tratam modificacoes sobre cobranças ja integradas.

---

## Rotina diaria recomendada

1. Acessar o dashboard de faturamento
2. Verificar a primeira aba — ela traz um overview de todos os casos
3. Filtrar por **Erro no retorno** e **Erro no envio** em cada aba
4. Tratar os casos com erro de retorno primeiro
5. Erro no envio e mais raro, mas quando aparece precisa de tratativa imediata

O erro no retorno significa que o sistema tentou integrar, recebeu uma resposta negativa do Benner e ficou pendente. O erro no envio significa que o sistema nem conseguiu enviar a requisicao.

---

## Como identificar se um registro precisa de tratativa

Na listagem do dashboard, registros em **negrito** indicam que precisam de acao diferente do padrao:

- Nome em negrito: usar **Forcar reenvio**
- Nome sem negrito: usar **Reenviar selecionados**

---

## Como verificar protocolos de um registro

Dentro de cada registro no dashboard ha um botao que abre a modal com os protocolos de envio. Ali e possivel ver todos os envios realizados, os retornos recebidos e os erros ocorridos.

Sempre consultar os protocolos antes de tomar qualquer acao. Eles mostram se o registro ja foi integrado com sucesso em algum envio anterior.

---

## Quando aprovar retorno

Usar "Aprovar retorno" quando:

- O protocolo anterior mostra que a integracao ja ocorreu com sucesso
- O registro foi enviado duas vezes e o primeiro deu certo — o segundo vai dar erro naturalmente
- O Benner confirma que o documento ja esta integrado corretamente

**Justificativa padrao para aprovacao de retorno:**
```
Ja foi integrado com sucesso
```

Sempre preencher a justificativa ao aprovar. O campo e obrigatorio.

---

## Fluxo do cartao — mais complexo

A aba Cartao gerencia um fluxo completo de integracao em cadeia:

```
Cobranca -> Baixa Desconto -> Baixa Cartao -> Conversao
```

Cada etapa depende da anterior. Ao analisar erros em Cartao, verificar em qual etapa do fluxo o problema ocorreu antes de tentar reenvio ou aprovacao.

---

## Verificando integracao de pessoa

Quando aparecer erro informando que uma pessoa nao esta integrada com o Benner:

1. Acessar: https://sgn.sesisenai.org.br/pages/administracao/integracao/pessoa/integracao-pessoa.html
2. Buscar no campo **Cliente** pelo CPF ou nome da pessoa
3. Selecionar **Aplicacao: Benner** e **Situacao: Todas**
4. Verificar o status do ultimo protocolo

Se a pessoa nao estiver integrada e precisar reenviar, acessar o cadastro da pessoa em https://sgn.sesisenai.org.br/pages/pessoa/buscar-pessoa.html e salvar o cadastro novamente. Isso dispara o reenvio.

---

## Planilhas de referencia

| Planilha | Link |
|---|---|
| Documentacao de erros e chamados | https://docs.google.com/spreadsheets/d/1KAFtXeZr6KQ3021KDhdisdD4lDsy7fwHLkISaIjRbnE/edit |
| Casos PIX SESI | https://docs.google.com/spreadsheets/d/1A2h2-ApqwfJOx7tHZ4TMlPgHzWu8YjeCAUSoOSRAL7c/edit |
| Casos PIX SENAI | https://docs.google.com/spreadsheets/d/1Mui0RQF_Yizj3exM3smGkflpdcGw4NYWu4udy4fvu8s/edit |

---

## CNPJs de referencia

| Entidade | CNPJ |
|---|---|
| SENAI | 03.774.688/0001-55 |
| SESI | 03.777.341/0001-66 |

---

*Conteudo baseado no repasse operacional da equipe de desenvolvimento — Squad Integracoes*
