# Week 4 Lab: Offline Password Cracking & Hash Extraction (Kali Linux)

A hands-on cybersecurity lab demonstrating password hash extraction and offline dictionary-based recovery on a password-protected PDF file using **Kali Linux**, **John the Ripper (`pdf2john`)**, and **Johnny** (GUI).

---

## 📋 Lab Summary

| Parameter | Details |
| :--- | :--- |
| **Environment** | Kali Linux (`2025.4`) on Oracle VirtualBox |
| **Target File** | `My Locked PDF12.pdf` |
| **Extracted Hash File** | `hash1.txt` |
| **Hash Format** | `$pdf$4*4*128*-10...` (`format=PDF`) |
| **Tools Used** | `pdf2john`, John the Ripper, Johnny (GUI) |
| **Recovered Password** | `good-luck` |

---

## 🛠️ Lab Methodology & Workflow

### 1. Tool Installation & Environment Setup
Installed **Johnny** (the graphical user interface for John the Ripper) via the Kali Linux terminal to manage hash sessions and monitor cracking progress visually:
```bash
sudo apt update && sudo apt install johnny -y
