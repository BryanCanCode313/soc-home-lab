# SOC Home Lab Setup

## Objective

Build a professional SOC Analyst home lab capable of collecting, monitoring, and investigating Windows security events using enterprise security tools.

---

## Lab Architecture

### Host Machine
- Windows 11
- Oracle VirtualBox
- Splunk Enterprise

### Virtual Machine
- Windows 11
- Sysmon
- Splunk Universal Forwarder

---

## Tools Used

- Oracle VirtualBox
- Windows 11
- Sysmon
- Splunk Enterprise
- Splunk Universal Forwarder

---

## What I Learned

During this stage of the project, I learned how enterprise log collection works by separating the endpoint (Windows VM) from the SIEM (Splunk Enterprise running on the host). I installed Sysmon to generate detailed endpoint telemetry and configured Splunk Enterprise to receive forwarded logs over TCP port 9997.

I also installed the Splunk Universal Forwarder
