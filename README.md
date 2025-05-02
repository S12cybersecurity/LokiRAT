# LokiRAT

![image](https://github.com/S12cybersecurity/LokiRAT/assets/79543461/39b518c0-8f8e-49d2-8552-d77d5cb54f62)

This project implements a **Remote Access Trojan (RAT)** developed from scratch. It is designed to explore and demonstrate advanced techniques used in malware development . This is not a basic tool but an implementation focusing on key functionalities that make these tools powerful.

The purpose of this project is to understand how real-world RATs function for both **offensive security** (pentesting) and **defensive security** (malware analysis, threat hunting, detection engineering). By understanding their construction, you can improve your ability to defend against them.

## 📘 Learn with the Course

Each feature implemented in LokiRAT, along with the full development process of a custom Remote Access Trojan, is explained step by step in the course:
🎓 Building a Custom Remote Access Trojan (RAT)

In this course, you'll learn:

- How to architect and build your own RAT from scratch

- Stealth and evasion techniques used by advanced malware

- How to build a full Command & Control infrastructure

- Windows internals, API hooking, and rootkit development

- How to implement reliable communication between client and server (C++ ↔ C2)

⚠️ The course is focused on malware development. While the repository includes a web dashboard (LokiWebViewer) built with Angular, web development fundamentals are not covered, as this is part of a Malware Development Academy. The web interface is provided for completeness, not as a teaching topic.

## 🛠️ Features

### Anti-Detection & Evasion

- **TimeStomping** – Alters file timestamps to mimic legitimate binaries.

- **Unhook NTDLL** – Restores a clean copy of NTDLL to bypass userland hooks.

- **Unhook NTDLL Hooks** – Replaces hooked NTDLL with a fresh copy to evade AV/EDR instrumentation.

- **Command Line Spoofing** – Masks malicious processes with benign command lines.

- **ETW Patcher** – Hooks and disables ETW logging at runtime.

- **No-New Thread Execution** – Executes shellcode without creating new threads.

- **Own VirtualAlloc (Module Stomping)** – Executes shellcode within legitimate module memory.

### Persistence & Privilege Escalation

- **Execute EXE As Admin** – Uses UAC bypass to escalate privileges.

- **Task Creator** – Creates scheduled tasks for persistence.

**Privilege Escalation to SYSTEM** – Token stealing via SYSTEM process handles.**

- **Information Gathering**

- **List Processes** – Enumerates running processes.

- **Enumeration** – Gathers OS, disk, registry, and network info.

- **Security Detector** – Checks for antivirus and monitoring tools.

- **Mapping Free Handles in Memory** – Reuses handles from trusted processes to evade detection.

### Rootkit

- **Userland Rootkit** – Intercepts system API calls.

- **File Hider** – Hides files and directories.

- **File Unhider** – Restores hidden files.

- **Process Hider** – Conceals malicious processes.

- **Registry Hider** - Hide Registry keys and values

### File Operations

- **File Upload** – Sends files to C2 using HTTP fragmentation.

- **File Download** – Retrieves files from C2.

- **File Explorer** – Browses file system remotely.

### Keylogging

- **Keylogger** – Captures and exfiltrates keystrokes.

### RDP & Credential Access

- **RDP Stealer** – Extracts saved RDP credentials and session info.

### ETW & Memory

- **ETW Patcher** – Neutralizes ETW logging.

- **Mapping Free Handles in Memory** – Leverages open handles from trusted processes.

## 💻 Technologies

LokiRAT is split into three main components, each using a specific technology stack suited to its role:
### 🔹 Loki (C++ Agent / Client)

- **Language:** C++

- **Platform:** Windows

- **Purpose:** Compiled malware payload executed on the victim's system.

- **Highlights:** Native Windows API usage, stealth techniques, memory manipulation, anti-analysis features.

### 🔸 LokiServer (C2 Server + API)

- **Language:** C# (.NET)

- **Framework:** ASP.NET Core

- **Purpose:** Acts as the Command and Control (C2) server and provides REST API endpoints for the frontend.

- **Highlights:** Token-based security, agent registration, real-time command relay.

### 🔺 LokiWebViewer (Attacker’s Web Dashboard)

- **Language:** TypeScript

- **Framework:** Angular

- **Purpose:** Web-based frontend for attackers to manage infected agents through the C2 API.

- **Highlights:** Clean UI for remote access, data display, and command execution on victims.

## ⚠️ Legal & Ethical Disclaimer

This project is for educational purposes only. All code and research are provided to support learning, detection engineering, and ethical red teaming. Do not use this project for unauthorized access or activity against systems you do not own or have permission to test.

Always follow local laws and industry best practices.

## 🧩 Contributions

Pull requests are welcome for new modules, improvements, or documentation enhancements.

If you're interested in contributing or collaborating, feel free to fork and open an issue.
