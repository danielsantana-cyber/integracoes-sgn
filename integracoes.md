# Erros de integração

Esta página reúne os erros que aparecem no dashboard de integração do SGN e que, na maior parte das vezes, são analisados diretamente pelo suporte. Antes de qualquer ação, abra o protocolo do registro e veja o histórico completo.

Também vale verificar [Chamados abertos](chamados.md) antes de escalar. Em vários casos, o problema já está em investigação.

---

## Casos que o suporte costuma resolver

### Documento já existe no sistema

**Mensagem:**
`Erro interno: Já existe um documento com essas informações cadastrado no sistema`

**Como identificar:**
O protocolo mostra que o documento já teve um envio com sucesso e o sistema tentou enviar de novo.

**O que fazer:**
1. Abra o protocolo.
2. Confirme o envio anterior com sucesso.
3. Use **Aprovar retorno**.
4. Justificativa: `Já foi integrado com sucesso`.

---

### Documento já integrado pelo nosso número

**Mensagem:**
`Foi encontrado o documento... com a AP... para o NOSSONUMERO... Verifique.`

**Como identificar:**
Na maior parte dos casos, o Benner já reconheceu o documento e o erro apareceu em uma nova tentativa de envio.

**O que fazer:**
1. Verifique o protocolo.
2. Se já houve sucesso anterior, aprove o retorno.
3. Se for primeiro envio e o erro persistir, consulte [Chamados abertos](chamados.md).

---

### Baixa já processada anteriormente

**Mensagem:**
`A requisição de baixa já foi processada anteriormente`

**O que fazer:**
1. Confira no Benner se a baixa já entrou corretamente.
2. Se estiver correta, use **Aprovar retorno**.
3. Justificativa: `Já foi integrado com sucesso`.

---

### CPF/CNPJ duplicado que resolve com reenvio

**Mensagem:**
`Existe mais de uma pessoa com este Cnpj/Cpf cadastrado no sistema`

**O que fazer:**
- Nome em negrito: **Forçar reenvio**.
- Nome sem negrito: **Reenviar selecionados**.

Se o erro persistir, escale para GETIC.

---

### Pessoa já está em fila de integração

**Mensagem:**
`O cliente já está sendo enviado para a fila de integração e não será enviado novamente até que a integração tenha um retorno.`

**O que fazer:**
Aguarde o retorno. Não force novo envio nesse momento, porque isso pode gerar duplicidade.

---

### Pessoa não encontrada no Benner

**Mensagem:**
`Não existe uma pessoa com este Cnpj/Cpf cadastrada no sistema`

**O que fazer:**
1. Acesse o dashboard de integração de pessoa.
2. Busque pelo CPF ou nome.
3. Verifique o último protocolo.
4. Se a pessoa não estiver integrada, abra o cadastro no SGN e salve novamente.
5. Se persistir, abra chamado na GETIC.

---

## Casos para GECON

### Conta financeira não preenchida

**Mensagem:**
`FINOBJ - Validação das contas financeiras: A conta deve ser preenchida!`

**Quando escalar:**
Quando o CR não tiver conta financeira configurada.

**Encaminhar para:**
GECON — carolini.silveira@fiesc.com.br / marcos@fiesc.com.br

---

### Centro de custo inválido para a filial

**Mensagem:**
`FINOBJ - Validação dos centros de custo: Centro de custo inválido para a filial`

**O que enviar:**
Filial, CR e evidência do protocolo.

---

### Filial não habilitada para faturar

**Mensagem:**
`Impossível faturar esta filial com o produto informado...`

**O que fazer:**
Monte o e-mail com Entidade, Unidade, Filial e Produto.

---

### Boleto automático não configurado

**Mensagem:**
`As configurações do boleto automático não foram encontradas. Verifique a operação 7151.`

**O que enviar:**
Informar a operação citada no erro.

---

### Parcela já liquidada com desconto duplicado

**Mensagem:**
`Parcela já foi liquidada...`

**Como analisar:**
Compare valor da cobrança, desconto e tesouraria. Se a conta não fechar, o desconto entrou duas vezes no Benner.

**O que fazer:**
1. Validar os valores.
2. Solicitar exclusão do desconto duplicado.
3. Reprocessar a baixa.
4. Abrir chamado para causa raiz.

---

## Casos para GETIC

### DependenciasPAISES

**Mensagem:**
`Não foi encontrado o registro na tabela DependenciasPAISES...`

**Quando escalar:**
Sempre. Referencie chamados anteriores, porque é erro recorrente.

---

### Out of Memory ou timeout ESB

**Mensagem:**
`Out of memory` ou `ESB-0004 - Excedeu o tempo limite...`

**O que fazer:**
1. Verificar se afeta várias abas.
2. Não reprocessar em massa.
3. Avisar no grupo e abrir chamado urgente.

---

*Última revisão: Abril de 2026*