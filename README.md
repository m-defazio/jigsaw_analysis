# UNIVERSITY OF NAPLES FEDERICO II

**Presented by:**  
Lorenzo Esposito  
Michele De Fazio
Armando Zevola

---

## Discovering the Risks of Extensive Use of Virtual Reality

---

### Static Analysis  
Static analysis is essential to understand the Jigsaw malware without activating it.  
It allows identification of typical ransomware characteristics and behaviors, such as text strings and encryption functions.  
Through this analysis, indicators of compromise and useful patterns for threat detection and mitigation are identified.

---

### Static Analysis Results  
- The malware appears under the name `BitcoinBlackmailer.exe`, disguising itself as Firefox.  
- It was written using the .NET framework and obfuscated to prevent reverse engineering.  
- Typical ransomware functions like `EncryptFile` and `DecryptFile` were identified.  
- A suspicious URL directing to Coinbase for bitcoin payment was found.

---

### Dependency Analysis  
- An obfuscated library used for encryption was detected.  
- The malware uses standard OS cryptographic functions.  
- Some Windows APIs are used for downloading data and managing network connections.

---

### Reverse Engineering  
- The code is obfuscated, but the main class managing encryption was identified.  
- Encrypted files use the `.fun` extension.  
- The encryption algorithm is symmetric and based on AES.  
- The malware prevents debugging through breakpoints and evasion techniques.

---

### Dynamic Analysis  
- In a controlled environment, the ransomware encrypts files and displays a GUI with ransom instructions.  
- If the ransom is not paid, the malware progressively deletes files.  
- Registry entries are created to maintain persistence after system reboot.  
- A process responsible for encrypting data runs and manipulates the system to escalate privileges.

---

### Persistence and Privilege Escalation Techniques  
- Modifies registry keys to start hidden processes (e.g., `firefox.exe`).  
- Uses system libraries to manipulate the Windows kernel and escalate privileges.

---

### Malware Detection and Prevention  
- Identification rules were developed based on specific malware patterns.  
- The MITRE ATT&CK framework was used to define tactics and techniques adopted by the malware, useful for prevention and response.

---

### MITRE ATT&CK Techniques Used by Jigsaw  
- **Phishing (T1566):** Distributed via emails with malicious attachments.  
- **User Execution (T1204):** User unknowingly executes the malware.  
- **Persistence (T1547.001):** Creates registry entries for automatic startup.  
- **Defense Evasion:** Code obfuscation and debugger detection.  
- **Discovery:** Scans the filesystem to identify files to encrypt.  
- **Impact:** Data encryption, periodic file deletion, and removal of restore points.

---

## Conclusions  
The Jigsaw ransomware represents a real threat due to its advanced obfuscation, persistence, and encryption techniques.  
Detection and prevention require specific tools and strategies based on established behavior models such as MITRE ATT&CK.
