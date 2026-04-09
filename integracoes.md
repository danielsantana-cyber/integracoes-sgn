# ⚡ Integrações — Erros e Tratativas

> Problemas relacionados ao fluxo de integração entre sistemas: APIs, ESB, WSO2, MovimentacaoFinanceira e serviços conectados.

---

## 🔹 API Subscription inválida — Acesso ao endpoint negado

**📌 Contexto**
Ocorre quando uma aplicação tenta consumir um endpoint de API. O gateway WSO2 bloqueia a requisição por falha na validação de subscription.

**Mensagem de erro:**
```
Resource forbidden. User is NOT authorized to access the Resource. API Subscription validation failed.
```

**🧠 Causa**
O usuário ou aplicação não possui subscription ativa para a API solicitada no WSO2. Pode ocorrer após criação de nova API, ambiente novo ou expiração de acesso.

**✅ Solução**
1. Identificar qual endpoint está sendo acessado e qual aplicação está fazendo a chamada.
2. Verificar no portal WSO2 se existe subscription ativa para essa combinação app/API.
3. Acionar **DevOps** para criar ou restaurar a subscription.
4. Após liberação, reprocessar as integrações afetadas.

**⚠️ Atenção**
Não tente criar subscriptions sem envolvimento do DevOps. Permissões incorretas podem expor endpoints sensíveis.

**👨‍💻 Escalonamento**
Acionar **DevOps** com: nome da API, nome da aplicação e ambiente (produção/homologação).

---

## 🔹 MovimentacaoFinanceiraV2 — Ambiente de homologação não retorna cobranças

**📌 Contexto**
Ocorre ao consultar cobranças integradas no ambiente de homologação do serviço MovimentacaoFinanceiraV2. A consulta retorna vazio mesmo com cobranças integradas.

**Mensagem de erro:**
```
Ambiente de homologação do MovimentacaoFinanceiraV2 não trazendo cobranças integradas
```

**🧠 Causa**
Problema no ambiente de homologação. Pode ser relacionado a configuração de filtros, base de dados de homologação desatualizada ou falha na sincronização.

**✅ Solução**
1. Confirmar que as cobranças foram integradas com sucesso no ambiente.
2. Testar a consulta com diferentes parâmetros de filtro.
3. Verificar logs da integração para identificar se houve retorno de erro silencioso.
4. Abrir chamado na GETIC se o problema persistir.

**⚠️ Atenção**
Chamado de referência: `TI0290489 - Ambiente de homologação do MovimentacaoFinanceiraV2 não trazendo cobranças integradas` (Em aberto).

**👨‍💻 Escalonamento**
Abrir chamado na **GETIC** com detalhes do ambiente, período de integração e parâmetros da consulta.

---

## 🔹 Filtro flParCancelada não funciona no MovimentacaoFinanceiraV2

**📌 Contexto**
Ocorre ao consultar cobranças usando o filtro `flParCancelada` no serviço MovimentacaoFinanceiraV2. O filtro é ignorado e retorna registros incorretos.

**Mensagem de erro:**
```
Filtro flParCancelada não está funcionando no serviço MovimentacaoFinanceiraV2
```

**🧠 Causa**
Bug no serviço MovimentacaoFinanceiraV2. O parâmetro de filtro não está sendo aplicado corretamente na consulta.

**✅ Solução**
1. Documentar o comportamento esperado vs. comportamento atual.
2. Registrar os parâmetros utilizados na consulta.
3. Abrir chamado na GETIC para correção do bug.

**⚠️ Atenção**
Chamado de referência: `TI0291201 - Filtro flParCancelada não está funcionando no serviço MovimentacaoFinanceiraV2` — **Concluído**. Se o problema reaparecer, referenciar este chamado como reincidência.

**👨‍💻 Escalonamento**
Abrir chamado na **GETIC** como reincidência do TI0291201.

---

## 🔹 Cobrança permanece em aberto após cancelamento integrado

**📌 Contexto**
Ocorre após o cancelamento de uma cobrança ser integrado com sucesso. No Benner, a cobrança continua com status "em aberto" ao invés de refletir o cancelamento.

**Mensagem de erro:**
```
Cobrança permanece em aberto no Benner após integração do cancelamento
```

**🧠 Causa**
Falha na atualização de status no Benner após integração do cancelamento. O processo de integração pode ter sido concluído do lado do sistema de origem, mas o Benner não atualizou o registro.

**✅ Solução**
1. Confirmar que a integração do cancelamento foi processada sem erros no sistema de origem.
2. Verificar no Benner o status atual da cobrança.
3. Se divergente, acionar GETIC para análise e correção manual.

**⚠️ Atenção**
Chamado de referência: `TI0291504 - Cobrança permanece em aberto no Benner após integração do cancelamento` (Em aberto). Caso semelhante: `TI0232988 - Cancelamento de Cobrança: a cobrança não constava no Benner`.

**👨‍💻 Escalonamento**
Abrir chamado na **GETIC** com ID da cobrança, data do cancelamento e evidência do processamento.

---

## 🔹 Timeout ESB — Excedeu tempo limite de integração com ERP

**📌 Contexto**
Ocorre durante integração via ESB (Enterprise Service Bus). A operação é interrompida por exceder o tempo máximo de espera.

**Mensagem de erro:**
```
ESB-0004 - Excedeu o tempo limite de 1800000 milissegundos para integrar com o ERP.
```

**🧠 Causa**
O ESB aguarda resposta do ERP (Benner) por até 30 minutos (1.800.000 ms). Quando o ERP não responde nesse período, a integração é cancelada. Geralmente associado a lentidão ou indisponibilidade do Benner.

**✅ Solução**
1. Verificar se o Benner está operacional no momento do erro.
2. Verificar se outras integrações também estão falhando (indica problema sistêmico).
3. Aguardar normalização e reprocessar.
4. Se persistir, abrir chamado na GETIC.

**⚠️ Atenção**
Chamado de referência: `TI0294054 - Erro ao integrar faturamento - ESB-0004 - Excedeu o tempo limite de 1800000 milissegundos` — Concluído.

**👨‍💻 Escalonamento**
Abrir chamado na **GETIC** se o timeout for recorrente, indicando o horário e os registros afetados.

---

## 🔹 Consulta de Baixas com erros

**📌 Contexto**
Ocorre ao realizar consultas de baixas no sistema. A API retorna erros que impedem a recuperação dos dados.

**Mensagem de erro:**
```
Erros - Consulta de Baixas
```

**🧠 Causa**
Causa específica não mapeada. Requer investigação caso a caso.

**✅ Solução**
1. Registrar os parâmetros utilizados na consulta (período, filtros, unidade).
2. Verificar se o problema é pontual ou afeta todas as consultas de baixas.
3. Abrir chamado na GETIC com os detalhes completos.

**⚠️ Atenção**
Chamado de referência: `TI0300405 - Erros - Consulta de Baixas` (Em aberto).

**👨‍💻 Escalonamento**
Abrir chamado na **GETIC** com logs e parâmetros da consulta.

---

## 🔹 Desconto de bolsa não refletido no boleto bancário (Banco do Brasil)

**📌 Contexto**
Ocorre na integração com o Banco do Brasil. O desconto de bolsa aplicado no sistema não aparece no boleto bancário gerado.

**Mensagem de erro:**
```
[Benner - Integração Banco do Brasil] Desconto de bolsa não refletido no boleto bancário
```

**🧠 Causa**
Divergência na transmissão do campo de desconto entre o Benner e o sistema do Banco do Brasil. Pode ser problema de mapeamento de campo ou timing de transmissão.

**✅ Solução**
1. Confirmar o desconto aplicado no Benner.
2. Verificar o boleto gerado e comparar os valores.
3. Registrar evidências (screenshots do Benner e do boleto).
4. Abrir chamado na GETIC com as evidências.

**⚠️ Atenção**
Chamado de referência: `TI0302257 - [Benner - Integração Banco do Brasil] Desconto de bolsa não refletido no boleto bancário` (Em aberto).

**👨‍💻 Escalonamento**
Abrir chamado na **GETIC** com: valor do desconto, número do documento, número do boleto e evidências.

---

## 🔹 DATABASE_ERROR ao consultar férias de colaborador

**📌 Contexto**
Ocorre ao consultar férias de colaboradores via serviço `servicesinovacao`. O sistema retorna erro de banco de dados.

**Mensagem de erro:**
```
DS Code: DATABASE_ERROR ao consultar férias de colaborador no ambiente servicesinovacao
```

**🧠 Causa**
Erro no banco de dados do ambiente `servicesinovacao`. Pode ser relacionado a query inválida, permissão de acesso ao banco ou dados inconsistentes.

**✅ Solução**
1. Identificar o colaborador e os parâmetros da consulta.
2. Testar a consulta em outro ambiente (homologação/produção) para isolar o problema.
3. Abrir chamado na GETIC com os detalhes técnicos.

**⚠️ Atenção**
Chamado de referência: `TI0305483 - Erro 'DS Code: DATABASE_ERROR' ao consultar férias de colaborador no ambiente servicesinovacao` (Em aberto).

**👨‍💻 Escalonamento**
Abrir chamado na **GETIC** com: ID do colaborador, ambiente, parâmetros da consulta e mensagem de erro completa.

---

## 🔹 Integração de pessoa sem retorno do Benner

**📌 Contexto**
Ocorre ao integrar o cadastro de uma pessoa. O sistema envia a requisição, mas o Benner não retorna resposta (timeout ou silêncio).

**Mensagem de erro:**
```
Integração de pessoa sem retorno do Benner
```

**🧠 Causa**
O Benner recebe a requisição mas não processa ou não retorna a resposta. Pode estar relacionado a lentidão, sobrecarga ou dados que causam loop interno.

**✅ Solução**
1. Aguardar alguns minutos e verificar se a pessoa foi integrada no Benner.
2. Se não integrada, tentar reenviar uma vez.
3. Se persistir, abrir chamado na GETIC.

**⚠️ Atenção**
Chamado de referência: `TI0294149 - Integração de pessoa sem retorno do Benner` (Em aberto).

**👨‍💻 Escalonamento**
Abrir chamado na **GETIC** com: CPF/CNPJ da pessoa, horário da tentativa e logs disponíveis.

---

## 🔹 dataNascimento duplicado — cvc-complex-type.2.4.e

**📌 Contexto**
Ocorre ao integrar o cadastro de uma pessoa. O XML gerado contém o campo `dataNascimento` repetido mais vezes do que o permitido pelo schema.

**Mensagem de erro:**
```
cvc-complex-type.2.4.e: 'dataNascimento' can occur a maximum of '3' times
```

**🧠 Causa**
O XML enviado ao Benner contém o campo `dataNascimento` repetido além do limite máximo de 3 ocorrências definido no schema XSD.

**✅ Solução**
1. Verificar o payload gerado para a pessoa com erro.
2. Identificar de onde vêm as ocorrências extras do campo `dataNascimento`.
3. Corrigir a geração do XML no sistema de origem.
4. Reprocessar a integração.

**⚠️ Atenção**
Chamado de referência: `TI0294162 - Erro ao integrar pessoa - cvc-complex-type.2.4.e: 'dataNascimento' can occur a maximum of '3' times` (Em aberto). Problema de geração de payload — pode requerer correção de código.

**👨‍💻 Escalonamento**
Abrir chamado na **GETIC** se não for possível identificar a origem do campo duplicado no sistema de origem.
