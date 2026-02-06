# CLAUDE.md — ZoneWise.AI Complete Rebrand Mission

> **You are Claude Code (Opus 4.6) executing an autonomous rebrand mission.**
> Read this entire file, then execute. Do not ask permission. Commit early, commit often.

---

## TARGET REPO

```
git clone https://github.com/breverdbidder/zonewise-web.git
cd zonewise-web
git checkout -b rebrand/navy-orange-statewide
npm install
npm run build  # verify clean build BEFORE changes
```

**Deploy target:** Render (auto-deploys from `main` branch)
**Live URL:** https://zonewise.ai
**Traycer Issue:** https://github.com/breverdbidder/zonewise-web/issues/1

---

## MISSION OBJECTIVE

Transform zonewise.ai from an outdated Brevard-only teal zoning tool into a Navy+Orange 67-county Florida real estate intelligence platform.

The rebrand must:
- Replace ALL teal (#0D9488) with navy (#1E3A5F) + orange (#F59E0B)
- Expand scope from "Brevard County 17 jurisdictions" to "67 Florida Counties"
- Credit **Ariel Shapira** as Inventor & Founder
- Link to **https://everestcapitalusa.com** (parent company) in hero AND footer
- Showcase a split-screen platform preview (static mockup, not live)
- Update stats to: 67 Counties | 298 KPIs | 10.8M Parcels | AI+ML

**Root cause:** Commit `976acc9c` (Jan 29) updated BRAND_COLORS.md documentation but never touched actual code files. Teal is hardcoded throughout.

---

## BRAND SYSTEM

### Colors
| Role | Hex | Usage |
|------|-----|-------|
| Primary | `#1E3A5F` | Headers, backgrounds, nav, buttons, text |
| Accent | `#F59E0B` | Stats numbers, CTAs, hover states, active tabs, badges |
| Light BG | `#F0F4F8` | Page backgrounds, card backgrounds |
| Dark BG | `#0F2439` | Footer, dark sections |
| White | `#FFFFFF` | Text on dark, card backgrounds |
| Text | `#1A202C` | Body text on light backgrounds |

### Navy Palette (Tailwind)
```
navy-50:  #E8EEF4
navy-100: #C5D3E3
navy-200: #9FB5D0
navy-300: #7897BD
navy-400: #5A80AE
navy-500: #3D6A9F
navy-600: #1E3A5F  ← PRIMARY
navy-700: #182F4D
navy-800: #12243B
navy-900: #0F2439  ← DARK BG
```

### Orange Palette (Tailwind)
```
orange-300: #FCD34D
orange-400: #FBBF24
orange-500: #F59E0B  ← ACCENT
orange-600: #D97706
orange-700: #B45309
```

### Font
**Inter** (via `next/font/google`) — replaces DM Sans

### BANNED
- Zero teal (#0D9488), cyan, or any blue-green
- Zero "Brevard County" in marketing copy
- Zero DM Sans references

---

## FILES TO MODIFY

### 1. `tailwind.config.ts`
- Add `navy` color scale (50-900) to `theme.extend.colors`
- Add `orange` color scale (300-700) to `theme.extend.colors`
- Remove any existing `teal` color definitions
- Verify Inter font configuration

### 2. `app/globals.css`
- Replace entire `:root` variable block with navy/orange semantic variables
- `--primary: #1E3A5F`, `--accent: #F59E0B`, etc.
- Remove ALL `--teal-*` variables
- Update selection color to navy bg + orange text
- Update focus rings to orange
- Update scrollbar thumb to navy
- Replace DM Sans font import with Inter
- Update gradient utilities to navy-to-orange

### 3. `app/layout.tsx`
- Title: `"ZoneWise.AI — Florida's AI-Powered Real Estate Intelligence"`
- Description: Include keywords: 67 Florida counties, foreclosure intelligence, tax deed analysis, zoning, ML predictions
- Theme color: `#0D9488` → `#1E3A5F`
- Font: Verify Inter via `next/font/google`
- Replace any hardcoded teal in className props

### 4. `app/(marketing)/page.tsx` — COMPLETE REWRITE

Build these sections top-to-bottom:

#### Header
- Sticky, navy bg (`bg-navy-900`), white text
- Logo: Navy with orange accent dot
- Nav: Login, Signup, Pricing, About
- Mobile hamburger menu

#### Hero
- Headline: **"Florida's AI-Powered Real Estate Intelligence"**
- Subheadline: **"Distressed Assets Decoded. For Everyone. Everywhere."**
- Orange badge: "Powering Everest Capital USA" → links to `https://everestcapitalusa.com`
- Founder: **"Founded by Ariel Shapira, Inventor & Founder"**
- CTA: Primary navy button, secondary orange-bordered button
- Background: Navy gradient

#### Stats Bar
- Navy bg (`bg-navy-900 py-12`)
- 4-column grid (responsive: 2 on tablet, 1 on mobile)
- **67** — "Florida Counties" (orange number, white label)
- **298** — "Intelligence KPIs"
- **10.8M** — "Parcels Analyzed"
- **AI+ML** — "Powered Intelligence"

#### "Our Edge" Feature Cards
4-card responsive grid (`grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-6`):

1. 🏛️ **Foreclosure Intelligence** — Automated lien discovery, title search automation, judgment analysis
2. 📜 **Tax Deed Analysis** — Certificate tracking, redemption period monitoring, surplus probability scoring
3. 🏗️ **Zoning & Land Use** — 3D building envelopes, Highest & Best Use analysis, setback calculations
4. 🤖 **ML Predictions** — XGBoost probability scoring, market trend analysis, risk assessment models

Card styling: `border-navy-300 hover:border-orange-500 hover:shadow-lg transition-all`

#### Origin Story
- "Built by a Florida Real Estate Veteran"
- Ariel Shapira's 20+ years Florida real estate experience
- Two-column layout (text + placeholder image)

#### Split-Screen Preview (import from components/SplitScreenPreview.tsx)
- See new file spec below

#### Pricing
- Update existing pricing section colors only (navy borders, orange featured plan)
- Keep pricing structure unchanged

#### Footer
- `bg-navy-900 text-white`
- **"Founded by Ariel Shapira · Powering Everest Capital USA"** with link to https://everestcapitalusa.com
- Nav: About, Terms, Privacy, Disclaimer
- Copyright: © 2026 ZoneWise.AI

### 5. `components/SplitScreenPreview.tsx` — NEW FILE

**This is a STATIC MOCKUP / interactive preview. No live API calls, no Mapbox tiles, no Supabase queries.**

```
┌──────────────────────┬───────────────────────────────────────────┐
│                      │  [🗺️ MAP] [📅 CALENDAR] [📊 ANALYTICS]   │
│  🤖 MULTILINGUAL     ├───────────────────────────────────────────│
│     NLP CHATBOT      │  Panel 1: Static heatmap placeholder      │
│  EN | ES | HE | RU   │  Panel 2: Static auction calendar grid    │
│                      │  Panel 3: Static KPI metric cards         │
└──────────────────────┴───────────────────────────────────────────┘
```

**Left panel (40% width):**
- Navy background, white text
- Static chat messages showing multilingual capability:
  - EN: "What can I build at 123 Main St, Orlando?"
  - ES: "¿Qué puedo construir en 456 Oak Ave, Miami?"
  - HE: "מה אפשר לבנות ב-789 Palm Blvd, Tampa?"
  - RU: "Что можно построить на 321 Pine St, Jacksonville?"
- Language toggle: EN | ES | HE | RU (useState, orange active state)
- Suggested actions list below chat

**Right panel (60% width):**
- Tab navigation: 🗺️ Map | 📅 Calendar | 📊 Analytics
- Active tab: `border-b-2 border-orange-500 text-orange-500`
- Inactive: `text-navy-600`
- Tab switching with `transition-all duration-300`
- **Map tab:** CSS gradient or placeholder simulating a heatmap (navy-to-orange gradient overlay on gray base)
- **Calendar tab:** Static grid with sample auction dates (Feb 2026), navy headers, orange highlighted dates
- **Analytics tab:** 4 KPI cards: Avg ARV $287K, Foreclosure Rate 2.3%, Median Days 145, Surplus Probability 34%
- Responsive: Stack vertically below 768px

**Existing components in zonewise-desktop repo (REFERENCE ONLY — do not import, just use as design inspiration):**
- `zonewise/components/web/AIChatBox.tsx`
- `zonewise/components/web/MapboxSatellite.tsx`
- `zonewise/components/web/Map.tsx`
- `zonewise/components/3d/BuildingEnvelope.tsx`
- `zonewise/services/kpiCalculator.ts`

---

## PHASE EXECUTION ORDER

### Phase 1: Color Foundation (tailwind.config.ts + globals.css)
### Phase 2: Metadata (layout.tsx)
### Phase 3: Marketing Page + SplitScreenPreview (page.tsx + new component)
### Phase 4: Global Search & Replace
```bash
# After all changes, verify zero teal remnants:
grep -ri "teal\|cyan\|0D9488\|0d9488" --include="*.tsx" --include="*.css" --include="*.ts" --include="*.json" .
# This MUST return zero results (excluding docs/ and node_modules/)
```
### Phase 5: QA
```bash
npm run build  # MUST pass with 0 errors
```
Verify:
- [ ] Zero teal/cyan visible anywhere
- [ ] Navy #1E3A5F is primary color throughout
- [ ] Orange #F59E0B is accent (stats, CTAs, active tabs)
- [ ] "67 Florida Counties" replaces "Brevard County"
- [ ] "Founded by Ariel Shapira" visible on homepage
- [ ] Link to everestcapitalusa.com in hero AND footer
- [ ] Stats: 67 / 298 / 10.8M / AI+ML
- [ ] Features: Foreclosure + Tax Deed + Zoning + ML
- [ ] SplitScreenPreview renders with 4 panels
- [ ] Tab switching works
- [ ] Multilingual toggle works
- [ ] Responsive at 375px / 768px / 1440px
- [ ] All routes work: /, /login, /signup, /terms, /privacy, /disclaimer

### Phase 6: Commit & Push
```bash
git add -A
git commit -m "feat: complete rebrand — navy+orange, 67 counties, founder credit, split-screen preview

- Replace teal with navy #1E3A5F + orange #F59E0B throughout
- Expand scope from Brevard County to 67 Florida Counties
- Add Ariel Shapira founder credit + Everest Capital USA link
- Create SplitScreenPreview component (4-panel mockup)
- Update stats: 67 Counties / 298 KPIs / 10.8M Parcels / AI+ML
- Add feature cards: Foreclosure, Tax Deed, Zoning, ML Predictions
- Font: Inter via next/font/google
- Closes breverdbidder/zonewise-web#1"

git push origin rebrand/navy-orange-statewide
```

Then create PR:
```bash
gh pr create \
  --repo breverdbidder/zonewise-web \
  --base main \
  --head rebrand/navy-orange-statewide \
  --title "feat: ZoneWise.AI complete rebrand — navy+orange, 67 counties, founder credit" \
  --body "## Summary
Complete visual and content rebrand of zonewise.ai marketing page.

## Changes
- Navy #1E3A5F + Orange #F59E0B color system
- 67 Florida Counties scope (was Brevard only)
- Ariel Shapira founder credit + Everest Capital USA link
- SplitScreenPreview 4-panel mockup component
- Stats: 67/298/10.8M/AI+ML
- Feature cards: Foreclosure, Tax Deed, Zoning, ML
- Inter font, responsive design

Closes #1"
```

---

## CRITICAL RULES (NON-NEGOTIABLE)

1. **ZERO teal/cyan** in final output — grep verify
2. **Navy #1E3A5F** is ONLY primary color
3. **Orange #F59E0B** is ONLY accent color
4. **"Brevard County"** appears NOWHERE in marketing copy
5. **Ariel Shapira** credited as "Inventor & Founder"
6. **everestcapitalusa.com** linked in hero AND footer
7. **All routes** must work: /, /login, /signup, /terms, /privacy, /disclaimer
8. **npm run build** must pass with 0 errors
9. **No new dependencies** without justification
10. **Commit early, commit often** with descriptive messages

---

## OUT OF SCOPE (DO NOT ATTEMPT)

- Dashboard/app UI rebrand (marketing page only this sprint)
- Working split-screen app (MOCKUP ONLY)
- Actual 67-county data pipeline
- Stripe pricing changes
- New auth flows
- Logo design finalization
- Live Mapbox tiles in preview
- Live Claude API calls in chatbot preview
- Live Supabase queries in analytics preview
