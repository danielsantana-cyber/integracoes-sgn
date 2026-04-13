# Benner — Erros e Tratativas

Esta página cobre erros que exigem conhecimento do **ERP Benner** — configurações, cadastros, estrutura financeira e comportamentos internos do sistema. São erros onde a resolução depende de algo que precisa ser ajustado dentro do Benner, não no SGN.

Antes de escalar, verifique [Chamados abertos](chamados.md).

---

## Como usar esta página

1. Identifique a mensagem de erro
2. Localize o caso abaixo
3. Execute a tratativa ou escalone conforme indicado
4. Se o erro apareceu no dashboard do SGN e não envolve configuração do Benner, consulte [Integrações](integracoes.md)

---

## Erros de cadastro de pessoa no Benner

---

### CPF/CNPJ duplicado — registros no Benner

**Mensagem:**
```
Impossibilidade de integrar cobrança - Existe mais de uma pessoa com este Cnpj/Cpf cadastrado
```
ou
```
Já existe uma pessoa com este CNPJ/CPF
```

**Causa:** Há mais de um cadastro de pessoa com o mesmo CPF/CNPJ dentro do Benner. O problema está no banco de dados do ERP, não no SGN.

**Encaminhar para:** GETIC para deduplicação
Referência: TI0294080, TI0294107

---

### Pessoa integrada mas Benner não localiza

**Mensagem:**
```
Não existe uma pessoa com este Cnpj/Cpf
```

**Causa:** A pessoa foi enviada com sucesso pelo SGN mas o Benner não está retornando o registro na consulta. Pode ser delay interno ou índice desatualizado no ERP.

**O que fazer:**
1. Verificar no protocolo de integração de pessoa se o último envio foi sucesso
2. Se foi sucesso mas o erro persiste, encaminhar para GETIC

**Encaminhar para:** GETIC — referência: TI0291818

---

### Tabela DependenciasPAISES — estado de nascimento

**Mensagem:**
```
Erro ao integrar a pessoa: Não foi encontrado o registro na tabela DependenciasPAISES, campo de busca: ESTADONASCIMENTO valor da busca: SC
```

**Causa:** O Benner não tem o estado de nascimento mapeado na sua tabela interna de dependências de países. É uma lacuna de configuração do próprio ERP — o SGN enviou o dado correto.

**Encaminhar para:** GETIC a cada novo caso. Mencionar chamados anteriores para pressionar por solução estrutural — as correções pontuais anteriores não eliminaram o problema.

Ver histórico completo em [Problemas recorrentes](problemas.md).

---

### dataNascimento duplicado no XML

**Mensagem:**
```
cvc-complex-type.2.4.e: 'dataNascimento' can occur a maximum of '3' times
```

**Causa:** O XML gerado para integração contém o campo `dataNascimento` repetido além do limite do schema XSD do Benner.

**O que fazer:**
1. Abrir o protocolo de envio e inspecionar o payload
2. Identificar de onde vêm as ocorrências extras do campo
3. Se identificado, corrigir na origem e reprocessar
4. Se não identificado, abrir tarefa para o Squad de Integrações

Referência: TI0294162

---

### Integração de pessoa sem retorno

**Situação:** O SGN envia a integração mas não recebe resposta do Benner — sem erro, sem sucesso.

**O que fazer:**
1. Aguardar alguns minutos e verificar se a pessoa integrou
2. Se não integrou, tentar reenviar uma vez (abrir o cadastro da pessoa no SGN e salvar)
3. Se o comportamento persistir, abrir chamado na GETIC

**Encaminhar para:** GETIC — referência: TI0294149

---

### Órgão emissor inválido no cadastro

**Situação:** Erro indicando problema no órgão emissor do documento de identidade da pessoa.

**Causa:** Dado incorreto no cadastro — não é erro de integração.

**O que fazer:** Solicitar que a própria **unidade** corrija o órgão emissor no cadastro da pessoa. Não é tratado pelo suporte de integrações nem pelo GECON — é dado cadastral da unidade.

---

## Erros de configuração financeira no Benner

---

### Conta financeira não configurada no CR

**Mensagem:**
```
FINOBJ - Validação das contas financeiras: A conta deve ser preenchida!
```

**Causa:** O CR (Centro de Responsabilidade) do lançamento não tem conta financeira configurada no Benner. Configuração feita pela área financeira.

**Encaminhar para:** GECON — informar o CR com problema
- carolini.silveira@fiesc.com.br / marcos@fiesc.com.br

---

### Centro de custo inválido para a filial

**Mensagem:**
```
FINOBJ - Validação dos centros de custo: Centro de custo inválido para a filial
```

**Causa:** O centro de custo não está vinculado à filial no Benner. Configuração da área financeira.

**O que fazer:** Abrir o protocolo, localizar o CR no campo de rateio e informar ao GECON junto com a filial.

**Encaminhar para:** GECON
- carolini.silveira@fiesc.com.br / marcos@fiesc.com.br

---

### Filial com cadastro incompleto no Benner

**Mensagem:**
```
Impossível faturar esta filial com o produto informado. É necessário concluir o cadastro no Benner (vínculos, CNAE, etc)
```

**Causa:** A filial não tem vínculos, CNAE ou habilitação de faturamento concluídos no Benner.

**O que fazer:**
Montar e-mail para GECON com a relação de casos no formato:
```
Entidade - Unidade - Filial - Produto
SESI - Lages II - 03.777.341/0478-04 - 1856.1
```
Todos os casos podem ir em um único e-mail.

**Encaminhar para:** GECON
- otavio.l.santos@fiesc.com.br / jackson.faria@fiesc.com.br / silvana.tkaczuk@fiesc.com.br

---

### Configuração de boleto automático ausente

**Mensagem:**
```
Não foi possível realizar a geração automática de boleto de cobrança. As configurações do boleto automático não foram encontradas. Verifique a operação 7151.
```

**Causa:** A unidade não tem as configurações de boleto automático cadastradas no Benner (operação 7151).

**Encaminhar para:** GECON — informar a operação mencionada no erro (2011 ou 7151)
- carolini.silveira@fiesc.com.br / marcos@fiesc.com.br

---

### Parcela já liquidada no Benner

**Mensagem:**
```
Parcela já foi liquidada. O documento foi baixado integralmente e restou um saldo de X,XX
```

**Causa mais comum:** O desconto foi integrado duas vezes dentro do Benner. O SGN enviou apenas uma vez — o problema é do ERP.

**Como confirmar:** `valor cobrança - desconto = valor tesouraria`. Se a conta não fechar, houve duplicidade.

**O que fazer:**
1. Confirmar com os valores acima
2. Solicitar ao **Alexandre** (grupo de integrações) a exclusão do desconto duplicado no Benner
3. Reprocessar após exclusão confirmada
4. Abrir chamado na GETIC para investigar causa raiz

Referência: TI0310505

---

### Cobrança em aberto após cancelamento integrado

**Situação:** O cancelamento foi integrado com sucesso no SGN, mas no Benner a cobrança continua com status em aberto.

**Causa:** O Benner não atualizou o status da cobrança após receber o cancelamento.

**O que fazer:**
1. Confirmar nos logs que a integração do cancelamento foi processada sem erro
2. Verificar o status da cobrança no Benner
3. Se ainda em aberto, abrir chamado com ID da cobrança e data do cancelamento

**Encaminhar para:** GETIC — referência: TI0291504

---

### Desconto de bolsa não refletido no boleto — Banco do Brasil

**Situação:** O desconto configurado no Benner não aparece no boleto gerado pela integração com o Banco do Brasil.

**O que fazer:**
1. Confirmar o desconto no Benner
2. Registrar: valor do desconto, número do documento, número do boleto
3. Abrir chamado com as evidências

**Encaminhar para:** GETIC — referência: TI0302257

---

## Erros de infraestrutura do Benner

---

### Out of Memory — servidor do Benner

**Mensagem:**
```
Erro 'Out of memory' nas integrações com o Benner
```
ou
```
ESB-0004 - Excedeu o tempo limite de 1800000 milissegundos para integrar com o ERP
```

**Causa:** Consumo excessivo de memória no servidor do Benner ou timeout do ESB. Não tem resolução pelo suporte.

**O que fazer:**
1. Verificar se múltiplas abas estão falhando ao mesmo tempo
2. Avisar o Renan no grupo de integrações
3. Abrir chamado na GETIC com urgência — não reprocessar em massa durante o incidente

Erro recorrente — referenciar sempre: TI0252965, TI0269739, TI0281296, TI0338268.

---

### Divergência de arquivos XML entre servidores

**Mensagem:**
```
cvc-complex-type.2.4.d: Invalid content was found starting with element 'codigoCentroResponsabilidade'
```

**Causa:** Divergência de arquivos entre os servidores do Benner. Sem resolução pelo suporte.

**Encaminhar para:** GETIC — referência: TI0232055, TI0271054

---

### Value cannot be null — documento financeiro

**Mensagem:**
```
Erro ao integrar documento financeiro: Value cannot be null. Parameter name: source
```

**O que fazer:**
1. Verificar se todos os campos obrigatórios estão preenchidos na origem
2. Tentar reprocessar uma vez
3. Se persistir, abrir chamado com dados completos do documento

**Encaminhar para:** GETIC — referência: TI0293893

---

*Última revisão: Abril 2026*
