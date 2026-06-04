<div align="center"> <img src="https://raw.githubusercontent.com/andreasbm/readme/master/assets/lines/rainbow.png" width="100%">
🧬 Mutation Machine

**[HIGH SCHOOL SENIOR PROJECT]** • **[ARCHIVED]** • **[HISTORICAL REFERENCE]**

[![Status:Archived](https://img.shields.io/badge/Status-Archived-red.svg?style=for-the-badge)](https://github.com/hutterfly/mutation-machine)
[![Language:Go](https://img.shields.io/badge/Language-Go-00ADD8.svg?style=for-the-badge&logo=go)](https://go.dev/)
[![Language:C](https://img.shields.io/badge/Language-C-A8B9CC.svg?style=for-the-badge&logo=c)](https://en.wikipedia.org/wiki/C_(programming_language))
[![Language:Python](https://img.shields.io/badge/Language-Python-3776AB.svg?style=for-the-badge&logo=python)](https://python.org/)

*A polymorphic engine for Linux binaries, exploring encryption and fileless execution.*
</div>

---

 ### 📜 Historical Context & Skill Level Notice
> This repository was my **High School Senior Project**. It represents a significant milestone in my early self-taught journey into systems programming, cybersecurity, and low-level logic.
>
> While functional and an ambitious undertaking for its time, the code and architecture found here **do not reflect my current professional standards or engineering practices.**
>
> **For examples of my current work, please visit my [Profile](https://github.com/hutterfly).**

---

### 🚀 Technical Overview
**Mutation Machine** is a polymorphic builder designed to "mutate" Linux binaries to evade signature-based detection. It transforms a compiled executable into a new, logically equivalent C program that decrypts and executes itself entirely in memory.

#### ⚙️ The Mutation Workflow:
1.  **Payload Preparation:** A Python utility converts the target binaryinto a C-compatible comma-separated hex array.
2.  **Go Mutation Engine:** The engine (`main.go`) performs several layers of obfuscation:
    *   **Dynamic XOR Encryption:** Generates a random key (1-128 chars) and XORs the payload.
    *   **Source-Level Polymorphism:** The engine contains **embedded C code strings** that it injects into the template.
    *   **Junk Code Injection:** It scans the source for `//marker` tags and injects "dead code" (e.g., `if(5 == 10)` or do-nothing `while` loops) to change the file's structure and cryptographic hash.
3.  **Fileless Execution:** The output C code utilizes `memfd_create` (to create an anonymous RAM-based file) and `fexecve` to execute the payload without ever touching the disk.

### 🛠️ The Legacy Stack
*   **Go:** The orchestration engine and polymorphic injector.
*   **Python:** Pre-processor for hex-formatting.
*   **C:** The "Stub" template (`decrypt-exec`) used for the final loader.
*   **Linux Internals:** Exploration of memory-backed file descriptors and process execution.

### 🧠 Retrospective: "The High School Era"
Building this project was my first deep-dive into:
*   **Binary Analysis:** Learning how ELF files are structured and how they run.
*   **Cryptography:** Implementing stream ciphers and key management.
*   **Evasion Techniques:** Understanding signature-based detection and the power of polymorphism.
*   **Self-Taught Architecture:** Managing multi-language workflows (Go/Python/C) before I learned modern CI/CD.

---

<div align="center">
    <sub>Built with passion in 2022 • Managed by Samantha H.</sub>
</div>
