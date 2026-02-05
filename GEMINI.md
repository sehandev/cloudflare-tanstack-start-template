# Language Rules

- all questions you ask: Korean
- all answers you give: Korean
- comment: Korean
- commit: English
- don't mix languages

# Project Name

???

# Overview

The goal of this project is ???

# User Request

User will send you request with template in Korean.
If you don't understand the request, ask the user to clarify.
If user requests something that is not possible, ask the user to clarify.
If user miss something, ask the user to fill template and check user with filled template.

## Template

```markdown
페이지 :
섹션 :
이유 : 에러 / 디자인 / 섹션 추가 / 기능 추가 / 다른 페이지와 연결

# 기존 모습

- 현재 바꾸고 싶은 부분
- 왜 바꾸고 싶은지 설명하면 결과물이 더 잘 나옵니다.

# 바꾼 모습

- 바꾼 뒤 예상되는 결과물

# 주의사항

- 바꾸지 말고 유지할 부분
- AI가 자주 실수하는 부분
- 추가로 주의해야 할 점
```

## Example

```markdown
페이지 : 랜딩
섹션 : 헤더
이유 : 디자인

# 기존 모습

- 헤더에 로고와 다른 페이지로 가는 버튼들이 있어
- 헤더 아래에 배너가 있어
- 로고 위치가 마음에 안 들어

# 바꾼 모습

- 헤더에 다른 페이지로 가는 버튼들이 있어
- 헤더 아래에 로고가 가운데 떠있어
- 로고 아래에 배너가 있어

# 주의사항

- 버튼들은 건드리지마
- 배너가 처음부터 화면에 조금이라도 보여야 해
```

# Page Structure

## 랜딩 (src/routes/index.tsx)

- ???

## 목록 (src/routes/list.tsx)

- ???

## 상세 (src/routes/detail.tsx)

- ???

## 관리 (src/routes/admin.tsx)

- ???

# Tech Stack

- **Framework:** React 19
- **Routing & SSR:** TanStack Router + TanStack Start (`@tanstack/react-start`)
- **Styling:** Tailwind CSS v4 (`@tailwindcss/vite`)
- **UI Components:** Shadcn UI (Base UI primitives + Tailwind)
- **Icons:** Hugeicons (`@hugeicons/react`)
- **Build Tool:** Vite 7
- **Deployment:** Cloudflare Workers (`wrangler`)
- **Testing:** Vitest

# Key Directories

- `src/routes/`: File-based routing for TanStack Router.
- `src/components/ui/`: Reusable UI components (buttons, inputs, etc.).
- `src/lib/utils.ts`: Utility functions, specifically `cn()` for conditional class merging.
- `src/styles.css`: Global styles (imported in `src/routes/__root.tsx`).

# Conventions

- **Styling:** Use Tailwind CSS utility classes. Use `cn()` helper from `src/lib/utils.ts` for dynamic classes.
- **Routing:** Create new routes in `src/routes/`. TanStack Router will auto-generate the route tree in `src/routeTree.gen.ts`.
- **Components:** Place shared UI components in `src/components/ui/`.
- **SSR:** The project uses TanStack Start for Server-Side Rendering. Ensure components are SSR-compatible where necessary.

# Commands

- `npm run build`: Build for production.
- `npm run check`: Run lint and format.
- `npm run dev`: Start development server.

# Style

- add `underline-offset-4` after `underline`, `hover:underline`

# Check List

## Check after editing

- run `npm run check`
- if error, fix it
- run `npm run build`
- if error, fix it

## Don't edit

- components/ui/\*

## Button with react-router Link

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

## Tailwind CSS v4

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

## Section comment

add section comment to each section for user to identify it next time editing

```tsx
return (
  <>
    {/* 섹션 : 프로필 */}
    <Profile />
    {/* 섹션 : 경력 하이라이트 */}
    <CareerHighlight />
    {/* 섹션 : 연락처 */}
    <Contact />
  </>
)
```
