# 🛡️ Sentinoid (Sentinel Edge)
## The Hardware-Bound, Air-Gapped Mobile Security Fortress

---

## 📜 1. The Sentinoid Manifesto

In an age of AI-driven swarm attacks and silent telemetry, we believe that if code can touch the internet, it can be compromised. **Sentinoid** is an uncompromising security framework designed for absolute isolation. By operating on a Strict Zero-Internet Policy, Sentinoid anchors your data directly to your device's physical silicon. We bind encryption to hardware-locked biometrics, ensuring your data exists only when you are physically present. No Cloud. No Backdoors. No Compromise.

---

## 🚀 2. Core Security Pillars

### 🔐 Biometric-Bound Cryptographic Shroud
- **Encrypted Wrapping:** Sensitive app data (Banking, Gallery, Notes) is encased in an AES-256-GCM shroud.
- **TEE Binding:** Decryption keys are generated within the Trusted Execution Environment (TEE) and are physically "unsealed" only via a successful biometric match.
- **Hardware Lockout:** No PINs or passwords. Access is physically tied to your unique biometric signature. No Biometric = No Key = No Data.

### 🔌 Connectivity Shield (Absolute Air-Gap)
- **Hardened Manifest:** The Sentinoid binary contains zero network permissions. It is architecturally incapable of communicating with any server.
- **Handshake Hardening:** Actively monitors and terminates unauthorized background Bluetooth, NFC, or Wi-Fi Direct requests to prevent side-channel exfiltration.

### 🛑 Feature Permission Manager (FPM)
- **Service-Level Interception:** Utilizes Android Accessibility and Device Admin layers to intercept hardware calls to the Mic, Camera, and GPS.
- **Mock-Stream Injection:** Instead of simply blocking requests (which alerts malware), FPM feeds unauthorized apps Null Data or Static Noise, neutralizing background spying while maintaining OS stability.

---

## ⚡ 3. Advanced Tactical Defense

### 🍯 The Honeypot Trap
- **Deception Strategy:** Generates realistic "Ghost Data" (fake logs and decoy files) to act as bait.
- **Silent Alarm:** Any unauthorized interaction with these files triggers a Total Lockdown, freezing the encryption layer and logging the intrusion locally.

### 🐕 Hardware Watchdog & Anti-Tamper
- **Integrity Monitoring:** Real-time checks for Rooting, Bootloader unlocking, and USB Debugging.
- **Self-Destruct Protocol:** Utilizing the InvalidatedByBiometricEnrollment flag, Sentinoid immediately purges all local keys if a new biometric (fingerprint/face) is added to system settings, preventing "forced entry" via secondary registration.

### 👾 Local Heuristic Malware Engine
- **Behavioral Analysis:** Detects overlay attacks and screen scraping using a local TFLite model and a compressed Hash-Registry.
- **Battery Optimized:** High-performance asynchronous monitoring with <1% battery impact on 2026-gen chipsets.

---

## 🛠️ 4. Technical Specifications

| Component | Technology | Detail |
|-----------|-----------|--------|
| **Encryption** | AES-256-GCM / RSA-4096 | Hardware-backed, non-exportable. |
| **Connectivity** | Air-Gapped | Zero INTERNET permissions in manifest. |
| **Recovery** | BIP39 Mnemonic | 24-word offline recovery seed. |
| **Key Storage** | Android Keystore / StrongBox | Isolated from main OS memory. |
| **Interception** | Accessibility Framework | Service-level hardware call masking. |

---

## ⚖️ 5. License & Verification

Sentinoid is released under the **GNU General Public License v3.0 (GPL-3.0)**.

To verify our "No Backdoor" promise, auditors can inspect:
- **AndroidManifest.xml:** Confirm the absence of `android.permission.INTERNET`.
- **SecurityModule.cpp:** Audit the hardware-bound key derivation logic.
- **BIP39Provider.kt:** Verify the offline recovery seed generation.

---

## 🚀 6. Getting Started

### Prerequisites
- Android 12+ device with biometric hardware
- Device Administrator and Accessibility Service permissions
- ~50MB storage for framework

### Installation
1. Clone the repository
2. Build using provided Makefile: `make build-android`
3. Install the APK on your device
4. Grant required permissions during first launch
5. Register your "Golden Biometric" signature

### Quick Setup
- Launch Sentinoid and follow the onboarding wizard
- Select apps you want to protect
- Set recovery seed (write it down, store securely offline)
- Test biometric unlock flow

---

## 📁 Project Structure

```
Sentinoid/
├── src/
│   ├── SecurityModule.cpp       # Biometric key derivation
│   ├── WatchdogService.java     # Anti-tamper monitoring
│   ├── FPM.java                 # Feature Permission Manager
│   └── HoneypotEngine.java       # Ghost data generation
├── res/
│   └── layout/                  # UI components
├── AndroidManifest.xml          # Zero-permission hardened manifest
├── Makefile                     # Build configuration
└── README.md
```

---

## 🔧 1-Month Development Roadmap

**Week 1:** Core biometric binding + AES encryption wrapper
**Week 2:** Accessibility framework integration + FPM mock-streaming
**Week 3:** Watchdog service + anti-tamper logic
**Week 4:** UI polish + testing + documentation

---

**Sentinoid: Secure by Design. Isolated by Choice.**