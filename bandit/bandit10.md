# Bandit Level 10 → Level 11

### 🔐 Goal:
The password is stored in a file that’s **base64 encoded**.

---

### 🧪 Steps Taken:

1. Logged in:
   ```bash
   ssh bandit10@bandit.labs.overthewire.org -p 2220
   ```

2. Decoded the file using `base64 -d`:
   ```bash
   cat data.txt | base64 -d
   ```

---

### ✅ Key Commands Used:

```bash
base64 -d data.txt
```

---

### 💡 What I Learned:

- `base64 -d` decodes base64-encoded files
- Always check file content before assuming it's random gibberish
