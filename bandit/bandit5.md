# Bandit Level 5 → Level 6

### 🔐 Goal:
Find the only file **with 1033 bytes** in the `inhere` directory (and subdirectories).

---

### 🧪 Steps Taken:

1. Logged in and navigated:
   ```bash
   ssh bandit5@bandit.labs.overthewire.org -p 2220
   cd inhere
   ```

2. Used `find` to locate a file with exactly 1033 bytes:
   ```bash
   find . -type f -size 1033c
   ```

3. Used `cat` to read the file’s content.

---

### ✅ Key Commands Used:

```bash
find . -type f -size 1033c
cat ./maybe/this/one
```

---

### 💡 What I Learned:

- `find` can search by size (`1033c` means 1033 bytes)
- Helpful for filtering through noisy file structures
