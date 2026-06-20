# Linux Server Security Baseline Auditor

A read-only Bash toolkit for reviewing the security posture of Linux servers and producing escalation-ready evidence.

## Scope

- SSH daemon configuration and root-login policy
- Password-authentication and empty-password settings
- Firewall status for UFW, firewalld, or nftables
- SELinux or AppArmor status
- Privileged groups and sudo configuration
- World-writable files in selected system paths
- Listening services and exposed ports
- Failed authentication events
- Automatic-update configuration
- Time synchronisation and audit service status
- Text and JSON summary reports

## Usage

```bash
chmod +x src/linux_security_baseline_audit.sh
sudo ./src/linux_security_baseline_audit.sh
```

Optional output path:

```bash
sudo ./src/linux_security_baseline_audit.sh --output /tmp/security-audit
```

## Safety

The script is diagnostic-only. It does not harden SSH, modify firewall rules, change users, install packages, or edit security policy.

## Interpretation

Findings are evidence for technician review, not automatic proof of compromise or non-compliance. Validate every deviation against business requirements, distribution defaults, and approved security policy.

## Validation checklist

- Test on Ubuntu/Debian and one RHEL-compatible system
- Test with OpenSSH absent and present
- Confirm all checks fail gracefully when tools are unavailable
- Review output for secrets before sharing
- Compare findings with the organisation's approved baseline

## Professional value

Demonstrates Linux security support, least-privilege thinking, safe evidence collection, and the ability to translate technical findings into actionable escalation notes.

## Author

Dewald Pretorius — L2 IT Support Engineer
