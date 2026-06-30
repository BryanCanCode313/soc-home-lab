# Incident Report #003 – Process Creation Investigation (ipconfig.exe)

## Scenario

A Sysmon Event ID 1 (Process Creation) alert was generated after a Windows command-line utility was executed. The objective of the investigation was to determine whether the activity represented legitimate administrative behavior or suspicious activity.

---

## Investigation Objective

Determine whether the execution of `ipconfig.exe` was legitimate or indicative of malicious activity.

---

## Evidence Collected

| Field | Value |
|-------|-------|
| Event ID | 1 |
| Time | 2026-06-30 15:04:49.803 |
| User | BRYAN-SOC-LAB\vboxuser |
| Image | C:\Windows\System32\ipconfig.exe |
| Parent Image | C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe |
| Command Line | "C:\WINDOWS\system32\ipconfig.exe" |

---

## Analysis

The process was identified as the legitimate Windows `ipconfig.exe` utility. The executable was launched from the expected Windows system directory (`C:\Windows\System32`). The parent process was `powershell.exe`, matching the interactive PowerShell session that I initiated. The timestamp of the event matched the time the command was manually executed within the virtual machine.

---

## Assessment

**Classification:** Benign

The activity was determined to be legitimate administrative behavior. The executable path, parent process, user account, and execution timeline were all consistent with expected Windows operation. No indicators of malicious activity were identified.

---

## Lessons Learned

- Investigated a Sysmon Event ID 1 (Process Creation).
- Verified the legitimacy of a Windows executable by examining its file path.
- Confirmed the expected parent-child process relationship.
- Correlated Splunk event timestamps with user activity in the virtual machine.
- Practiced distinguishing benign administrative activity from suspicious process execution.
