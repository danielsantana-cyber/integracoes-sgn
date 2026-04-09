# 🔗 Benner — Erros de Integração

> Problemas relacionados à integração com o ERP Benner: faturamento, cobranças, pessoas e documentos financeiros.

---

## 🔹 Conta financeira não configurada no Benner

**📌 Contexto**
Ocorre ao tentar integrar lançamentos financeiros. O sistema retorna erro de validação de contas financeiras.

**Mensagem de erro:**
```
Erro interno: Erro ao integrar lançamento: FINOBJ - Validação das contas financeiras: A conta deve ser preenchida!
```

**🧠 Causa**
O CR (Centro de Responsabilidade) não está com conta financeira configurada no Benner.

**✅ Solução**
1. Identificar o CR associado ao lançamento com erro.
2. Verificar no Benner se o CR possui conta financeira configurada.
3. Acionar a GECON para realizar a configuração:
   - `carolini.silveira@fiesc.com.br`
   - `marcos@fiesc.com.br`
4. Após configuração, reprocessar o lançamento.

**⚠️ Atenção**
Não tente alterar manualmente a configuração do CR sem envolvimento da GECON. Alterações incorretas podem impactar outros lançamentos vinculados.

**👨‍💻 Escalonamento**
Acionar **GECON** diretamente. Não há resolução técnica pela equipe de suporte sem a configuração realizada pela área financeira.

---

## 🔹 Divergência de arquivos entre servidores Benner (cvc-complex-type)

**📌 Contexto**
Ocorre durante integração de faturamento RPC no Benner. O sistema retorna erro de validação de conteúdo XML.

**Mensagem de erro:**
```
cvc-complex-type.2.4.d: Invalid content was found starting with element 'codigoCentroResponsabilidade'.
```

**🧠 Causa**
Erro no Benner causado por divergência de arquivos entre os servidores da aplicação.

**✅ Solução**
1. Registrar o erro com a mensagem completa.
2. Acionar a **GETIC** abrindo chamado com referência ao padrão estabelecido.
3. Monitorar resolução via chamado.

**⚠️ Atenção**
Este erro não possui resolução pela equipe de suporte ou GECON. É um problema de infraestrutura do Benner que requer intervenção da GETIC.

**👨‍💻 Escalonamento**
Abrir chamado na **GETIC** — modelo de referência: `TI0232055 / TI0271054 - Erro ao integrar faturamento RPC no Benner`.

---

## 🔹 Cadastro incompleto de filial no Benner

**📌 Contexto**
Ocorre ao tentar faturar uma filial específica com determinado produto. O sistema bloqueia a operação por inconsistência cadastral.

**Mensagem de erro:**
```
Impossível faturar esta filial com o produto informado. É necessário concluir o cadastro no Benner (vínculos, CNAE, etc) entre o produto e filial ou, a filial ainda não está habilitada a faturar.
```

**🧠 Causa**
A filial possui cadastro incompleto no Benner. Vínculos, CNAE ou configurações de habilitação de faturamento estão ausentes ou incorretos.

**✅ Solução**
1. Identificar a filial e o produto que geraram o erro.
2. Não tentar contornar o bloqueio pelo sistema.
3. Acionar a GECON para regularização do cadastro:
   - `otavio.l.santos@fiesc.com.br`
   - `jackson.faria@fiesc.com.br`
   - `silvana.tkaczuk@fiesc.com.br`
4. Após regularização confirmada pela GECON, reprocessar o faturamento.

**⚠️ Atenção**
A mensagem orienta contato com a "área de negócio responsável pelos cadastros de produto e filial". Essa área é a **GECON**.

**👨‍💻 Escalonamento**
Acionar **GECON** com identificação da filial e produto envolvidos.

---

## 🔹 Centro de custo inválido para a filial

**📌 Contexto**
Ocorre ao integrar lançamentos no Benner. O sistema não reconhece o centro de custo informado como válido para a filial em questão.

**Mensagem de erro:**
```
Erro interno: Erro ao integrar lançamento: FINOBJ - Validação dos centros de custo: Centro de custo inválido para a filial.
```

**🧠 Causa**
O centro de custo utilizado não está vinculado ou não é permitido para a filial informada no lançamento.

**✅ Solução**
1. Identificar o centro de custo e a filial do lançamento com erro.
2. Acionar a GECON para verificar e corrigir o vínculo:
   - `carolini.silveira@fiesc.com.br`
   - `marcos@fiesc.com.br`
3. Reprocessar após regularização.

**⚠️ Atenção**
Chamado de referência registrado: `TI0232261 - Erro 'Centro de custo inválido' ao integrar documentos com o Benner`.

**👨‍💻 Escalonamento**
Acionar **GECON**. Se não resolvido, abrir chamado na **GETIC** com referência ao TI0232261.

---

## 🔹 Complemento de endereço excede 60 caracteres

**📌 Contexto**
Ocorre ao tentar integrar o cadastro de uma Pessoa Física (PF). O sistema rejeita o cadastro por limite de caracteres no campo Complemento.

**Mensagem de erro:**
```
Erro ao integrar a pessoa: O tamanho máximo do campo "Complemento (COMPLEMENTO)" é 60 caracteres.
```

**🧠 Causa**
O campo "Complemento" no cadastro da PF possui mais de 60 caracteres, ultrapassando o limite aceito pelo Benner.

**✅ Solução**
1. Localizar o cadastro da PF no sistema de origem.
2. Editar o campo Complemento, reduzindo para no máximo 60 caracteres.
3. Reprocessar a integração para que o cadastro seja enviado ao Benner.
4. Após a integração bem-sucedida, editar novamente o cadastro para restaurar o complemento completo (se necessário para registros internos).

**⚠️ Atenção**
A edição temporária é necessária apenas para viabilizar a integração. O dado completo pode ser mantido no sistema de origem após o envio.

**👨‍💻 Escalonamento**
Resolução pela própria equipe de suporte. Não requer acionamento de GECON ou GETIC.

---

## 🔹 Configuração de boleto automático ausente no Benner

**📌 Contexto**
Ocorre ao desbloquear um documento no Benner. O sistema não consegue gerar automaticamente o boleto de cobrança por ausência de configuração.

**Mensagem de erro:**
```
Erro interno: DOCOBJ - Problema ocorrido ao desbloquear o documento: TFINANCEIROAposConfirmacaoDocumento - Não foi possível realizar a geração automática de boleto de cobrança. As configurações do boleto automático não foram encontradas. Verifique a operação 7151, na carga "Configuração boletos automáticos", no cadastro de Operações.
```

**🧠 Causa**
A unidade não possui as configurações de boleto automático cadastradas no Benner (operação 7151).

**✅ Solução**
1. Identificar a unidade (filial) associada ao documento.
2. Acionar a GECON para configurar o boleto automático no Benner:
   - `carolini.silveira@fiesc.com.br`
   - `marcos@fiesc.com.br`
3. Após configuração, reprocessar o desbloqueio do documento.

**⚠️ Atenção**
O erro menciona especificamente a operação **7151** e a carga **"Configuração boletos automáticos"**. Incluir essa informação ao acionar a GECON acelera a resolução.

**👨‍💻 Escalonamento**
Acionar **GECON**. Configuração requer acesso ao cadastro de operações do Benner.

---

## 🔹 Duplicidade de CNPJ/CPF — Impossibilidade de integrar cobrança

**📌 Contexto**
Ocorre ao tentar integrar uma cobrança. O sistema identifica mais de um registro de pessoa com o mesmo CNPJ/CPF no Benner.

**Mensagem de erro:**
```
Impossibilidade de integrar cobrança - Existe mais uma pessoa com este Cnpj/Cpf cadastrado
```

**🧠 Causa**
Há duplicidade de cadastro de pessoa (mesmo CNPJ/CPF) no Benner, impedindo a vinculação correta da cobrança.

**✅ Solução**
1. Identificar o CNPJ/CPF com cadastro duplicado.
2. Abrir chamado na GETIC referenciando o padrão estabelecido.
3. A GETIC realizará a deduplicação ou merge do cadastro.

**⚠️ Atenção**
Chamado de referência: `TI0294206 / TI0294080 - Impossibilidade de integrar cobrança - Existe mais uma pessoa com este Cnpj/Cpf cadastrado`.

**👨‍💻 Escalonamento**
Abrir chamado na **GETIC**. Inclui também o caso de pessoa integrada mas Benner não reconhecendo (`TI0291818`).

---

## 🔹 Cobrança sem integração com o Benner (unidade não integrada)

**📌 Contexto**
Ocorre ao tentar realizar a baixa de tesouraria. O serviço retorna status diferente de 200 (Bad Request).

**Mensagem de erro:**
```
Erro: serviço de baixa tesouraria retornou status diferente de 200[OK]: Bad Request. Mensagem: A unidade da cobrança não está integrada com o Benner. id cobrança 4.401.485 - id unidade 394
```

**🧠 Causa**
A unidade referenciada na cobrança não está integrada com o Benner, impedindo o processamento da baixa.

**✅ Solução**
1. Identificar o ID da cobrança e o ID da unidade no erro.
2. Verificar com a GECON se a unidade deveria estar integrada ao Benner.
3. Se confirmado, acionar a GETIC para configurar a integração da unidade.

**⚠️ Atenção**
Este erro pode indicar problema de configuração permanente da unidade. Verificar se outras cobranças da mesma unidade apresentam o mesmo comportamento.

**👨‍💻 Escalonamento**
Acionar **GECON** para confirmar se unidade deve ser integrada. Após confirmação, escalar para **GETIC**.

---

## 🔹 Registro não encontrado na tabela DependenciasPAISES (ESTADONASCIMENTO)

**📌 Contexto**
Ocorre ao integrar o cadastro de uma pessoa. O Benner não encontra o estado de nascimento na tabela de dependências de países.

**Mensagem de erro:**
```
Erro ao integrar a pessoa: Não foi encontrado o registro na tabela DependenciasPAISES, campo de busca: ESTADONASCIMENTO valor da busca: SC
```

**🧠 Causa**
O estado de nascimento informado (ex: SC) não está mapeado na tabela `DependenciasPAISES` do Benner. Trata-se de um problema recorrente de configuração na base do ERP.

**✅ Solução**
1. Registrar o estado e o CNPJ/CPF da pessoa com erro.
2. Abrir chamado na GETIC com referência ao padrão estabelecido.
3. A GETIC realizará o mapeamento na tabela de dependências.

**⚠️ Atenção**
Este é um **erro recorrente** com múltiplos chamados registrados. Novos casos devem sempre ser registrados como chamados separados para controle de frequência.

Chamados de referência: `TI0302721 / TI0305920 / TI0306713 / TI0310502 / TI0311474 / TI0312092 / TI0312689`.

**👨‍💻 Escalonamento**
Abrir chamado na **GETIC** com o padrão: `Impossibilidade de integrar cobrança - Não foi encontrado o registro na tabela Dependencias`.

---

## 🔹 Acesso negado — Resource Forbidden (WSO2)

**📌 Contexto**
Ocorre ao tentar acessar um endpoint da API. O sistema retorna erro de autorização via WSO2 (gateway de APIs).

**Mensagem de erro:**
```
Resource forbidden. User is NOT authorized to access the Resource. API Subscription validation failed.
```

**🧠 Causa**
O usuário ou aplicação configurada no WSO2 não possui permissão para acessar o endpoint solicitado. Falta de subscription ou permissão insuficiente.

**✅ Solução**
1. Identificar o endpoint que gerou o erro.
2. Verificar qual usuário/aplicação está sendo utilizado na chamada.
3. Acionar o **DevOps** para revisar e corrigir as permissões no WSO2.

**⚠️ Atenção**
Não tentar contornar o controle de acesso. A liberação deve ser feita de forma controlada pelo DevOps.

Chamado de referência: `TI0308217 - Impossibilidade alterar a forma de pagamento - Resource forbidden`.

**👨‍💻 Escalonamento**
Acionar **DevOps** para configuração de permissão no WSO2.

---

## 🔹 Parcela já liquidada — Impossibilidade de integrar cobrança

**📌 Contexto**
Ocorre ao tentar integrar uma cobrança. O documento já foi baixado integralmente no Benner, com saldo residual.

**Mensagem de erro:**
```
Parcela já foi liquidada. Verifique o valor da movimentação, pois o documento foi baixado integralmente e restou um saldo de 12,80.
```

**🧠 Causa**
A parcela já foi liquidada no Benner. Pode haver divergência de valores entre os sistemas, gerando saldo residual.

**✅ Solução**
1. Verificar o valor da movimentação e o saldo residual indicado no erro.
2. Acionar o **Alexandre** no grupo de integrações para análise.
3. Após ajuste realizado pelo Alexandre, reprocessar a integração.

**⚠️ Atenção**
O ajuste deve ser feito antes de reprocessar. Reprocessar sem ajuste pode gerar duplicidade ou inconsistência financeira.

Chamado de referência: `TI0310505 - Impossibilidade de integrar cobrança - Parcela já foi liquidada`.

**👨‍💻 Escalonamento**
Contatar **Alexandre** no grupo de integrações. Se necessário, abrir chamado na GETIC com referência ao TI0310505.

---

## 🔹 Erro ao integrar documento financeiro — Value cannot be null (source)

**📌 Contexto**
Ocorre ao tentar integrar um documento financeiro. O sistema retorna erro genérico de parâmetro nulo.

**Mensagem de erro:**
```
Erro ao integrar documento financeiro: Value cannot be null. Parameter name: source
```

**🧠 Causa**
Parâmetro obrigatório não preenchido ou nulo na origem da integração. Causa específica ainda não mapeada — requer investigação caso a caso.

**✅ Solução**
1. Identificar o documento financeiro e os dados da integração.
2. Verificar se todos os campos obrigatórios estão preenchidos na origem.
3. Registrar o caso com dados completos e acionar suporte técnico.

**⚠️ Atenção**
Este erro não possui causa confirmada na base atual. Registrar chamado com o máximo de detalhes para apoiar diagnóstico.

Chamado de referência: `TI0293893 - Erro ao integrar faturamento - Falha ao autorizar operação. Value cannot be null`.

**👨‍💻 Escalonamento**
Abrir chamado na **GETIC** com dados completos do documento e da integração.

---

## 🔹 Out of Memory — Integrações com o Benner

**📌 Contexto**
Ocorre durante integrações com o Benner. O serviço retorna erro de falta de memória, interrompendo o processamento.

**Mensagem de erro:**
```
Erro 'Out of memory' nas integrações com o Benner
```
ou
```
ESB-0004 - Excedeu o tempo limite de 1800000 milissegundos para integrar com o ERP.
```

**🧠 Causa**
Problema de infraestrutura no servidor do Benner. Consumo excessivo de memória ou timeout do ESB (Enterprise Service Bus).

**✅ Solução**
1. Registrar o horário e o contexto da integração com erro.
2. Verificar se outras integrações estão falhando simultaneamente (indica problema geral).
3. Abrir chamado na GETIC imediatamente.

**⚠️ Atenção**
Este é um **erro recorrente** com histórico confirmado. Chamados de referência: `TI0252965 / TI0269739 / TI0281296 / TI0294054 / TI0338268`.

**👨‍💻 Escalonamento**
Abrir chamado na **GETIC** com urgência, indicando o padrão recorrente e referenciando chamados anteriores.

---

## 🔹 Documento duplicado no primeiro envio (Foi encontrado o documento...)

**📌 Contexto**
Ocorre no primeiro envio de um documento ao Benner. O sistema retorna erro indicando que o documento já existe, mesmo sendo a primeira tentativa.

**Mensagem de erro:**
```
Foi encontrado o documento ... no primeiro envio
```

**🧠 Causa**
Causa ainda em investigação pela GETIC. Pode estar relacionada a reprocessamentos automáticos ou duplicidade de protocolo.

**✅ Solução**
1. Confirmar que é realmente o primeiro envio do documento.
2. Registrar o identificador do documento e os dados da integração.
3. Abrir chamado na GETIC.

**⚠️ Atenção**
Chamados de referência: `TI0287291 (2025-08-15, Em aberto) / TI0332905 (2026-03-12, Em aberto)`. Problema ainda sem resolução definitiva.

**👨‍💻 Escalonamento**
Abrir chamado na **GETIC** referenciando os chamados anteriores TI0287291 e TI0332905.
