# 📁 Server Message Block (SMB)

## 📌 Overview

**Server Message Block (SMB)** is a network communication protocol primarily used for **file and printer sharing** between devices on a network. It enables applications to read and write files and request services from remote systems in a seamless and efficient manner.

## 🔧 Features

- Remote file access and management
- Printer and device sharing
- Inter-process communication
- Symbolic and hard link support
- File locking and access control
- Authentication via NTLM or Kerberos

## 🖥️ Implementations

- **Windows:** Native SMB client/server support
- **Linux/macOS:** SMB access via **Samba**
- **Network Attached Storage (NAS):** Commonly supports SMB for device interoperability

---

## 📚 Real-World Use Cases

| Use Case                  | Description                                                               |
|---------------------------|---------------------------------------------------------------------------|
| 🗂️ File Sharing          | Sharing files and folders over LAN/WAN using SMB                           |
| 🖨️ Printer Access        | Accessing and managing networked printers                                 |
| 🧠 Virtual Machine Storage| Hosting VM images for platforms like Hyper-V over SMB                      |
| 🧮 SQL Server on SMB      | Running databases off remote SMB shares                                   |
| 🧰 Data Center Storage    | Employed in Storage Spaces Direct and Storage Replica technologies         |
| 🧑‍💻 Container Volumes    | Enabling container access to shared directories using SMB global mapping    |

---

## 🛡️ Vulnerabilities and CVEs

While SMB is useful, it has also been a frequent target for attackers. Below are notable vulnerabilities:

### ⚠️ High-Impact CVEs

| CVE ID         | Description                                                                 | Impact                       |
|----------------|-----------------------------------------------------------------------------|-------------------------------|
| CVE-2025-33073 | Privilege escalation in Windows SMB due to faulty access control            | SYSTEM-level access          |
| CVE-2020-0796  | SMBv3 compression vulnerability enabling remote code execution              | Unauthenticated RCE          |
| CVE-2017-0144  | EternalBlue exploit targeting SMBv1, used in WannaCry ransomware             | Widespread malware infection |
| CVE-2017-7494  | Samba RCE via uploading shared library files                                 | Arbitrary code execution     |
| CVE-2021-44142 | Samba heap out-of-bounds R/W via extended attribute manipulation             | Remote code execution        |

### 🧠 Exploit Techniques

- **Remote Code Execution (RCE):** Crafted packets or malicious SMB requests allow attackers to run arbitrary code.
- **Privilege Escalation:** Exploiting flaws in access control mechanisms to gain elevated privileges.
- **Information Disclosure:** Weak authentication or misconfigured shares may leak sensitive information.
- **SMB signing disabled:** Allowing unauthenticated users to read files from the "shares" share—potentially exposing sensitive data without login.
---

## 🧠 Recommendations

- Always **disable SMBv1**, which is outdated and vulnerable.
- Apply **security patches** and updates promptly.
- Use **strong authentication** mechanisms and **network segmentation** to reduce exposure.
- Monitor SMB traffic with intrusion detection systems (IDS) and log analysis tools.

---

## ✍️ Authors & Contributions

This document was created to educate and support secure software development practices.

---

## 📜 License

This README is provided under the MIT License for educational and informational purposes.

