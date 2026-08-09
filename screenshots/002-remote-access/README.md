# Remote Access Screenshots

Screenshots documenting the SSH, Termius, and Tailscale remote-access project.


## Verification

The remote-access configuration was successfully verified after restarting the lab environment.

### Tailscale Service

The Tailscale daemon was confirmed to be active and running on the Ubuntu virtual machine.

### Network Connectivity

Connectivity between the Ubuntu VM and the iPhone was verified using Tailscale ping.

The test returned a successful `pong` response.

### SSH Connectivity

The iPhone successfully connected to the Ubuntu virtual machine using Termius over the Tailscale network.

This confirmed the complete remote-access path:

iPhone → Tailscale → Ubuntu VM → SSH
