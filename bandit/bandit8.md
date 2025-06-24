# Bandit Level 8 → Level 9

### 🔐 Goal:
The password is in a file that’s **a single line**, but **occurs only once** — all others are duplicates.

---

### 🧪 Steps Taken:

1. Logged in:
   ```bash
   ssh bandit8@bandit.labs.overthewire.org -p 2220
   ```

2. Used these commands:
   ```bash
   sort data.txt | uniq -u
   ```

---

### ✅ Key Commands Used:

```bash
sort data.txt | uniq -u
```

---

### 💡 What I Learned:

- `sort` prepares the data for `uniq`
- `uniq -u` shows only the line that **occurs once**
