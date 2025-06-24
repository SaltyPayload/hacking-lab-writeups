# Bandit Level 3 → Level 4

### 🔐 Goal:
The password for the next level is stored in a hidden file in the `inhere` directory.

---

### 🧪 Steps Taken:

1. Logged in:
   ```bash
   ssh bandit3@bandit.labs.overthewire.org -p 2220
   ```

2. Changed into the `inhere` directory:
   ```bash
   cd inhere
   ```

3. Listed files using `-a` to show hidden ones:
   ```bash
   ls -a
   ```

4. Found a hidden file called `.hidden` and displayed its contents:
   ```bash
   cat .hidden
   ```

---

### ✅ Key Commands Used:

```bash
cd inhere
ls -a
cat .hidden
```

---

### 💡 What I Learned:

- `ls -a` shows hidden files (those starting with a dot)
- Hidden files can hold important data — always check for them
