# 🛠️ PromptMaster Pro — Tech Stack & Architecture

A technical deep-dive into the technologies powering the platform.

---

## Core Stack

| Technology | Version | Purpose |
|---|---|---|
| **React** | 18.3.1 | UI framework with hooks and suspense |
| **TypeScript** | 5.8.3 | Type-safe development |
| **Vite** | 5.4.19 | Build tool with HMR |
| **Tailwind CSS** | 3.4.17 | Utility-first styling |
| **GSAP** | 3.14.2 | Professional-grade animations |

## UI & Components

| Technology | Purpose |
|---|---|
| **shadcn/ui** | 40+ accessible UI component primitives |
| **Radix UI** | Headless component architecture (Dialog, Accordion, Tabs, Toast, etc.) |
| **Lucide React** | 200+ consistent SVG icons |
| **class-variance-authority** | Component variant management |
| **cmdk** | Command palette (⌘K) component |

## Animations & Visual Effects

| Technology | Purpose |
|---|---|
| **GSAP + ScrollTrigger** | Scroll-linked animations, page transitions, element reveals |
| **@gsap/react** | React-specific GSAP hooks (`useGSAP`) |
| **OGL** | Lightweight WebGL library for Threads background |
| **Three.js** | 3D WebGL effects (available for future use) |
| **Custom CSS** | Floating orbs, gradient meshes, grid backgrounds, keyframe animations |

### Animation Components Built
- `Threads.tsx` — WebGL fragment shader rendering 40 Perlin noise-distorted thread lines with mouse interaction
- `FloatingOrbs.tsx` — CSS-animated floating gradient orbs
- `ScrollReveal.tsx` — GSAP ScrollTrigger-powered element entrance animations
- `SplitTextReveal.tsx` — Character-by-character stagger text reveal
- `AnimatedCounter.tsx` — Number counting animation with intersection observer
- `SpotlightCard.tsx` — Mouse-tracking radial spotlight effect on cards
- `AnimatedGradientText.tsx` — Animated gradient-shifting text
- `ShinyButton.tsx` — Hover-activated shine effect button
- `Marquee.tsx` — Infinite scrolling text marquee
- `TextRevealOnScroll.tsx` — Progressive text reveal as user scrolls
- `CodeMockup.tsx` — Animated code editor mockup in hero
- `InteractiveWorkflow.tsx` — Step-by-step interactive workflow visualization
- `PremiumBento.tsx` — Bento grid layout for feature showcase

## Backend & Auth

| Technology | Purpose |
|---|---|
| **Supabase** | PostgreSQL database + Row Level Security |
| **Supabase Auth** | Google OAuth 2.0 + email/password authentication |
| **Supabase Edge Functions** | Serverless API endpoints (Deno runtime) |
| **Lemon Squeezy** | Payment processing (one-time lifetime purchase) |

## Data Architecture

| File | Lines | Content |
|---|---|---|
| `curriculum.ts` | 6,387 | 10-module prompt engineering curriculum |
| `vibeCodingData.ts` | 1,818 | 19 vibe coding tutorials + MCP server configs |
| `automationData.ts` | 851 | 9-module automation course (19 lessons) |
| `mcpData.ts` | 1,180 | MCP servers course content |
| `glossary.ts` | — | Searchable AI terminology database |
| `realWorldExamples.ts` | — | 30 production-tested prompt examples |
| `boltGuideData.ts` | — | Bolt & OpenClaw build guide content |

**Total content data:** 10,000+ lines of structured TypeScript

## Infrastructure

| Technology | Purpose |
|---|---|
| **Vercel** | Edge-optimized hosting with automatic deployments |
| **React Router v6** | Client-side routing with lazy-loaded pages |
| **TanStack React Query** | Server state management and caching |
| **Vitest** | Unit and integration testing |
| **ESLint** | Code quality and linting |

## Key Architectural Decisions

### 1. Content as Code
All course content lives in TypeScript data files rather than a CMS. This enables:
- Type-safe content authoring
- Zero API calls for content loading (instant page loads)
- Git-versioned content with full history
- IDE autocomplete for content structure

### 2. Progressive Enhancement
- CSS animations serve as fallbacks for GSAP
- WebGL components detect GPU support and degrade gracefully
- Pages render immediately, animations enhance progressively
- Page transitions use CSS `page-enter-fallback` as primary, GSAP as secondary

### 3. Premium Content Gating
- Scroll-based content walls (not route-based)
- Users can see premium content exists before purchasing
- Smooth GSAP-powered blur/lock animations at the gate boundary
- Server-side RLS policies as additional protection

### 4. Performance
- Lazy-loaded routes with React Suspense
- Vite code-splitting per page
- WebGL canvas cleanup on unmount
- Debounced resize handlers for responsive animations

---

## File Structure

```
src/
├── components/
│   ├── animations/           # 15+ GSAP & WebGL animation components
│   ├── auth/                 # AuthProvider, login guards
│   ├── security/             # Content protection utilities
│   └── ui/                   # 40+ shadcn/ui components
├── data/                     # All course content (10,000+ lines)
├── hooks/                    # Custom hooks (progress, theme, mobile, toast)
├── lib/                      # Supabase client, Lemon Squeezy checkout, utils
├── pages/                    # 20 page components
└── test/                     # Vitest test files
```

---

## Local Development

```bash
# Install dependencies
npm install

# Start dev server (Vite HMR)
npm run dev

# Build for production
npm run build

# Run tests
npm test

# Lint
npm run lint
```

**Requirements:** Node.js 18+, npm 9+
