# Central de Conhecimento — Suporte SGN

Base de conhecimento estruturada para a equipe de suporte, organizada para consulta rápida, onboarding de novos colaboradores e evolução contínua com base em casos reais da operação.

---

## O que este projeto entrega

- Site estático pronto para GitHub Pages
- Busca rápida por erros, sintomas e sistemas
- Categorias organizadas por contexto operacional
- Página de onboarding com acessos e primeiros passos
- Página de governança para alimentar a base com consistência
- Template pronto para registrar novos casos

---

## Estrutura do projeto

```text
faq-suporte-sgn/
├── index.html
├── README.md
├── .nojekyll
└── docs/
    ├── home.md
    ├── _sidebar.md
    ├── integracoes.md
    ├── benner.md
    ├── dashboard.md
    ├── acessos.md
    ├── contribuicao.md
    ├── modelo-de-registro.md
    └── problemas.md
```

---

## Como publicar no GitHub Pages

1. Crie um repositório no GitHub
2. Envie todos os arquivos desta pasta para a raiz do repositório
3. Vá em **Settings > Pages**
4. Em **Build and deployment**, selecione **Deploy from a branch**
5. Escolha a branch `main` e a pasta `/ (root)`
6. Salve e aguarde a geração do link

---

## Como a equipe pode usar

1. Acessar a central pelo link do GitHub Pages
2. Pesquisar pelo erro, sistema ou sintoma
3. Consultar a tratativa documentada
4. Seguir o escalonamento indicado
5. Registrar novos casos relevantes no mesmo padrão

---

## Fluxo de atualização recomendado

1. Identificar um caso relevante
2. Escolher a categoria correta
3. Registrar usando o modelo padrão
4. Revisar clareza e consistência
5. Publicar no repositório

---

## Páginas principais

| Página | Finalidade |
|---|---|
| `home.md` | Visão geral da central e navegação inicial |
| `integracoes.md` | Casos de APIs, integrações, serviços e sincronizações |
| `benner.md` | Casos ligados ao ERP, faturamento, documentos e cadastros |
| `acessos.md` | Onboarding, acessos, permissões e primeiros passos |
| `dashboard.md` | Estrutura para dúvidas e erros da camada analítica |
| `problemas.md` | Padrões recorrentes e histórico consolidado |
| `contribuicao.md` | Regras de governança para manter a base |
| `modelo-de-registro.md` | Template para novos casos |

---

## Observação importante

Antes de publicar no ambiente oficial da empresa, revise:

- responsáveis por liberação de acesso
- canais formais de escalonamento
- links oficiais dos sistemas
- informações que ainda estejam em análise

---

*Versão 1.0 · Pronto para apresentação inicial à liderança*
