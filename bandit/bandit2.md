# Bandit Level 2 → Level 3

### 🔐 Goal:
The password for the next level is stored in a file called `spaces in this filename`.

---

### 🧪 Steps Taken:

1. Logged in:
   ```bash
   ssh bandit2@bandit.labs.overthewire.org -p 2220
   ```

2. Listed files:
   ```bash
   ls
   ```

3. Found a file named:
   ```
   spaces in this filename
   ```

4. Used quotes to handle the spaces:
   ```bash
   cat "spaces in this filename"
   ```

---

### ✅ Key Commands Used:

```bash
ls
cat "spaces in this filename"
```

---

### 💡 What I Learned:

- Filenames with spaces need to be **quoted** or escaped.
- You can also use backslashes like:
  ```bash
  cat spaces\ in\ this\ filename
  ```
