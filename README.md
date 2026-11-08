# AEGIS — Intelligent Security Network

Plataforma SaaS de proteção web profissional (inspirada em Cloudflare, Akamai, Imperva e Sucuri).

**Status atual: Fase 1 — Fundação**

## Stack

| Camada        | Tecnologia                          |
|---------------|-------------------------------------|
| Frontend      | React 18 + TypeScript + Vite        |
| UI            | Tailwind CSS + shadcn/ui + Lucide   |
| Charts        | Recharts                            |
| Auth / DB     | Supabase (Auth + PostgreSQL + RLS)  |
| Backend API   | Node.js + Express (esqueleto)       |
| Deploy (web)  | Netlify (preparado)                 |

## Estrutura do monorepo

```
aegis/
├── apps/
│   ├── web/          # Frontend React
│   └── api/          # Backend API (esqueleto Fase 1)
├── packages/
│   └── shared/       # Tipos e constantes compartilhadas
├── supabase/
│   └── migrations/   # Schema + RLS
└── docs/
```

## Pré-requisitos

- Node.js ≥ 20
- Conta Supabase (projeto criado)
- npm

## Configuração rápida

### 1. Clonar e instalar

```bash
cd aegis
npm install
```

### 2. Configurar Supabase

1. Crie um projeto em [supabase.com](https://supabase.com)
2. No SQL Editor, execute o conteúdo de:
   `supabase/migrations/20241107000001_initial_schema.sql`
3. Em Authentication → URL Configuration, adicione `http://localhost:5173` nas Redirect URLs

### 3. Variáveis de ambiente

```bash
cp apps/web/.env.example apps/web/.env
```

Preencha:

```
VITE_SUPABASE_URL=https://xxxx.supabase.co
VITE_SUPABASE_ANON_KEY=eyJ...
```

### 4. Rodar o frontend

```bash
npm run dev:web
```

Acesse: http://localhost:5173

### 5. (Opcional) API

```bash
cd apps/api
cp .env.example .env   # se existir
npm run dev
```

## O que já funciona (Fase 1)

- [x] Landing page
- [x] Login / Cadastro (Supabase Auth)
- [x] Layout profissional (sidebar + header) com identidade visual AEGIS
- [x] Dashboard com KPIs e gráficos (dados claramente marcados como demo)
- [x] Schema de banco completo (organizations, members, domains, audit_logs)
- [x] Row Level Security (isolamento multi-tenant)
- [x] Trigger de criação de profile no signup
- [x] Roles: owner, administrator, security_analyst, developer, viewer
- [x] Planos preparados (free / pro / business / enterprise)
- [x] Navegação completa com placeholders para módulos futuros

## O que NÃO está implementado ainda

- Gerenciamento real de domínios e verificação de propriedade (Fase 2)
- WAF, Rate Limiting, IP Access, Logs (Fase 3)
- DNS, SSL/TLS, CDN reais (Fase 4)
- Analytics e AEGIS AI (Fase 5)
- Integração com proxy reverso / WAF externo (nunca simulado)

## Identidade visual

| Cor       | Hex       |
|-----------|-----------|
| Preto     | `#080B12` |
| Grafite   | `#111827` |
| Azul      | `#2563EB` |
| Ciano     | `#06B6D4` |
| Branco    | `#F8FAFC` |
| Verde     | `#22C55E` |
| Vermelho  | `#EF4444` |

Dark mode padrão.

## Próximas fases

Consulte o documento de requisitos original e o plano de desenvolvimento.

---

**Princípio fundamental:** AEGIS não simula proteção ativa. Status de integração é sempre explícito.
