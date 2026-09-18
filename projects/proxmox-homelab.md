# Proxmox Homelab

## Project Overview

I built a dedicated Proxmox VE server using repurposed PC hardware to create a permanent environment for developing practical IT, networking, systems administration and cybersecurity skills.

Rather than relying entirely on temporary virtual machines created for coursework, I wanted an environment that I could continuously build, modify, break, troubleshoot and expand as my skills develop.

## Hardware

The current Proxmox host consists of:

- Intel Core i7-4770
- 16 GB RAM
- NVIDIA GeForce GTX 760
- SSD storage for virtual machines
- Separate storage for backups
- Physical Ethernet connection to the home network

The hardware was primarily assembled from components I already had available.

## Proxmox Configuration

The server currently runs Proxmox VE 9.2.2.

The environment has been configured with:

- Linux bridge networking
- Static management addressing
- Dedicated VM storage
- Separate backup storage
- VM snapshots
- Scheduled backups
- VM startup configuration
- PCIe device passthrough
- Windows and Linux virtual machines

## Networking

The Proxmox host connects to a private `/24` LAN.

A Linux bridge (`vmbr0`) connects the virtual environment to the physical network.

Conceptually:

Physical Network
      |
Physical NIC
      |
    vmbr0
    /   \
Ubuntu  Windows
  VM      VM

`vmbr0` functions similarly to a virtual network switch. Virtual network adapters attached to the bridge can communicate with the physical LAN through the Proxmox host's physical network interface.

The Proxmox management interface uses a static IP address so that the host remains at a predictable address for administration.

Exact addressing and device identifiers have been omitted from this public documentation.

## Virtual Machines

### Ubuntu Server

The Ubuntu Server VM is currently configured with:

- 4 vCPUs
- 12 GB RAM
- 100 GB virtual disk
- VirtIO networking
- Linux guest configuration

The VM has been used for Linux administration and self-hosted services, including a Fabric Minecraft server.

Its current resource allocation was selected for the game-server workload rather than simultaneous operation with every other lab VM.

### Windows VM

The Windows VM is currently configured with:

- 4 vCPUs
- 8 GB RAM
- 64 GB virtual disk
- UEFI/OVMF firmware
- Virtual TPM
- PCIe passthrough
- Dedicated NVIDIA GeForce GTX 760

PCIe passthrough allows the physical GPU to be assigned directly to the Windows virtual machine rather than relying entirely on virtualised graphics.

## Resource Management

The host currently contains 16 GB of physical memory.

Because configured VM memory can exceed the amount that should realistically be used simultaneously, resources are allocated according to the current workload.

For example, the Ubuntu Server VM was allocated additional memory while operating as a game server. As the lab develops into a multi-VM business environment, CPU and memory allocations will be adjusted to allow several systems to operate simultaneously while maintaining resources for the Proxmox host.

This has provided practical experience with VM sizing, resource allocation and capacity planning.

## Storage and Backups

The environment uses separate storage for virtual machine workloads and backups.

I have used:

- Virtual disks
- SSD-backed VM storage
- VM snapshots
- Scheduled backups
- Separate backup storage

This allows changes to be tested while maintaining recovery options if a configuration causes problems.

## Troubleshooting and Learning

Building and operating the environment has involved troubleshooting issues across several areas, including:

- VM configuration
- Network connectivity
- Static addressing
- Linux bridge networking
- CPU and memory allocation
- Storage performance
- VM startup behaviour
- PCIe passthrough
- Linux and Windows guest configuration
- Service and application performance

One of the most useful parts of maintaining the lab has been learning to investigate problems across multiple layers rather than assuming the first apparent cause is the actual problem.

For example, application performance issues can require investigation of the application itself, guest operating system, VM resource allocation and underlying Proxmox host.

## What I Learned

This project has helped develop practical understanding of:

- Type-1 hypervisors
- Virtual machines
- CPU and memory allocation
- Virtual storage
- Virtual networking
- Linux bridges
- Static IP addressing
- VM snapshots and backups
- UEFI virtual machines
- Virtual TPMs
- PCIe passthrough
- Linux and Windows administration
- Infrastructure troubleshooting

The Proxmox environment now acts as the foundation for future IT infrastructure and cybersecurity projects documented in this repository.
