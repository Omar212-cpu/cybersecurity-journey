## Client–Server Trust Boundaries

### Key Insight
Anything running in the browser is attacker-controlled. Front-end logic cannot enforce security.

### Why this matters
Many vulnerabilities exist because applications:
- trust client-side validation
- hide functionality in the UI instead of restricting it server-side
- assume users follow the intended workflow

This leads to issues like:
- IDOR
- logic flaws
- unauthorized actions via crafted requests

### How I approach testing
I ignore the UI and interact directly with requests, parameters, and endpoints to test what the server actually enforces.

### Fix mindset
Authorization, validation, and business logic must always be enforced on the server, never the client.
