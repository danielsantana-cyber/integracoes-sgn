# 🔁 Problemas Recorrentes — Histórico e Padrões

> Erros que se repetem com frequência, exigem atenção contínua e possuem histórico de chamados registrados.

---

## 🔹 Registro na tabela DependenciasPAISES — Erro recorrente mais crítico

**📌 Contexto**
Este é o erro com **maior frequência de chamados** na base. Ocorre ao integrar pessoas no Benner quando o estado de nascimento não está mapeado na tabela de dependências.

**Mensagem de erro:**
```
Não foi encontrado o registro na tabela DependenciasPAISES, campo de busca: ESTADONASCIMENTO valor da busca: SC
```

**🧠 Causa**
O Benner não possui o estado de nascimento da pessoa mapeado na tabela `DependenciasPAISES`. O problema está na configuração interna do Benner, não nos dados enviados.

**📊 Histórico de Chamados**

| Chamado | Data | Status |
|---|---|---|
| TI0302721 | 16/10/2025 | Concluído |
| TI0305920 | 29/10/2025 | Concluído |
| TI0306713 | 03/11/2025 | Concluído |
| TI0310502 | 18/11/2025 | Concluído |
| TI0311474 | 25/11/2025 | Em aberto |
| TI0312092 | 27/11/2025 | Em aberto |
| TI0312689 | 01/12/2025 | Em aberto |

**✅ Protocolo Padrão**
1. Identificar o CPF/CNPJ da pessoa e o estado de nascimento.
2. Abrir chamado na GETIC imediatamente.
3. Referenciar chamados anteriores para demonstrar reincidência.
4. Acompanhar até resolução.

**⚠️ Atenção**
A resolução "Concluída" em chamados anteriores não resolveu o problema de forma definitiva — novos casos continuam surgindo. **É necessário pressionar a GETIC por uma solução estrutural**, não apenas pontual.

**👨‍💻 Escalonamento**
Abrir chamado na **GETIC**. Em caso de demora, escalar para liderança com o histórico completo acima como evidência de recorrência.

---

## 🔹 Out of Memory no Benner — Reincidência confirmada

**📌 Contexto**
Erro de falta de memória que interrompe integrações com o Benner. Apresenta histórico de reincidência ao longo de 2025 e 2026.

**Mensagem de erro:**
```
Erro 'Out of memory' nas integrações com o Benner
```

**📊 Histórico de Chamados**

| Chamado | Data | Status |
|---|---|---|
| TI0252965 | 28/03/2025 | — |
| TI0269739 | 05/06/2025 | Concluído |
| TI0281296 | 22/07/2025 | Concluído |
| TI0338268 | 02/04/2026 | Em aberto |

**✅ Protocolo Padrão**
1. Verificar se o problema afeta múltiplas integrações simultaneamente.
2. Registrar horário de início e contexto.
3. Abrir chamado na GETIC com urgência, referenciando chamados anteriores.
4. Não tentar reprocessar em massa durante o incidente — aguardar resolução.

**⚠️ Atenção**
A reincidência em 2026 (TI0338268) confirma que as resoluções anteriores foram paliativas. Pressionar por investigação definitiva da causa raiz.

**👨‍💻 Escalonamento**
Abrir chamado na **GETIC** com caráter de urgência, referenciando o histórico completo.

---

## 🔹 Erro 'Foi encontrado o documento...' no primeiro envio

**📌 Contexto**
Ocorre no primeiro envio de um documento ao Benner. O sistema rejeita alegando que o documento já existe, mesmo sem envio anterior confirmado.

**📊 Histórico de Chamados**

| Chamado | Data | Status |
|---|---|---|
| TI0287291 | 15/08/2025 | Em aberto |
| TI0332905 | 12/03/2026 | Em aberto |

**✅ Protocolo Padrão**
1. Confirmar que é realmente o primeiro envio.
2. Verificar se há registros duplicados por reprocessamento automático.
3. Abrir chamado na GETIC referenciando os dois chamados anteriores.

**⚠️ Atenção**
Ambos os chamados estão **Em aberto**. Problema sem resolução. Ao abrir novo chamado, enfatizar que já existem dois chamados anteriores sem solução.

**👨‍💻 Escalonamento**
Abrir chamado na **GETIC** referenciando TI0287291 e TI0332905.

---

## 🔹 Duplicidade de pessoa (CNPJ/CPF) — Padrão de chamados

**📌 Contexto**
Erro de duplicidade de cadastro de pessoa no Benner. Impede integração de cobranças e faturamentos.

**Mensagens de erro:**
```
Impossibilidade de integrar cobrança - Existe mais uma pessoa com este Cnpj/Cpf cadastrado
```
```
Erro ao integrar pessoa - Já existe uma pessoa com este CNPJ/CPF
```
```
Erro – Não existe uma pessoa com este Cnpj/Cpf (mesmo com pessoa integrada)
```

**📊 Histórico de Chamados**

| Chamado | Data | Status | Descrição |
|---|---|---|---|
| TI0294054 | 11/09/2025 | Concluído | Existe mais uma pessoa com este Cnpj/Cpf |
| TI0294080 | 11/09/2025 | Em aberto | Existe mais uma pessoa com este Cnpj/Cpf |
| TI0294107 | 11/09/2025 | Em aberto | Já existe uma pessoa com este CNPJ/CPF |
| TI0291818 | 03/09/2025 | Concluído | Não existe uma pessoa com este Cnpj/Cpf |

**✅ Protocolo Padrão**
1. Identificar o CNPJ/CPF com problema.
2. Verificar no Benner se há registros duplicados.
3. Abrir chamado na GETIC para deduplicação ou merge.

**⚠️ Atenção**
Múltiplos chamados abertos no mesmo dia (11/09/2025) sugerem problema sistêmico pontual. Em caso de novo surto, verificar se há múltiplas pessoas afetadas antes de abrir chamados individuais.

**👨‍💻 Escalonamento**
Abrir chamado na **GETIC** com o CNPJ/CPF e evidências dos registros duplicados.

---

## 🔹 API de Colaboradores — Histórico de instabilidade

**📌 Contexto**
A API de colaboradores (versão 1.1.0) apresentou erros em homologação e produção, incluindo retornos vazios via SOAP.

**📊 Histórico de Chamados**

| Chamado | Data | Status | Ambiente |
|---|---|---|---|
| TI0235070 | — | — | Homologação |
| TI0261290 | 05/05/2025 | — | Produção |
| TI0286502 | — | — | Produção (SOAP vazio) |

**✅ Protocolo Padrão**
1. Identificar se o erro é em homologação ou produção.
2. Testar a consulta diretamente via SOAP/REST para isolar o problema.
3. Abrir chamado na GETIC com o ambiente e os dados da consulta.

**⚠️ Atenção**
A consulta via SOAP retornando vazio (TI0286502) é um comportamento distinto dos erros de API. Pode indicar problema de configuração do endpoint SOAP.

**👨‍💻 Escalonamento**
Abrir chamado na **GETIC** especificando: versão da API (1.1.0), ambiente, método de acesso (REST/SOAP) e retorno obtido.

---

## 📋 Resumo de Chamados GETIC — Visão Geral

| Período | Total de Chamados | Em aberto | Concluídos |
|---|---|---|---|
| Jan–Mar 2025 | 8 | 0 | — |
| Abr–Jun 2025 | 5 | 0 | 2 |
| Jul–Set 2025 | 14 | 8 | 5 |
| Out–Dez 2025 | 11 | 8 | 3 |
| Jan–Abr 2026 | 2 | 2 | 0 |
| **Total** | **39** | **18** | **10** |

> ⚠️ **Atenção**: 18 chamados ativos em aberto. Os erros mais críticos por volume são: **DependenciasPAISES** (7 chamados) e **duplicidade de CNPJ/CPF** (4 chamados).
