Room type: Walkthrough • Difficulty: Medium • Tasks: 10

What I practiced:

Identifying SSTI sinks across popular engines (PHP/Smarty, NodeJS/Pug, Python/Jinja2) and confirming execution with arithmetic probes (e.g., {{7*7}}, #{7*7}, ${7*7}).

Moving from proof-of-execution to data access/RCE: reading variables, reaching filesystem/OS where features allow, and extracting flags in the PHP (Smarty) and Python (Jinja2) labs.

Hunting injection points beyond obvious form fields (headers, cookies, hidden inputs) and understanding context (escaped vs raw blocks, filters, sandbox limitations).

Automating exploitation with a repeatable process and tooling (e.g., tplmap) to fingerprint the engine, test payloads, and escalate.

Mini-cheatsheet (generic probes):

Jinja2 / Twig / Liquid style: {{7*7}}

Pug/Jade: #{7*7}

ERB / Velocity / generic EL: ${7*7}

Smarty quick info: {$smarty.version} (then escalate via permitted plugins/functions)

Typical escalation path used: detect → enumerate engine/features → access objects (config/env) → file read / command execution (when supported) → evidence/flag.

Mitigation notes:

Never render untrusted input as a template; pass it only as data.

Use safe/strict render APIs, enable auto-escaping, and disable dangerous helpers/plugins.

Sandbox or containerize template execution; least privilege for the app user.

Validate/encode user input by context, and log/alert on template errors or unexpected render tokens.

Artifacts: Screenshots and notes are saved in my repo (TryHackMe-Labs/SSTI).
