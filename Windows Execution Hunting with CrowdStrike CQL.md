# Windows Execution Hunting with CrowdStrike Humio CQL

## Subtitle
How parent-child process lineage exposes post-exploitation tradecraft faster than binary-name hunting.

## Social preview blurb
A practical threat hunting article focused on suspicious Windows execution chains, high-signal parent-child relationships, and production-ready CrowdStrike Humio CQL examples.

## Header image idea
A dark process-tree graphic showing `w3wp.exe -> cmd.exe -> powershell.exe -> certutil.exe` with highlighted suspicious branches.

***

## Introduction
Threat hunting on Windows becomes far more effective when the focus shifts from isolated binaries to execution chains. Parent-child process relationships, command-line intent, and launch context consistently expose suspicious behavior even when attackers rename tools or rotate payloads [1][2].

## BLUF
- Parent-child process analysis is more durable than binary-name matching because behavior survives renaming and minor tooling changes [2].
- Multi-line CrowdStrike Humio CQL pipelines improve hunt readability, tuning, and collaboration during detection engineering workflows [1][2].
- Web-facing processes that launch shells or scripting engines should be treated as high-value pivots for triage and enrichment [3].

## Why this matters
Attackers rarely execute payloads in a vacuum. They stage activity through trusted services, script interpreters, and administrative utilities to blend with normal operations. That is why process ancestry remains one of the most reliable ways to spot execution abuse in enterprise telemetry [2][3].

A suspicious child process is useful, but a suspicious child process launched by a web worker, office application, or remote management parent is much more actionable. This framing helps analysts reduce noise while keeping hunts resilient against superficial attacker changes [1][2].

## Hunt logic
A strong Windows execution hunt starts with three questions:

1. Which parent process launched the activity?
2. What command interpreter or LOLBin executed next?
3. Did the command line suggest download, decode, discovery, or privilege-related behavior?

This structure mirrors how LogScale CQL is intended to be written: narrow the event type, apply field filters, then aggregate or enrich for triage [1][3].

## CrowdStrike Humio CQL

### Suspicious shell execution from web-facing parents
```cql
#event_simpleName=ProcessRollup2
| ParentBaseFileName=/w3wp\.exe|httpd\.exe|nginx\.exe|php-cgi\.exe/i
| FileName=/cmd\.exe|powershell\.exe|pwsh\.exe/i
| groupBy([ComputerName, UserName, ParentBaseFileName, FileName, CommandLine], function=count(as=exec_count))
| sort(exec_count, order=desc)
```

### Office application spawning script interpreters
```cql
#event_simpleName=ProcessRollup2
| ParentBaseFileName=/winword\.exe|excel\.exe|powerpnt\.exe|outlook\.exe/i
| FileName=/cmd\.exe|powershell\.exe|wscript\.exe|cscript\.exe|mshta\.exe/i
| groupBy([ComputerName, UserName, ParentBaseFileName, FileName, CommandLine], function=count(as=spawn_count))
| sort(spawn_count, order=desc)
```

### Remote management followed by suspicious child process activity
```cql
#event_simpleName=ProcessRollup2
| ParentBaseFileName=/psexesvc\.exe|wmiprvse\.exe|winrm\.exe|services\.exe/i
| FileName=/cmd\.exe|powershell\.exe|rundll32\.exe|regsvr32\.exe/i
| groupBy([ComputerName, ParentBaseFileName, FileName, CommandLine], function=count(as=activity_count))
| sort(activity_count, order=desc)
```

## Triage guidance
Prioritize results where the parent process is externally exposed, user context is unexpected, or the command line includes indicators of staging activity such as URLs, encoded commands, compression, or archive extraction. Analysts should also check for follow-on behavior including network connections, credential access attempts, or persistence activity within the same execution window.

## Detection notes
The most effective tuning pattern is to keep the parent-child relationship strict while allowing command-line logic to be broader during the first hunt pass. After recurring benign cases are identified, exclusions can be scoped around specific hosts, service accounts, signed maintenance scripts, or approved software deployment jobs [2][3].

## Visual representation
```text
Internet-facing process
        |
        v
   Shell spawn
        |
        v
 Script interpreter or LOLBin
        |
        v
 Staging / download / discovery
        |
        v
 Follow-on attacker objective
```

### Good Windows hunts do not start with a filename. They start with ancestry, intent, and execution context.

## Closing note
The analyst who can explain why a process launched is usually ahead of the analyst who only knows that it launched. That is the difference between noisy search and durable hunting.
