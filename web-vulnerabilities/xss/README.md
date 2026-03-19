# Cross-Site Scripting (XSS)

## Overview
Cross-Site Scripting (XSS) is a web application vulnerability that occurs when user-controlled input is included in a web page without proper output encoding or sanitization.

This allows attackers to inject and execute malicious JavaScript in the victim’s browser.

---

## Types of XSS

### 1. Reflected XSS
Occurs when user input is immediately reflected in the server response and executed in the browser.

### 2. Stored XSS
Occurs when malicious input is stored on the server (e.g., database) and executed when users access the affected page.

### 3. DOM-Based XSS
Occurs when client-side JavaScript processes user input and dynamically updates the DOM without proper sanitization.

---

## Impact

- Session hijacking (stealing cookies)
- Account takeover
- Performing actions on behalf of the user
- Phishing and UI manipulation
- Data exfiltration

---

## Testing Approach

1. Identify all user-controlled inputs (parameters, forms, headers)
2. Check for reflection of input in responses
3. Determine context (HTML, attribute, JavaScript)
4. Test basic payloads (e.g., <script>alert(1)</script>)
5. Adjust payload based on context and filters
6. Confirm execution
7. Assess impact

---

## Prevention

- Proper output encoding (context-aware)
- Input validation
- Use secure frameworks
- Implement Content Security Policy (CSP)
- Avoid unsafe JavaScript functions (e.g., innerHTML, eval)

---

## Tools Used

- Burp Suite
- Browser DevTools
- Manual testing techniques
