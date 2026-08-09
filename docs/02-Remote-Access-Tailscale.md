# Remote Access with SSH, Termius, and Tailscale

## Objective

Configure secure remote administration of my Ubuntu virtual machine from an iPhone without exposing SSH directly to the public Internet.

## Technologies Used

- Windows 11 Host
- Oracle VirtualBox
- Ubuntu 24.04 SIFT Workstation
- OpenSSH
- Termius
- Tailscale

## Initial Approach

I initially experimented with VirtualBox NAT port forwarding to allow SSH access to the Ubuntu virtual machine.

The configuration forwarded host port `2222` to the Ubuntu SSH port `22`.

This allowed SSH connectivity to be tested locally, but it was not the preferred solution for remote access.

## Final Solution

Tailscale was installed on both the Ubuntu virtual machine and the iPhone.

The Ubuntu VM was assigned the Tailscale address:

`xxx.xx.xxx.xxx`

The iPhone was also added to the same Tailscale network.

Termius was then used on the iPhone to establish an SSH connection to the Ubuntu VM.

## Connection Flow

```
iPhone
   |
Termius
   |
Tailscale VPN
   |
Ubuntu VM
   |
OpenSSH
```

## Evidence

Screenshots documenting the configuration and verification of the remote-access setup.

- [Tailscale installation on Ubuntu](../screenshots/002-remote-access/01-tailscale-install-ubuntu.png)
- [Tailscale VPN configuration on iPhone](../screenshots/002-remote-access/02-tailscale-vpn-configuration.png)
- [Tailscale connected devices](../screenshots/002-remote-access/03-tailscale-connected-devices.png)
- [Termius Tailscale status verification](../screenshots/002-remote-access/04-termius-tailscale-status.png)
- [Successful Termius SSH connection](../screenshots/002-remote-access/05-termius-ssh-success.png)
