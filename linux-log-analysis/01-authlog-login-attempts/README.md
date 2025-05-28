# Audit Linux Auth Log – SSH Login Attempts Monitoring

## Project Overview

This project demonstrates how to monitor SSH login attempts on a Linux system by analyzing the `/var/log/auth.log` file using command-line tools like `grep`. It focuses on identifying successful and failed SSH login activities for security monitoring.

## Setup Steps

1. Ensure `rsyslog` is installed and running to capture system logs:

   ```bash
   sudo apt update && sudo apt install rsyslog -y  
   sudo systemctl enable rsyslog  
   sudo systemctl start rsyslog  
   ```
2. Install and start SSH server if not already running:

   ```bash
   sudo apt install openssh-server -y  
   sudo systemctl enable ssh  
   sudo systemctl start ssh  
   ```
3. Generate SSH login attempts (e.g., failed attempt):

   ```bash
   ssh fakeuser@localhost  
   ```
4. View recent SSH login entries in auth.log:

   ```bash
   grep -i "ssh" /var/log/auth.log | tail -n 20  
   ```

## Summary

This simple log inspection method helps detect unauthorized SSH login attempts, an important part of Linux host-based security monitoring.

---
