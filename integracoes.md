# Integrações — Erros e Tratativas

> 📌 Esta página reúne os principais erros de integração entre SGN, Benner e serviços externos, com orientação direta de tratativa e escalonamento.

---

## 🔴 Erro: CPF/CNPJ duplicado

**Mensagem:**
Erro interno: Existe mais uma pessoa com este Cnpj/Cpf cadastrado no sistema.

**Tratativa:**
- Se o nome estiver em negrito → usar **Forçar Reenvio**
- Caso contrário → clicar em **Reenviar selecionados**

---

## 🔴 Erro: Value cannot be null

**Mensagem:**
Falha ao autorizar operação. Value cannot be null. Parameter name: key

**Tratativa:**
- Tentar reenviar
- Se persistir → abrir chamado

**Direcionamento:**
➡️ Benner

---

## 🔴 Erro: Documento já existe

**Mensagem:**
Erro interno: Já existe um documento com essas informações cadastrado no sistema

**Tratativa:**
- Conferir logs
- Clicar em **Aprovar retorno**
- Justificativa:

Já foi integrado com sucesso


---

## 🔴 Erro: Documento já integrado (NOSSO NÚMERO)

**Mensagem:**
Foi encontrado o documento...

**Tratativa:**
- Conferir dados
- Clicar em **Aprovar retorno**
- Justificativa:

Já foi integrado com sucesso


---

## 🔴 Erro: Baixa já processada

**Mensagem:**
A requisição de baixa já foi processada anteriormente

**Tratativa:**
- Conferir logs
- Aprovar retorno
- Justificativa:

Já foi integrado com sucesso


---

## 🔴 Erro: Invalid variant operation

**Mensagem:**
Erro ao integrar documento... Invalid variant operation

**Tratativa:**
- Se nome em negrito → Forçar reenvio
- Senão → Reenviar selecionados

---

# ⚠️ ERROS BENNER (MAIORIA ESCALONAMENTO)

---

## 🔴 Conta financeira não preenchida

**Erro:**
FINOBJ - A conta deve ser preenchida

**Causa:**
CR sem conta financeira no Benner

**Direcionamento:**
➡️ GECON  
carolini.silveira@fiesc.com.br  
marcos@fiesc.com.br

---

## 🔴 Centro de custo inválido

**Erro:**
Centro de custo inválido para a filial

**Direcionamento:**
➡️ GECON

---

## 🔴 Produto não pode ser faturado

**Erro:**
Filial não habilitada para faturar

**Causa:**
Cadastro incompleto no Benner

**Direcionamento:**
➡️ GECON  
otavio.l.santos@fiesc.com.br  
jackson.faria@fiesc.com.br  
silvana.tkaczuk@fiesc.com.br

---

## 🔴 Complemento maior que 60 caracteres

**Erro:**
Campo complemento excede limite

**Tratativa:**
- Reduzir para até 60 caracteres
- Integrar
- Depois ajustar novamente

---

## 🔴 Boleto automático não configurado

**Erro:**
Configuração de boletos não encontrada

**Direcionamento:**
➡️ GECON

---

# ⚙️ ERROS DE INFRA / SISTEMA

---

## 🔴 Divergência de arquivos / XML inválido

**Erro:**
cvc-complex-type...

**Direcionamento:**
➡️ GETIC  
TI0232055

---

## 🔴 Pessoa não encontrada (DependenciasPAISES)

**Erro:**
Não encontrado ESTADONASCIMENTO

**Direcionamento:**
➡️ GETIC  
TI0302721 / TI0305920

---

## 🔴 Unidade não integrada ao Benner

**Erro:**
Status diferente de 200 / Bad Request

**Direcionamento:**
➡️ GETIC

---

## 🔴 Parcela já liquidada

**Tratativa:**
- Validar com Alexandre (grupo integrações)
- Após ajuste → reprocessar

**Direcionamento:**
➡️ GETIC  
TI0310505

---

# 🔐 ERROS DE PERMISSÃO / API

---

## 🔴 Resource forbidden

**Erro:**
User is NOT authorized

**Causa:**
Permissão no WSO2

**Direcionamento:**
➡️ DevOps

---

# 📌 COMO USAR ESTA PÁGINA

1. Identifique a mensagem de erro
2. Procure pelo erro nesta lista
3. Execute a tratativa
4. Se necessário → escale com base no direcionamento

---

# 🚀 EVOLUÇÃO FUTURA

Esta página deve evoluir para:

- busca por erro
- categorização por sistema
- ranking de erros mais frequentes
- integração com dashboard

---

*Base inicial construída a partir de histórico operacional da equipe*
