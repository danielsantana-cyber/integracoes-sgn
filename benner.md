# Erros do Benner

Esta página reúne os erros que dependem de comportamento interno, cadastro, configuração ou retorno do ERP Benner. Em geral, quando a causa está do lado do ERP, o suporte analisa, reúne evidências e encaminha.

Antes de escalar, consulte [Chamados abertos](chamados.md).

---

## Como usar esta página

1. Identifique a mensagem principal do erro.
2. Veja se o caso já está documentado abaixo.
3. Entenda se é erro de cadastro, financeiro ou infraestrutura.
4. Encaminhe com contexto completo quando o suporte não puder resolver.

---

## Cadastro de pessoa

### CPF/CNPJ duplicado no Benner

**Mensagem:**
`Existe mais de uma pessoa com este CnpjCpf cadastrado`

**Leitura prática:**
O problema está no banco do Benner, não no SGN.

**Quando escalar:**
Encaminhar para GETIC com referência aos chamados anteriores.

---

### Pessoa integrada, mas Benner não localiza

**Mensagem:**
`Não existe uma pessoa com este CnpjCpf`

**Como validar:**
Verifique se o último protocolo de integração da pessoa está com sucesso. Se estiver, o envio aconteceu e o problema é de retorno ou indexação do ERP.

**Quando escalar:**
Abrir chamado na GETIC.

---

### Estado de nascimento em DependenciasPAISES

**Mensagem:**
`Não foi encontrado o registro na tabela DependenciasPAISES... ESTADONASCIMENTO`

**Leitura prática:**
É uma lacuna de configuração do Benner. O SGN enviou o dado, mas o ERP não reconheceu a dependência esperada.

**Quando escalar:**
Sempre para GETIC, mencionando histórico do problema.

---

## Configuração financeira

### Conta financeira não configurada

**Mensagem:**
`A conta deve ser preenchida`

**Leitura prática:**
O CR não tem conta financeira configurada.

**Quando escalar:**
GECON, informando o CR com problema.

---

### Centro de custo inválido para a filial

**Mensagem:**
`Centro de custo inválido para a filial`

**O que enviar:**
Filial e CR encontrados no protocolo.

---

### Filial com cadastro incompleto

**Mensagem:**
`Impossível faturar esta filial com o produto informado`

**Leitura prática:**
A filial ou o vínculo do produto não está pronto para faturar no Benner.

**Quando escalar:**
GECON, com Entidade, Unidade, Filial e Produto.

---

### Boleto automático ausente

**Mensagem:**
`As configurações do boleto automático não foram encontradas`

**Quando escalar:**
GECON, com a operação citada no erro.

---

### Cobrança em aberto após cancelamento

**Situação:**
O cancelamento integrou, mas o Benner ainda mostra a cobrança em aberto.

**Quando escalar:**
GETIC, com ID da cobrança e data do cancelamento.

---

## Infraestrutura e comportamento sistêmico

### Out of Memory ou timeout

**Mensagem:**
`Out of memory` ou `ESB-0004`

**Leitura prática:**
É incidente de ambiente. Não adianta reprocessar em massa no meio da instabilidade.

**O que fazer:**
1. Verificar se várias abas falham ao mesmo tempo.
2. Registrar horário e evidências.
3. Acionar GETIC com urgência.

---

### Divergência XML entre servidores

**Mensagem:**
`Invalid content was found starting with element codigoCentroResponsabilidade`

**Leitura prática:**
Indica divergência de arquivos ou estrutura entre servidores do Benner.

**Quando escalar:**
GETIC.

---

*Última revisão: Abril de 2026*