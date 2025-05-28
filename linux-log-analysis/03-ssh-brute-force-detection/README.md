
````markdown
# SSH Failed Login Analysis

## Description
This project analyzes SSH failed login attempts by parsing `/var/log/auth.log` to identify suspicious login activity. It focuses on extracting IP addresses with failed SSH password attempts and filtering out localhost entries.

## Steps Taken
1. Accessed the Kali Linux terminal and elevated to root using `sudo su`.
2. Used the following command to extract the IP addresses of failed SSH login attempts:
   ```bash
   grep "Failed password" /var/log/auth.log | awk '{print $(NF-3)}' | sort | uniq -c | sort -nr | head -n 10
````

3. Filtered out local addresses (::1 and 127.0.0.1) to focus on external IPs:

   ```bash
   grep "Failed password" /var/log/auth.log | awk '{print $(NF-3)}' | grep -vE '(^::1$|^127\.0\.0\.1$)' | sort | uniq -c | sort -nr | head -n 10
   ```
4. Reviewed the output to check for suspicious IP addresses indicating possible brute force attempts.

## Screenshot


## Summary

This project demonstrates how to identify potential brute force SSH login attempts on a Linux system by analyzing authentication logs. Filtering out local addresses helps focus on genuine external threats. This monitoring can help system admins respond to and mitigate unauthorized access attempts.

```
