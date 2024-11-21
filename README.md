# Ansible Server Preparation Playbook

## Overview
This project prepares servers with specific configurations:
1. Encrypts the second disk and the root-adjacent partition.
2. Disables CPU C-state and switches to performance mode.
3. Renames the active network interface and displays details.

## Requirements
- Ansible 2.9+ installed on the control machine.
- Ensure SSH access and `sudo` permissions to the target server.

## Usage
### Step 1: Define the Inventory
Edit `inventory/hosts` with the server details.

### Step 2: Run the Playbook
```bash
ansible-playbook -i inventory/hosts playbooks/prepare_server.yml
