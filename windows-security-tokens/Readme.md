# 🛡️ Windows Access Tokens: A Quick Guide

This README provides a clear explanation of two types of access tokens used in Windows security: **Primary Access Tokens** and **Impersonation Tokens**. These tokens are critical for identity and privilege management in multi-user environments.

---

## 📌 Overview

Access tokens define the security context under which code is executed. They contain information about the user's identity and privileges.

---

## 🧑‍💼 Primary Access Tokens

### ✅ What They Are
Primary tokens are generated when a user logs on. They represent the full security context of that user.

### 📋 Key Features
- Tied to a user session
- Associated with processes started by that user
- Used to launch applications with user-specific privileges

### 🧠 Example
When a user signs in and opens Notepad, the Notepad process receives the primary token of that user.

---

## 🔄 Impersonation Tokens

### ✅ What They Are
Impersonation tokens let one thread or process temporarily take on the identity of another user (typically for resource access).

### 📋 Key Features
- Used in multi-tiered applications (e.g., client-server)
- Not tied to a session—used for temporary access
- Associated with individual threads rather than processes

### 🧠 Example
A web server impersonates a user to access a file on their behalf using their access rights.

---

## 🧩 Key Differences

| Feature               | Primary Access Token                        | Impersonation Token                        |
|----------------------|---------------------------------------------|--------------------------------------------|
| Scope                | Entire process                              | Individual thread                          |
| Identity             | Full user context                           | Borrowed user identity                     |
| Creation             | On user logon                               | Through impersonation APIs                 |
| Typical Use Case     | Launching apps under a user account         | Delegated access in server applications    |
| Lifespan             | Persistent during session                   | Temporary, revertible                      |

---

## 🆚 Impersonation vs `setuid` in Linux

`setuid` in Linux is a conceptually similar mechanism:
- It lets executables run with the permissions of the file owner.
- Impersonation tokens, however, are more dynamic and thread-specific.

### 🔍 Comparison

| Feature               | `setuid` (Linux)                           | Impersonation Token (Windows)               |
|------------------------|--------------------------------------------|---------------------------------------------|
| Mechanism              | Set on executable                          | API call (`ImpersonateLoggedOnUser`)        |
| Scope                  | Whole process                              | Specific thread                              |
| Use Case               | Elevate privilege for safe operations       | Delegate user access in multi-user systems  |
| Security Context       | Fixed via file ownership                   | Dynamic via token switching                  |

---

## 📚 Further Exploration

- Windows API: `ImpersonateLoggedOnUser()`, `RevertToSelf()`
- Linux: `setuid`, `seteuid`, `setgid`
- Security considerations for impersonation and privilege escalation

---

## 🔧 Notes

When designing secure applications:
- Use impersonation judiciously to avoid privilege escalation risks
- Always revert to the original token after impersonation
- Audit token usage during sensitive operations

