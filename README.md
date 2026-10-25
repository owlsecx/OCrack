# 🦉 Ocrack

<p align="center">
  <img src="https://img.shields.io/badge/Platform-Linux-0a0c10?style=flat-square"/>
  <img src="https://img.shields.io/badge/Category-OPass-blue?style=flat-square"/>
  <img src="https://img.shields.io/badge/License-MIT-green?style=flat-square"/>
  <img src="https://img.shields.io/badge/Part%20of-OwlSec%20Toolkit-7b5ea7?style=flat-square"/>
  <img src="https://img.shields.io/badge/Version-1.0-cyan?style=flat-square"/>
</p>

> **Ocrack** — Advanced password and hash cracker supporting dictionary.

---

> ⚠️ **AUTHORISED USE ONLY** — Use only on systems you own or have explicit written permission to test. Unauthorised use is illegal.

---

## 📌 Overview

OCrack is a professional hash and password auditing tool for authorised recovery and strength testing. It combines dictionary, mutation, mask, and related attack modes with hash identification so defenders can validate credentials and measure password policy effectiveness. Reports and logging support lab and assessment workflows.

---

## ✨ Features

- Dictionary cracking with optional mutation rules against a target hash
- Mask attacks and batch mode for files of many hashes
- Hash type identification and hash generation helpers for known plaintext
- Multi-threaded cracking with configurable worker count
- JSON report output and optional file logging for audit trails
- Modes spanning dictionary, brute force, rainbow, hybrid, PCFG, combinator, and Markov-style analysis

---

## ⚙️ Requirements

- **Linux**
- **No Python installation needed** — runs as a standalone executable

---

## 🚀 Usage

```bash
./Ocrack -i 5f4dcc3b5aa765d61d8327deb882cf99
./Ocrack -H 5f4dcc3b5aa765d61d8327deb882cf99 -w rockyou.txt -m
./Ocrack -b hashes.txt -w wordlist.txt -t 8 -o report.json
./Ocrack --help
```

---

## 📦 Part of OwlSec Toolkit

This tool is part of the **OwlSec** suite — a collection of 300+ security and privacy tools.

🔗 [owlsec.org](https://owlsec.org)

---

## ©️ License

MIT License — © Khaled S. Haddad

*Tools are distributed as pre-built executables. Source code is proprietary.*
