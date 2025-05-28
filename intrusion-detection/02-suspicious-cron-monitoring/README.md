# Suspicious Cron Job Monitoring

This project focuses on monitoring cron jobs on a Linux system to detect suspicious or unauthorized scheduled tasks that may indicate a security breach.

##  **Tools Used**

- **cron**: Linux built-in scheduler.
- **grep**, **awk**, **ls**: Command-line tools for inspecting cron job files and logs.
- **Kali Linux**: Host operating system.

---

##  **Steps Taken**

###  1. **List User Cron Jobs**

Checked the cron jobs scheduled by the current user:

```bash
crontab -l

````

###  2. **Inspect System-Wide Cron Directories**

Checked system cron directories for unusual scripts or jobs:

```bash
ls -la /etc/cron.*
```

###  3. **Review Cron Logs**

Examined cron logs for suspicious activity (location may vary by distro):

```bash
sudo grep CRON /var/log/syslog
```


###  4. **Identify Unauthorized or Unexpected Jobs**

Looked for unexpected entries or scripts that could indicate persistence or malicious activity.

---

##  **Screenshots**


---

##  **Summary**

Regular monitoring of cron jobs is essential to detect unauthorized persistence mechanisms. This project demonstrated how to list and inspect scheduled jobs, review cron logs, and identify suspicious entries that may indicate compromise.

---

```
