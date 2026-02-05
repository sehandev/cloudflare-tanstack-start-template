# <YOUR_PROJECT_NAME>

This is a template for a new TanStack Start project with React, TypeScript, and shadcn/ui, designed for deployment on Cloudflare Workers.

## Tech Stack

- **Package Manager:** pnpm
- **Framework:** React 19
- **Routing & SSR:** TanStack Router + TanStack Start (`@tanstack/react-start`)
- **Server State Management:** TanStack Query (`@tanstack/react-query`)
- **Client State Management:** Zustand (`zustand`)
- **Styling:** Tailwind CSS v4 (`@tailwindcss/vite`)
- **UI Components:** Shadcn UI (Base UI primitives + Tailwind)
- **Icons:** Hugeicons (`@hugeicons/react`, `@hugeicons/core-free-icons`)
- **Build Tool:** Vite 7
- **Deployment:** Cloudflare Workers (`wrangler`)
- **Testing:** Vitest

## Getting Started

1. **Install Dependencies:**

   ```bash
   pnpm install
   ```

2. **Setup Project Name:**

   Update the `name` field in `package.json` and `wrangler.jsonc` with your project name.

3. **Start Development Server:**

   ```bash
   pnpm run dev
   ```

4. **Deploy to Cloudflare Workers:**

   ```bash
   pnpm run build
   pnpm run deploy
   ```
