# 2025-08-17_OWASP-Top10-2021 

## OWASP Top 10 (2021) – TryHackMe

**Overview:**  
Covered the 10 most critical web security risks and practiced exploitation on lab targets. Focus was on understanding vulnerable patterns, reproducing issues, and thinking like a tester (observe → test → exploit → confirm).

### Categories Covered
1. Broken Access Control (incl. **IDOR**)  
2. Cryptographic Failures  
3. Injection (e.g., SQLi)  
4. Insecure Design  
5. Security Misconfiguration  
6. Vulnerable & Outdated Components  
7. Identification & Authentication Failures  
8. Software & Data Integrity Failures  
9. Security Logging & Monitoring Failures  
10. Server-Side Request Forgery (SSRF)

### Hands-On Highlights
- **IDOR:** Bypassed authorization by manipulating identifiers in requests.  
- **Cryptographic Failures:** Observed how weak/misused crypto leaks sensitive data.  
- **Injection:** Demonstrated impact of unsanitized input on queries/commands.

### Pentester Workflow Basics
- Accessed targets (VPN/AttackBox), browsed the app, and inspected requests/responses.  
- Modified parameters to test access control and input handling.  
- Confirmed findings with repeatable steps and clear evidence.

### Skills Strengthened
- Recognizing vulnerable web patterns quickly.  
- Applying practical, low-noise tests before heavy tooling.  
- Building a clean path from observation to exploitation to proof.

**Progress:** 23 tasks completed, +208 points.
