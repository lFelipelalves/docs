# LF Connect — Documentação (Mintlify)

Documentação técnica do **LF Connect**, plataforma de atendimento omnichannel
da LF Automatiza. Stack: **Mintlify** (markdown-based, hosted, com OpenAPI nativo).

---

## Rodar localmente

### 1. Instalar o CLI (uma vez só)

```bash
npm install -g mintlify
```

### 2. Rodar o servidor de dev

```bash
cd api-docs
mintlify dev
```

Abre em `http://localhost:3000`. Hot reload — você salva o `.mdx`, ele atualiza
o navegador na hora.

### 3. Validar a configuração

```bash
mintlify broken-links
```

Mostra todos os links quebrados antes de publicar.

---

## Estrutura

```
api-docs/
├── mint.json                       # Config (cores, navegação, font)
├── introduction.mdx                # Capa
│
├── essentials/                     # Conceitos transversais
│   ├── authentication.mdx
│   ├── rate-limits.mdx
│   └── webhooks.mdx
│
├── features/                       # Páginas descritivas de funcionalidade
│   ├── canais.mdx
│   ├── captain.mdx
│   ├── kanban.mdx
│   ├── campanhas.mdx
│   └── automacoes.mdx
│
├── api-reference/
│   ├── introduction.mdx            # Visão geral da API
│   ├── openapi.yaml                # Spec OpenAPI 3.1 (endpoints core)
│   └── kanban/
│       ├── funnels.mdx
│       ├── items.mdx
│       ├── movement.mdx
│       ├── checklist.mdx
│       ├── notes.mdx
│       ├── bulk.mdx
│       └── automations.mdx
│
├── logo/                           # Logos (light/dark) e favicon
└── _mega_kanban_api_reference.md   # Fonte original MEGA (referência interna)
```

---

## Adicionar uma nova página

1. Crie o arquivo `.mdx` no lugar certo da árvore
2. Adicione frontmatter:
   ```mdx
   ---
   title: "Título da página"
   description: "Subtítulo de 1 linha"
   ---
   ```
3. Registre a página no `mint.json` dentro do array `navigation[].pages`
4. Salve — o `mintlify dev` atualiza sozinho

---

## Deploy

### Setup (uma vez)

1. Crie conta em [mintlify.com](https://mintlify.com)
2. **Dashboard → Add Deployment** → conecte o repositório Git desta pasta
3. Aponte o domínio custom `docs.lfautomatiza.com` (Settings → Domain)

### Pra publicar mudanças

```bash
git add .
git commit -m "docs: atualiza X"
git push
```

Mintlify detecta o push e faz deploy automático em ~30s. Preview em PRs também
funciona — cada PR gera URL temporária pra revisar antes de mergear.

---

## Cor e tipografia

Tudo no [mint.json](mint.json):

- **Primary:** `#00B86B` (verde LF)
- **Light variant:** `#1FD980`
- **Background dark:** `#0a0a0a`
- **Font:** Manrope (headings + body)
- **Modo default:** dark

Pra mudar cor, edite só a seção `colors` do `mint.json`. Pra mudar o logo,
substitua os arquivos em `logo/`.

---

## Custos

| Tier | Limite | Custo |
| --- | --- | --- |
| **Hobby (grátis)** | 25 páginas, custom domain, search, analytics | R$ 0 |
| Pro | Páginas ilimitadas, API playground, AI search | ~R$ 750/mês |
| Enterprise | SSO, audit logs, SLA | Custom |

Pra começar, **Hobby grátis** já cobre tudo que está aqui (16 páginas hoje).

---

## Componentes Mintlify usados nesta doc

- [`<Card>`](https://mintlify.com/docs/content/components/cards) — caixinhas com ícone + link
- [`<CardGroup>`](https://mintlify.com/docs/content/components/cards#card-group) — grid de cards
- [`<Steps>`](https://mintlify.com/docs/content/components/steps) — passo-a-passo numerado
- [`<CodeGroup>`](https://mintlify.com/docs/content/components/code-group) — tabs de linguagens
- [`<Accordion>`](https://mintlify.com/docs/content/components/accordions) — colapsável
- [`<Note>` / `<Warning>` / `<Tip>` / `<Info>`](https://mintlify.com/docs/content/components/callouts) — callouts

Tudo nativo do Mintlify — não precisa importar nada.

---

## Fonte das informações

Esta documentação foi construída a partir de:

- Documentação oficial do MEGA (`github.com/megaapp977/stack`)
- Documentação interna LF Automatiza (`MEGA_MASTER_DOC.md`, `agente-marketing/references/mega-platform.md`)
- API reference do Kanban (`_mega_kanban_api_reference.md` — fonte preservada nesta pasta)
- PRICING_MODEL.md (para limites e tiers)

Adaptada pro brand e voz do LF Connect.
