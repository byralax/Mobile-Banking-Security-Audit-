# Mobile-Banking-Security-Audit-
Mobile application security assessment identifying critical authentication flaws  OWASP Mobile Frida Burp Suite Android Studio
# 📱 Mobile Banking Security Audit

A mobile application security assessment targeting a simulated banking app, revealing critical authentication flaws and insecure data handling. This project leverages **dynamic analysis**, **instrumentation**, and **OWASP MASVS** best practices.

## 🧠 Objective

To evaluate the security of a mobile banking application through reverse engineering, traffic interception, and runtime manipulation. Focus was placed on authentication mechanisms, data storage, and communication security.

## 🛠️ Tools & Technologies

| Tool            | Purpose                                 |
|-----------------|------------------------------------------|
| **OWASP MASVS** | Security testing framework & checklist   |
| **Frida**       | Dynamic instrumentation & hook injection |
| **Burp Suite**  | SSL pinning bypass, traffic interception |
| **Android Studio** | APK decompilation and debugging      |

## 🧪 Methodology

Follows **OWASP Mobile Application Security Verification Standard (MASVS)**:

1. **Static Analysis**
   - Decompile APK using jadx
   - Review code for hardcoded secrets, insecure logic

2. **Dynamic Analysis**
   - Intercept and manipulate API traffic via Burp Suite
   - Bypass SSL pinning using Frida hooks

3. **Runtime Instrumentation**
   - Hook login functions to reveal credentials & tokens
   - Monitor cryptographic operations and auth flows

4. **Authentication Testing**
   - Brute-force and logic bypass attempts
   - Token tampering and replay attack simulation

## 💥 Key Findings

| Vulnerability                     | Impact                                |
|----------------------------------|----------------------------------------|
| **Hardcoded API Keys**           | Allowed attacker to access backend API |
| **Insecure Token Storage**       | Tokens stored in plain SharedPrefs     |
| **Bypassable SSL Pinning**       | Enabled full traffic interception      |
| **Weak Authentication Flow**     | Allowed login bypass via token reuse   |
| **Lack of Root Detection**       | No mitigation against rooted devices   |

## 🔬 Exploitation Examples

### 🔸 SSL Pinning Bypass (Frida)
```javascript
Java.perform(function () {
  var CertPinning = Java.use("okhttp3.CertificatePinner");
  CertPinning.check.overload("java.lang.String", "java.util.List").implementation = function () {
    console.log("[+] SSL pinning bypassed");
    return;
  };
});
⚠️ This audit was conducted in a controlled environment with a test application. All findings are disclosed responsibly and for educational purposes only.
