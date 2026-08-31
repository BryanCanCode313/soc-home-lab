# Ubuntu Splunk Universal Forwarder Integration

## Objective

Integrate an Ubuntu Server VM into the SOC home lab by installing and configuring the Splunk Universal Forwarder, establishing a connection to Splunk Enterprise, and preparing Linux security and web-server logs for centralized monitoring.


## Technologies Used

- Ubuntu Server
- Splunk Universal Forwarder
- Splunk Enterprise
- Apache2
- systemd / journald
- SSH
- Termius
- Tailscale
- TCP port 9997

## Implementation

1. Installed the Splunk Universal Forwarder on the Ubuntu Server VM.
2. Configured Splunk Enterprise on the Windows host to receive forwarded data over TCP port 9997.
3. Verified network connectivity between Ubuntu and the Splunk Enterprise receiver.
4. Configured the Universal Forwarder to send data to the Splunk Enterprise instance.
5. Verified the destination appeared under **Active forwards**.
6. Configured the Forwarder service account with permission to read Apache logs.
7. Added `/var/log/apache2/access.log` as a monitored data source.
8. Configured a `journald` input for SSH authentication telemetry.
9. Verified Ubuntu was recording successful SSH authentication events through the systemd journal.


## Troubleshooting

During implementation, several issues were identified and resolved:

- The Splunk receiver was not initially listening on TCP port 9997.
- Network testing with `nc` was used to verify connectivity between the Ubuntu VM and the Splunk Enterprise receiver.
- The Universal Forwarder initially contained an incorrect forwarding destination.
- The forwarding destination was corrected and verified under **Active forwards**.
- The `splunkfwd` service account initially lacked permission to read Apache logs.
- Log permissions were corrected and verified before configuring monitoring.
- Ubuntu authentication events were stored in the systemd journal rather than a traditional `/var/log/auth.log` file.
- A journald input was configured for SSH authentication telemetry.



## Results

The Ubuntu Universal Forwarder successfully established an active connection to the Splunk Enterprise receiver over TCP port 9997.

Apache access logs were configured for forwarding, and SSH authentication telemetry was configured through the systemd journal.

Local testing confirmed that SSH authentication events were being generated and that the Universal Forwarder recognized the `journald://ssh` input.

Final verification of the forwarded events within Splunk Search is pending due to a temporary Splunk Free license search restriction.

## Evidence

The following screenshots document the Ubuntu Splunk integration:

- [Active Splunk Forwarding](../screenshots/004-ubuntu-splunk/01-active-forward-redacted.jpeg)
- [TCP 9997 Connectivity](../screenshots/004-ubuntu-splunk/02-tcp-9997-connectivity-redacted.jpeg)
- [Apache Log Monitoring](../screenshots/004-ubuntu-splunk/03-Apache-monitor-redacted.png)
- [SSH Journald Input](../screenshots/004-ubuntu-splunk/04-ssh-journald-input-redacted.png)
    
