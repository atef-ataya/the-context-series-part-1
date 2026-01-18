# System Architecture

## High-Level Overview

```
┌─────────────────────────────────────────────────────────────┐
│                        VERCEL                               │
│  ┌─────────────────────────────────────────────────────┐   │
│  │                  Next.js App                         │   │
│  │  ┌──────────┐  ┌──────────┐  ┌──────────────────┐   │   │
│  │  │  Public  │  │  Admin   │  │   API Routes     │   │   │
│  │  │  Pages   │  │  Pages   │  │   /api/*         │   │   │
│  │  └──────────┘  └────┬─────┘  └────────┬─────────┘   │   │
│  │                     │                  │             │   │
│  │                     ▼                  ▼             │   │
│  │              ┌─────────────────────────────┐         │   │
│  │              │      NextAuth + 2FA         │         │   │
│  │              └─────────────────────────────┘         │   │
│  └─────────────────────────┬───────────────────────────┘   │
└────────────────────────────┼───────────────────────────────┘
                             │
        ┌────────────────────┼────────────────────┐
        ▼                    ▼                    ▼
┌──────────────┐    ┌──────────────┐    ┌──────────────┐
│  PostgreSQL  │    │  UploadThing │    │  YouTube API │
│   (Prisma)   │    │   (Files)    │    │   (Videos)   │
└──────────────┘    └──────────────┘    └──────────────┘
```

## Data Flow

### Public Visitor

```
Visitor → Public Pages → Server Components → Prisma → PostgreSQL
                                          → YouTube API (videos)
```

### Admin User

```
Admin → Login → NextAuth → 2FA Check → Admin Dashboard
                                     → Prisma → PostgreSQL
                                     → UploadThing (images)
```

## Key Components

### Authentication Flow

1. User enters email/password
2. NextAuth validates credentials
3. If 2FA enabled → redirect to `/verify-2fa`
4. User enters TOTP code from authenticator app
5. Session created, redirect to admin

### Blog System

- **Editor**: TipTap rich text editor
- **Storage**: Content stored in PostgreSQL via Prisma
- **Images**: Uploaded to UploadThing, URLs stored in DB
- **Rendering**: Server-side with DOMPurify sanitization

### YouTube Integration

- Fetches latest videos via YouTube Data API
- Displays in `LatestVideosSection` component
- Thumbnails loaded from `img.youtube.com`

## External Services

| Service              | Purpose         | Auth Method       |
| -------------------- | --------------- | ----------------- |
| PostgreSQL           | Database        | Connection string |
| UploadThing          | File uploads    | API key           |
| YouTube API          | Video data      | API key           |
| Cloudflare Turnstile | Spam protection | Site key          |
| Vercel               | Hosting         | Git integration   |

## Security Considerations

- 2FA required for admin access
- Rate limiting on API routes (`lib/rate-limit.ts`)
- Turnstile on contact form
- Environment variables for all secrets
- DOMPurify for HTML sanitization
