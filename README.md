# Pet Feliz

Aplicação web construída com Next.js (App Router), React e TypeScript.

## Tech Stack

- [Next.js 16](https://nextjs.org) (App Router, Turbopack)
- [React 19](https://react.dev)
- TypeScript
- [Tailwind CSS 4](https://tailwindcss.com)
- ESLint (`eslint-config-next`)

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
components/     # Componentes de feature
components/ui/  # Primitivos reutilizáveis (shadcn/ui)
lib/            # Helpers, clients (supabase, stripe), configurações
types/          # Tipos globais e schemas Zod compartilhados
```

Ver `CLAUDE.md` para convenções de código, arquitetura e workflow detalhados.

## Variáveis de ambiente

Copie `.env.example` para `.env.local` e preencha os valores necessários. Apenas variáveis prefixadas com `NEXT_PUBLIC_` ficam expostas no client — segredos (DB, API keys) devem ser usados apenas em Server Actions ou Route Handlers.

## Deploy

O jeito mais simples de publicar é usar a [Vercel](https://vercel.com/new). Veja a [documentação de deploy do Next.js](https://nextjs.org/docs/app/building-your-application/deploying) para outras opções.
