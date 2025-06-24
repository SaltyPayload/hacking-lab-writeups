# Bandit Level 0 → Level 1

### 🔐 Goal:
Connect to the server using SSH and find the password for the next level.

---

### 🧪 Steps Taken:

1. Used the SSH command provided by the challenge:
   ```bash
   ssh bandit0@bandit.labs.overthewire.org -p 2220
   ```

2. Logged in using the password:
   ```
   bandit0
   ```

3. Once logged in, I used:
   ```bash
   cat readme
   ```
   to read the contents of the file.

---

### ✅ Key Commands Used:

```bash
ssh bandit0@bandit.labs.overthewire.org -p 2220
cat readme
```

---

### 💡 What I Learned:

- How to connect to a remote server using SSH
- How to read a file using `cat`
- Sometimes the challenge is about **getting comfortable in the terminal**
