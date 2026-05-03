# Zero-Cost-Automation-Observability
A high-performance, hybrid CI/CD automation framework designed to solve the "Black Box" problem in headless browser testing. This project utilizes Oracle Cloud Infrastructure (OCI) and GitHub Actions to provide real-time visual monitoring and automated failure replays at zero infrastructure cost.
**The Innovation: "Headed" Observability in a "Headless" World**
Standard CI/CD runners often execute tests in a "Black Box," making it nearly impossible to debug UI-specific failures or flaky tests. This framework overcomes that by:
**Virtual X11 Redirection:** Mapping headless execution to a virtual display buffer.

**Live VNC Streaming:** Allowing developers to "dial in" to the cloud runner to watch tests execute in real-time.

**Rolling FFmpeg Replays:** Maintaining a constant background video buffer that only saves and uploads a clip when a test failure is detected.

**Technical Architecture**
The Zero-Cost-Automation-Observability lab is built on a high-performance, cloud-native stack designed for maximum efficiency without overhead costs:

**Cloud Infrastructure:** Utilizes an Oracle Cloud Infrastructure (OCI) "Always-Free" ARM compute instance with 24GB of RAM.

**Secure Orchestration:** Powered by a self-hosted GitHub Actions runner that executes tests within a private, hardened environment.

**Modern Tech Stack:** Built using Java 21 and Maven, ensuring compatibility with the latest enterprise features and performance optimizations.

**Automation Engine:** Leverages Selenium 4.x to handle complex interactions, including JavaScript execution, explicit waits, and alert management.

**Virtual Display Management:** Employs Xvfb to create a virtual X11 display buffer, allowing "headed" browser execution in a cloud environment.

**Observability Logic:** Integrates an FFmpeg rolling background buffer that constantly records the execution stream in a 10-second window.

**Automated Artifact Generation:** Dynamically clips and uploads the recorded buffer as a .mp4 file only when a TestNG failure is detected, providing 100% visibility into errors.



**Observability Proof (Execution Results)**
The strength of this framework is proven in the GitHub Actions Dashboard, where the infrastructure and observability logic are validated during every run.

**1. CI/CD Pipeline Orchestration**
**Self-Hosted Execution:** Tests bypass public GitHub runners and execute directly on the hardened OCI instance.

**Environment Initialization:** Automated setup of the X11 display server and VNC monitoring during the "Initialize Environment" step.

**2. Automated Artifact Generation**
When a test fails, the framework automatically extracts a 10-second failure replay. This is visible in the Artifacts section of the Action run, ensuring that no bug remains a mystery.

**Note:** Core implementation files (BaseTest.java) and OCI environment configurations are kept private to protect infrastructure security and proprietary logic.

**Advanced Features Demonstrated**
**JavaScript Executor Integration:** Handling complex UI interactions and element highlighting.

**Synchronization Strategies:** Implementation of Explicit and Fluent Waits to eliminate test flakiness.

**Dynamic Alert Handling:** Robust management of browser-level modal windows and JavaScript alerts.

Created and maintained by Bharath, software Tester.
