# Playbooks Directory

## Description
This directory contains the main playbooks for configuring and preparing servers for operation.

## Playbooks
- `prepare_server.yml`: The primary playbook for server preparation, which includes roles for CPU, network, and disk encryption configuration.
- `server_facts.yml`: A playbook for gathering and displaying server facts for debugging and validation.

## Usage
To run a playbook, use the following command:
```bash
ansible-playbook -i inventory/hosts playbooks/<playbook_name>.yml
