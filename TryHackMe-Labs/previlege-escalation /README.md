Windows Privilege Escalation — TryHackMe

Goal: move from a low-privilege Windows user to Administrator/SYSTEM using both manual techniques and targeted exploits.

What I practiced

Credential harvesting: pulled saved creds from common locations (registry, config files, scripts).
Example (PuTTY):

HKEY_CURRENT_USER\Software\SimonTatham\PuTTY\Sessions


→ recovered thom.smith / CoolPass2021. Noted similar risks for WinSCP/RDP clients.

Quick wins: searched for plaintext passwords in config files, scheduled tasks, registry keys—fast, low-noise escalation paths.

Service misconfigurations: identified services running as SYSTEM with writable paths/unquoted paths; replacing the service binary yielded a SYSTEM shell.

Dangerous privileges: reviewed whoami /priv and abused high-risk rights (e.g., SeImpersonatePrivilege) using RogueWinRM.exe + nc for elevated shells.

Vulnerable software: leveraged outdated/misconfigured apps (running as SYSTEM) to trigger privileged code execution.

Tooling:

WinPEAS – automated enumeration

PowerUp – PowerShell checks for privesc paths

RogueWinRM – privilege abuse to SYSTEM

Manual registry & file hunts

Outcomes

Extracted stored credentials from the registry.

Achieved SYSTEM via service abuse / dangerous privilege exploitation.

Built a repeatable Windows privesc workflow (enum → validate → exploit → verify).

Completed the Jr Penetration Tester path milestones for Windows post-exploitation.
