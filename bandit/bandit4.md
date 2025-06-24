# Bandit Level 4 → Level 5

### 🔐 Goal:
The password for the next level is stored in a file **with human-readable text**, located in the `inhere` directory among other non-readable files.

---

### 🧪 Steps Taken:

1. Logged in and moved to the directory:
   ```bash
   ssh bandit4@bandit.labs.overthewire.org -p 2220
   cd inhere
   ```

2. Used `file *` to find the human-readable file:
   ```bash
   file *
   ```

3. Found the file that says “ASCII text” and used `cat` to read it.

---

### ✅ Key Commands Used:

```bash
cd inhere
file *
cat <filename>
```

---

### 💡 What I Learned:

- `file` tells you what kind of data is in a file
- Super useful when content isn’t obvious from the name or extension
