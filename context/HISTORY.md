# Project History

> Significant changes and decisions. Not a git log — human-readable context.

---

## 2026

### January 2026

#### 2026-01-11 — Added .context/ folder

**Type**: Feature

**What changed:**
Added Universal Context pattern for LLM-assisted development.

**Why:**
Setting up portfolio as demo project for "The Context Layer" YouTube tutorial.

**Files added:**

- `.context/PROJECT.md`
- `.context/CONVENTIONS.md`
- `.context/ARCHITECTURE.md`
- `.context/CURRENT.md`
- `.context/HISTORY.md`

---

## Previous (Before .context/)

> Add significant past decisions here as you remember them.

#### Example: 2FA Implementation

**Type**: Security

**What changed:**
Added two-factor authentication to admin section.

**Why:**
Protect admin dashboard from unauthorized access.

**Approach:**

- Used `otplib` for TOTP generation
- QR code setup flow with `qrcode` package
- Verify page at `/verify-2fa`

---

## Technical Debt

_Track things you want to fix later._

- [ ] (Add items as you identify them)

---

## Deprecated Patterns

_Document old approaches you've moved away from._

- None yet
