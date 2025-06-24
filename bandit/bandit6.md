# Bandit Level 6 → Level 7

### 🔐 Goal:
Find a file **owned by user bandit7, group bandit6**, and **exactly 33 bytes** in size.

---

### 🧪 Steps Taken:

1. Logged in:
   ```bash
   ssh bandit6@bandit.labs.overthewire.org -p 2220
   ```

2. Used `find` with owner/group/size filters:
   ```bash
   find / -user bandit7 -group bandit6 -size 33c 2>/dev/null
   ```

3. Read the file’s contents.

---

### ✅ Key Commands Used:

```bash
find / -user bandit7 -group bandit6 -size 33c 2>/dev/null
cat /path/to/file
```

---

### 💡 What I Learned:

- `2>/dev/null` hides permission errors from `find`
- You can search by **owner**, **group**, and **exact file size**
