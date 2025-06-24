# Bandit Level 7 → Level 8

### 🔐 Goal:
Find the password stored in a file that’s **next to the word “millionth”** in a large text file.

---

### 🧪 Steps Taken:

1. Logged in:
   ```bash
   ssh bandit7@bandit.labs.overthewire.org -p 2220
   ```

2. Searched for the line containing “millionth”:
   ```bash
   grep millionth data.txt
   ```

---

### ✅ Key Commands Used:

```bash
grep millionth data.txt
```

---

### 💡 What I Learned:

- `grep` is great for searching specific strings in big files
- You don’t need to scroll through thousands of lines manually
