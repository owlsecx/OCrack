# 🦉 Ocrack

<p align="center">
  <img src="https://img.shields.io/badge/Platform-Linux-0a0c10?style=flat-square"/>
  <img src="https://img.shields.io/badge/Category-OPass-blue?style=flat-square"/>
  <img src="https://img.shields.io/badge/License-Proprietary-orange?style=flat-square"/>
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

This tool is part of the **OwlSec** suite — a collection of 275+ security and privacy tools.

🔗 [owlsec.org](https://owlsec.org)

---

## ©️ License

Proprietary — © 2026 Owlsec LLC. All rights reserved.

*Tools are distributed as pre-built executables. Source code is proprietary.*

---

## 🔍 Verification & Transparency

This tool is closed-source. These files let you see exactly what is inside it,
without the source:

- [`SBOM.cdx.json`](SBOM.cdx.json) — CycloneDX inventory: SHA-256 of this
  binary, bundled CPython version, and every bundled library with its exact
  version and license. Feed it to Grype, Trivy or Dependency-Track to audit
  our dependencies for CVEs yourself.
- [`THIRD-PARTY-NOTICES.md`](THIRD-PARTY-NOTICES.md) — the full license text
  of every third-party component, extracted from this binary.

**No telemetry, no analytics, no licence check-in.** This tool does not phone
home. Verify that claim yourself:

```bash
sudo strace -f -e trace=network ./Ocrack --help   # watch every network call
firejail --net=none ./Ocrack --help               # deny the network entirely
```

Release signing, GPL compliance and vulnerability reporting:
[**TRUST.md**](https://github.com/owlsecx/owl-os/blob/main/TRUST.md)
