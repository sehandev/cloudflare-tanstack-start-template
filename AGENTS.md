# AGENTS.md

## Language Rules

- all questions you ask: English
- all answers you give: English
- comment: English
- commit: English
- don't mix languages

## Project Name

???

## Overview

The goal of this project is ???

## User Request

User will send you request with template in English.
If you don't understand the request, ask the user to clarify.
If user requests something that is not possible, ask the user to clarify.
If user miss something, ask the user to fill template and check user with filled template.

## Template

```markdown
page :
section :
reason : error / design / new section / new feature / link to other page

## before

- 

## after

- 

## warnings

- Parts to keep unchanged
- Common AI mistakes
- Additional precautions
```

## Example

```markdown
page : Landing
section : Header
reason : design

## before

- bad logo position

## after

- logo is centered

## warnings

- don't touch buttons
```

## Page Structure

### Landing (src/routes/index.tsx)

- ???

### List (src/routes/list.tsx)

- ???

### Detail (src/routes/detail.tsx)

- ???

### Admin (src/routes/admin.tsx)

- ???

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

### Key Directories

- `src/routes/`: File-based routing for TanStack Router.
- `src/components/ui/`: Reusable UI components (buttons, inputs, etc.).
- `src/lib/utils.ts`: Utility functions, specifically `cn()` for conditional class merging.
- `src/styles.css`: Global styles (imported in `src/routes/__root.tsx`).

## Conventions

- **UI Components:** Always prioritize using existing components from `src/components/ui/` (Shadcn UI). Use them for all UI elements to ensure consistency. If a required component is missing, prefer composing it from existing Shadcn UI primitives rather than writing custom HTML/CSS.
- **Styling:** Use Tailwind CSS utility classes. Use `cn()` helper from `src/lib/utils.ts` for dynamic classes.
- **Routing:** Create new routes in `src/routes/`. TanStack Router will auto-generate the route tree in `src/routeTree.gen.ts`.
- **Components:** Place shared UI components in `src/components/ui/`.
- **SSR:** The project uses TanStack Start for Server-Side Rendering. Ensure components are SSR-compatible where necessary.

## Commands

- `pnpm run build`: Build for production.
- `pnpm run check`: Run lint and format.
- `pnpm run dev`: Start development server.

## Style

- add `underline-offset-4` after `underline`, `hover:underline`

## Check List

### Check after editing

- run `pnpm run check`
- if error, fix it
- run `pnpm run build`
- if error, fix it

### Don't edit

- components/ui/\*

### Shadcn UI

Use Shadcn UI components for everything. Check `src/components/ui/` for available components before creating anything new.

```tsx
import { Button } from "@/components/ui/button"
import { Card, CardHeader, CardTitle, CardContent } from "@/components/ui/card"

function MyComponent() {
  return (
    <Card>
      <CardHeader>
        <CardTitle>Title</CardTitle>
      </CardHeader>
      <CardContent>
        <Button>Click me</Button>
      </CardContent>
    </Card>
  )
}
```

### Hugeicons

Import the HugeiconsIcon component and any icon from the free package to get started.

```tsx
import { HugeiconsIcon } from '@hugeicons/react'
import { Notification03Icon } from '@hugeicons/core-free-icons'

function App() {
  return <HugeiconsIcon icon={Notification03Icon} size={24} color="currentColor" strokeWidth={1.5} />
}
```

You can adjust the size, color, and strokeWidth props to match your design system.

### Button with react-router Link

```tsx
import { Link } from '@tanstack/react-router'
import { Button } from '@/components/ui/button'

// wrong
<Button asChild>
  <Link to="/">
    <HugeiconsIcon icon={ArrowLeft01Icon} size={20} className="mr-2" />
    link
  </Link>
</Button>

// correct
<Link to="/">
  <Button>
    <HugeiconsIcon icon={ArrowLeft01Icon} size={20} className="mr-2" />
    link
  </Button>
</Link>
```

### Tailwind CSS v4

| Deprecated | Replacement |
| `bg-opacity-*` | Use opacity modifiers like `bg-black/50` |
| `text-opacity-*` | Use opacity modifiers like `text-black/50` |
| `border-opacity-*` | Use opacity modifiers like `border-black/50` |
| `divide-opacity-*` | Use opacity modifiers like `divide-black/50` |
| `ring-opacity-*` | Use opacity modifiers like `ring-black/50` |
| `placeholder-opacity-*` | Use opacity modifiers like `placeholder-black/50` |
| `flex-shrink-*` | `shrink-*` |
| `flex-grow-*` | `grow-*` |
| `overflow-ellipsis` | `text-ellipsis` |
| `decoration-slice` | `box-decoration-slice` |
| `decoration-clone` | `box-decoration-clone` |
| `aspect-[9/16]` | `aspect-9/16` |
| `bg-gradient-to-t` | `bg-linear-to-t` |

| v3 | v4 |
| `shadow-sm` | `shadow-xs` |
| `shadow` | `shadow-sm` |
| `drop-shadow-sm` | `drop-shadow-xs` |
| `drop-shadow` | `drop-shadow-sm` |
| `blur-sm` | `blur-xs` |
| `blur` | `blur-sm` |
| `backdrop-blur-sm` | `backdrop-blur-xs` |
| `backdrop-blur` | `backdrop-blur-sm` |
| `rounded-sm` | `rounded-xs` |
| `rounded` | `rounded-sm` |
| `outline-none` | `outline-hidden` |
| `ring` | `ring-3` |

### Section comment

add section comment to each section for user to identify it next time editing

```tsx
return (
  <>
    {/* section : Profile */}
    <Profile />
    {/* section : Career Highlight */}
    <CareerHighlight />
    {/* section : Contact*/}
    <Contact />
  </>
)
```
