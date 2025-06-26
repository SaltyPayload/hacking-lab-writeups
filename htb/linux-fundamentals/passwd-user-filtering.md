# Linux Fundamentals – `/etc/passwd` Filtering Challenge

This challenge involves filtering and extracting meaningful data from the `/etc/passwd` file using common Linux tools like `cat`, `grep`, `cut`, `tr`, `awk`, and `wc`.

---

## 🔍 Goals

1. A line with the username `cry0l1t3`  
2. All usernames  
3. Username `cry0l1t3` and their UID  
4. Username `cry0l1t3` and UID, separated by a comma  
5. Username `cry0l1t3`, UID, and shell, separated by a comma  
6. All usernames with UID and shell (comma-separated)  
7. Same as #6, but excluding entries with `nologin` or `false`  
8. Count of #7  

---

## ✅ Solutions

```bash
# 1. Get the line for username cry0l1t3
cat /etc/passwd | grep cry0l1t3

# 2. Get all usernames
cat /etc/passwd | cut -d":" -f1

# 3. Username cry0l1t3 and UID
cat /etc/passwd | grep cry0l1t3 | cut -d":" -f1,3

# 4. Same as above, but with commas
cat /etc/passwd | grep cry0l1t3 | cut -d":" -f1,3 | tr ":" ","

# 5. Username, UID, and shell for cry0l1t3
cat /etc/passwd | grep cry0l1t3 | awk -F: '{print $1 "," $3 "," $NF}'

# 6. All users with UID and shell
cat /etc/passwd | awk -F: '{print $1 "," $3 "," $NF}'

# 7. Exclude users with nologin or false shells
grep -vE 'false|nologin' /etc/passwd | awk -F: '{print $1 "," $3 "," $NF}'

# 8. Count of users from step 7
grep -vE 'false|nologin' /etc/passwd | awk -F: '{print $1 "," $3 "," $NF}' | tee /dev/tty | wc -l
