# Central Operacional de Suporte — SGN

Esta base foi construida para apoiar o dia a dia do suporte com informacoes concretas vindas da operacao real. Cada tratativa aqui documentada foi validada com o time de desenvolvimento.

---

## Para que serve esta central

Qualquer pessoa do suporte, ao consultar esta base, deve conseguir responder:

- Qual e o erro ou sintoma que estou vendo?
- Existe tratativa documentada para esse caso?
- Consigo resolver no proprio suporte ou preciso escalar?
- Se precisar escalar, vai para GECON, GETIC ou devs?
- Quais evidencias preciso enviar junto?

---

## Onde esta cada coisa

| Secao | O que voce encontra |
|---|---|
| [Primeiros acessos ao SGN](acessos.md) | Como solicitar acesso, validar permissoes e iniciar a operacao |
| [Tratativa de chamados no SGN](fluxo-tratativa.md) | O que fazer antes de escalar qualquer caso |
| [Integracoes](integracoes.md) | Erros tecnicos entre sistemas, APIs e sincronizacoes |
| [Benner](benner.md) | Erros ligados ao ERP, faturamento, cadastros e documentos |
| [Erros operacionais do dia a dia](erros-operacionais.md) | Casos reais com tratativas validadas pelo time de desenvolvimento |
| [PIX](pix.md) | Fluxo especifico de integracao de pagamentos via PIX |
| [Unidade nao integrada](unidade-nao-integrada.md) | Processo para resolver erro de unidade sem cadastro no Benner |
| [Como usar o Dashboard SGN](dashboard-sgn.md) | Links, abas, rotina diaria e como navegar no dashboard |
| [Chamados abertos](chamados.md) | Registro de chamados em andamento e status atual |
| [Direcionamento e escalonamento](direcionamento.md) | Como decidir para qual equipe encaminhar o caso |
| [Problemas recorrentes](problemas.md) | Padroes repetidos com historico de ocorrencias |
| [Como registrar novos casos](contribuicao.md) | Fluxo e padrao para manter a base atualizada |

---

## Como usar na pratica

1. Pesquise pelo erro na barra lateral ou use a busca
2. Leia o contexto e a causa documentada
3. Aplique a tratativa descrita
4. Se necessario, escale com as evidencias indicadas
5. Se o erro nao estiver documentado, registre seguindo o modelo padrao

---

## Antes de escalar qualquer caso

Verifique se ja existe um chamado aberto para o mesmo problema em [Chamados abertos](chamados.md). Isso evita chamados duplicados e acelera a resolucao.

---

## Para novos colaboradores

Esta base substitui orientacoes verbais e memoria individual. Antes de perguntar para alguem da equipe, consulte aqui. Se nao encontrar o que precisa, e um sinal de que vale registrar.

---

## Canais de acionamento rapido

| Situacao | Canal |
|---|---|
| Erro tecnico do Benner, infra, API | Abrir chamado na GETIC via SeSuite |
| Configuracao financeira, cadastro incompleto | E-mail para GECON |
| Permissao de API, WSO2 | DevOps |
| Desconto duplicado, parcela liquidada | Alexandre no grupo de integracoes |
| Duvida tecnica de integracao | Grupo de integracoes no Hangouts |

---

*Versao 1.0*
