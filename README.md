[README.md](https://github.com/user-attachments/files/27319210/README.md)
#  Zero-Cost-Automation-Observability

> **Solving the "Black Box" Problem in Headless Browser Testing — at Zero Infrastructure Cost.**

A high-performance, hybrid CI/CD automation framework that brings full visual observability to cloud-based test execution. Built on Oracle Cloud Infrastructure (OCI) and GitHub Actions, this project enables real-time browser monitoring and automated failure replays without spending a single dollar on infrastructure.

---

## The Innovation: "Headed" Observability in a "Headless" World

Standard CI/CD pipelines execute tests in a **Black Box** — invisible, silent, and nearly impossible to debug when UI-specific failures or flaky tests occur. This framework shatters that limitation through three core mechanisms:

| Mechanism | What It Does |
|---|---|
|  **Virtual X11 Redirection** | Maps headless execution to a virtual display buffer, enabling "headed" browser behaviour in a fully cloud-native environment |
|  **Live VNC Streaming** | Allows developers to dial in to the cloud runner and watch tests execute in real-time |
|  **Rolling FFmpeg Replays** | Maintains a constant 10-second background video buffer — saves and uploads a `.mp4` clip **only** when a test failure is detected |

---

##  Technical Architecture

The framework is built on a cloud-native stack designed for **maximum efficiency with zero overhead cost**.

###  Cloud Infrastructure
- **Oracle Cloud Infrastructure (OCI)** — Always-Free ARM compute instance
- **24 GB RAM** — High-performance execution without pay-as-you-go billing

###  Orchestration & Automation
- **Self-Hosted GitHub Actions Runner** — Tests bypass public runners and execute directly on the hardened OCI instance within a private, secured environment
- **Java 21 + Maven** — Modern enterprise stack with the latest performance optimizations and language features
- **Selenium 4.x** — Handles complex UI interactions including JavaScript execution, explicit waits, and alert management

###  Observability Stack
- **Xvfb** — Creates a virtual X11 display buffer, enabling fully "headed" browser execution in a headless cloud environment
- **FFmpeg Rolling Buffer** — Continuously records the execution stream in a 10-second sliding window
- **Automated `.mp4` Artifact Generation** — Dynamically clips and uploads the buffer **only on TestNG failure**, providing 100% visibility into bugs with zero storage waste

---

##  Observability Proof (Execution Results)

The framework's strength is validated in the **GitHub Actions Dashboard** on every single run.

### 1. CI/CD Pipeline Orchestration

```
✅ Initialize Environment      → Xvfb display server + VNC monitoring spun up automatically
✅ Self-Hosted Execution       → Tests run on hardened OCI instance, not public GitHub runners
✅ Test Suite Execution        → Full Selenium suite with real-time display streaming
✅ Artifact Upload (on fail)   → 10-second .mp4 failure replay clipped and uploaded
```

### 2. Automated Failure Artifact Generation

When a test fails, the framework **automatically extracts a 10-second replay clip** and makes it available in the **Artifacts section** of the GitHub Actions run.

> No bug remains a mystery. Every failure is captured, clipped, and accessible.

---

##  Advanced Features

###  JavaScript Executor Integration
Handles complex UI interactions that standard WebDriver commands cannot reach — including dynamic element highlighting, scroll-into-view, and client-side state manipulation.

###  Synchronization Strategies
Implements both **Explicit Waits** and **Fluent Waits** with custom polling intervals to eliminate test flakiness caused by dynamic content and asynchronous rendering.

###  Dynamic Alert Handling
Robust management of browser-level modal windows, JavaScript `alert()` / `confirm()` / `prompt()` dialogs, and unexpected pop-ups — ensuring tests never hang silently on unhandled alerts.

---

##  Security & Privacy Note

> Core implementation files (`BaseTest.java`) and OCI environment configurations are intentionally kept private to protect infrastructure security and proprietary observability logic.

---

##  Known Edge Cases & Hardening Notes

| Risk | Mitigation |
|---|---|
| **FFmpeg race condition** on failure | Add a 1–2s delay before clip extraction to ensure final frames are flushed |
| **Xvfb display collision** on concurrent runs | Dynamically assign display numbers (`:99`, `:100`) seeded by GitHub Actions run ID |
| **VNC left open post-run** | Kill VNC server in a teardown step using `always()` condition in Actions YAML |
| **JVM crash bypasses TestNG listener** | Add a JVM shutdown hook or post-step safety net for non-TestNG failures |
| **10s buffer may miss root cause** | Make buffer duration configurable via `REPLAY_BUFFER_SECONDS` env variable (recommended: 20–30s) |

---

##  Tech Stack Summary

![Java](https://img.shields.io/badge/Java-21-orange?style=flat-square&logo=openjdk)
![Maven](https://img.shields.io/badge/Maven-Build-blue?style=flat-square&logo=apachemaven)
![Selenium](https://img.shields.io/badge/Selenium-4.x-green?style=flat-square&logo=selenium)
![TestNG](https://img.shields.io/badge/TestNG-Framework-red?style=flat-square)
![GitHub Actions](https://img.shields.io/badge/GitHub_Actions-CI%2FCD-black?style=flat-square&logo=githubactions)
![OCI](https://img.shields.io/badge/Oracle_Cloud-Always--Free-red?style=flat-square&logo=oracle)
![FFmpeg](https://img.shields.io/badge/FFmpeg-Recording-darkgreen?style=flat-square&logo=ffmpeg)

---

##  Author

**Bharath** — Junior Software Tester

*Designed and built with a focus on practical observability, zero-cost infrastructure, and production-grade reliability.*

---

> ⭐ *If this framework helped you debug a flaky test or eliminate a black-box failure, give it a star!*
