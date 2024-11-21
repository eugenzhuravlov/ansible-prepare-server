# Role: CPU

## Overview

The `cpu` role provides tasks to optimize CPU performance on a server by:
1. Disabling CPU C-states to reduce latency.
2. Configuring the CPU frequency scaling governor to `performance` mode.

This role is designed for systems where CPU performance is critical and power-saving features are not required.

---

## Features

- Disables CPU C-states by updating the GRUB configuration.
- Configures the CPU governor using either:
  - **cpupower**: A standard Linux tool for managing CPU performance.
  - **cpufrequtils**: Another tool for directly setting CPU frequency governors.
- Includes handlers for applying GRUB updates when required.

### Reboot Handling
- The role ensures that the CPU governor setting persists across reboots using one of the following methods:
  - Updating GRUB to disable Intel pstate and enable cpufreq scaling.
  - Configuring `/etc/default/cpufrequtils` for systems using `cpufrequtils`.
  - Using the `cpupower` systemd service for systems with `cpupower`.

### Dynamic Checks
- The role dynamically checks for CPU scaling support. If unsupported, tasks are skipped gracefully, and a debug message is displayed.

### Default Variables

| Variable            | Description                                             | Default Value           |
|---------------------|---------------------------------------------------------|-------------------------|
| `governor_tool`     | The tool to use for governor configuration (`cpupower` or `cpufrequtils`). | `cpufrequtils`          |
| `cpu_governor_mode` | The CPU governor mode to set (e.g., `performance`).      | `performance`           |
