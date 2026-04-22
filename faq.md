# Guia rápido — Integrações financeiras (Benner)

##  Como usar este guia

1. Identifique rapidamente o tipo do problema
2. Veja para qual área encaminhar
3. Se precisar de detalhes, consulte:
   - [Integrações](integracoes.md)
   - [Benner](benner.md)

---

## Decisão rápida (em 10 segundos)

| Se o problema for… | Vá para |
|---|---|
| Conta financeira, centro de custo, boleto, produto x filial | **GECON** |
| Cadastro duplicado, erro técnico, dependência cadastral, integração travada | **GETIC** |
| Erro de permissão, endpoint, WSO2 | **DevOps** |

---

##  Visão geral de encaminhamento

| Tipo de problema | Encaminhar para |
|---|---|
| Conta financeira, centro de custo, boleto automático, cadastro de filial/produto | **GECON** |
| Divergência técnica, duplicidade de cadastro, dependências cadastrais | **GETIC** |
| Permissão no WSO2 / acesso ao endpoint | **DevOps** |

---

## Contatos úteis

### GECON
- **carolini.silveira@fiesc.com.br**
- **marcos@fiesc.com.br**

### Cadastro de produto / filial no Benner
- **otavio.l.santos@fiesc.com.br**
- **jackson.faria@fiesc.com.br**
- **silvana.tkaczuk@fiesc.com.br**

### Outros
- **Alexandre** — ajustes no grupo de integrações
- **DevOps** — erros de autorização e acesso ao endpoint

---

## 1. Conta financeira não preenchida

### Erro
`Erro interno: Erro ao integrar lançamento: FINOBJ - Validação das contas financeiras: A conta deve ser preenchida!`

### Causa
O **CR não está com conta financeira configurada no Benner**.

### Tratativa
Acionar a **GECON** para análise e regularização.

### Encaminhamento
**GECON**  
carolini.silveira@fiesc.com.br  
marcos@fiesc.com.br

---

## 2. Erro de conteúdo inválido no XML

### Erro
`cvc-complex-type.2.4.d: Invalid content was found starting with element 'codigoCentroResponsabilidade'`

### Causa
- Erro no Benner
- Ou divergência de arquivos entre os servidores

### Tratativa
Acionar a **GETIC**.

### Chamados relacionados
- **TI0232055**
- **TI0271054**

---

## 3. Filial não habilitada para faturamento

### Erro
`Impossível faturar esta filial com o produto informado.`

### Causa
A filial está com **cadastro incompleto no Benner**, podendo envolver:
- vínculos
- CNAE
- habilitação para faturar

### Tratativa
Solicitar regularização do cadastro de produto e filial no Benner.

### Encaminhamento
**Área de negócio / GECON**  
otavio.l.santos@fiesc.com.br  
jackson.faria@fiesc.com.br  
silvana.tkaczuk@fiesc.com.br

---

## 4. Centro de custo inválido

### Erro
`Erro interno: Erro ao integrar lançamento: FINOBJ - Validação dos centros de custo: Centro de custo inválido para a filial.`

### Causa
O **centro de custo está inválido para a filial/conta financeira**.

### Tratativa
Acionar a **GECON** para conferência da parametrização.

### Encaminhamento
**GECON**  
carolini.silveira@fiesc.com.br  
marcos@fiesc.com.br

---

## 5. Complemento acima do limite permitido

### Erro
`Erro ao integrar a pessoa: O tamanho máximo do campo "Complemento (COMPLEMENTO)" é 60 caracteres.`

### Causa
O campo **Complemento** no cadastro da pessoa possui **mais de 60 caracteres**.

### Tratativa
1. Editar o cadastro e reduzir temporariamente o complemento
2. Realizar a integração
3. Se necessário, ajustar novamente o texto completo depois

---

## 6. Falha na geração automática de boleto

### Erro
`Erro interno: DOCOBJ - Problema ocorrido ao desbloquear o documento: TFINANCEIROAposConfirmacaoDocumento - Não foi possível realizar a geração automática de boleto de cobrança. As configurações do boleto automático não foram encontradas.`

### Causa
A unidade **não possui configuração de boleto automático no Benner**.

### Tratativa
Verificar a operação **7151**, na carga **Configuração boletos automáticos**, no cadastro de operações.

### Encaminhamento
**GECON**  
carolini.silveira@fiesc.com.br  
marcos@fiesc.com.br

---

## 7. CPF/CNPJ duplicado

### Erro
`Impossibilidade de integrar cobrança - Existe mais uma pessoa com este Cnpj/Cpf cadastrado`

### Causa
Há **duplicidade de cadastro** para o mesmo CPF/CNPJ.

### Tratativa
Acionar a **GETIC**.

### Chamado relacionado
- **TI0294206**

---

## 8. Unidade não integrada com o Benner

### Erro
`Erro: serviço de baixa tesouraria retornou status diferente de 200 [OK]: Bad Request. Mensagem: A unidade da cobrança não está integrada com o Benner.`

### Causa
A **unidade vinculada à cobrança ainda não está integrada** com o Benner.

### Tratativa
Validar a integração da unidade antes de tentar novo reprocessamento.

### Exemplo citado
- **ID cobrança:** 4.401.485
- **ID unidade:** 394

---

## 9. Dependência cadastral não encontrada

### Erro
`Erro ao integrar a pessoa: Não foi encontrado o registro na tabela DependenciasPAISES, campo de busca: ESTADONASCIMENTO, valor da busca: SC`

### Causa
Não foi localizado o registro necessário na tabela **DependenciasPAISES**.

### Tratativa
Acionar a **GETIC**.

### Chamados relacionados
- **TI0302721**
- **TI0305920**

---

## 10. Usuário sem permissão no WSO2

### Erro
`Resource forbidden User is NOT authorized to access the Resource. API Subscription validation failed.`

### Causa
O usuário **não possui permissão para acessar o endpoint** no WSO2.

### Tratativa
Acionar o **DevOps**.

---

## 11. Parcela já liquidada

### Erro
`Parcela já foi liquidada. Verifique o valor da movimentação, pois o documento foi baixado integralmente e restou um saldo de 12,80`

### Causa
O documento **já foi baixado integralmente**, mas a movimentação ainda apresenta saldo.

### Tratativa
1. Verificar o valor da movimentação
2. Validar com o **Alexandre** no grupo de integrações
3. Após o ajuste, tentar reprocessar

### Chamado relacionado
- **TI0310505**

---

## 12. Campo nulo no documento financeiro

### Erro
`Erro ao integrar documento financeiro: Value cannot be null. Parameter name: source`

### Causa
O documento informa apenas que um parâmetro obrigatório está nulo.

### Tratativa
Necessário aprofundar a análise técnica conforme o contexto da integração.

---

##  Exemplos práticos

### Exemplo 1 — Filial e unidade LAB 365 Florianópolis

**Situação:**  
Foram registrados os seguintes erros:
- **Impossível faturar esta filial com o produto informado**
- **A unidade da cobrança não está integrada com o Benner**

| Campo | Informação |
|---|---|
| Entidade | SENAI |
| Unidade | LAB 365 Florianópolis |
| Filial | 03.774.688/0092-92 |
| Produto | 4026.1 |
| Produto | 2943.1 |

---

### Exemplo 2 — Centro de custo inválido em RPC

**Situação:**  
Erro relacionado à validação de centro de custo.

| Campo | Informação |
|---|---|
| Entidade | SESI |
| Filial | 03.777.341/0093-84 |
| Produto | STT-587.1 |
| Conta financeira | 1.1.01.03.07.01-Médico-Ambulatoriais |
| Centro de custo | 06.2.02.07.01.01.11-Reabilitação |

---

##  Resumo rápido

- **Acione GECON** quando o problema envolver parametrização financeira no Benner.
- **Acione GETIC** quando o problema for técnico, cadastral ou de inconsistência sistêmica.
- **Acione DevOps** quando houver falha de permissão ou acesso ao endpoint.
