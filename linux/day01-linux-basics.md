# Linux Day 1 - Basic Commands

## Objective

Learn basic Linux navigation and file management commands.

---

## 1. pwd (Print Working Directory)

Displays the current directory path.

### Command

```bash
pwd
```

### Example Output

```text
/home/ubuntu
```

---

## 2. ls (List Files and Directories)

Lists files and directories.

### Command

```bash
ls
```

### Command with Details

```bash
ls -l
```

### Command Including Hidden Files

```bash
ls -la
```

---

## 3. cd (Change Directory)

Used to move between directories.

### Go to Home Directory

```bash
cd
```

### Go to Specific Directory

```bash
cd /var/log
```

### Move One Directory Back

```bash
cd ..
```

---

## 4. mkdir (Make Directory)

Creates a new directory.

### Command

```bash
mkdir devops
```

### Verify

```bash
ls
```

---

## 5. touch (Create File)

Creates an empty file.

### Command

```bash
touch test.txt
```

### Verify

```bash
ls
```

---

## 6. cat (Display File Content)

Displays file content.

### Command

```bash
cat test.txt
```

---

## 7. echo (Write Content to File)

Writes text into a file.

### Command

```bash
echo "Hello Linux" > test.txt
```

### Check Content

```bash
cat test.txt
```

---

## 8. cp (Copy Files)

Copies files from one location to another.

### Command

```bash
cp test.txt backup.txt
```

---

## 9. mv (Move or Rename)

Rename file:

```bash
mv test.txt linux.txt
```

Move file:

```bash
mv linux.txt /tmp/
```

---

## 10. rm (Remove File)

Deletes files.

### Command

```bash
rm test.txt
```

### Delete Directory

```bash
rm -r mydirectory
```

---

## Hands-On Practice

Commands executed today:

```bash
pwd
ls -la
mkdir devops
cd devops
touch test.txt
echo "Hello Linux" > test.txt
cat test.txt
cp test.txt backup.txt
mv backup.txt backup1.txt
rm backup1.txt
```

---

## Key Learnings

- pwd shows current directory.
- ls lists files and directories.
- cd changes directories.
- mkdir creates directories.
- touch creates files.
- cat displays file content.
- cp copies files.
- mv moves or renames files.
- rm removes files and directories.

---

## Status

✅ Linux Day 1 Completed
