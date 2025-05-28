# AIDE File Integrity Monitoring on Linux

This project demonstrates how to monitor file integrity on a Linux system using [AIDE (Advanced Intrusion Detection Environment)](https://aide.github.io/). AIDE helps detect unauthorized changes to files and directories, making it useful for intrusion detection and system hardening.

---

## Tools & Setup

- **OS:** Kali Linux (on VirtualBox)
- **Tool:** AIDE (Advanced Intrusion Detection Environment)
- **User Mode:** Root (sudo)
- **Terminal:** Default Linux terminal

---

## Steps Performed

1. **Installed AIDE:**
   ```bash
   sudo apt update
   sudo apt install aide
   
2. **Initialized AIDE Database:**
   sudo aideinit

3. **Copied Generated DB to Default Location:**
   sudo cp /var/lib/aide/aide.db.new /var/lib/aide/aide.db

4. **Modified Files to Simulate Change:**
  Opened /etc/passwd using sudo nano /etc/passwd
  Added a test string to simulate file tampering

5. **Ran AIDE Check for Changes:**
   sudo aide --check

