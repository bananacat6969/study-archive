# 🪟 Week 4: Windows Internals for Hackers

## 📌 Goals:
- Understand Windows file system, processes, services
- Learn PowerShell basics for red teaming
- Study registry, UAC, and scheduled tasks

---

## 🧠 Core Concepts

### 🗂️ Windows Layout
- `%SystemRoot%` → C:\Windows
- `%APPDATA%`, `%TEMP%`, `%ProgramFiles%`

### ⚙️ Admin Tools
- `taskmgr`, `regedit`, `services.msc`, `eventvwr`
- `powershell`, `cmd`

### 🔒 Registry & UAC
- Registry stores system configs (e.g., HKLM\Software\Microsoft\Windows)
- UAC (User Account Control) restricts privilege elevation

### 🖥️ Services and Tasks
- `schtasks`, `Get-Service`, `sc query`
- Malicious persistence can hide here

---

## 💻 PowerShell Basics
```powershell
Get-Process
Get-Service
Get-EventLog -LogName Security -Newest 10
Set-ExecutionPolicy Bypass -Scope Process
