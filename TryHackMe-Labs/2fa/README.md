# TryHackMe — Multi-Factor Authentication (MFA)

**Room type:** Walkthrough • **Difficulty:** Easy • **Tasks:** 8

## What I Practiced
- MFA factors & flows (knowledge, possession, inherence) and how OTPs work (HOTP/RFC4226, TOTP/RFC6238: shared secret + counter/time, drift/TTL).
- Where MFA plugs into **session management** (pre-auth vs post-auth) and how sessions/cookies are upgraded after second factor.
- Inspecting session cookies (e.g., `PHPSESSID=…`) in browser DevTools and tracing how they change across the MFA step.

## Attack Scenarios Demonstrated
- **OTP leakage:** Codes exposed via logs/URLs/client-side rendering.
- **Insecure verification:** Client-side checks, predictable or reused OTPs, missing server enforcement.
- **Rate-limit/lockout gaps:** Brute forcing OTPs without throttling/backoff.
- **Replay/Reuse:** Re-submitting a previously valid OTP or reusing a pre-MFA session.
- **Auto-logout bypass:** Keeping the session alive by reusing the cookie or racing the timeout.
- **Cookie weaknesses:** Missing `Secure`, `HttpOnly`, or `SameSite` flags; no session rotation after MFA.

## Blue-Team Hardening (Key Takeaways)
- **Bind OTPs** to user + nonce + short TTL; one-time use only; verify **server-side**.
- Enforce **rate limiting**, lockouts, and exponential backoff; monitor for **push-fatigue**/MFA bombing.
- **Rotate session IDs** after successful MFA; invalidate all pre-MFA sessions; destroy on logout.
- Set cookies with **`Secure` + `HttpOnly` + `SameSite=Strict`**; prefer HTTPS everywhere.
- Protect the flow: strict **redirect URI** handling, CSRF defenses on verification endpoints.
- Prefer **WebAuthn/FIDO2** or device-bound factors where possible.

## Summary
MFA raises the bar, but it doesn’t rescue weak **session management** or **app logic**. Testing the entire flow—enrollment → challenge → verification → session upgrade—caught issues like OTP leakage, missing throttling, and session reuse. This lab strengthened both my attacker mindset (where to poke) and defender checklist (what to harden).
