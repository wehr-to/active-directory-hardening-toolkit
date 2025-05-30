# 🏰 active-directory-hardening-toolkit

This repository contains security best practices, hardening scripts, detection logic, and blue team simulations for **securing Windows and Active Directory environments**. It’s built to reflect how real attackers move laterally — and how defenders can shut them down.

## 🎯 Why This Exists

Active Directory is **the crown jewel** in most enterprise environments. When misconfigured, it allows:
- Credential harvesting
- Lateral movement
- Privilege escalation
- Stealthy persistence

This toolkit is for defenders who want to:
- Harden AD without breaking usability
- Simulate attack paths before the attackers do
- Detect abuse via logs and custom rules
- Automate cleanup of stale accounts, GPOs, and misconfigs

## 🔐 What's Covered

| Area | Focus |
|------|-------|
| `ad-basics/` | Key AD components, trust relationships, attack paths |
| `hardening-checklists/` | GPO settings, DC hardening, Kerberos configs |
| `detection-and-monitoring/` | Event IDs, ticket abuse detection, SIEM-ready logging |
| `scripts-and-automation/` | PowerShell scripts to audit & enforce AD hygiene |
| `logging-and-telemetry/` | Sysmon configs, audit policies, telemetry mapping |
| `attack-surface-reduction/` | Admin tiering, SMB/LDAP/NTLM mitigation |
| `labs-and-simulations/` | Purple-team labs (AS-REP roasting, golden ticket drills) |

## 🧠 Sample Play: Detect Golden Ticket Abuse

- **Tactic**: Attacker creates forged TGT for a high-privilege user  
- **Detection**: Look for Event ID 4769 with high-value SPNs + impossible geography  
- **Prevention**: 
  - Constrain delegation
  - Rotate KRBTGT
  - Monitor SIDHistory changes

## 🧰 Sample Script: Password Policy Check

```powershell
# password-policy-check.ps1
Get-ADDefaultDomainPasswordPolicy | Select-Object MinPasswordLength, LockoutThreshold, MaxPasswordAge
