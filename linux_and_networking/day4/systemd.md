## Unit

| Option                   | Purpose                                            |
| ------------------------ | -------------------------------------------------- |
| `Description`            | Human-readable description of the service          |
| `Documentation`          | Links to docs (man pages, URLs)                    |
| `After`                  | Start this unit **after** specified units          |
| `Before`                 | Start this unit **before** specified units         |
| `Requires`               | Hard dependency (if this fails, service stops)     |
| `Wants`                  | Soft dependency (tries to start, but not critical) |
| `BindsTo`                | Stronger than Requires; stops if bound unit stops  |
| `PartOf`                 | Restart/stop together with another unit            |
| `Conflicts`              | Cannot run simultaneously with listed units        |
| `ConditionPathExists`    | Run only if a file exists                          |
| `ConditionPathNotExists` | Run only if a file does NOT exist                  |
| `ConditionHost`          | Run only on specific host                          |
| `AssertPathExists`       | Fail if path does not exist                        |
| `StartLimitIntervalSec`  | Time window for restart attempts                   |
| `StartLimitBurst`        | Max restart attempts in interval                   |

## Service

### Execution & Process
| Option             | Purpose                       |
| ------------------ | ----------------------------- |
| `ExecStart`        | Main command to start service |
| `ExecStartPre`     | Commands before main start    |
| `ExecStartPost`    | Commands after start          |
| `ExecStop`         | Command to stop service       |
| `ExecStopPost`     | Cleanup after stopping        |
| `ExecReload`       | Command for reload            |
| `WorkingDirectory` | Working directory             |
| `Environment`      | Set environment variables     |
| `EnvironmentFile`  | Load env variables from file  |

### Service Type 
| Option | Purpose                                                         |
| ------ | --------------------------------------------------------------- |
| `Type` | Service type (`simple`, `forking`, `oneshot`, `notify`, `idle`) |

simple → default (Node apps, scripts)
forking → daemon processes
oneshot → runs once and exits

### Restart & Reliability
| Option            | Purpose                                       |
| ----------------- | --------------------------------------------- |
| `Restart`         | Restart policy (`no`, `on-failure`, `always`) |
| `RestartSec`      | Delay before restart                          |
| `TimeoutStartSec` | Start timeout                                 |
| `TimeoutStopSec`  | Stop timeout                                  |
| `WatchdogSec`     | Watchdog timeout                              |

### User and Permissions
| Option  | Purpose               |
| ------- | --------------------- |
| `User`  | Run as specific user  |
| `Group` | Run as specific group |
| `UMask` | File permission mask  |

### Resource Control
| Option        | Purpose            |
| ------------- | ------------------ |
| `LimitNOFILE` | Max open files     |
| `LimitNPROC`  | Max processes      |
| `CPUQuota`    | CPU usage limit    |
| `MemoryLimit` | Memory usage limit |
| `Nice`        | Process priority   |

### Security
| Option                  | Purpose                      |
| ----------------------- | ---------------------------- |
| `PrivateTmp`            | Isolated `/tmp`              |
| `ProtectSystem`         | Restrict filesystem access   |
| `ProtectHome`           | Restrict home dir access     |
| `NoNewPrivileges`       | Prevent privilege escalation |
| `CapabilityBoundingSet` | Limit Linux capabilities     |


### Logging
| Option             | Purpose                               |
| ------------------ | ------------------------------------- |
| `StandardOutput`   | Output handling (journal, file, etc.) |
| `StandardError`    | Error output handling                 |
| `SyslogIdentifier` | Custom log tag                        |


## Install
| Option            | Purpose                                     |
| ----------------- | ------------------------------------------- |
| `WantedBy`        | Target that will include this service       |
| `RequiredBy`      | Hard dependency target                      |
| `Alias`           | Alternative names                           |
| `Also`            | Additional units to enable/disable together |
| `DefaultInstance` | For template units                          |


## What is WantedBy?
Which systemd target will “want” (include) this service when it is enabled

### What is a target?

In systemd, a target is a group of services that represents a system state.

Examples:
multi-user.target → normal server mode (no GUI)
graphical.target → GUI desktop mode
network.target → networking ready

Example:
```bash
[Install]
WantedBy=multi-user.target
```

This means:
“When this service is enabled, attach it to multi-user.target so it starts automatically when the system reaches that state.”

So when we run 
```bash
systemctl enable myservice
```

systemd creates a syslink
/etc/systemd/system/multi-user.target.wants/myservice.service
This folder (*.wants/) defines what services that target should start.

So, when multi-user.target starts
- It looks inside its .wants/ directory
- It starts all services listed there


## Common systemd targets


### Boot & System State Targets

| Target              | Purpose                                |
| ------------------- | -------------------------------------- |
| `default.target`    | Default boot target (like entry point) |
| `multi-user.target` | Non-GUI system (servers)               |
| `graphical.target`  | Full GUI desktop                       |
| `rescue.target`     | Single-user rescue mode                |
| `emergency.target`  | Minimal shell, critical recovery       |


### System Initialization Targets
| Target             | Purpose                                 |
| ------------------ | --------------------------------------- |
| `basic.target`     | Basic system initialized                |
| `sysinit.target`   | Low-level system init (mounts, devices) |
| `local-fs.target`  | Local filesystems mounted               |
| `remote-fs.target` | Remote filesystems mounted              |
| `swap.target`      | Swap space active                       |

### Networking Targets
| Target                  | Purpose                                |
| ----------------------- | -------------------------------------- |
| `network.target`        | Basic networking stack ready           |
| `network-online.target` | Network fully configured (IP assigned) |
| `nss-lookup.target`     | DNS resolution ready                   |
| `rpcbind.target`        | RPC services ready                     |

### Service Grouping Targets
| Target             | Purpose                 |
| ------------------ | ----------------------- |
| `timers.target`    | Timer units             |
| `sockets.target`   | Socket-based activation |
| `paths.target`     | Path-based activation   |
| `bluetooth.target` | Bluetooth services      |
| `sound.target`     | Audio system            |


### Hardware/Devices Target
| Target              | Purpose               |
| ------------------- | --------------------- |
| `devices.target`    | All devices available |
| `cryptsetup.target` | Disk encryption ready |

### Shutdown Target
| Target            | Purpose           |
| ----------------- | ----------------- |
| `shutdown.target` | System shutdown   |
| `reboot.target`   | System reboot     |
| `halt.target`     | Stop system       |
| `poweroff.target` | Power off machine |

