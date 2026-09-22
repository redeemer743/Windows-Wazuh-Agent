# Technical Lab Report: Centralized EDR Agent Enrollment

**Course/Module:** Security Operations & Infrastructure Lab  
**Date:** September 21, 2026  
**Status:** Completed & Validated  

---

## 1. Objective & Scope
The primary objective of this laboratory deployment task was to install, configure, and register an enterprise-grade endpoint security monitoring agent onto a remote target workstation using the **Wazuh SIEM architecture**. This enrollment procedure establishes automated asset tracking, initializes configuration compliance monitoring, and secures communication tunnels to stream runtime telemetry straight to a centralized management master controller.

---

## 2. Laboratory Environment Specifications
The complete operational baseline metrics parsed from the active infrastructure configurations consist of the following structural parameters:

### Architecture Configuration Matrix

| Environment Parameter | Specification / Value | Architectural Context / Status |
| :--- | :--- | :--- |
| **Wazuh Manager Version** | `v4.14.7` | Central Master Core Engine [1] |
| **Wazuh Manager IP** | `192.168.6.133` | Master Listener IP [1] |
| **Target Hostname** | `GAL1LEO` | Monitored Deployment Target Asset [1] |
| **Assigned Agent ID** | `002` | Unique Database Asset Index [1] |
| **Assigned Agent Name** | `Windows 11` | Friendly Node Identifier [1] |
| **Target Operating System** | `Windows 11 Pro (10.0.26200.9457)` | Client Platform Workspace [1] |
| **Target Hardware Specs** | `8 Cores \| Intel i5-8250U @ 1.60GHz \| 16.0 GB RAM` | Endpoint System Footprint [1] |

---

## 3. Implementation Steps & Script Analysis

### Step 1: Deployment Package Configuration
The enrollment vector was initiated inside the **Wazuh Manager Web Dashboard Console** by routing through the `Endpoints` option to the `Deploy new agent` wizard interface. The target parameters were configured by selecting **Windows (MSI 32/64 bits)** as the baseline installation format, pinning the static listening manager IP address `192.168.6.133`, and explicitly dedicating `Windows_11` as the client enrollment identifier.

[INSERT SCREENSHOT: Wazuh Manager Web Console Interface - Deploy New Agent Selection Screen]

### Step 2: Unattended PowerShell Installation Execution
An elevated, high-privilege administrative **Windows PowerShell session** was opened on the target machine `GAL1LEO` to handle the installation sequence. The system-generated string argument payload was entered into the console window to trigger an automated, non-interactive deployment background task:

[INSERT SCREENSHOT: Elevated Windows PowerShell Console Running Unattended Web Ingestion Command Strings]
```powershell

#### Detailed Command Parameters Breakdown:
* **`Invoke-WebRequest`:** Instructs the local runtime workspace to pull down the official `Wazuh Agent v4.14.7` binary file from the secure online package mirror.
* **`-OutFile $env:tmp\...`:** Buffers and names the package inside the host system's temporary directory storage sector to streamline background file management.
* **`msiexec.exe /i ... /q`:** Invokes the native Windows Installer engine to process deployment routines completely silently (`/q`), suppressing graphical setup windows and system reboots.
* **`WAZUH_MANAGER='192.168.6.133'`:** Hardcodes the target server's communication parameters into the agent environment configuration for authenticated TLS transport authorization.
* **`WAZUH_AGENT_NAME='Windows_11'`:** Grants a friendly descriptor variable to map neatly inside database indices across active endpoint monitoring views.

---

## 4. Verification & Validation Metrics

To meet enterprise compliance auditing procedures, agent operational state validation was verified across both local endpoints and centralized management layers.

### 4.1 Local Host Validation (PowerShell Console)
A persistent runtime daemon diagnostic scan was run using the local system management terminal to check the core process states:

```powershell
PS C:\Windows\system32> NET START Wazuh
The requested service has already been started.
More help is available by typing NET HELPMSG 2182.
```
[INSERT SCREENSHOT: Local Host Terminal Verification - Output Confirming Already Running Wazuh Service]

* **Technical Ingress Analysis:** The terminal exception tracking indicates that the background daemon engine successfully provisioned its service properties and auto-started background processes right after the silent script completed execution.

### 4.2 Centralized Dashboard Monitoring Telemetry
Upon logging back into the security monitoring console, the newly enrolled node registered immediately. The centralized dashboard confirmed active data streams across the following modules:

* **Endpoint Activity Status:** `Agent 002 (Windows_11)` swapped over to a green **`active`** status block at network node `192.168.8.1`, maintaining stable, real-time connection heartbeats.
* **Security Configuration Assessment (SCA):** The policy auditing mechanism ran scanning checklists based on the *CIS Microsoft Windows 11 Enterprise Benchmark v3.0.0* auditing rule book. This initial assessment cataloged **124 passed verification items**, **349 compliance deviations**, and generated an overall configuration posture score of **26%**.
* **Hardware Asset Indexing:** Automated system asset collection successfully scraped hardware specifications, identifying an 8-core processor setup powered by an Intel Core i5-8250U CPU throttling at 1.60GHz alongside a 16.0 GB physical RAM pool.
* **SIEM Event Stream Ingestion:** Live log pipelines began routing data arrays into Threat Hunting index panels, MITRE ATT&CK matrix view plots, and Compliance monitoring views.
  
[INSERT SCREENSHOT: Centralized Wazuh Dashboard Showing Active Node 002 Asset Inventory details]
[INSERT SCREENSHOT: Security Configuration Assessment SCA Overview Page for Windows 11 Node]

---

## 5. Conclusion & Operational Findings
The deployment and registration processes of the security monitoring asset onto the Windows 11 lab VM environment were concluded successfully. Endpoint check commands verified that background monitoring loops are working as intended, and the web console charts show consistent log streaming, baseline posture checking, and centralized tracking visibility across the network environment.
