# Sysmon Log Ingestion Troubleshooting

## Objective

Troubleshoot why Sysmon logs were not appearing in Splunk Enterprise after configuring the Splunk Universal Forwarder.

## Problem

The Windows Security, System, and Application logs were successfully forwarded to Splunk, but the Microsoft-Windows-Sysmon/Operational log was not appearing in searches.

## Investigation

To diagnose the issue, I:

* Verified that `inputs.conf` contained the correct Sysmon event log configuration.
* Used `splunk.exe btool inputs list --debug` to confirm the Universal Forwarder was reading the configuration file.
* Confirmed in Event Viewer that the Sysmon Operational log existed and was actively generating events.
* Reviewed the `splunkd.log` file to identify any forwarding errors.

## Error Identified

The `splunkd.log` file reported:

```
Could not subscribe to Windows Event Log channel 'Microsoft-Windows-Sysmon/Operational'
errorCode=5
```

Error Code 5 indicates **Access Denied**, meaning the SplunkForwarder service did not have permission to read the Sysmon event log.

## Resolution

I opened the SplunkForwarder service properties and changed the service account from **NT SERVICE\SplunkForwarder** to the **Local System** account. After restarting the service, the Universal Forwarder was able to subscribe to the Sysmon event log successfully.

## Result

After updating the service account, Sysmon events were successfully forwarded to Splunk Enterprise. I verified that Sysmon Event ID 1 (Process Creation) events were searchable, confirming that the endpoint telemetry pipeline was working correctly.
