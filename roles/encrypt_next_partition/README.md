# Role: encrypt_next_partition

## Overview

The `encrypt_next_partition` role automates the encryption of the partition that exists on the same disk as the root partition but is located immediately after it. This role performs the following steps:

1. Identifies the root partition and its disk.
2. Locates the next partition on the same disk.
3. Ensures the partition is neither encrypted nor mounted.
4. Encrypts the partition using `cryptsetup`.
5. Opens the encrypted partition and creates a filesystem.
6. Mounts the encrypted partition to the specified path.
7. Updates `/etc/crypttab` and `/etc/fstab` to persist the setup across reboots.

This role is idempotent, meaning it can be safely rerun without disrupting the system.

---

## Requirements

- The target system must have `cryptsetup` installed (the role installs it if not already present).
- The disk must have a partition available immediately after the root partition.

---

## Role Variables

### Mandatory Variables
You must define the following variables for the role to function:
- `mount_path`: The directory where the encrypted partition will be mounted (e.g., `/mnt/encrypted_next`).

### Example Variable Configuration
```yaml
mount_path: /mnt/encrypted_next
