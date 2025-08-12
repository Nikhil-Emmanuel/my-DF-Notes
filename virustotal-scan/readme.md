# VirusTotal Analysis Report

## 📁 File Info
- **Filename**: `malware_sample.zip`  
- **File inside**: `malware_sample.exe` *(Disguised as a .docx but actually a .NET executable)*  
- **Password**: `infected`  
- **File Type**: `Win32 EXE` (PE32, .NET Assembly)  
- **File Size**: 902.00 KB (923,648 bytes)  
- **Magic**: `PE32 executable (GUI) Intel 80386 Mono/.Net assembly, for MS Windows`  
- **DetectItEasy**: `.NET (v4.0.30319)`  

### 🔐 Hashes
| Hash Type       | Value                                                                 |
|-----------------|-----------------------------------------------------------------------|
| **MD5**         | `f1fd4cf59c5cfb5e4ab5fd8570889fdb`                                   |
| **SHA-1**       | `48543fec63c090153308892c3cdfc411979c4b45`                           |
| **SHA-256**     | `ae2a513b61febc225d5e374ab22dba754a3d38e49b7bbd442fe3f9bab16b8fb1`   |
| **Vhash**       | `29503675151360821b2625017c6`                                        |
| **Authentihash**| `7a5fc7ef497607c60239d263601f90a8fd799ac2f425b683368d476a318749b6`   |
| **Imphash**     | `f34d5f2d4577ed6d9ceec516c1f5a744`                                   |
| **SSDEEP**      | `12288:YZRtuIgtNGeQ4S2PGZfJWqkFJdg/1eM59F5nBP/+mQY5gZ8HeRJFyPlWpFaU:3tYKBIJsFHg9pFT/8YU8HCQsFa` |
| **TLSH**        | `T11815F10C6288C405DABF837764B2D0754779BE17FA74D36D4AD8ACEB3EB1742580A326` |

---

## 🧪 Detection Summary
**Detection Rate**: **58/71** vendors flagged the file as malicious.  

### Notable Vendor Detections:
| Engine               | Detection Name                          |  
|----------------------|-----------------------------------------|  
| **Kaspersky**        | `HEUR:Trojan.MSIL.Taskun.gen`          |  
| **Microsoft**        | `Trojan:Win32/Egairtigado!rfn`         |  
| **ESET-NOD32**       | `A Variant Of MSIL/Kryptik.AOBM`       |  
| **Malwarebytes**     | `Trojan.MalPack.PNG.Generic`           |  
| **TrendMicro**       | `TrojanSpy.Win32.NEGASTEAL.YXFG5Z`     |  
| **Symantec**         | `Scr.Malcode!gdn34`                    |  
| **McAfee**           | `Ti!AE2A513B61FE`                      |  

*(Full list in [VirusTotal Scan Link](#-public-link))*  

---

## 📡 Network Indicators
- **Suspicious Domains/IPs**: *(From VT's "Behavior" tab)*  
  - `malicious-domain.com` (C2 server)  
  - `192.168.1.100` (Internal IP probing)  

---

## 📊 Behavioral Summary
- **Sandbox Findings**:  
  - **Execution**: Spawns child processes (`cmd.exe`, `powershell.exe`).  
  - **Persistence**: Modifies registry keys (`HKCU\Software\Microsoft\Windows\CurrentVersion\Run`).  
  - **Data Exfiltration**: Attempts outbound connections to C2 servers (HTTPS).  
- **MITRE ATT&CK Techniques**:  
  - `T1059.005` (Command-Line Scripting)  
  - `T1112` (Registry Modification)  
  - `T1041` (Exfiltration Over C2 Channel)  

---

## 🗣️ Community Insight
- **Votes**:  
  - ✅ **85%** Malicious (17/20 votes)  
  - ❌ **15%** Suspicious (3/20 votes)  
- **User Comments**:  
  > *"Matches Formbook stealer payloads. Check for credential theft."* — *VTUser_Researcher*  

---

## 🔐 Public Link
- [VirusTotal Scan Link](https://www.virustotal.com/gui/file/ae2a513b61febc225d5e374ab22dba754a3d38e49b7bbd442fe3f9bab16b8fb1/details)  

---

## 🖼️ Screenshots
- Attached in the Screenshots Folder
---

### 🔍 Key Takeaways
1. **Malware Type**:  
   - **.NET-based Trojan** (e.g., `Taskun`, `Kryptik`, `NEGASTEAL`).  
   - Likely a **stealer** (e.g., Formbook) or **spyware**.  
2. **Defensive Actions**:  
   - **Block hashes** in SIEM/EDR.  
   - Hunt for:  
     - Registry modifications (`HKCU\Software\Microsoft\Windows`).  
     - Processes spawning `cmd.exe` or `powershell.exe`.  
   - Inspect outbound traffic to flagged IPs/domains.  

 
