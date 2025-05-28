#  Auditd Monitoring – Sudo Activity Monitoring

This project demonstrates how i monitord and detected the use of `sudo` on a Linux system using the `auditd` framework. Sudo commands are a common vector for privilege escalation, and tracking their usage is a critical Blue Team skill.

---

##  Objective

To Detect and investigate all usage of the `sudo` command, including suspicious privilege escalation attempts like `sudo su`, `sudo bash`, or direct access to sensitive files (e.g., `/etc/shadow`).

---

##  Tools Used

- `auditd` – Linux Auditing System
- `auditctl` – Runtime rule control
- `ausearch` – Audit log query tool
- Kali Linux

---

##  Step-by-Step Implementation

###  1. Ensure `auditd` is active

```bash
sudo systemctl status auditd
````

---

###  2. Added audit rule to monitor `sudo`

```bash
sudo auditctl -w /usr/bin/sudo -p x -k sudo-monitoring
```

* `-w`: Watched the file
* `-p x`: Monitored executions
* `-k`: Added a custom key (`sudo-monitoring`) for easy log filtering

---

###  3. Simulate `sudo` usage

```bash
sudo ls /
sudo whoami
sudo su
exit      # to leave root shell
sudo bash
sudo cp /etc/shadow /tmp/shadow.bak
sudo rm /tmp/shadow.bak
```

---

###  4. Search logs with ausearch

```bash
sudo ausearch -k sudo-monitoring
```

This displays detailed records of all `sudo` activity: user, timestamp, and command executed.

---

##  Screenshot

Below is a sample of the `ausearch` output after running monitored `sudo` commands.

![sudo-monitoring](./screenshot.png)

---

##  Summary

This setup is a lightweight and effective method to detect and investigate potential privilege escalation activity.

```
