# Rootkit Detection with chkrootkit

This project demonstrates how to detect potential rootkits on a Linux system using the `chkrootkit` tool.

##  **Tools Used**

- **chkrootkit**: A Linux tool to locally check for signs of a rootkit.
- **Kali Linux**: Host operating system.

---

##  **Steps Taken**

###  1. **Update System Packages**

Updated the package list to ensure the latest versions:
```bash
sudo apt update

````

###  2. **Install chkrootkit**

Installed chkrootkit using the APT package manager:

```bash
sudo apt install chkrootkit -y
```

###  3. **Run chkrootkit Scan**

Performed a full system scan:

```bash
sudo chkrootkit
```

###  4. **Save Output **

The scan output can be saved to a file for later review:

```bash
sudo chkrootkit > chkrootkit-scan-report.txt
```

---

##  **Screenshot**

![chkrootkit scan result](./screenshot.png)

---

##  **Summary**

The `chkrootkit` tool scanned the system for rootkit infections by checking binaries, processes, and known indicators. No infections were found during the scan, confirming the system’s integrity. This process is essential for Linux-based intrusion detection and periodic system auditing.

```

--- 

