# Ansible Collection - ibt23sec5.system_show

## Prerequisites
At first you have to install the `psutil` python module on each node:

```
pip install psutil
```
Or ensure the installation via `pip` play before:

```yaml
---
- name: Install psutil
  pip:
    name: psutil
...
```

## Modules

### system_facts
Retrieves several facts about operating system, actual state and configuration:
- CPU usage
- memory usage
- disk usage
- network connections
- running processes including children

#### Options
* `subsets`: List of available subsets; returns all if empty
  Accepted subsets:
      - `boot_time`
      - `cpu_count`
      - `cpu_freq`
      - `cpu_percent`
      - `cpu_stats`
      - `cpu_times`
      - `cpu_times_percent`
      - `disk_io_counters`
      - `disk_partitions`
      - `disk_usage`
      - `hosts`
      - `net_connections`
      - `net_if_addrs`
      - `net_if_stats`
      - `net_io_counters`
      - `pids`
      - `resolv_conf`
      - `sensors_battery`
      - `sensors_fans`
      - `sensors_temperatures`
      - `swap_memory`
      - `users`
      - `virtual_memory`
* `pid_columns`: List of columns for `pids` subset (default values: `pid`, `name`, `username`)
  Accepted columns:
      - `children`
      - `cpu_affinity`
      - `cwd`
      - `threads`
      - `username`
      - `environ`
      - `uids`
      - `exe`
      - `memory_full_info`
      - `connections`
      - `cpu_percent`
      - `open_files`
      - `memory_percent`
      - `cmdline`
      - `name`
      - `num_threads`
      - `io_counters`
      - `nice`
      - `num_ctx_switches`
      - `terminal`
      - `status`
      - `cpu_times`
      - `create_time`
      - `gids`
      - `ppid`
      - `ionice`
      - `cpu_num`
      - `pid`
      - `memory_info`
      - `num_fds`
      - `memory_maps`

* `net_connections_kind`: Filters connection types related `net_connections` subset (default value: `inet`)
  Accepted subsets:
      - `inet`
      - `inet4`
      - `inet6`
      - `tcp`
      - `tcp4`
      - `tcp6`
      - `udp`
      - `udp4`
      - `udp6`
      - `unix`
      - `all`

#### Usage
```yaml
---
- host: all
  collections:
    - ibt23sec5.system_show
  tasks:
    # Returns all system facts
    - name: Get all system facts
      system_facts:

    # Returns only cpu_percent and cpu_times subsets
    - name: Get CPU metrics
      system_facts:
        subsets:
          - cpu_percent
          - cpu_times
...
```
