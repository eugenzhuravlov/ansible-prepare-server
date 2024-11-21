# Role: encrypt_second_disk

## Description
This Ansible role encrypts the specified partition using `cryptsetup`, creates a filesystem, and mounts it.

## Overview

The `encrypt_second_disk` role automates the encryption of a specified disk on the system using `cryptsetup`. It performs the following actions:
1. Validates that the specified disk exists.
2. Creates a partition on the disk if none exist.
3. Encrypts the partition using `cryptsetup luksFormat`.
4. Opens the encrypted partition and maps it.
5. Creates a filesystem on the encrypted partition.
6. Mounts the partition to the specified path.
7. Updates `/etc/crypttab` and `/etc/fstab` for persistence across reboots.

This role is designed to be reusable and idempotent, ensuring the process can be safely rerun without adverse effects.

---

## Requirements

- The target system must have `cryptsetup` installed. The role will install it if missing.
- The disk must be unmounted and not already in use.

---

## Role Variables

### Mandatory Variables
You must provide the following variables either in your inventory or in the playbook:
- `disk_name`: The name of the disk to encrypt (e.g., `/dev/xvdf`).
- `partition_name`: The name of the partition to create and encrypt (e.g., `/dev/xvdf1`).
- `encrypted_partition_name`: The name of the mapped encrypted partition (e.g., `encrypted_disk`).
- `mount_path`: The directory where the encrypted partition will be mounted (e.g., `/mnt/encrypted`).

### Example Inventory Configuration
```yaml
all:
  vars:
    disk_name: /dev/xvdf
    partition_name: /dev/xvdf1
    encrypted_partition_name: encrypted_disk
    mount_path: /mnt/encrypted
