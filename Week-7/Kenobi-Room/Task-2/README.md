# Task 2 - SMB & NFS Enumeration

## 🎯 Goal
Enumerate SMB shares and identify NFS mounts.

## 🔍 Steps Performed

### SMB Enumeration

```bash
nmap -p 445 --script=smb-enum-shares.nse,smb-enum-users.nse 10.65.159.55
```

```bash
smbclient //10.65.159.55/anonymous
```

```bash
ls
```

```bash
smbget -R smb://10.65.159.55/anonymous
```

---

### NFS Enumeration

```bash
showmount -e 10.65.159.55
```

```bash
nmap -p 111 --script=nfs-ls,nfs-showmount 10.65.159.55
```

## 📌 Key Findings
- SMB anonymous share accessible
- File found: `log.txt`
- FTP service identified later on port **21**
- NFS mount exposed: `/var`

## 🧠 What I Learned
- SMB anonymous access risks
- How logs reveal sensitive paths
- NFS misconfigurations expose internal directories
