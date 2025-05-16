# 🚀 Federated Fairness Verification

[![Build Status](https://github.com/your‑username/federated-fairness-verification/actions/workflows/ci.yml/badge.svg)](https://github.com/your‑username/federated-fairness-verification/actions)  
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)  
[![NuSMV](https://img.shields.io/badge/NuSMV-v2.7.0-blue.svg)](http://nusmv.fbk.eu/)

> **Formal verification of fairness properties** in a 3‑client federated learning protocol using CTL & NuSMV.

---

## 📖 Table of Contents

- [Motivation](#-motivation)  
- [Key Features](#-key-features)  
- [Getting Started](#-getting-started)  
  - [Prerequisites](#prerequisites)  
  - [Installation](#installation)  
  - [Quick Run](#quick-run)  
- [Model & Specs](#-model--specs)  
- [Results](#-results)  
- [Future Work](#-future-work)  
- [Contributing](#-contributing)  
- [License](#-license)  
- [Contact](#-contact)  

---

## 🔍 Motivation

In federated learning, a server aggregates updates from many clients—but how can we **prove** that no honest client’s update ever gets starved or ignored? We model the protocol as an FSM and encode fairness, liveness, and safety properties in CTL, then automatically verify them with NuSMV.

---

## ✨ Key Features

- **NuSMV FSM**  
  - States: `idle`, `broadcast`, `collect`, `aggregate`, `evaluate`  
  - Round counter (0 – 5), 3‐client aggregation  
- **CTL Properties**  
  - **Eventual impact**: `AG (Submitted_i -> AF Applied_i)`  
  - **No starvation**: `AG (EF Applied_i)`  
  - **Collective fairness**: `AG (EF (Applied_1 & Applied_2 & Applied_3))`  
  - **Deadlock freedom** & **bounded rounds**  
- **Automated Verification**  
  - Shell script to install NuSMV, run model checks, and summarize pass/fail.  

---

## 🚀 Getting Started

### Prerequisites

- **NuSMV ≥ 2.7.0**  
- Linux / macOS (or Windows + WSL)  
- `git`, `bash`

### Installation

```bash
# Clone repository
git clone https://github.com/devendrasaim/federated-fairness-verification.git
cd federated-fairness-verification

# (optional) install NuSMV system‑wide or locally
# e.g. on Ubuntu:
sudo apt-get update && sudo apt-get install nusmv
