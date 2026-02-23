# Microsoft-SOC-Analyst-Simulation-Lab

## Objective

Designed and deployed a Microsoft-native SOC environment using Microsoft Sentinel and Defender XDR. Simulated phishing, risky sign-ins, and endpoint-based attack techniques to validate detection capabilities, investigate security events and validate preventative security controls using Zero Trust principles. 


The lab focused on:
- Connecting data sources into Sentinel
- Configuring Microsoft Defender security policies
- Generating phishing and risky sign-in telemetry
- Investigating incidents using Defender XDR

---

## Environment Architecture
- Microsoft Sentinel (SIEM)
- Microsoft Defender for Endpoint
- Microsoft Defender for Office 365
- Microsoft Entra ID (Azure AD) sign-in telemetry
- Attack simulation via Microsoft Learn telemetry + manual technique simulation

## Skills Demonstrated
- Investigating risky sign-ins and identity-based attacks
- Configuring Conditional Access (MFA enforcement)
- Deploying and validating Attack Surface Reduction (ASR) rules
- Configuring Safe Links and Anti-Phishing Policies
- Correlating identity and endpoint telemetry

## Tools Used
- Microsoft Sentinel (SIEM)
- Microsoft Defender for Endpoint
- Microsoft Defender for Office 365
- Microsoft Entra ID (Azure AD)
- KQL (Kusto Query Language) 
- VMware (Windows Endpoint Simulation) 

## Detection & Simulation Scenarios
### 1. Phishing Email Simulation
- Configured Safe Links and Anti-Phishing policies
- Generated phishing telemetry
- Validated detection within Defender
- Reviewed URL detonation and click tracking

### 2. Risky Sign-in Investigation
- Simulated suspicious login behavior
- Analyzed Azure AD risk indicators
- Investigated user activity timeline
- Correlated identity + endpoint signals

### 3. ASR Rule Monitoring
- Enabled ASR rules for endpoint hardening
- Triggered test behaviors
- Analyzed Defender alerts
- Validated policy enforcement

## Screenshots

### Environment Setup
Ref 1 - Resource Group Creation
Microsoft Azure resource group SOC-Lab01-RG-JO successfully created in the UK South region. This resource group acts as the logical container for all infrastructure and security resources used in the SOC Detection Lab.
<img width="1640" height="190" alt="Screenshot 2026-02-21 at 17 41 58" src="https://github.com/user-attachments/assets/20369a9f-32bb-4a93-8481-969fab62275f" />

Ref 2 - Log Analytics Workspace Deployment
Log Analytics workspace **SOC-Lab01-LAW-JO** successfully deployed and linked to the SOC lab resource group. This workspace is used by Microsoft Sentinel to ingest, store, and query security telemetry from connected data sources. 
<img width="1921" height="691" alt="Screenshot 2026-02-21 at 17 49 55" src="https://github.com/user-attachments/assets/62f58892-5a2b-4a91-9ab4-c574cbf7d77b" />

Ref 3 - Microsoft Sentinel Enabled
Microsoft Sentinel successfully enabled on the Log Analytics workspace **SOC-Lab01-LAW-JO**, providing centralised SIEM capabilities including incident management, analytics, data connectors, and security monitoring. 
<img width="1919" height="952" alt="Screenshot 2026-02-21 at 17 55 38" src="https://github.com/user-attachments/assets/aabf6f26-825f-450d-ba2d-a0fddee19576" />

Ref 4 - Microsoft Entra ID Data Connector Enabled
The Microsoft Entra ID data connector is successfully configured and connected. Sign-in and Audit logs are now being ingested into Microsoft Sentinel, enabling identity telemetry collection and security monitoring within the SIEM. 
<img width="1636" height="642" alt="Screenshot 2026-02-23 at 19 34 38" src="https://github.com/user-attachments/assets/226566f6-a535-4807-81c6-63996b2fb0ad" />

Ref 5 - Log Ingestion Verification (SignInLogs)
A KQL query executed in Microsoft Sentinel confirmed successful ingestion of Microsoft Entra ID SignInLogs. The query was run against the SignInLogs table and returned both successful and failed authentication events, verifying that identity telemetry is actively flowing into the SIEM and available for security monitoring and investigation.
<img width="1600" height="925" alt="Screenshot 2026-02-23 at 19 40 02" src="https://github.com/user-attachments/assets/f9ef42f2-7079-4942-8209-15197d55cd46" />

Ref 6 - Endpoint Onboarded to Microsoft Defender 
The VMware Windows endpoint was successfully onboarded into Microsoft Defender for Endpoint. The device is now actively reporting telemetry and security events to the Microsoft security ecosystem.
<img width="1641" height="920" alt="Screenshot 2026-02-23 at 19 57 29" src="https://github.com/user-attachments/assets/e3cf0bf5-378b-4c59-a6b3-e8862633f9e0" />

---

### Policy Configuration

Ref 7 - Attack Surface Reduction (ASR) Policy 
An Attack Surface Reduction (ASR) policy was configured to harden the endpoint by blocking common attack vectors, including credential theft from LSASS, malicious Office child processes, ransomware behaviour, and suspicious remote process execution.
<img width="1717" height="933" alt="Screenshot 2026-02-23 at 20 04 25" src="https://github.com/user-attachments/assets/9b8e2659-87d2-49eb-9ef3-c2d35a8feb1d" />

Ref 8 - ASR Policy Successfully Applied 
The Attack Surface Reduction policy was successfully deployed to the endpoint, confirming the policy was applied and enforced.
<img width="1719" height="828" alt="Screenshot 2026-02-23 at 20 11 58" src="https://github.com/user-attachments/assets/2d6da49d-ee2b-48ba-a888-60d93c6f74bb" />

Ref 9 - Safe Links Policy Configuration
A Safe Links policy was configured to provide real-time URL scanning and protection against malicious links in email messages. URL rewriting and detonation capabilities were enabled to ensure links are analysed at the time of click, preventing users from accessing malicious destinations and reducing the risk of phishing-based compromise.
<img width="591" height="805" alt="Screenshot 2026-02-23 at 20 16 43" src="https://github.com/user-attachments/assets/fe144a15-3f4b-45d9-ba43-f21ac967567e" />

Ref 10 - Anti-Phishing Policy Configuration 
An Anti-Phishing policy was configured to detect impersonation and spoofing attacks using mailbox intelligence and anti-spoofing protections. Suspicious emails are automatically quarantined to prevent user exposure to phishing attempts.
<img width="590" height="800" alt="Screenshot 2026-02-23 at 20 22 33" src="https://github.com/user-attachments/assets/f5c8af07-7a97-4be1-bbe1-2cd659c0fee5" />

Ref 11 - Conditional Access Policy (MFA Enforcement) 
A Conditional Access policy was implemented to enforce Zero Trust identity protection by requiring multi-factor authentication (MFA) for access to cloud resources. The policy ensures that only strongly authenticated users operating from approved conditions can access organisational services, significantly reducing the risk of credential compromise and unauthorised access. 
<img width="1640" height="928" alt="Screenshot 2026-02-23 at 21 03 32" src="https://github.com/user-attachments/assets/a98dad9a-36ad-4087-8284-864ce04d59be" />

---

### Telemetry Generation

Ref 12 - Phishing Email Detection and Quarantine
A simulated phishing email was sent from an external source and successfully detected by Microsoft Defender for Office 365. The email was classified as phishing and automatically quarantined, demonstrating the effectiveness of Anti-Phishing and Safe Links protection policies. 
<img width="1644" height="345" alt="Screenshot 2026-02-23 at 20 45 58" src="https://github.com/user-attachments/assets/26bc0cc4-e324-432b-b354-876f035596c9" />

**MITRE ATT&CK Mapping:**
- Initial Access - Phishing (T1566)
- Credential Access - Credential Phishing (T1566.002) 

Ref 13 - Endpoint Malware Detection
Microsoft Defender for Endpoint generated a security alert after simulated malicious activity was detected on the test device. The threat was automatically identified and blocked, demonstrating effective endpoint protection and Attack Surface Reduction (ASR) enforcement.
<img width="1632" height="909" alt="Screenshot 2026-02-23 at 20 52 55" src="https://github.com/user-attachments/assets/86fbfeab-44e1-4198-a570-b75601743d84" />

**MITRE ATT&CK Mapping:**
- Execution - Commmand & Scripting Inerpreter (T1059)
- Defense Evasion - Impair Defenses (T1562)
