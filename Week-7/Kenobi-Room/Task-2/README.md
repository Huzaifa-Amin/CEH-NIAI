# Task 2 - SMB and NFS Enumeration

## 🎯 Goal
Enumerate Samba shares and discover useful mount points.

## 🔍 Steps Performed
- Enumerated SMB shares using Nmap and smbclient.
- Found an anonymous share with a log file.
- Read the log file and found useful clues.
- Enumerated NFS exports using showmount and Nmap.

```bash
nmap -p 445 --script=smb-enum-shares.nse,smb-enum-users.nse 10.10.101.17
```bash
smbclient //10.10.101.17/anonymous
```bash
smbget -R smb://10.10.101.17/anonymous
```bash
showmount -e 10.10.101.17
```bash
nmap -p 111 --script=nfs-ls,nfs-showmount 10.10.101.17
