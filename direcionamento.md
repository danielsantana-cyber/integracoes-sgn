# Direcionamento e escalonamento

Esta página ajuda a decidir para qual equipe um caso deve ser encaminhado quando ele sai da alçada do suporte. O foco aqui é evitar dúvida na triagem e melhorar a qualidade do escalonamento.

---

## Antes de escalar

Só vale encaminhar depois de validar estes quatro pontos:

1. Em qual sistema e em qual fluxo o problema aconteceu.
2. Qual foi a mensagem exata do erro.
3. Se já existe tratativa documentada em [Erros de integração](integracoes.md) ou [Erros do Benner](benner.md).
4. Se já existe chamado aberto para o mesmo comportamento em [Chamados abertos](chamados.md).

Se um desses pontos estiver faltando, complete antes de seguir.

---

## Quando encaminhar para GECON

Encaminhe para GECON quando o caso envolver principalmente regra de negócio, configuração financeira ou cadastro operacional que depende da área.

Situações mais comuns:

- conta financeira não configurada;
- centro de custo inválido para a filial;
- filial ou produto sem vínculo completo;
- configuração de boleto automático;
- período financeiro fechado;
- dúvida funcional sobre como o processo deveria operar.

| Tipo de caso | Contatos mais usados |
|---|---|
| Configurações financeiras no Benner | carolini.silveira@fiesc.com.br, marcos@fiesc.com.br |
| Cadastro de produto, vínculo ou filial | otavio.l.santos@fiesc.com.br, jackson.faria@fiesc.com.br, silvana.tkaczuk@fiesc.com.br |

---

## Quando encaminhar para GETIC

Encaminhe para GETIC quando o caso tiver perfil técnico, sistêmico ou de infraestrutura.

Situações mais comuns:

- falha de ambiente;
- Benner sem retorno;
- timeout ou out of memory;
- erro técnico recorrente sem causa funcional;
- comportamento que afeta mais de uma aba, mais de um usuário ou mais de um processo.

Sempre que houver reincidência, envie também os chamados anteriores como referência.

---

## Quando encaminhar para DevOps

Encaminhe para DevOps quando o problema estiver ligado a permissão de API, WSO2 ou comportamento com forte sinal de bug técnico que não depende de configuração da área financeira.

Situações mais comuns:

- Resource forbidden em API;
- problema de permissão ou rota no WSO2;
- fluxo que falha mesmo com contexto correto e sem indício de erro funcional.

---

## Decisão rápida

| Situação | Encaminhamento |
|---|---|
| Regra de negócio, configuração financeira, cadastro incompleto | GECON |
| Falha técnica, infraestrutura, integração interrompida | GETIC |
| API, WSO2, bug técnico específico | DevOps |

---

## O que enviar em qualquer escalonamento

Monte o contexto de forma objetiva:

- número do chamado;
- resumo do problema em até duas linhas;
- sistema afetado;
- mensagem exata do erro;
- print ou evidência;
- o que o suporte já validou;
- referência de chamado anterior, se houver.

Quanto melhor o contexto chegar, menor a chance de retrabalho na área que vai receber.

---

*Última revisão: Abril de 2026* 
