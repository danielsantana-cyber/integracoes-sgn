# Erros operacionais do dia a dia

Esta página reúne situações práticas já vividas pela operação. O foco aqui é ajudar o suporte a decidir rápido sem perder segurança na análise.

Antes de agir, consulte sempre o protocolo do registro.

---

## Casos que o suporte costuma resolver

### Documento já existe no sistema

Se o protocolo mostrar sucesso em envio anterior, não reenvie. Nesse caso, use **Aprovar retorno** com a justificativa `Já foi integrado com sucesso`.

---

### Documento enviado duas vezes

Quando o protocolo mostrar um envio com sucesso e outro com erro logo depois, o segundo erro costuma ser só reflexo da duplicidade. O dado já entrou antes.

---

### Pessoa não encontrada no Benner

Antes de escalar, veja o dashboard de integração de pessoa. Se a pessoa não estiver integrada, salvar o cadastro novamente no SGN costuma disparar o reenvio.

---

### Cliente em fila de integração

Se o sistema informar que o cliente já está na fila, aguarde o retorno. Reenviar nesse momento não acelera e ainda pode atrapalhar.

---

## Casos para GECON

### Filial não habilitada para faturar

Monte o e-mail com Entidade, Unidade, Filial e Produto. Quando houver vários casos da mesma filial, envie tudo de forma organizada na mesma mensagem.

---

### Centro de custo inválido

Abra o protocolo, encontre o CR no rateio e envie junto com a filial. Sem isso, a análise da GECON costuma voltar pedindo complemento.

---

### Boleto automático não configurado

Encaminhe informando a operação mencionada no erro.

---

## Casos para Squad de Integrações

### Erro ao abrir tela de erro de envio em matrícula

Se outras abas funcionam e a aba matrícula não abre corretamente os casos de erro de envio, registre tarefa para o squad.

---

### RPC sem resposta ao reprocessar

Se clicar em reenviar não gera protocolo novo, não insista em massa. Registre tarefa para análise técnica.

---

## Casos urgentes de infra

### Out of Memory nas integrações

Se várias abas começam a falhar juntas, trate como incidente. Registre horários, evidências e acione a GETIC com urgência.

---

### Benner demorando mais de 1 hora para responder

Não é comportamento normal. Avise no grupo de integrações com print da fila atual e aguarde normalização antes de pensar em reprocessamento em massa.

---

*Última revisão: Abril de 2026*