# Linux Minecraft Server

## Project Overview

I deployed and administered a self-hosted Fabric Minecraft server using an Ubuntu Server virtual machine running on my Proxmox homelab.

The project began as a way to host a private game server, but developed into a practical Linux administration and troubleshooting project involving networking, services, Java configuration, backups and performance investigation.

## Environment

The server runs inside an Ubuntu Server VM hosted by Proxmox VE.

Current VM configuration:

- Ubuntu Server
- 4 vCPUs
- 12 GB RAM
- 100 GB virtual disk
- VirtIO networking
- Connected to the physical LAN through the Proxmox Linux bridge

The VM resources were configured specifically for the game-server workload and can be reduced when the host is required to run several lab systems simultaneously.

## Linux Administration

Managing the server has provided practical experience using Ubuntu Server without relying on a graphical interface.

Tasks have included:

- Remote administration using SSH
- Linux command-line navigation
- File and directory management
- File permissions
- Software installation and updates
- Service management
- Log inspection
- Resource monitoring
- Configuration file editing
- Server restarts and maintenance

## Minecraft Server Deployment

A Fabric-based Minecraft server was installed and configured on Ubuntu Server.

The server files are maintained within a dedicated directory and the server configuration can be administered remotely through Linux.

The deployment involved:

- Installing and configuring Java
- Deploying the Fabric server
- Managing server files
- Installing and configuring compatible mods
- Configuring server properties
- Allocating JVM memory
- Managing world data
- Testing client connectivity
- Monitoring server performance

## systemd Service

Rather than manually starting Minecraft from an interactive terminal each time, I configured it as a Linux `systemd` service.

This allows the operating system to manage the Minecraft server as a service.

This provided practical experience with:

- Creating a systemd service
- Defining the application startup command
- Configuring automatic startup
- Starting and stopping services
- Restarting services after configuration changes
- Checking service status
- Troubleshooting service startup

This also made the server behave more like a normal production Linux service rather than an application that depended on an open terminal session.

## Networking

Hosting the server required configuring both the Ubuntu VM and the surrounding network.

The project involved:

- Private IPv4 addressing
- Static server addressing
- TCP/IP
- Ports
- Router/NAT configuration
- Port forwarding
- DNS/hostname concepts
- Connectivity testing

The server used the standard Minecraft Java server port, TCP `25565`.

A static local address ensured that router configuration continued directing incoming traffic to the correct server rather than the VM receiving an unpredictable address.

Exact IP addresses and public-facing network information are intentionally omitted from this repository.

## Backups and Recovery

The Minecraft environment was protected using the backup and snapshot functionality available through the Proxmox host.

This provided experience with:

- VM snapshots
- Scheduled backups
- Separate backup storage
- Protecting persistent server data
- Considering recovery before making configuration changes

Backups are particularly important for a persistent game server because world data and configuration change continuously.

## JVM Resource Configuration

Because Minecraft runs on Java, server performance is affected by the configuration of the Java Virtual Machine (JVM).

During performance investigation I reviewed and adjusted JVM memory allocation rather than assuming that assigning as much RAM as possible would improve performance.

The server was eventually configured with:

- `-Xms6G`
- `-Xmx8G`

`-Xms` controls the initial JVM heap allocation, while `-Xmx` controls the maximum heap allocation.

This helped me better understand the difference between VM memory allocation and application-level memory allocation.

## Performance Investigation

While operating the server, periods of severe lag occurred even though performance was generally healthy.

Instead of immediately assuming that additional hardware resources would solve the issue, I investigated the problem at multiple layers.

Areas investigated included:

- Minecraft TPS
- MSPT
- CPU utilisation
- Memory utilisation
- JVM configuration
- Entity processing
- Chunk activity
- Server logs
- Proxmox host utilisation
- VM resource allocation
- Potential storage delays

## Profiling

I installed and used the Spark profiler to investigate server performance.

Profiling showed that the server spent much of the captured period waiting for the next game tick rather than continuously exhausting the CPU.

During active processing, workloads included:

- World ticking
- Chunk processing
- Entity processing
- Mob AI
- Natural mob spawning

This was useful because it demonstrated that a performance problem should not automatically be attributed to CPU utilisation simply because the application experiences lag.

## Log Analysis

Server logs were also examined during performance issues.

Warnings included instances where the server reported that it could not keep up and had fallen significantly behind the expected tick schedule.

The investigation required comparing application-level information with resource utilisation on the underlying Proxmox host.

A single definitive cause was not established for every severe stall, so the issue was treated as an ongoing troubleshooting investigation rather than assuming a cause without sufficient evidence.

## Troubleshooting Approach

One of the main lessons from this project was to investigate problems across the complete stack.

For example:

Minecraft Server
↓
Java / JVM
↓
Ubuntu Server
↓
Virtual Machine
↓
Proxmox
↓
Physical Hardware
↓
Network

A symptom at the application layer can originate from another layer of the environment.

This project helped reinforce a more structured troubleshooting process:

1. Identify the symptom
2. Gather logs and performance data
3. Establish what is operating normally
4. Isolate possible causes
5. Change one relevant variable where possible
6. Test again
7. Avoid claiming a root cause without supporting evidence
8. Document the results

## Skills Developed

This project provided practical experience with:

- Ubuntu Server
- Linux command line
- SSH
- Linux files and permissions
- systemd
- Java and JVM configuration
- TCP/IP
- TCP ports
- Static IP addressing
- NAT and port forwarding
- DNS and hostnames
- Virtual machines
- Resource allocation
- Server logs
- Performance monitoring
- Application profiling
- Backups and snapshots
- Structured troubleshooting
- Technical documentation

## Future Improvements

The server can continue to be used as a Linux administration environment and as a platform for further experiments involving:

- Service monitoring
- Improved backup and recovery testing
- Network segmentation
- Firewall configuration
- Centralised logging
- Security hardening
- Automated administration

The knowledge gained from this project will also be applied to future non-game Linux services within the homelab.
