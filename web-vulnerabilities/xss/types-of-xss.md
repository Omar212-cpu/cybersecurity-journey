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

## 2. Stored XSS

### Description
Stored XSS occurs when malicious user input is saved on the server (e.g., in a database) and later rendered to other users without proper sanitization or encoding.

The payload is persistent and executes whenever the affected page is loaded.

---

### Example

*Input submitted (e.g., comment field):*
�
alert(1)

*Stored in database → displayed later:*
``html
<div class="comment">
  <script>alert(1)</script>
</div>
The script executes when any user views the page.

Common Locations:
Comment sections
User profiles
Reviews or feedback forms
Chat/messages

Impact:
Affects multiple users
Session hijacking
Account takeover
Worm-like spreading (self-propagating payloads)

Notes:
Does not require victim interaction aft


## 3. DOM-Based XSS

### Description
DOM-Based XSS occurs when client-side JavaScript processes user-controlled input and updates the DOM without proper sanitization.

The vulnerability exists entirely in the browser, not in the server response.

---

### Example

*JavaScript code:*
``javascript
var input = new URLSearchParams(window.location.search).get("q");
document.write("<p>" + input + "</p>");
URL:

/search?q=<script>alert(1)</script>
The script executes in the browser.

Common Locations:
URL parameters
Fragments (#)
Client-side routing
JavaScript functions like:
document.write
innerHTML
eval

Impact:
Same as other XSS types:
Session hijacking
Account takeover
DOM manipulation

Notes:
Not visible in server response
Requires analyzing JavaScript code
Often found using Burp + browser DevTools
