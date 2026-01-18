# Coding Conventions

## File Naming

### Components

- PascalCase: `HeroSection.tsx`, `BlogCard.tsx`
- Suffix pattern: `[Name]Section.tsx`, `[Name]Card.tsx`, `[Name]Skeleton.tsx`
- Skeletons alongside components: `BlogCard.tsx` + `BlogCardSkeleton.tsx`

### Routes (App Router)

- Folders: lowercase with hyphens if needed: `app/verify-2fa/`
- Page files: `page.tsx`
- Layouts: `layout.tsx`
- API routes: `app/api/[endpoint]/route.ts`

### Lib Files

- Lowercase: `auth.ts`, `prisma.ts`, `helpers.ts`
- Group by feature: `lib/uploadthing/core.ts`

## Component Structure

### File Organization

```
src/
├── app/           # Routes and API endpoints
├── components/    # Reusable UI components (flat structure)
└── lib/           # Utilities, configs, database
```

### Component Pattern

- Functional components only
- Use `.tsx` extension for all React components
- Client components: Add `"use client"` directive at top
- Server components: Default (no directive needed)

## Styling

### Tailwind CSS

- Use Tailwind utility classes directly in JSX
- No separate CSS files per component
- Global styles in `globals.css` only
- Use Framer Motion for animations

## State & Data

### Database

- Prisma for all database operations
- Schema in `prisma/schema.prisma`
- Use `lib/prisma.ts` for client instance

### Authentication

- NextAuth v5 for auth
- 2FA flow: `lib/2fa.ts`, `lib/2fa-token.ts`
- Protected routes check session server-side

### API Routes

- Use Next.js App Router API routes (`route.ts`)
- Rate limiting via `lib/rate-limit.ts`
- Return proper HTTP status codes

## TypeScript

### General

- Strict mode enabled
- Prefer `type` over `interface` for consistency
- Use `import type` for type-only imports

### Props

```tsx
// ✅ DO: Define props inline or with type
type BlogCardProps = {
  title: string;
  slug: string;
  publishedAt: Date;
};

export function BlogCard({ title, slug, publishedAt }: BlogCardProps) {
  // ...
}
```

## Error Handling

- Use try/catch in API routes
- Return consistent error response format
- Log errors server-side before returning generic message to client

## Images

### Remote Patterns (next.config.ts)

Allowed domains:

- `img.youtube.com`, `i.ytimg.com` — YouTube thumbnails
- `*.googleusercontent.com` — Google profile images
- `utfs.io`, `*.uploadthing.com` — UploadThing files

### Usage

- Use Next.js `<Image>` component
- Always provide `alt` text
- Use `width` and `height` or `fill` prop
