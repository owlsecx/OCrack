# 🦉 OCrack

<p align="center">
  <img src="https://img.shields.io/badge/Platform-Linux%20%2F%20Windows-informational?style=flat-square&logo=linux&logoColor=white&color=0a0c10"/>
  <img src="https://img.shields.io/badge/Category-OAttack%20%2F%20Password%20Auditing-red?style=flat-square"/>
  <img src="https://img.shields.io/badge/No%20Dependencies-Stdlib%20Only-green?style=flat-square"/>
  <img src="https://img.shields.io/badge/License-MIT-green?style=flat-square"/>
  <img src="https://img.shields.io/badge/Part%20of-OwlSec%20Toolkit-7b5ea7?style=flat-square"/>
  <img src="https://img.shields.io/badge/Version-1.0-cyan?style=flat-square"/>
</p>

> **OCrack** is a password and hash auditing tool — multi-threaded dictionary attack, exhaustive brute-force, mutation rule engine, hash identifier, hash generator, batch cracking, and JSON export. Zero external dependencies.

---

> ⚠️ **AUTHORISED SECURITY TESTING ONLY** — Use only on hashes you own or have written consent to test.

---

## 📌 Overview

OCrack identifies hash types from pattern and length, then attempts to recover the plaintext using dictionary, mutation, or brute-force methods. The engine automatically tries all candidate algorithms for each word — no need to specify the algorithm manually for standard hash lengths.

---

## 🖥️ Modules

| # | Module | Description |
|---|--------|-------------|
| **[1] Hash Identifier** | Detect hash algorithm from pattern and length — batch input supported |
| **[2] Dictionary Attack** | Wordlist attack with optional mutation rules — built-in sample or custom file |
| **[3] Brute Force** | Exhaustive charset-based search with configurable min/max length |
| **[4] Rule Mutator** | Generate an expanded mutated wordlist from an input file |
| **[5] Hash Generator** | Compute all supported hash types for any input string |
| **[6] Batch Crack** | Crack multiple hashes from a `.txt` file in one run |
| **[E] Export Session** | Save the full session log as JSON |

---

## 🔍 Supported Hash Algorithms

| Algorithm | Length | Notes |
|-----------|--------|-------|
| MD5 | 32 | Also matches NTLM, MD4, LM |
| SHA-1 | 40 | Also matches MySQL5, RIPEMD-160 |
| SHA-224 / SHA3-224 | 56 | |
| SHA-256 / SHA3-256 / BLAKE2s | 64 | |
| SHA-384 / SHA3-384 | 96 | |
| SHA-512 / SHA3-512 / Whirlpool / BLAKE2b | 128 | |
| NTLM | 32 | MD4 of UTF-16-LE encoding |
| bcrypt | 60 | Detected only — not crackable via dictionary |
| DES Unix Crypt | 13 | Pattern match |
| MD5 / SHA-256 / SHA-512 Unix Crypt | 34/98/106 | `$1$`, `$5$`, `$6$` format |

Auto-detection tries all candidate algorithms for the detected hash length — no manual algorithm selection required.

---

## 🔠 Brute Force Charsets

| Option | Charset |
|--------|---------|
| **[1] Digits only** | `0-9` |
| **[2] Lowercase alpha** | `a-z` |
| **[3] Mixed alphanum** | `a-z` + `0-9` |
| **[4] Full printable** | `a-Z` + `0-9` + symbols |
| **[5] Custom** | User-defined charset string |

Configurable min and max length. Large search spaces (length > 7 + charset > 36) trigger a confirmation warning before proceeding.

---

## 🔄 Mutation Rules

The mutation engine expands each base word with:

| Rule | Variants Generated |
|------|--------------------|
| **Case** | lowercase, UPPERCASE, Capitalize, tOGGLE |
| **Reverse** | `drowssap` |
| **Append digits** | `word0`–`word9`, `word00`, `word12`, `word123`, `word1234`, `word12345` |
| **Prepend digits** | `0word`–`9word` |
| **Year append** | `word1990`–`word2000`, `word2020`–`word2025` |
| **Symbol append** | `word!`, `word@`, `word#`, `word$`, `word.`, `word_`, `word-`, `word*`, plus `+1` variants |
| **Leet speak** | `a→4`, `e→3`, `i→1`, `o→0`, `s→5`, `t→7`, `b→8`, `g→9` |
| **Duplicate** | `wordword` |
| **Space normalise** | spaces removed or replaced with `_` |

The Rule Mutator module (standalone) processes up to 2,000 input words and saves the expanded list to a file. Dictionary Attack applies mutations to up to 500 words from the active wordlist inline.

---

## 📋 Built-in Wordlist

OCrack includes a 60-word built-in sample covering the most common weak passwords (including `password`, `admin`, `P@ssw0rd`, service defaults like `cisco`, `postgres`, `redis`, etc.) — used automatically when no custom wordlist is provided.

---

## 💻 CLI Mode

OCrack supports direct command-line usage without the menu:

```bash
# Identify a hash
./OCrack -i 5f4dcc3b5aa765d61d8327deb882cf99

# Generate hashes for a string
./OCrack -g "password"

# Dictionary attack with wordlist
./OCrack -H <hash> -w wordlist.txt

# Dictionary attack with mutations
./OCrack -H <hash> -w wordlist.txt -m

# Batch crack from file
./OCrack -b hashes.txt -w wordlist.txt

# Save results to JSON
./OCrack -H <hash> -w wordlist.txt -o results.json
```

### CLI Flags

| Flag | Description |
|------|-------------|
| `-H` / `--hash` | Target hash to crack |
| `-w` / `--wordlist` | Custom wordlist file |
| `-m` / `--mutate` | Apply mutation rules to wordlist |
| `-b` / `--batch` | File with multiple hashes (one per line) |
| `-g` / `--gen` | Generate all hash types for input text |
| `-i` / `--identify` | Identify hash type |
| `-o` / `--output` | Save JSON report to file |

---

## 📤 Export

JSON reports saved as `ocrack_<label>_YYYYMMDD_HHMMSS.json`:

| Label | Contents |
|-------|----------|
| `dict` | Hash, wordlist size, found plaintext + algorithm |
| `brute` | Hash, charset, tried count, found plaintext + algorithm |
| `batch` | All hashes, cracked map, total tried |
| `generator` | Input text, all computed hashes |
| `session` | Full session log of all operations |

---

## ⚙️ Requirements

- **Linux or Windows**
- **No Python installation needed** — runs as a standalone executable
- **No external dependencies** — stdlib only

---

## 🚀 Usage

```bash
# Interactive menu
./OCrack

# Direct CLI
./OCrack -H <hash> -w wordlist.txt
```

---

## 📦 Part of OwlSec Toolkit

This tool is part of the **OwlSec** suite — a collection of 300+ security and privacy tools.

🔗 [owlsec.org](https://owlsec.org)

---

## ©️ License

MIT License — © Khaled S. Haddad

*Tools are distributed as pre-built executables. Source code is proprietary.*
