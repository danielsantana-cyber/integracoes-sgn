# Integrações — erros e tratativas

> 📌 Esta página reúne os principais erros de integração entre SGN, Benner e serviços externos, com orientação direta de tratativa e escalonamento.

## 🧠 Como decidir rapidamente

Antes de tudo, responda:

- Esse erro já aconteceu antes?
- Já foi integrado?
- É erro técnico, operacional ou de cadastro?

## 🚀 Decisão rápida

| Situação | Ação |
|---|---|
| Já integrado | Aprovar retorno |
| Duplicidade | Aprovar retorno |
| Erro transitório | Reenviar |
| Erro técnico | GETIC |
| Erro de cadastro / configuração funcional | GECON |
| Permissão / API / WSO2 | DevOps |
| Payload estranho / bug | Squad / devs |

## 🔴 CPF/CNPJ duplicado

**Mensagem:**  
Erro interno: Existe mais uma pessoa com este Cnpj/Cpf cadastrado no sistema.

**Tratativa do suporte:**  
- Se o nome estiver em negrito → usar **Forçar Reenvio**
- Caso contrário → clicar em **Reenviar selecionados** fileciteturn2file3

## 🔴 Documento já existente

**Mensagem:**  
Erro interno: Já existe um documento com essas informações cadastrado no sistema.

**Tratativa do suporte:**  
- Conferir os logs
- Clicar em **Aprovar retorno**
- Na justificativa, informar: `Já foi integrado com sucesso` fileciteturn2file7turn3file0

## 🔴 Documento encontrado / AP / Nosso Número

**Mensagem:**  
Foi encontrado o documento [...] Verifique.

**Tratativa do suporte:**  
- Conferir os dados
- Clicar em **Aprovar retorno**
- Justificativa: `Já foi integrado com sucesso` fileciteturn2file3

## 🔴 Baixa já processada anteriormente

**Mensagem:**  
A requisição de baixa [...] já foi processada anteriormente.

**Tratativa do suporte:**  
- Conferir logs
- Clicar em **Aprovar retorno**
- Justificativa: `Já foi integrado com sucesso` fileciteturn2file3

## 🔴 Invalid variant operation

**Mensagem:**  
Erro ao integrar o documento [...] Invalid variant operation

**Tratativa do suporte:**  
- Se o nome estiver em negrito → usar **Forçar Reenvio**
- Caso contrário → clicar em **Reenviar selecionados** fileciteturn2file3

## 🔴 Pessoa não integrada ao Benner

**Mensagem:**  
O cliente de documento [...] não está integrado com a Aplicação Benner.

**Tratativa do suporte:**  
1. Acessar a tela de integração de pessoa
2. Buscar pelo CPF ou nome
3. Aplicação: Benner
4. Situação: Todas
5. Verificar o status do último protocolo
6. Se necessário, reenviar a pessoa salvando o cadastro da pessoa no SGN fileciteturn3file0

## 🔴 DependenciasPAISES / Estado de nascimento não encontrado

**Mensagem:**  
Erro ao integrar a pessoa: Não foi encontrado o registro na tabela DependenciasPAISES.

**Tratativa do suporte:**  
- Verificar se o dado enviado está válido
- Se o dado estiver válido, tratar como problema do lado de lá
- Abrir chamado / acionar GETIC quando necessário
- Registrar caso recorrente porque já houve incidente de causa raiz sobre isso fileciteturn3file0turn2file5

## 🔴 Unidade não integrada ao Benner

**Mensagem:**  
Serviço de baixa tesouraria retornou status diferente de 200 [OK]: Bad Request. A unidade da cobrança não está integrada com o Benner.

**Leitura operacional:**  
Renan explicou que, para integrar a baixa tesouraria, precisa existir `id_externo` da unidade cadastrado na base. Depois, o caso deve ser documentado com a observação de que esse `id_externo` corresponde ao campo **Código da Filial** no Benner. fileciteturn3file0

**Direcionamento:**  
➡️ Tratativa técnica / apoio de DBA / GETIC, conforme o fluxo validado internamente

## 🔴 XML inválido / divergência entre servidores

**Mensagem:**  
cvc-complex-type... Invalid content...

**Direcionamento:**  
➡️ GETIC fileciteturn2file3

## 🔴 Resource forbidden

**Mensagem:**  
Resource forbidden. User is NOT authorized to access the Resource. API Subscription validation failed.

**Causa conhecida:**  
Usuário no WSO2 não tem permissão para acessar o endpoint.

**Direcionamento:**  
➡️ DevOps fileciteturn2file3

## 🔴 Parcela já liquidada

**Mensagem:**  
Parcela já foi liquidada.

**Leitura operacional:**  
Nem sempre significa erro do suporte. Em vários casos o Renan orientou verificar se:
- já houve protocolo anterior com sucesso
- houve duplicação de desconto
- o valor enviado pelo SGN está correto e o erro é do lado do Benner fileciteturn3file0

**Tratativa do suporte:**  
- validar protocolos
- comparar valor original, valor de desconto e valor da baixa tesouraria
- se o SGN enviou certo e o Benner retornou errado → escalar como incidente

## 🔴 Janela de atualização do Benner

**Leitura operacional:**  
Em alguns dias, vários erros de retorno surgem porque o Benner atualizou e “derrubou tudo”. Nesses cenários, o Renan orientou reenviar os casos. fileciteturn3file0

## 🔴 Casos sem erro visível na tela, mas falha ao reprocessar

**Tratativa do suporte:**  
Quando a tela não mostra claramente o erro e o reenvio estoura erro na própria interface, a orientação recorrente foi abrir tarefa para o squad avaliar se o problema é do nosso lado ou do lado de lá. fileciteturn3file0

*Base inicial construída a partir de histórico operacional da equipe e repasses do desenvolvedor.*
