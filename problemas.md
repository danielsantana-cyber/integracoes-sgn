# Problemas recorrentes

Esta página consolida erros que se repetem com frequência, têm histórico de chamados acumulado ou exigem atenção especial da equipe. O objetivo é transformar conhecimento repetido em referência rápida.

---

## DependenciasPAISES — maior volume de chamados da base

**Mensagem:**
```
Não foi encontrado o registro na tabela DependenciasPAISES, campo de busca: ESTADONASCIMENTO
```

**Contexto:** Ocorre ao integrar cadastros de pessoas. O Benner não encontra o estado de nascimento na tabela de dependências. É um problema de configuração interna do ERP, não dos dados enviados.

**Histórico:**

| Chamado | Data | Status |
|---|---|---|
| TI0302721 | 16/10/2025 | Concluído |
| TI0305920 | 29/10/2025 | Concluído |
| TI0306713 | 03/11/2025 | Concluído |
| TI0310502 | 18/11/2025 | Concluído |
| TI0311474 | 25/11/2025 | Em aberto |
| TI0312092 | 27/11/2025 | Em aberto |
| TI0312689 | 01/12/2025 | Em aberto |

**O que fazer:** Abrir chamado no GETIC a cada novo caso. Mencionar os chamados anteriores para demonstrar reincidência e pressionar por uma solução estrutural — as resoluções pontuais anteriores não eliminaram o problema.

---

## Out of Memory — reincidência confirmada

**Mensagem:**
```
Erro 'Out of memory' nas integrações com o Benner
```

**Contexto:** Interrompe integrações em produção. Reincide ao longo de 2025 e 2026 com resoluções temporárias.

**Histórico:**

| Chamado | Data | Status |
|---|---|---|
| TI0252965 | 28/03/2025 | — |
| TI0269739 | 05/06/2025 | Concluído |
| TI0281296 | 22/07/2025 | Concluído |
| TI0338268 | 02/04/2026 | Em aberto |

**O que fazer:** Abrir chamado urgente no GETIC referenciando o histórico. A abertura em 2026 (TI0338268) confirma que as resoluções anteriores foram paliativas.

---

## Documento duplicado no primeiro envio

**Mensagem:**
```
Foi encontrado o documento... no primeiro envio
```

**Contexto:** O Benner rejeita o primeiro envio de um documento alegando que ele já existe. Causa ainda em investigação.

**Histórico:**

| Chamado | Data | Status |
|---|---|---|
| TI0287291 | 15/08/2025 | Em aberto |
| TI0332905 | 12/03/2026 | Em aberto |

**O que fazer:** Abrir chamado no GETIC. Ambos os chamados anteriores estão sem resolução — incluir essa informação na abertura e referenciá-los.

---

## Duplicidade de CPF/CNPJ — padrão recorrente

**Mensagens:**
```
Impossibilidade de integrar cobrança - Existe mais de uma pessoa com este Cnpj/Cpf cadastrado
Erro ao integrar pessoa - Já existe uma pessoa com este CNPJ/CPF
```

**Contexto:** Múltiplos chamados abertos no mesmo dia (11/09/2025) sugerem que o problema pode ter surgido como falha sistêmica pontual. Novos casos individuais devem ser abertos separadamente para controle de volume.

**Histórico:**

| Chamado | Data | Status |
|---|---|---|
| TI0294054 | 11/09/2025 | Concluído |
| TI0294080 | 11/09/2025 | Em aberto |
| TI0294107 | 11/09/2025 | Em aberto |
| TI0291818 | 03/09/2025 | Concluído |

**O que fazer:** Abrir chamado no GETIC com CPF/CNPJ e evidências dos registros duplicados.

---

## API de colaboradores — histórico de instabilidade

**Contexto:** A API de colaboradores (versão 1.1.0) apresentou falhas em homologação e produção, incluindo retornos vazios via SOAP.

**Histórico:**

| Chamado | Data | Ambiente |
|---|---|---|
| TI0235070 | — | Homologação |
| TI0261290 | 05/05/2025 | Produção |
| TI0286502 | — | Produção — SOAP vazio |

**O que fazer:** Verificar se o erro é em homologação ou produção e testar a consulta diretamente para isolar o problema. Abrir chamado no GETIC com ambiente, versão da API e método de acesso.

---

## Resumo geral de chamados GETIC

| Período | Total | Em aberto | Concluídos |
|---|---|---|---|
| Jan–Mar 2025 | 8 | — | — |
| Abr–Jun 2025 | 5 | — | 2 |
| Jul–Set 2025 | 14 | 8 | 5 |
| Out–Dez 2025 | 11 | 8 | 3 |
| Jan–Abr 2026 | 2 | 2 | — |
| Total | 40 | 18 | 10 |

Os erros com maior volume são DependenciasPAISES (7 chamados) e duplicidade de CPF/CNPJ (4 chamados).

---

*Última revisão: Abril 2026*
