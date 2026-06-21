# Linux Server Security Baseline Auditor

A Linux support toolkit for auditing server security posture and applying selected guarded baseline repairs.

## Audit script

```bash
chmod +x src/linux_security_baseline_audit.sh
sudo ./src/linux_security_baseline_audit.sh
```

The audit reviews SSH policy, firewall state, SELinux or AppArmor, privileged groups, sudo configuration, exposed services, failed authentication, automatic updates, time synchronisation and audit services.

## Repair script

Preview configuration-permission repair:

```bash
chmod +x src/linux_security_baseline_repair.sh
sudo ./src/linux_security_baseline_repair.sh --fix-permissions --dry-run
```

Repair SSH and sudo configuration permissions:

```bash
sudo ./src/linux_security_baseline_repair.sh --fix-permissions
```

Enable an installed audit or time service:

```bash
sudo ./src/linux_security_baseline_repair.sh --enable-audit
sudo ./src/linux_security_baseline_repair.sh --enable-time-sync
```

Create a validated SSH policy drop-in:

```bash
sudo ./src/linux_security_baseline_repair.sh \
  --ssh-root-login no \
  --ssh-password-auth no
```

## What the repair does

- Corrects standard permissions on SSH and sudo configuration files.
- Validates sudo configuration with `visudo`.
- Can enable installed audit and time-synchronisation services.
- Can create a managed SSH drop-in, validate it with `sshd -t`, and reload SSH.
- Backs up an existing managed SSH drop-in before replacement.
- Supports confirmation prompts, dry-run, logs and post-repair verification.

## Safety and limitations

SSH policy changes can lock out remote users. Confirm working key-based access and an emergency console path before disabling password authentication. Firewall policy and user accounts are not changed by this tool.

## Author

Dewald Pretorius — L2 IT Support Engineer
