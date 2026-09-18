# Home IT & Cybersecurity Lab

A hands-on IT and cybersecurity homelab used to develop practical skills in systems administration, networking, virtualisation, Linux, Windows, troubleshooting and security.

This repository documents the environment I have built and administered, the problems I have encountered, how I troubleshot them, and the projects I complete as I continue developing my IT and cybersecurity skills.

The lab is an ongoing project and will continue to expand as I work through new IT infrastructure, networking and cybersecurity projects.

## Current Lab Environment

My homelab is built around a dedicated Proxmox VE virtualisation server assembled using repurposed hardware I already had available.

The environment provides a platform for running Windows and Linux virtual machines, self-hosted services and future infrastructure and cybersecurity projects.

### Proxmox Host

- Proxmox VE 9.2.2
- Intel Core i7-4770
- 16 GB RAM
- NVIDIA GeForce GTX 760
- Dedicated SSD VM storage
- Separate backup storage
- Static management IP
- Linux bridge networking
- Virtual machine snapshots and scheduled backups
- PCIe GPU passthrough configured for a Windows VM

### Current Virtual Machines

**Ubuntu Server**
- Ubuntu Linux server
- Currently configured with 4 vCPUs and 12 GB RAM
- 100 GB virtual disk
- Used for Linux administration and self-hosted services
- Configured as a Fabric Minecraft server
- Minecraft configured to run as a systemd service
- Current resource allocation was designed for the game-server workload and will be adjusted when running alongside additional lab VMs

**Windows**
- Windows virtual machine
- 4 vCPUs
- 8 GB RAM
- 64 GB virtual disk
- UEFI/OVMF
- Virtual TPM configured
- NVIDIA GeForce GTX 760 passed directly through to the VM using PCIe passthrough
- Used for Windows administration, testing and virtualisation experiments

### Resource Management

The Proxmox host has 16 GB of physical memory, so VM resources are allocated according to the workload being used rather than running every VM at its maximum configured allocation simultaneously.

The Ubuntu Server VM was allocated 12 GB RAM for its game-server workload. When the environment expands to run multiple Windows and Linux systems simultaneously, VM memory and CPU allocations will be resized to maintain sufficient resources for the Proxmox host and each active guest.

This allows the lab to also be used for practical experience with resource allocation, capacity planning and performance monitoring.

## Network

The current lab operates on a private IPv4 network using RFC1918 addressing.

- Private `/24` LAN
- Static management address configured for the Proxmox host
- DHCP provided by the home router
- Proxmox connected to the LAN using a Linux bridge (`vmbr0`)
- Virtual machines connect to the physical LAN through the Proxmox bridge

Detailed network architecture and diagrams are documented separately within this repository.

## Projects

### Proxmox Virtualisation Lab

Built and administer a dedicated Proxmox VE server for creating and managing Windows and Linux virtual machines.

Areas of practical experience include:

- Proxmox VE installation and administration
- VM creation and resource allocation
- Virtual disks and storage management
- Linux bridge networking
- Static IP configuration
- VM snapshots
- Scheduled VM backups
- VM startup configuration
- Windows and Linux guest systems
- PCIe GPU passthrough
- Hardware and VM configuration
- CPU, memory and storage performance monitoring
- Host and VM troubleshooting

### Linux Game Server Administration

Deployed and administered a Fabric Minecraft server on an Ubuntu Server virtual machine.

The project provided hands-on experience with:

- Ubuntu Server administration
- Linux command line
- SSH remote administration
- File and directory management
- Linux permissions
- systemd service configuration
- Automatic service startup
- Java/JVM configuration and memory allocation
- Server configuration
- TCP/UDP ports
- Router/NAT and port-forwarding configuration
- Static IP addressing
- DNS/hostname concepts
- Performance monitoring
- Log analysis
- Scheduled backups and VM snapshots
- Connectivity troubleshooting
- Server performance troubleshooting

The Minecraft server was configured to run as a managed Linux systemd service, allowing it to start automatically with the server rather than relying on an interactive terminal session.

During operation, server performance issues were investigated using server-side profiling alongside Proxmox host monitoring. This included analysing CPU utilisation, memory allocation, tick performance and potential storage-related delays.

### Windows Virtual Machine

Configured a Windows virtual machine within Proxmox for Windows administration, testing and future infrastructure projects.

The VM uses UEFI/OVMF and a virtual TPM and has also been configured with PCIe passthrough to provide direct access to a dedicated NVIDIA GPU.

This provides a reusable Windows environment for future administration, troubleshooting and infrastructure labs.

## Troubleshooting Experience

A major goal of this lab is not simply getting systems working, but developing a repeatable troubleshooting process when systems fail.

Problems investigated while building and operating the environment have included:

- Virtual machine connectivity problems
- SSH connectivity failures
- Game server connection issues
- NAT and port-forwarding configuration
- Static IP configuration
- Linux service configuration
- Server startup and restart behaviour
- Game server performance and tick-rate issues
- JVM memory allocation and optimisation
- CPU and memory performance investigation
- Storage performance investigation
- VM resource allocation
- Network troubleshooting
- PCIe hardware passthrough configuration

Troubleshooting processes, causes and lessons learned are documented within individual projects where appropriate.

## Current Learning Focus

I am currently completing a Certificate IV in Cyber Security while using this lab to develop practical experience beyond coursework.

Current areas of focus include:

- IT support and troubleshooting
- Windows administration
- Linux administration
- Networking fundamentals
- TCP/IP
- DNS and DHCP
- Common network protocols and ports
- Active Directory
- Microsoft 365 and Entra ID
- PowerShell
- Security monitoring
- Microsoft Defender
- SIEM fundamentals
- Incident response
- Network segmentation and VLANs

## Planned Lab Development

The environment will progressively be developed into a simulated small-business network.

Planned projects include:

1. Complete documentation and diagrams of the existing infrastructure
2. Deploy a dedicated Windows Server VM
3. Build an Active Directory domain
4. Configure DNS and DHCP services
5. Create organisational units, users and security groups
6. Implement Group Policy
7. Configure shared folders and NTFS/share permissions
8. Deploy and join Windows client VMs to the domain
9. Simulate realistic Level 1 IT help desk incidents
10. Introduce VLANs and network segmentation
11. Deploy infrastructure monitoring and centralised logging
12. Build a security monitoring / SIEM environment
13. Develop an isolated cybersecurity testing environment

## Documentation Approach

For major projects I aim to document:

- Objective
- Architecture and design
- Technologies used
- Implementation and configuration
- Testing and verification
- Problems encountered
- Troubleshooting process
- Resolution
- Security considerations
- Lessons learned

The goal is to document not only successful configurations, but also the troubleshooting and decision-making involved in building and maintaining the environment.

This repository will continue to evolve as the homelab grows and I gain further practical IT and cybersecurity experience.
