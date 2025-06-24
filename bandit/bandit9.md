# Bandit Level 9 → Level 10

### 🔐 Goal:
Find the password in a file with **lots of random characters**, but the password is **only lowercase and uppercase letters**.

---

### 🧪 Steps Taken:

1. Logged in:
   ```bash
   ssh bandit9@bandit.labs.overthewire.org -p 2220
   ```

2. Used `strings` with `grep` to isolate the password:
   ```bash
   strings data.txt | grep '^[a-zA-Z]\+$'
   ```

---

### ✅ Key Commands Used:

```bash
strings data.txt | grep '^[a-zA-Z]\+$'
```

---

### 💡 What I Learned:

- `strings` pulls readable text from a binary or noisy file
- `grep '^[a-zA-Z]\+$'` finds lines with **only letters**
