# Task 2 - Enumerating Samba for Shares

## 🎯 Objective
Identify SMB shares and extract sensitive information.

## 🔍 SMB Enumeration

```bash
nmap -p 445 --script=smb-enum-shares.nse,smb-enum-users.nse 10.65.159.55
```

## 📂 Connect to SMB Share

```bash
smbclient //10.65.159.55/anonymous
```

## 📄 List Files

```bash
ls
```

## 📥 Download File

```bash
smbget -R smb://10.65.159.55/anonymous
```

## 📡 NFS Enumeration

```bash
nmap -p 111 --script=nfs-ls,nfs-statfs,nfs-showmount 10.65.159.55
```

## 📌 Key Findings
- SMB shares found: **3**
- File discovered: `log.txt`
- FTP service identified: **port 21**
- NFS mount exposed: `/var`

## 🧠 Notes
- Anonymous SMB access enabled file leakage
- log.txt contained SSH key path and service hints
