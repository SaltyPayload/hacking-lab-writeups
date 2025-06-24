# Bandit Level 1 → Level 2

### 🔐 Goal:
Find the password for the next level. The password is stored in a file called `-` located in the home directory.

---

### 🧪 Steps Taken:

1. Logged in using:
   ```bash
   ssh bandit1@bandit.labs.overthewire.org -p 2220
   ```

2. Listed files in the home directory:
   ```bash
   ls
   ```

3. Saw a file named `-`, which is tricky because `-` is usually interpreted as a flag.

4. To safely read the file, used:
   ```bash
   cat ./-
   ```

---

### ✅ Key Commands Used:

```bash
ssh bandit1@bandit.labs.overthewire.org -p 2220
ls
cat ./-
```

---

### 💡 What I Learned:

- Filenames that start with `-` can confuse commands.
- Use `./` to tell the shell it’s a file in the current directory.
