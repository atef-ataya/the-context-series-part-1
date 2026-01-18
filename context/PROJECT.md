# Project Context

## Overview

Personal portfolio and content platform for Atef Ataya. Showcases projects,
blog posts, YouTube videos, and sponsorship opportunities. Includes admin
dashboard with 2FA authentication for content management.

## Tech Stack

- **Framework**: Next.js 16.1 (App Router)
- **Language**: TypeScript 5
- **UI**: React 19, Tailwind CSS 4, Framer Motion
- **Database**: PostgreSQL with Prisma ORM 7.2
- **Auth**: NextAuth v5 (beta) with 2FA (otplib, QR codes)
- **Editor**: TipTap (rich text for blog posts)
- **File Uploads**: UploadThing
- **Analytics**: Vercel Analytics
- **Deployment**: Vercel

## Key Features

- **Public**: Hero, About, Projects, Blog, Latest Videos, Newsletter, Contact
- **Admin**: Dashboard with 2FA, blog editor, project management, sponsorships
- **Integrations**: YouTube API (latest videos), Cloudflare Turnstile (spam protection)

## File Structure

- `src/app/` — Next.js App Router pages
- `src/components/` — React components (.tsx)
- `src/lib/` — Utilities, Prisma client, auth helpers
- `prisma/` — Database schema

## Commands

- `npm run dev` — Start development server
- `npm run build` — Build for production
- `npm run db:push` — Push Prisma schema to database
- `npm run db:studio` — Open Prisma Studio

## Related Context

- See CONVENTIONS.md for coding standards
- See CURRENT.md for active work
