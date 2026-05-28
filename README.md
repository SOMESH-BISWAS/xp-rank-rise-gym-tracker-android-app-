# ⚡ Ascend (xp-rank-rise)

> **Train. Gain XP. Climb the Ranks.**

🔗 **Live Web Application**: [xp-rank-rise.someshbiswas71.workers.dev](https://xp-rank-rise.someshbiswas71.workers.dev)

Ascend is a premium, gamified fitness application that transforms physical workouts into an interactive RPG-style progression. Build muscle, log sets, and track your lift history while earning currency, claiming achievements, activating XP boosters, and competing across global rank tiers.

Built using React 19, TanStack Start, Tailwind CSS, Supabase, and deployed as a server-side rendered (SSR) application to Cloudflare Workers.

---

## 🚀 Key Features

* 🏋️‍♂️ **Workout Tracker & Analytics**: Log your sets, reps, and weights. The app automatically calculates your estimated 1-Rep Max (1RM) for Bench Press, Squat, and Deadlift and plots progress over time using interactive Recharts graphs.
* 🏆 **Competitive League Ranks**: Your rank is determined by your **Strength Ratio** (total 1RM divided by body weight, with normalized scaling for female lifters). Climb across 10 tiers:
  * *Bronze ➔ Silver ➔ Gold ➔ Platinum ➔ Diamond ➔ Master ➔ Grandmaster ➔ Elite ➔ Titan ➔ Ascended*
* 💪 **Muscle Mastery**: Track your training split across specific muscle groups (Chest, Back, Shoulders, Biceps, Triceps, Forearms, Quadriceps, Hamstrings, Glutes, Calves, Core, Cardio). Completing sets awards anatomical XP to level up individual muscle masteries.
* 🧪 **Virtual Market & Inventory**: Earn *Sparks* and *Cores* from workouts and achievements to purchase double-XP potions, quest boosters, streak freezes, and custom aesthetics in the Shop.
* 📦 **Cosmetic Customs**: Equip username styles and banners to personalize your card, featuring glowing name effects (Toxic Green, Ember Flame), Neon Halos, and animated cyberpunk grid banners.
* 🛡️ **Streak Protection**: Maintain your workout consistency streak. In case of rest days, protect your streak status using Streak Freezes purchased in the shop.
* 🎯 **Achievements**: Unlock milestones for logging your first workout, reaching high XP goals, keeping up streaks, or entering diamond/master/ascended ranks to claim Sparks and Cores.

---

## 🛠️ Technology Stack

* **Front-End & Framework**: [React 19](https://react.dev/), [TypeScript](https://www.typescriptlang.org/), and [TanStack Start](https://tanstack.com/router/latest/docs/start/overview) (file-based routing, server functions, and SSR).
* **Styling**: [Tailwind CSS v4](https://tailwindcss.com/) with a futuristic glassmorphic and neon-accented dark theme.
* **Database & Auth**: [Supabase](https://supabase.com/) (PostgreSQL, custom RPC triggers for claims/purchases, Row-Level Security, and Auth).
* **Hosting & SSR Runtime**: [Cloudflare Workers](https://workers.cloudflare.com/) (configured via `wrangler.jsonc` and built using `@cloudflare/vite-plugin`).
* **Charts & Animations**: [Recharts](https://recharts.org/) for lift tracking, [Framer Motion](https://www.framer.com/motion/) for fluid animations, and [Lucide Icons](https://lucide.dev/).

---

## 📂 Project Structure

```
xp-rank-rise/
├── .lovable/                 # Lovable environment metadata
├── public/                   # Static public assets (manifest, icons, well-known)
├── src/
│   ├── components/           # Reusable UI components (buttons, badges, charts, dialogs)
│   │   ├── ui/               # Radix primitives & layout elements
│   │   ├── loading-scanner.tsx  # Interactive biometric scanning loader
│   │   └── simple-loader.tsx    # Lightweight animated loader
│   ├── hooks/                # Custom React context state hooks (auth, profile)
│   ├── integrations/         # Supabase client declarations
│   ├── lib/                  # Helper utilities, algorithms, and static databases
│   │   └── ranks.ts          # League tiers, strength ratio calculations, achievements
│   ├── routes/               # TanStack router tree
│   │   ├── _authenticated/   # Protected routes (Dashboard, Shop, Leaderboard, Workout, Profile)
│   │   ├── auth.tsx          # Authentication (Sign in, Sign up)
│   │   └── onboarding.tsx    # Interactive questionnaire for new users
│   ├── styles.css            # Base Tailwind imports and keyframe declarations
│   ├── server.ts             # SSR worker entry wrapper
│   └── start.ts              # TanStack start bootstrap
├── tsconfig.json             # TypeScript configuration
├── vite.config.ts            # Vite config with TanStack & Cloudflare plugins
└── wrangler.jsonc            # Cloudflare Worker bindings and compatibility config
```

---

## 💻 Local Development

### 1. Prerequisites
Ensure you have [Node.js](https://nodejs.org/) installed (v18+ recommended) along with `npm`.

### 2. Clone and Setup
Clone this repository to your local system and navigate inside the folder:
```bash
git clone https://github.com/SOMESH-BISWAS/xp-rank-rise.git
cd xp-rank-rise
```

### 3. Install Dependencies
```bash
npm install
```

### 4. Configure Environment Variables
Create a `.env` file in the root directory and add your Supabase project keys:
```env
VITE_SUPABASE_URL=your-supabase-url
VITE_SUPABASE_PUBLISHABLE_KEY=your-supabase-anon-key
```

### 5. Start Development Server
Launch the local dev server:
```bash
npm run dev
```
Open [http://localhost:3000](http://localhost:3000) in your web browser.

---

## 🌐 Production Build & Deployment

### Build the Project
To compile the client and SSR server bundles for production:
```bash
npm run build
```
This command compiles and bundles the assets into the `dist/` directory.

### Deploy to Cloudflare
Deployments are automatically managed via Cloudflare's git integration upon pushing commits to the `main` branch. 

To trigger manually via the command line (if wrangler CLI is authenticated):
```bash
npx wrangler deploy
```
