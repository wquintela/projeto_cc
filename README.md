# Pet Feliz

Boilerplate/starter de aplicação web construído com Next.js (App Router), React e TypeScript. Serve como ponto de partida para novos projetos, já configurado com as convenções de arquitetura e código do time — ainda não possui features de negócio implementadas.

## Estado atual

Repositório recém-gerado (scaffold do `create-next-app`). As pastas `actions/`, `components/`, `lib/` e `types/` existem mas estão vazias, prontas para receber o código específico do produto que for construído aqui.

## Tech Stack

**Instalado:**
- [Next.js 16](https://nextjs.org) (App Router, Turbopack)
- [React 19](https://react.dev)
- TypeScript 5
- [Tailwind CSS 4](https://tailwindcss.com)
- ESLint 9 (`eslint-config-next`)

**Previsto pelas convenções do projeto** (ver `CLAUDE.md`), a instalar conforme a necessidade de cada feature:
- [shadcn/ui](https://ui.shadcn.com) + Radix UI (componentes)
- React Hook Form + Zod (formulários e validação)
- Supabase (autenticação e acesso a dados)

## Arquitetura e convenções

O projeto segue Server Component First com separação clara de responsabilidades, documentada em `CLAUDE.md` e `.claude/rules/`:

- **Server Components por padrão** — `'use client'` só entra quando há hooks, eventos ou APIs de browser
- **Server Actions** para mutações, em `actions/` (ou `_actions/` por página) — nunca acessar banco direto em Client Component
- **Data Access Layer** separada da UI (`_data-access/` por página) para centralizar queries
- **Validação com Zod** em toda entrada de dados; formulários com React Hook Form + shadcn/ui
- Componentes de página específicos ficam em `_components/`; só sobem para `components/` quando reutilizados em múltiplas páginas

## Getting Started

Instale as dependências e copie as variáveis de ambiente:

```bash
npm install
cp .env.example .env.local
```

Rode o servidor de desenvolvimento:

```bash
npm run dev
```

Abra [http://localhost:3000](http://localhost:3000) para ver o resultado. A página inicial pode ser editada em `app/page.tsx` — as mudanças são refletidas automaticamente.

## Scripts

| Comando | Descrição |
|---|---|
| `npm run dev` | Servidor local com Turbopack (porta 3000) |
| `npm run build` | Build de produção |
| `npm run start` | Roda o build de produção |
| `npm run type-check` | Checagem de tipos (`tsc --noEmit`) |
| `npm run lint` | Lint (ESLint) |

## Estrutura do projeto

```
app/            # Rotas (App Router), agrupadas por (grupo)/
actions/        # Server Actions (mutações — nunca chamar DB direto em Client Components)
components/     # Componentes de feature reutilizados em múltiplas páginas
components/ui/  # Primitivos reutilizáveis (shadcn/ui)
lib/            # Helpers, clients (supabase, stripe), configurações
types/          # Tipos globais e schemas Zod compartilhados
```

Ver `CLAUDE.md` para convenções de código, arquitetura e workflow detalhados.

## Variáveis de ambiente

Copie `.env.example` para `.env.local` e preencha os valores necessários. Apenas variáveis prefixadas com `NEXT_PUBLIC_` ficam expostas no client — segredos (DB, API keys) devem ser usados apenas em Server Actions ou Route Handlers.

## Deploy

O jeito mais simples de publicar é usar a [Vercel](https://vercel.com/new). Veja a [documentação de deploy do Next.js](https://nextjs.org/docs/app/building-your-application/deploying) para outras opções.
