# Integrações — Erros e Tratativas

Esta página cobre erros que aparecem no **dashboard de integração do SGN** durante o processamento de cobranças, baixas e envios. São erros que o suporte visualiza diretamente na tela e pode agir sem precisar entrar no Benner.

Antes de qualquer ação, abra o protocolo do registro para ver o histórico de envios. E antes de escalar, verifique [Chamados abertos](chamados.md).

---

## Erros resolvidos pelo próprio suporte

---

### Documento já existe no sistema

**Mensagem:**
```
Erro interno: Já existe um documento com essas informações cadastrado no sistema
```

**O que significa:** O documento foi enviado duas vezes. O primeiro envio deu certo, o segundo gerou esse erro. Não precisa reenviar.

**O que fazer:**
1. Abrir o protocolo e confirmar que o envio anterior foi sucesso
2. Clicar em **Aprovar retorno**
3. Justificativa: `Já foi integrado com sucesso`

---

### Documento já integrado — NOSSO NÚMERO

**Mensagem:**
```
Foi encontrado o documento... com a AP: XXXXXXXXX para o NOSSONUMERO: XXXXXXXXXXXXX. Verifique.
```

**O que significa:** O Benner identificou que o documento já existe pelo número de boleto. Geralmente o primeiro envio funcionou.

**O que fazer:**
1. Verificar no protocolo se houve envio anterior com sucesso
2. Se sim: **Aprovar retorno** — justificativa: `Já foi integrado com sucesso`
3. Se for o **primeiro envio** e o erro ainda aparecer: esse é um comportamento em investigação — consulte [Chamados abertos](chamados.md) (TI0287291 e TI0332905)

---

### Baixa já processada anteriormente

**Mensagem:**
```
A requisição de baixa já foi processada anteriormente
```
ou
```
A requisição de baixa de número XXXXXXXXXX, já foi processada anteriormente.
```

**O que fazer:**
1. Verificar no Benner se a baixa já está registrada com valor correto
2. Se estiver: **Aprovar retorno** — justificativa: `Já foi integrado com sucesso`

---

### CPF/CNPJ duplicado — reenvio resolve

**Mensagem:**
```
Erro interno: Existe mais de uma pessoa com este Cnpj/Cpf cadastrado no sistema.
```

**O que fazer:**
- Nome em **negrito** na tela: usar **Forçar reenvio**
- Nome sem negrito: usar **Reenviar selecionados**

Na maioria dos casos o reenvio resolve. Se o erro persistir após reenvio, encaminhar para GETIC.

---

### Invalid variant operation

**Mensagem:**
```
Erro ao integrar documento... Invalid variant operation
```

**O que fazer:**
- Nome em **negrito**: **Forçar reenvio**
- Nome sem negrito: **Reenviar selecionados**

---

### Pessoa em fila — não reenviar

**Mensagem:**
```
O cliente de documento XXX.XXX.XXX-XX não está integrado com a Aplicação Benner. O cliente já está sendo enviado para a fila de integração e não será enviado novamente até que a integração tenha um retorno.
```

**O que significa:** O sistema já está tentando integrar a pessoa. Forçar um reenvio agora vai gerar duplicidade.

**O que fazer:** Aguardar. Monitorar o protocolo da integração de pessoa até retornar.

---

### Pessoa não encontrada no Benner — verificar integração

**Mensagem:**
```
Erro interno: Não existe uma pessoa com este Cnpj/Cpf cadastrada no sistema.
```

**O que fazer:**
1. Acessar o [Dashboard de Integração de Pessoa](https://sgn.sesisenai.org.br/pages/administracao/integracao/pessoa/integracao-pessoa.html)
2. Buscar pelo CPF ou nome — Aplicação: Benner / Situação: Todas
3. Verificar o último protocolo
4. Se a pessoa não estiver integrada: abrir o cadastro dela no SGN e **salvar** — isso dispara o reenvio
5. Se o erro persistir após o reenvio, abrir chamado na GETIC

> Cadastros com data de envio muito antiga (ex: 2018) podem precisar de reenvio mesmo sem erro visível.

---

### Complemento de endereço acima de 60 caracteres

**Mensagem:**
```
O tamanho máximo do campo "Complemento (COMPLEMENTO)" é 60 caracteres
```

**O que fazer:**
1. Editar o cadastro e reduzir o complemento para até 60 caracteres
2. Reprocessar a integração
3. Após integrar com sucesso, restaurar o complemento completo no cadastro se necessário

Resolvido pelo suporte, sem escalonamento.

---

## Erros de faturamento — escalonar para GECON

Esses erros indicam problemas de configuração financeira ou cadastral que dependem da área de negócio.

---

### Conta financeira não preenchida

**Mensagem:**
```
FINOBJ - Validação das contas financeiras: A conta deve ser preenchida!
```

**Causa:** O CR (Centro de Responsabilidade) não tem conta financeira configurada no Benner.

**Encaminhar para:** GECON — informar o CR com problema
- carolini.silveira@fiesc.com.br / marcos@fiesc.com.br

---

### Centro de custo inválido para a filial

**Mensagem:**
```
FINOBJ - Validação dos centros de custo: Centro de custo inválido para a filial
```

**O que fazer:** Abrir o protocolo de envio, localizar o CR no campo de rateio e informar ao GECON com a filial.

**Encaminhar para:** GECON
- carolini.silveira@fiesc.com.br / marcos@fiesc.com.br

---

### Filial não habilitada para faturar

**Mensagem:**
```
Impossível faturar esta filial com o produto informado. É necessário concluir o cadastro no Benner (vínculos, CNAE, etc)
```

**O que fazer:**
1. Verificar nos protocolos: Entidade, Unidade, Filial e Produto
2. Montar e-mail para GECON no formato:
```
Entidade - Unidade - Filial - Produto
SESI - Lages II - 03.777.341/0478-04 - 1856.1
```
Todos os casos podem ir em um único e-mail, separados por linha.

**Encaminhar para:** GECON
- otavio.l.santos@fiesc.com.br / jackson.faria@fiesc.com.br / silvana.tkaczuk@fiesc.com.br

---

### Boleto automático não configurado

**Mensagem:**
```
As configurações do boleto automático não foram encontradas. Verifique a operação 7151.
```

**Encaminhar para:** GECON — informar a operação mencionada no erro (2011 ou 7151)
- carolini.silveira@fiesc.com.br / marcos@fiesc.com.br

---

### Parcela já liquidada — desconto duplicado

**Mensagem:**
```
Parcela já foi liquidada. Verifique o valor da movimentação, pois o documento foi baixado integralmente e restou um saldo de XX,XX
```

**Como diagnosticar:** Pegar três valores:
- Valor da cobrança original
- Valor da baixa de desconto
- Valor da baixa tesouraria

Se `cobrança - desconto ≠ tesouraria`, o desconto foi integrado duas vezes no Benner. O SGN enviou corretamente — o problema é do lado do Benner.

**O que fazer:**
1. Confirmar os valores
2. Solicitar ao **Alexandre** (grupo de integrações) a exclusão do desconto duplicado
3. Reprocessar a baixa tesouraria após exclusão
4. Abrir chamado na GETIC para investigar a causa raiz

---

### Período financeiro fechado para CRE

**Mensagem:**
```
FINOBJ - Validação do documento: Documento não está dentro do período de abertura do financeiro para CRE!
```

**Encaminhar para:** GECON — é configuração de período financeiro.

---

## Erros técnicos — escalonar para GETIC

---

### Tabela DependenciasPAISES — estado de nascimento

**Mensagem:**
```
Não foi encontrado o registro na tabela DependenciasPAISES, campo de busca: ESTADONASCIMENTO
```

**Encaminhar para:** GETIC. É o erro com maior volume da base — ao abrir, referencie os chamados anteriores para demonstrar reincidência. Ver [Problemas recorrentes](problemas.md).

---

### Out of Memory / Timeout ESB

**Mensagem:**
```
Out of memory
```
ou
```
ESB-0004 - Excedeu o tempo limite de 1800000 milissegundos
```

**O que fazer:**
1. Verificar se o problema afeta múltiplas abas simultaneamente
2. Não reprocessar em massa durante o incidente
3. Avisar o Renan no grupo de integrações e abrir chamado na GETIC com urgência

Erro recorrente — referenciar: TI0252965, TI0269739, TI0281296, TI0338268.

---

### Divergência XML entre servidores

**Mensagem:**
```
cvc-complex-type.2.4.d: Invalid content was found starting with element 'codigoCentroResponsabilidade'
```

**Encaminhar para:** GETIC — referência: TI0232055, TI0271054

---

### Unidade da cobrança não integrada ao Benner

**Mensagem:**
```
A unidade da cobrança não está integrada com o Benner. id cobrança XXXXXXX - id unidade XXX
```

**O que fazer:** Anotar os IDs e consultar a página [Unidade não integrada](unidade-nao-integrada.md) para o processo completo de resolução.

---

### Value cannot be null

**Mensagem:**
```
Falha ao autorizar operação. Value cannot be null. Parameter name: key
```

**O que fazer:** Tentar reenviar uma vez. Se persistir, abrir chamado na GETIC — referência: TI0293893.

---

## Erros de permissão — escalonar para DevOps

---

### Resource forbidden — WSO2

**Mensagem:**
```
Resource forbidden. User is NOT authorized to access the Resource. API Subscription validation failed.
```

**Encaminhar para:** DevOps — informar nome da API, aplicação e ambiente (produção ou homologação).

---

## Erros que exigem tarefa para o Squad de Integrações

---

### Erro ao abrir aba Matrícula — erro de envio

**Situação:** A aba Matrícula trava ao tentar abrir registros com erro de envio. Outras abas funcionam normalmente.

**O que fazer:** Abrir tarefa para o Squad de Integrações com link de trace do Glowroot se disponível.

---

### Baixa sem retorno — não permite reprocessar

**Situação:** A baixa ficou sem retorno do Benner e o sistema bloqueia o reenvio.

**O que fazer:** Abrir tarefa para o Squad de Integrações. Não aprovar manualmente sem orientação.

---

### RPC sem resposta ao reenviar

**Situação:** Clica em reenviar no RPC, nada acontece, nenhum protocolo novo é criado.

**O que fazer:** Abrir tarefa para o Squad de Integrações.

---

### Erro de rateio em RPC

**Mensagem:**
```
Não foi possível integrar a entidade K9_FN_DOCUMENTOITENS. Erro nos valores de campos adicionais...
```

**O que fazer:** Abrir tarefa para o Squad de Integrações. Pode ser erro de cálculo no RPC ou problema de integração — o time avalia. Verificar se há chamado aberto antes de abrir um novo.

---

*Última revisão: Abril 2026*
