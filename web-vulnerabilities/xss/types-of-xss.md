# Types of Cross-Site Scripting (XSS)

## 1. Reflected XSS

### Description
Reflected XSS occurs when user input is immediately included in the server response without proper sanitization or encoding.

The payload is not stored on the server — it is reflected directly in the response.

---

### Example

*Request:*
/search?q=alert(1)

*Response:*

<p>You searched for: <script>alert(1)</script></p>
The script executes in the victim’s browser.

Common Locations:
Search parameters
URL parameters
Error messages
Form inputs


Impact:
Session hijacking
Account takeover
Phishing attacks
Redirecting users


Notes:
Requires user interaction (e.g., clicking a crafted link)
Often found during parameter testing
