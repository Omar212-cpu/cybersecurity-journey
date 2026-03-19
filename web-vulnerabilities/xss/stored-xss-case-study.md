# Stored XSS – Comment Section

## Target Overview

- Application: Blog platform
- Feature: Comment submission
- Endpoint: /post/{id}/comment

---

## Vulnerability Discovery

The application allows users to submit comments that are stored and displayed to other users.

Test input:
test123

The input was successfully stored and displayed when revisiting the page.

---

## Context Analysis

The comment is rendered in HTML context:

html
<div class="comment">
  test123
</div>
No output encoding is applied.
Proof of Concept (PoC)
Payload submitted:

<script>alert(1)</script>
 id="n0y2kp"

Result:

- Payload stored in database
- Executes whenever any user views the page

---

## Impact

An attacker can exploit this vulnerability to:

- Affect multiple users
- Steal session cookies
- Perform actions on behalf of victims
- Inject persistent malicious scripts

---

## Severity

High (persistent and affects multiple users)

---

## Recommendation

- Apply proper output encoding on all stored content
- Validate and sanitize input before storage
- Implement Content Security Policy (CSP)
