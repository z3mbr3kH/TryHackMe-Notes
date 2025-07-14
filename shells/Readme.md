# 🛡️ Penetration Testing 101: Getting a Shell

This document covers the fundamentals of gaining shell access during a penetration test. It outlines shell types, shellcode strategies, and the tools used in exploitation.

---

## 🎯 Objective

Once code injection is possible (e.g., via RFI vulnerability), the ultimate goal is to execute system commands remotely. This typically involves getting a shell on the target system.

**Shellcode**  
A piece of code designed to launch a remote shell on the compromised host, allowing the attacker to execute system commands.

---

## 🧠 Types of Shells

Shells are classified using the following criteria:

### 1. Privileges
- **Unprivileged Shells**: Limited to user-level commands and files.
- **Privileged Shells**: Execute system-wide commands and modify services/files.

> Shells inherit their privileges from the process being exploited.

### 2. Direction
- **Bind Shell**: Victim listens on a port, attacker connects to it.
- **Reverse Shell**: Victim connects to the attacker's machine.

### 3. Complexity
- **Simple Shellcode**:
  - Uses built-in system utilities
  - Less traceable
  - Basic functionality
- **Complex Shellcode**:
  - Custom programs/scripts
  - Advanced features (screenshots, keylogging)
  - Easier to trace and attribute

### 4. Structure
- **Stageless**:
  - Entire shellcode sent at once
  - Larger but self-contained
- **Staged**:
  - Sent in parts (e.g., stage0 and main payload)
  - Useful for small buffer exploits

---

## 🛠️ Tools

### `netcat` (nc)
- Create/listen to TCP/UDP connections
- Common usage:
  - Listen: `nc -lvp <port>`
  - Connect: `nc <host> <port>`

### `msfvenom`
- Part of Metasploit Framework
- Generate payloads/shellcodes
- Supports multiple OSs and interpreters
- Example args:
  - Payload selection: `-p <payload>`
  - List options: `--list payloads` or `--list-options`

### `msfconsole`
- Exploit execution and shell management
- Key commands:
  ```bash
  use exploit/multi/handler
  set payload <payload>
  show options
  set lport <your-listen-port>
  set lhost <your-ip>
  exploit
## 📚 Credits

This guide is based on the lecture material from:

**Daniele Ferla**  
*Sicurezza dell'informazione M (19/20)*  
**Università degli Studi di Bologna**
