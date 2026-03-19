# XSS Testing Methodology

## 1. Identify Input Points

Start by identifying all user-controlled inputs in the application:

- URL parameters
- Search fields
- Forms (login, comments, profile updates)
- HTTP headers (User-Agent, Referer)

---

## 2. Test for Reflection

Inject simple payloads to check if input is reflected:
test123

Look for where and how the input appears in the response.

---

## 3. Determine Context

Analyze where the input is reflected:

- HTML context → <p>input</p>
- Attribute context → <input value="input">
- JavaScript context → var x = "input"

Understanding the context determines the payload used.

---

## 4. Test Basic Payloads

Start with simple payloads:

alert(1)

If blocked or not working:
- Try breaking out of context
- Adjust payload based on filtering

---

## 5. Bypass Filters

If input is filtered or encoded:

- Try alternative payloads
- Break out of quotes or tags
- Use different encoding or injection techniques

---

## 6. Confirm Execution

Ensure that JavaScript executes:

- Alert box appears
- Code runs in browser console
- DOM is modified

---

## 7. Identify XSS Type

Classify the vulnerability:

- Reflected XSS
- Stored XSS
- DOM-Based XSS

---

## 8. Assess Impact

Evaluate what the attacker can do:

- Steal session cookies
- Perform actions as the user
- Modify page content
- Redirect users

---

## 9. Recommend Fix

- Output encoding (context-aware)
- Input validation
- Avoid unsafe JS functions
- Implement Content Security Policy (CSP)
