# Benner — Erros e Tratativas

Esta seção reúne erros, causas e tratativas ligados ao Benner: cadastros, faturamento, cobranças e documentos financeiros.

Antes de escalar, verifique se o problema já tem chamado aberto em [Chamados abertos](chamados.md).

---

## Como usar esta página

1. Identifique a mensagem de erro
2. Localize o caso correspondente abaixo
3. Execute a tratativa descrita
4. Escale apenas se a tratativa não resolver ou se o caso indicar escalonamento direto

---

## Erros de cadastro e pessoa

---

### Complemento de endereço acima do limite

**Mensagem:**
```
O tamanho máximo do campo "Complemento (COMPLEMENTO)" é 60 caracteres
```

**Causa:** O campo complemento do cadastro de Pessoa Física tem mais de 60 caracteres.

**Tratativa:**
1. Editar o cadastro e reduzir o complemento para até 60 caracteres
2. Processar a integração
3. Após integrar com sucesso, editar novamente para restaurar o complemento completo se necessário

Esse caso é resolvido pelo suporte sem escalonamento.

---

### CPF/CNPJ duplicado no Benner

**Mensagem:**
```
Impossibilidade de integrar cobrança - Existe mais de uma pessoa com este Cnpj/Cpf cadastrado
```
ou
```
Já existe uma pessoa com este CNPJ/CPF
```

**Causa:** Há mais de um registro de pessoa com o mesmo CPF/CNPJ no Benner.

**Encaminhar para:** GETIC

Referência: TI0294080, TI0294107

---

### Pessoa integrada mas Benner não reconhece o CPF/CNPJ

**Mensagem:**
```
Não existe uma pessoa com este Cnpj/Cpf
```

**Causa:** A pessoa foi integrada com sucesso, mas o Benner não localizou o registro na consulta.

**Encaminhar para:** GETIC
Referência: TI0291818 — concluído, usar como modelo de abertura.

---

### Tabela DependenciasPAISES — estado de nascimento não encontrado

**Mensagem:**
```
Erro ao integrar a pessoa: Não foi encontrado o registro na tabela DependenciasPAISES, campo de busca: ESTADONASCIMENTO valor da busca: SC
```

**Causa:** O estado de nascimento informado não está mapeado na tabela de dependências do Benner. Problema de configuração interna do ERP.

**Encaminhar para:** GETIC

Este é o erro mais frequente da base. Novos casos devem ser abertos como chamados separados. Ao abrir, mencione o histórico de chamados anteriores para demonstrar reincidência. Veja [Chamados abertos](chamados.md).

---

### dataNascimento duplicado no XML

**Mensagem:**
```
cvc-complex-type.2.4.e: 'dataNascimento' can occur a maximum of '3' times
```

**Causa:** O payload enviado ao Benner contém o campo `dataNascimento` repetido além do limite permitido pelo schema XSD.

**O que fazer:**
1. Verificar o payload gerado para a pessoa com erro
2. Identificar de onde vêm as ocorrências extras do campo
3. Corrigir na origem e reprocessar

Se não for possível identificar a origem, encaminhar para GETIC.
Referência: TI0294162

---

### Integração de pessoa sem retorno do Benner

**Mensagem:** sem mensagem de erro visível — a integração é enviada, mas não retorna resposta.

**O que fazer:**
1. Aguardar alguns minutos e verificar se a pessoa foi integrada no Benner
2. Se não integrada, tentar reenviar uma vez
3. Se persistir, abrir chamado

**Encaminhar para:** GETIC
Referência: TI0294149

---

## Erros de faturamento e cobrança

---

### Conta financeira não configurada

**Mensagem:**
```
FINOBJ - Validação das contas financeiras: A conta deve ser preenchida!
```

**Causa:** O CR (Centro de Responsabilidade) não tem conta financeira configurada no Benner.

**Encaminhar para:** GECON
- carolini.silveira@fiesc.com.br
- marcos@fiesc.com.br

Informar qual CR está com o problema.

---

### Centro de custo inválido para a filial

**Mensagem:**
```
FINOBJ - Validação dos centros de custo: Centro de custo inválido para a filial
```

**Encaminhar para:** GECON
- carolini.silveira@fiesc.com.br
- marcos@fiesc.com.br

Referência: TI0232261

---

### Filial não habilitada para faturar produto

**Mensagem:**
```
Impossível faturar esta filial com o produto informado. É necessário concluir o cadastro no Benner (vínculos, CNAE, etc)
```

**Causa:** Cadastro incompleto no Benner — vínculos, CNAE ou habilitação ausentes.

**Encaminhar para:** GECON
- otavio.l.santos@fiesc.com.br
- jackson.faria@fiesc.com.br
- silvana.tkaczuk@fiesc.com.br

---

### Configuração de boleto automático ausente

**Mensagem:**
```
Não foi possível realizar a geração automática de boleto de cobrança. As configurações do boleto automático não foram encontradas. Verifique a operação 7151.
```

**Causa:** A unidade não possui configuração de boleto automático no Benner (operação 7151).

**Encaminhar para:** GECON
- carolini.silveira@fiesc.com.br
- marcos@fiesc.com.br

Informar na abertura: operação 7151, carga "Configuração boletos automáticos".

---

### Parcela já liquidada

**Mensagem:**
```
Parcela já foi liquidada. O documento foi baixado integralmente e restou um saldo de X,XX
```

**O que fazer:**
1. Verificar o valor da movimentação e o saldo residual indicado no erro
2. Contatar Alexandre no grupo de integrações para realizar o ajuste
3. Após confirmação do ajuste, reprocessar a integração

**Encaminhar para:** GETIC se o ajuste não resolver.
Referência: TI0310505

---

### Cobrança permanece em aberto após cancelamento

**Situação:** O cancelamento foi integrado com sucesso, mas a cobrança continua com status "em aberto" no Benner.

**O que fazer:**
1. Confirmar nos logs que a integração do cancelamento foi processada sem erro
2. Verificar o status atual da cobrança no Benner
3. Se ainda aparecer em aberto, abrir chamado com o ID da cobrança e data do cancelamento

**Encaminhar para:** GETIC
Referência: TI0291504

---

### Unidade da cobrança não integrada ao Benner

**Mensagem:**
```
A unidade da cobrança não está integrada com o Benner. id cobrança XXXXXXX - id unidade XXX
```

**O que fazer:**
1. Anotar o ID da cobrança e o ID da unidade informados no erro
2. Verificar com GECON se a unidade deveria estar integrada
3. Se confirmado, abrir chamado no GETIC para configurar a integração

---

## Erros de infraestrutura e sistema

---

### Out of Memory nas integrações

**Mensagem:**
```
Erro 'Out of memory' nas integrações com o Benner
```
ou
```
ESB-0004 - Excedeu o tempo limite de 1800000 milissegundos para integrar com o ERP
```

**Causa:** Problema de infraestrutura no servidor do Benner. Consumo excessivo de memória ou timeout do ESB.

**O que fazer:**
1. Verificar se outras integrações também estão falhando ao mesmo tempo
2. Se sim, registrar como incidente sistêmico
3. Abrir chamado com urgência

**Encaminhar para:** GETIC

Esse erro é recorrente. Ao abrir, mencione os chamados anteriores para registrar o histórico: TI0252965, TI0269739, TI0281296, TI0338268.

---

### Divergência de arquivos XML entre servidores

**Mensagem:**
```
cvc-complex-type.2.4.d: Invalid content was found starting with element 'codigoCentroResponsabilidade'
```

**Causa:** Divergência de arquivos entre os servidores do Benner. Não tem resolução pelo suporte.

**Encaminhar para:** GETIC
Referência: TI0232055, TI0271054

---

### Value cannot be null

**Mensagem:**
```
Erro ao integrar documento financeiro: Value cannot be null. Parameter name: source
```

**O que fazer:**
1. Verificar se todos os campos obrigatórios estão preenchidos na origem
2. Tentar reprocessar uma vez
3. Se persistir, abrir chamado com os dados completos do documento

**Encaminhar para:** GETIC
Referência: TI0293893

---

### Desconto de bolsa não refletido no boleto — Banco do Brasil

**Situação:** O desconto configurado no Benner não aparece no boleto gerado pela integração com o Banco do Brasil.

**O que fazer:**
1. Confirmar o desconto no Benner
2. Registrar evidências: valor do desconto, número do documento, número do boleto
3. Abrir chamado com as evidências

**Encaminhar para:** GETIC
Referência: TI0302257

---

*Última revisão: Abril 2026*
