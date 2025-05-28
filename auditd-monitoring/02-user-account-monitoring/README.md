# Auditd Monitoring – User Account/Group Changes

This project demonstrates how to monitor user and group management activities on a Linux system using `auditd`. The goal is to detect actions such as user creation, modification, deletion, password changes, and group management — all of which are critical events for system integrity and insider threat detection.

---

##  Tools Used

- **Kali Linux**
- `auditd` – Audit daemon for tracking system-level events
- `ausearch`, `aureport` – For log querying and summaries

---

##  Objective

Track and log execution of user and group management commands:

- `/usr/sbin/useradd`, `/usr/sbin/usermod`, `/usr/sbin/userdel`
- `/usr/sbin/groupadd`, `/usr/sbin/groupmod`, `/usr/sbin/groupdel`
- `/usr/bin/passwd`

---

##  Steps Taken

### 1. Installed and Started `auditd`

```bash
sudo apt install auditd audispd-plugins -y
sudo systemctl enable auditd
sudo systemctl start auditd
````

### 2. Added Audit Rules

```bash
sudo auditctl -w /usr/sbin/useradd -p x -k user-activity
sudo auditctl -w /usr/sbin/usermod -p x -k user-activity
sudo auditctl -w /usr/sbin/userdel -p x -k user-activity
sudo auditctl -w /usr/sbin/groupadd -p x -k user-activity
sudo auditctl -w /usr/sbin/groupmod -p x -k user-activity
sudo auditctl -w /usr/sbin/groupdel -p x -k user-activity
sudo auditctl -w /usr/bin/passwd -p x -k user-activity
```

> 🔁 These rules ensure that every execution of the above binaries is logged.

### 3. Triggered User/Group Events

```bash
sudo useradd testuser
sudo passwd testuser
sudo usermod -aG sudo testuser
sudo groupadd testgroup
sudo groupmod -n newgroup testgroup
sudo groupdel newgroup
sudo userdel testuser
```

### 4. Queried Audit Logs

```bash
sudo ausearch -k user-activity
```

This returned all the audit logs tied to the keyword `user-activity`.

---

##  Screenshot

> The screenshot below shows successful log capture of user-related activities.

![Auditd User Activity Logs](./screenshot.png)

---

##  Summary

This project successfully demonstrated how to monitor user and group changes using `auditd` on Linux. Monitoring these events helps detect unauthorized account manipulation or privilege escalation attempts.

---

