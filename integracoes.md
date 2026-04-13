# Integrações — Erros e Tratativas

Esta página reúne os principais erros de integração entre SGN, Benner e serviços externos. Para cada erro: o que é, como tratar e para onde encaminhar se necessário.

Antes de escalar, verifique se já existe um chamado aberto para o mesmo problema em [Chamados abertos](chamados.md).

---

## Erros tratáveis pelo suporte

Esses erros têm tratativa direta. O suporte resolve sem precisar acionar outra equipe.

---

### CPF/CNPJ duplicado

**Mensagem:**
```
Erro interno: Existe mais de uma pessoa com este Cnpj/Cpf cadastrado no sistema.
```

**O que fazer:**
- Se o nome estiver em negrito na tela: usar "Forçar reenvio"
- Se o nome não estiver em negrito: usar "Reenviar selecionados"

---

### Documento já existe no sistema

**Mensagem:**
```
Erro interno: Já existe um documento com essas informações cadastrado no sistema
```

**O que fazer:**
1. Conferir os logs da integração
2. Clicar em "Aprovar retorno"
3. Justificativa a usar: `Já foi integrado com sucesso`

---

### Documento já integrado (NOSSO NÚMERO)

**Mensagem:**
```
Foi encontrado o documento...
```

**O que fazer:**
1. Conferir os dados
2. Clicar em "Aprovar retorno"
3. Justificativa: `Já foi integrado com sucesso`

**Atenção:** se for o primeiro envio e o erro ainda assim aparecer, consulte os chamados TI0287291 e TI0332905 em [Chamados abertos](chamados.md) — esse comportamento está em investigação.

---

### Baixa já processada anteriormente

**Mensagem:**
```
A requisição de baixa já foi processada anteriormente
```

**O que fazer:**
1. Conferir os logs
2. Aprovar retorno
3. Justificativa: `Já foi integrado com sucesso`

---

### Invalid variant operation

**Mensagem:**
```
Erro ao integrar documento... Invalid variant operation
```

**O que fazer:**
- Nome em negrito: "Forçar reenvio"
- Nome sem negrito: "Reenviar selecionados"

---

### Value cannot be null

**Mensagem:**
```
Falha ao autorizar operação. Value cannot be null. Parameter name: key
```

**O que fazer:**
1. Tentar reenviar uma vez
2. Se persistir, abrir chamado

**Encaminhar para:** GETIC

---

## Erros que exigem escalonamento para GECON

---

### Conta financeira não preenchida

**Mensagem:**
```
FINOBJ - A conta deve ser preenchida
```

**Causa:** CR sem conta financeira configurada no Benner

**Encaminhar para:** GECON
- carolini.silveira@fiesc.com.br
- marcos@fiesc.com.br

---

### Centro de custo inválido para a filial

**Mensagem:**
```
Centro de custo inválido para a filial
```

**Encaminhar para:** GECON
- carolini.silveira@fiesc.com.br
- marcos@fiesc.com.br

---

### Filial não habilitada para faturar

**Mensagem:**
```
Impossível faturar esta filial com o produto informado
```

**Causa:** Cadastro incompleto no Benner (vínculos, CNAE, etc.)

**Encaminhar para:** GECON
- otavio.l.santos@fiesc.com.br
- jackson.faria@fiesc.com.br
- silvana.tkaczuk@fiesc.com.br

---

### Complemento de endereço acima de 60 caracteres

**Mensagem:**
```
O tamanho máximo do campo "Complemento" é 60 caracteres
```

**O que fazer:**
1. Reduzir o complemento para até 60 caracteres no cadastro
2. Reprocessar a integração
3. Após integrar, ajustar o cadastro com o texto completo novamente

Esse caso é resolvido no suporte, sem necessidade de escalonamento.

---

### Boleto automático não configurado

**Mensagem:**
```
As configurações do boleto automático não foram encontradas. Verifique a operação 7151.
```

**Encaminhar para:** GECON
- carolini.silveira@fiesc.com.br
- marcos@fiesc.com.br

Informar na abertura: operação 7151, carga "Configuração boletos automáticos".

---

## Erros que exigem escalonamento para GETIC

---

### Divergência de arquivos XML entre servidores

**Mensagem:**
```
cvc-complex-type.2.4.d: Invalid content was found starting with element 'codigoCentroResponsabilidade'
```

**Encaminhar para:** GETIC
Referência: TI0232055 / TI0271054

---

### Tabela DependenciasPAISES — estado de nascimento não encontrado

**Mensagem:**
```
Não foi encontrado o registro na tabela DependenciasPAISES, campo de busca: ESTADONASCIMENTO
```

**Encaminhar para:** GETIC

Este é o erro com maior volume de chamados na base. Ao abrir, mencione os chamados anteriores para demonstrar reincidência. Veja histórico completo em [Chamados abertos](chamados.md).

---

### Unidade da cobrança não integrada ao Benner

**Mensagem:**
```
A unidade da cobrança não está integrada com o Benner. Status diferente de 200.
```

**Encaminhar para:** GETIC com o ID da cobrança e o ID da unidade informados no erro.

---

### Parcela já liquidada

**O que fazer:**
1. Validar o valor da movimentação e o saldo residual informado no erro
2. Contatar Alexandre no grupo de integrações para ajuste
3. Após confirmação do ajuste, reprocessar

**Referência:** TI0310505

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

**Encaminhar para:** GETIC com urgência.

Esse erro é recorrente. Ao abrir, mencione os chamados anteriores: TI0252965, TI0269739, TI0281296, TI0338268.

---

## Erros de permissão — DevOps

---

### Resource forbidden — acesso negado no WSO2

**Mensagem:**
```
Resource forbidden. User is NOT authorized to access the Resource. API Subscription validation failed.
```

**Causa:** Usuário ou aplicação sem permissão no WSO2

**Encaminhar para:** DevOps com o nome da API, nome da aplicação e ambiente (produção ou homologação).

---

*Última revisão: Abril 2026*
