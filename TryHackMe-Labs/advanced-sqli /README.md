# TryHackMe — SQL Injection (SQLi) Summary

## What I Practiced
- How unsanitized input alters SQL queries (read/modify data, sometimes OS command exec).
- Fingerprinting DB engines (MySQL, MSSQL, PostgreSQL) and tailoring payloads to features.
- Bypassing filters (no quotes, no spaces, keyword blocks) and exploiting non-UI inputs (headers).

## Core Payloads & Bypasses
- Classic truthy: `' OR 1=1--`
- Space evasion: `/**/`, `%0A` (newline), `%09` (tab) → `1/**/OR/**/1=1--`
- No-quote style: numeric comparisons / `CONCAT()` / `CHAR()` to build strings
- Header SQLi: inject via `User-Agent`/`X-Forwarded-For` if the app stores headers in DB
- Unsafe stored procedures (dynamic SQL) are injectable if parameters aren’t sanitized

## Out-of-Band (OOB) Exfil
- Use DNS/SMB/file-write paths when results aren’t reflected:
  - Encode data into DNS queries or write to a file (e.g., `/tmp/out.txt`) and retrieve it

## Engine Highlights
- Identify engine: `SELECT version()` / `@@version`
- MSSQL: `xp_cmdshell` (if enabled) can reach OS
- MySQL: `LOAD_FILE`, `INTO OUTFILE` (permissions dependent)
- PostgreSQL: `version()`, COPY/file techniques

## Tools
- **Burp Suite**: intercept/modify parameters & headers; replay payloads
- **sqlmap**: automate detection/exploitation (`--dbs`, `--tables`, `--dump`, tamper options)

## Defenses (for devs/blue teams)
- Parameterized queries / prepared statements (no string-concatenated SQL)
- Input validation + contextual output encoding
- Least-privilege DB accounts; restrict file/network capabilities
- Safe stored procedures (no dynamic SQL) + proper error handling/logging
- Continuous testing (SAST/DAST), SQLi test cases, and WAF rules

**In short:** I practiced how SQLi works, how to bypass naïve filters, how to exfiltrate data when it’s not reflected, how to fingerprint and leverage DB-specific features, and the controls that prevent these attacks.
