# Erros operacionais — Tratativas do dia a dia

Esta pagina reune erros identificados na operacao real do suporte, com as tratativas validadas pela equipe de desenvolvimento. Os casos aqui documentados vem de situacoes reais resolvidas em conjunto com o Squad de Integracoes.

Antes de qualquer acao, verifique os protocolos do registro para entender o historico de envios.

---

## Erros resolvidos pelo proprio suporte

---

### Documento ja existe no sistema

**Mensagem:**
```
Erro interno: Ja existe um documento com essas informacoes cadastrado no sistema!
```

**O que fazer:**
1. Consultar os protocolos — verificar se houve um envio anterior com sucesso
2. Se sim, clicar em **Aprovar retorno**
3. Justificativa: `Ja foi integrado com sucesso`

Este erro ocorre quando o sistema tenta enviar um documento que ja foi integrado. O primeiro envio deu certo, o segundo gerou esse erro. Nao e necessario reenviar.

---

### Documento ja integrado — NOSSO NUMERO

**Mensagem:**
```
Foi encontrado o documento... com a AP: XXXXXXXXX para o NOSSONUMERO: XXXXXXXXXXXXX. Verifique.
```

**O que fazer:**
1. Verificar no Benner se o documento realmente esta integrado
2. Se estiver, clicar em **Aprovar retorno**
3. Justificativa: `Ja foi integrado com sucesso`

Se o documento nao estiver no Benner e o erro aparecer no primeiro envio, este e um problema diferente — consulte a secao de [Problemas recorrentes](problemas.md).

---

### Baixa ja processada anteriormente

**Mensagem:**
```
A requisicao de baixa ja foi processada anteriormente
```
ou
```
A requisicao de baixa de numero XXXXXXXXXX, ja foi processada anteriormente.
```

**O que fazer:**
1. Verificar no Benner se a baixa ja foi registrada com o valor correto
2. Se estiver registrada, clicar em **Aprovar retorno**
3. Justificativa: `Ja foi integrado com sucesso`

---

### Documento enviado duas vezes — duplicidade no protocolo

**Situacao:** O protocolo mostra dois envios, o primeiro com sucesso e o segundo com erro.

**O que fazer:**
Aprovar o retorno do segundo envio. Como o primeiro ja deu certo, o dado esta integrado. O erro no segundo e esperado — o Benner nao aceita o mesmo documento duas vezes.

Justificativa: `Ja foi integrado com sucesso`

---

### CPF/CNPJ duplicado — reenvio resolve

**Mensagem:**
```
Erro interno: Existe mais uma pessoa com este Cnpj/Cpf cadastrado no sistema.
```

**O que fazer:**
- Se o nome estiver em negrito: usar **Forcar reenvio**
- Se o nome nao estiver em negrito: usar **Reenviar selecionados**

Na maioria dos casos o reenvio resolve. Se persistir, abrir chamado na GETIC.

---

### Pessoa nao encontrada no Benner

**Mensagem:**
```
Erro interno: Nao existe uma pessoa com este Cnpj/Cpf cadastrada no sistema.
```

**O que fazer:**
1. Acessar o dashboard de integracao de pessoa
2. Buscar pelo CPF ou nome na aba Benner com situacao Todas
3. Verificar o ultimo protocolo — se mostrar sucesso, a pessoa ja esta integrada
4. Se a pessoa nao estiver integrada, abrir o cadastro dela no SGN e salvar novamente para disparar o reenvio
5. Se o erro persistir apos o reenvio, abrir chamado na GETIC

**Importante:** Uma data de envio muito antiga (ex: 2018) pode indicar que o cadastro desatualizou. Salvar o cadastro novamente e suficiente para reenviar.

---

### Cliente em fila de integracao — nao reenviar

**Mensagem:**
```
O cliente de documento XXX.XXX.XXX-XX nao esta integrado com a Aplicacao Benner. O cliente ja esta sendo enviado para a fila de integracao e nao sera enviado novamente ate que a integracao tenha um retorno.
```

**O que fazer:**
Aguardar. O sistema ja esta tentando integrar a pessoa. Forcando um novo envio neste momento nao vai adiantar e pode gerar duplicidade. Monitorar o protocolo da integracao de pessoa ate que retorne.

---

### Filial nao habilitada para faturar — envio de e-mail

**Mensagem:**
```
Impossivel faturar esta filial com o produto informado. E necessario concluir o cadastro no Benner (vinculos, CNAE, etc) entre o produto e filial ou, a filial ainda nao esta habilitada a faturar.
```

**O que fazer:**
1. Verificar nos protocolos a Entidade, Unidade, Filial e Produto do caso
2. Quando houver varios casos da mesma filial, verificar se e o mesmo produto ou produtos diferentes — cada combinacao filial/produto e uma linha separada no e-mail
3. Montar o e-mail para GECON no formato:

```
Entidade - Unidade - Filial - Produto
SESI - Lages II - 03.777.341/0478-04 - 1856.1
```

Pode botar todos os casos em um unico e-mail, separados em linhas.

**Encaminhar para:** GECON
- otavio.l.santos@fiesc.com.br
- jackson.faria@fiesc.com.br
- silvana.tkaczuk@fiesc.com.br

---

### Centro de custo invalido — informar CR e filial

**Mensagem:**
```
FINOBJ - Validacao dos centros de custo: Centro de custo invalido para a filial
```

**O que fazer:**
1. Abrir o protocolo de envio e localizar o CR (Centro de Responsabilidade) — fica no campo de rateio
2. Informar a filial e o CR ao GECON

**Encaminhar para:** GECON
- carolini.silveira@fiesc.com.br
- marcos@fiesc.com.br

---

### Boleto automatico nao configurado

**Mensagem:**
```
Nao foi possivel realizar a geracao automatica de boleto de cobranca. As configuracoes do boleto automatico nao foram encontradas. Verifique a operacao 2011 (ou 7151), na carga Configuracao boletos automaticos.
```

**Encaminhar para:** GECON com o numero da operacao mencionada no erro (2011 ou 7151).
- carolini.silveira@fiesc.com.br
- marcos@fiesc.com.br

---

### Parcela ja liquidada — desconto integrado duas vezes

**Mensagem:**
```
Parcela ja foi liquidada. Verifique o valor da movimentacao, pois o documento foi baixado integralmente e restou um saldo de XX,XX
```

**Como diagnosticar:**
Pegar tres valores para analise:
- Valor da cobranca original (sem desconto)
- Valor da baixa de desconto
- Valor da baixa tesouraria

Se o calculo `cobranca - desconto = tesouraria` nao fechar, e porque o desconto foi integrado duas vezes no Benner. O SGN enviou apenas uma vez — o problema e do lado do Benner.

**O que fazer:**
1. Confirmar a duplicidade com os valores acima
2. Solicitar ao Alexandre (grupo de integracoes) que exclua o desconto duplicado no Benner
3. Apos a exclusao, reprocessar a baixa tesouraria
4. Abrir chamado na GETIC para investigacao da causa raiz — pois o desconto foi enviado uma vez e integrou duas

---

### Erro de validacao de campos — FINOBJ ABATIMENTOS

**Mensagem:**
```
FINOBJ - Inclusao de documento: DC: Erro na definicao de campos: ABATIMENTOS:; ABRANGENCIA:; ACRESCIMOCOMERCIAL...
```

**O que fazer:**
1. Tentar reenviar uma vez
2. Se o erro persistir, abrir chamado — provavelmente GETIC, possivelmente GECON dependendo da avaliacao

---

### Periodo de abertura financeiro fechado para CRE

**Mensagem:**
```
FINOBJ - Validacao do documento: Documento nao esta dentro do periodo de abertura do financeiro para CRE!
```

**Encaminhar para:** GECON — e uma configuracao de periodo financeiro que precisa ser ajustada pela area.

---

### Orgao emissor invalido no cadastro de pessoa

**Situacao:** Erro indicando problema no orgao emissor do documento de identidade da pessoa.

**O que fazer:**
Solicitar que a propria unidade corrija o orgao emissor no cadastro da pessoa. Nao e um erro de integracao — e um dado incorreto no cadastro que precisa ser corrigido na origem.

---

## Erros que exigem abertura de tarefa para o Squad de Integracoes

---

### Erro ao abrir tela de erro de envio em Matricula

**Situacao:** A aba Matricula apresenta erro ao tentar abrir registros com erro de envio. Outras abas funcionam normalmente.

**O que fazer:**
Abrir tarefa para o Squad de Integracoes incluindo o link de trace do Glowroot se disponivel.

---

### Baixa sem retorno — nao permite reenvio

**Situacao:** A baixa ficou sem retorno do Benner e o sistema nao permite reprocessar.

**O que fazer:**
Abrir tarefa para o Squad de Integracoes. Nao tente aprovar manualmente sem orientacao — pode gerar inconsistencia.

---

### RPC com erro ao reprocessar — sem resposta no dashboard

**Situacao:** Clica em reenviar no RPC, mas nada acontece. O registro continua sem protocolo novo.

**O que fazer:**
Abrir tarefa para o Squad de Integracoes.

---

### Erro de rateio em RPC — informacao errada no payload

**Mensagem:**
```
Nao foi possivel integrar a entidade K9_FN_DOCUMENTOITENS. Erro nos valores de campos adicionais...
```

**O que fazer:**
Abrir tarefa para o Squad de Integracoes. Pode ser erro de calculo no RPC ou problema de integracao — o time avalia caso a caso. Verificar se ha chamado aberto para o mesmo problema antes de abrir um novo.

---

### Produto duplicado na tabela PD_PRODUTOS

**Mensagem:**
```
Foram encontrados mais de um registro na tabela PD_PRODUTOS, campo de busca: PRODUTO valor da busca: XXXX.X
```

**O que fazer:**
Verificar com o responsavel pelo chamado aberto para esse erro (no momento do registro desta base, o chamado estava com o Paolo). Abrir tarefa se nao houver chamado em andamento.

---

## Erros de infra — acionar GETIC com urgencia

---

### Out of Memory nas integracoes

**Mensagem:**
```
Out of memory
```
ou
```
ESB-0004 - Excedeu o tempo limite de 1800000 milissegundos
```

**O que fazer:**
1. Verificar se o problema afeta multiplas abas ao mesmo tempo
2. Registrar os casos afetados e os horarios
3. Acionar o Renan ou abrir chamado na GETIC com urgencia
4. Nao tentar reprocessar em massa durante o incidente

Esse erro e recorrente — ao abrir o chamado, mencionar os chamados anteriores para pressionar por solucao definitiva. Ver [Problemas recorrentes](problemas.md).

---

### Benner demorando mais de 1 hora para integrar

**Situacao:** Registros enviados ficam aguardando retorno por mais de uma hora sem resposta.

**O que fazer:**
Passar print dos casos para o Renan ou acionar diretamente no grupo de integracoes. Nao e normal aguardar mais de uma hora — indica problema no Benner.

---

### Benner instavel — integracao lenta no geral

**Situacao:** O Benner esta respondendo mas muito lentamente, causando acumulo de casos pendentes.

**O que fazer:**
Avisar no grupo de integracoes com print da fila atual. O Renan repassa para a GETIC. Aguardar normalizacao antes de reprocessar em massa.

---

*Conteudo baseado em casos reais operados pelo suporte em conjunto com o Squad de Integracoes*
