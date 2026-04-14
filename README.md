# Central de Conhecimento — Suporte SGN

Base de conhecimento operacional para a equipe de suporte do Squad Integracoes, Movimentacoes Financeiras. Construida com base em casos reais da operacao.

Versao 1.2 — Abril 2026

---

## O que este projeto entrega

- Documentacao de erros reais com tratativas validadas
- Pagina de chamados abertos para consulta antes de escalar
- Fluxo de tratativa inicial padronizado
- Guia de direcionamento entre GECON, GETIC e DevOps
- Onboarding para novos colaboradores
- Template e governanca para manutencao continua

---

## Estrutura do projeto

```
integracoes-sgn/
├── index.html               Entrada do site (Docsify)
├── README.md                Este arquivo
├── .nojekyll                Necessario para GitHub Pages
├── home.md                  Pagina inicial
├── _sidebar.md              Navegacao lateral
├── integracoes.md           Erros de integracao entre sistemas
├── benner.md                Erros do ERP Benner
├── chamados.md              Chamados abertos e historico
├── problemas.md             Padroes recorrentes com historico
├── dashboard.md             Painel de monitoramento
├── direcionamento.md        Como decidir para onde escalar
├── fluxo-tratativa.md       Fluxo inicial do suporte
├── acessos.md               Primeiros acessos e onboarding
├── contribuicao.md          Como alimentar a base
└── modelo-de-registro.md    Template para novos casos
```


## Como manter a base atualizada

**Novo erro identificado:**
1. Abrir o arquivo da categoria correta (integracoes.md ou benner.md)
2. Adicionar o caso seguindo o modelo em modelo-de-registro.md
3. Revisar clareza e objetividade
4. Publicar via commit

**Novo chamado aberto:**
1. Adicionar linha na tabela "Chamados em aberto" em chamados.md
2. Incluir: numero, problema, sistema, data, responsavel

**Chamado encerrado:**
1. Mover a linha para a tabela "Concluidos" em chamados.md
2. Adicionar a data de encerramento

---

## Principios de governanca

Registre apenas o que foi confirmado. Causas em analise devem ser sinalizadas como tal. Escalonamento sem criterio claro nao deve ser publicado. Contatos devem ser validados pela equipe antes de entrar na base.

---

## Cobertura atual

| Categoria | Conteudo |
|---|---|
| Integracoes | 14 erros documentados |
| Benner | 15 erros documentados |
| Chamados abertos | 17 em acompanhamento |
| Problemas recorrentes | 5 padroes com historico |
