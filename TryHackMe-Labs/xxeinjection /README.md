Completed the TryHackMe XXE Injection room and practiced how unsafe XML parsing can be abused to read local files, trigger SSRF, 
and exfiltrate data in-band or out-of-band: I reviewed XML/DTD basics, general vs. parameter entities, and built payloads for classic file read 
(file:///etc/passwd), PHP filter base64 reads, SSRF to internal endpoints, and OOB exfiltration via a remote DTD that forces the victim to call back with stolen
content; I followed a repeatable workflow (locate XML inputs—SOAP/SAML/uploads/APIs—probe with a minimal <!DOCTYPE>, attempt in-band reads, 
fall back to OOB when output is blind, then try SSRF), and documented evidence (requests/responses, base64 decodes, attacker server hits);
key mitigations include disabling DTD/external entities in parsers (e.g., Java SAX/DOM/StAX features, .NET XmlReaderSettings.DtdProcessing=Prohibit/XmlResolver=null,
Python defusedxml, PHP safe libxml flags), validating against whitelisted schemas, isolating parser egress (no network/file access), and sanitizing errors; 
biggest lesson: defaults differ by stack, OOB techniques are essential when responses don’t reflect data,
and XXE often chains into SSRF for deeper internal access.
