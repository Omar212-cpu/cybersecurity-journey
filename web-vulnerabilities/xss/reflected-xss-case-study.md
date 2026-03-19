## Target Overview

- Application: E-commerce website
- Feature: Search functionality
- Endpoint: /search?q=

---

## Vulnerability Discovery

The application reflects user input from the q parameter directly into the response without proper sanitization.

Initial test:
test123

The input was reflected in the response, confirming that the parameter is injectable.

---

## Context Analysis

The input is reflected inside HTML context:

html
<p>You searched for: test123</p>
No output encoding is applied.
Proof of Concept (PoC)
Payload used:

<script>alert(1)</script>
 id="4gqz1m"

Result:

- JavaScript executed in the browser
- Alert box displayed

---

## Impact

An attacker can exploit this vulnerability to:

- Steal session cookies
- Perform actions on behalf of the user
- Inject malicious scripts
- Redirect users to phishing pages

---

## Severity

Medium to High (depending on context and user interaction)

---

## Recommendation

- Implement proper output encoding
- Validate and sanitize user input
- Use secure frameworks with automatic escaping
- Apply Content Security Policy (CSP)
