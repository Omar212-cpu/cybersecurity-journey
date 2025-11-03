CORS controls which external origins can interact with a web application’s resources. A misconfigured CORS policy can expose sensitive data by allowing unauthorized origins to make credentialed requests.

What I practiced:

Identified CORS misconfigurations by inspecting request and response headers.

Understood the impact of insecure combinations like
Access-Control-Allow-Origin: * or null with
Access-Control-Allow-Credentials: true.

Built and tested a small JavaScript PoC to demonstrate how an attacker-controlled origin could read authenticated responses.

Learned secure configurations and mitigations (strict whitelisting, removing credentials, proper SameSite cookie use).

Takeaway:
Even a single incorrect CORS header can leak private user data. Understanding how browsers enforce origin policies is essential for secure web development and pentesting.
