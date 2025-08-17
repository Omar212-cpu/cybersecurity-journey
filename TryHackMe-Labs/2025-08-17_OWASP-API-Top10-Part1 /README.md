2025-08-17_OWASP-API-Top10-Part1
OWASP API Security Top 10 – Part 1 (TryHackMe)

Overview: Studied API fundamentals (requests, headers, auth tokens, responses) and reproduced common API-specific weaknesses on a lab target. Focused on recognizing insecure patterns, proving impact, and documenting fixes.

Categories Covered

BOLA / IDOR (Broken Object Level Authorization) – accessed other users’ objects by manipulating IDs/path params.

BUA (Broken User Authentication) – observed weak token/session handling that enables impersonation.

Excessive Data Exposure – identified sensitive fields returned in JSON that should not be exposed.

Lack of Rate Limiting – demonstrated how unthrottled endpoints increase abuse/DoS risk.

Hands-On Highlights

Crafted and modified requests in a REST client (headers, auth tokens, query/path params).

Flipped insecure trust-by-client flags (e.g., isAdmin: 1) and verified unauthorized data access.

Enumerated predictable IDs to retrieve admin objects and extract the flag from JSON responses.

Mapped each exploit path back to the relevant OWASP API Top 10 category.

Techniques & Checks

Enforce per-request object authorization on server side.

Minimize response payloads (least data exposure).

Harden token lifecycle & storage (scope, expiry, signature; validate on every request).

Add rate limiting, anomaly detection, and audit logging around sensitive endpoints.
