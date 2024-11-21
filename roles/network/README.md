# Network Role

## Description
This role is responsible for configuring network settings on the target servers. It includes tasks for renaming network interfaces and applying persistent configurations using Netplan.

## Tasks
- Identify the active network interface.
- Rename the active network interface to `net0`.
- Update the Netplan configuration to persist the new interface name.
- Apply the Netplan changes and ensure the renamed interface is functional.

## Usage
Include this role in your playbook targeting hosts that require network configuration updates. Example:

```yaml
- name: Configure network settings
  hosts: dev-network
  roles:
    - network
