TryHackMe — NoSQL Injection (MongoDB) | Overview: practiced exploiting NoSQLi on a MongoDB-backed app where user input is parsed directly into queries;
used Burp to intercept and modify params/JSON/headers/cookies and confirmed impact via status/body-size changes.
| What I practiced: auth bypass with operators (`username[$ne]=x&password[$ne]=x`), truthy numeric comparisons (`username=admin&password[$gt]=0`), 
regex validation bypass (`field[$regex]=^.{7}$`), URL-encoding of operators/brackets (`password%5B%24ne%5D=x`), 
alternate vectors in headers (e.g., User-Agent), and boolean probing by watching 200/401/500 or length deltas.
| Sample payloads: 1) username\[\$ne]=x\&password\[\$ne]=x  2) username=admin\&password\[\$gt]=0  3) field\[\$regex]=^.{7}\$  4) 
JSON: {"username":{"\$ne"\:null},"password":{"\$ne"\:null}}. 
| Workflow: map inputs → replace literals with `$ne`/`$gt`/`$regex` → compare responses → tighten patterns 
(e.g., `^admin$`, `^.{7}$`) → enumerate and extract with low-noise checks → record request, payload, behavior, impact. 
| Defenses: enforce strict schemas/allowlists for request shapes; use driver APIs and object shaping (never build JSON from user input);
disable/guard `$where` (server-side JS); normalize/strip keys starting with `$`; least-privilege DB users; log/alert on operator use from user-controlled fields;
add proper authorization on queries. | Notes: observed requests like `GET /?err=1`, tested cookie/header vectors, 
used regex `^.{7}$` to satisfy validation, completed 8 tasks. | Tags: NoSQL, MongoDB, Injection, BurpSuite, AppSec, TryHackMe.
