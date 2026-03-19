# DOM-Based XSS – Search Functionality

## Target Overview

- Application: E-commerce website
- Feature: Search functionality
- Endpoint: /search?q=

---

## Vulnerability Discovery

The application uses client-side JavaScript to read user input from the URL and dynamically update the page.

Test input:
test123

The value is processed by JavaScript and written to the page.

---

## Context Analysis

The input is handled in client-side JavaScript:

javascript
var query = new URLSearchParams(window.location.search).get("q");
document.write("<p>" + query + "</p>");
The input is directly inserted into the DOM without sanitization.
Proof of Concept (PoC)
Payload used:

<script>alert(1)</script>
 id="dom3"

Result:

- JavaScript executed in the browser
- Alert box displayed

---

## Impact

An attacker can exploit this vulnerability to:

- Execute arbitrary JavaScript in the victim’s browser
- Steal sensitive data
- Manipulate the page content
- Perform actions on behalf of the user

---

## Severity

Medium to High (depending on user interaction)

---

## Recommendation

- Avoid using unsafe functions like document.write and innerHTML
- Sanitize user input before inserting into the DOM
- Use safe DOM APIs (e.g., textContent)
- Implement Content Security Policy (CSP)
