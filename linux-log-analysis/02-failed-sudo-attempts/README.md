````markdown
# Failed Sudo Authentication Attempts

## 🛠 Description

This project demonstrates how failed `sudo` authentication attempts are logged in Linux via `/var/log/auth.log`. Such events are critical in detecting brute-force or unauthorized access attempts on a system.

---

## 🔍 Steps Taken

1. Ensured `rsyslog` is installed and running:

   ```bash
   sudo apt update && sudo apt install rsyslog -y
   sudo systemctl enable rsyslog
   sudo systemctl start rsyslog
````

2. Forced `sudo` to request password again:

   ```bash
   sudo -k
   ```

3. Entered `sudo ls` and **intentionally typed the wrong password three times**.

4. Verified the log entries:

   ```bash
   sudo grep 'sudo' /var/log/auth.log | grep 'authentication failure' | tail -n 20
   ```

---

## 🖼 Screenshot

![Failed sudo attempt logs](screenshot.png)

---

## ✅ Summary

Failed `sudo` login attempts generate `authentication failure` entries in `/var/log/auth.log`. Monitoring these logs helps detect unauthorized privilege escalation attempts or brute-force activity targeting administrative access.

```
```
