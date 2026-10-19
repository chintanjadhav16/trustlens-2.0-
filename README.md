# TrustLens 2.0 — AI-Powered Scam Detection & Digital Safety Platform

**TrustLens** is a modern, responsive cybersecurity web application engineered specifically for the Indian threat landscape. It empowers everyday citizens and families to detect suspicious messages, scam screenshots, phishing links, fraudulent payment requests, and digital impersonation attempts.

Built under an **Explainable AI** philosophy, TrustLens bridges the gap between complex cyber threat intelligence and everyday action: explaining *why* a message is dangerous, *how* the trap operates, and providing concise, prioritized next steps.

---

## 🚀 Quick Start (Running TrustLens)

TrustLens has zero external build prerequisites and is ready to run immediately:

### Option A: Direct Browser Launch (Easiest)
Simply open `standalone.html` directly in Google Chrome, Microsoft Edge, Brave, or Firefox:
```text
C:\Users\Aparna Amol\.gemini\antigravity\scratch\trustlens\standalone.html
```
*(No local web server required — all datasets, components, and logic are self-contained.)*

### Option B: Local HTTP Server (Modular Mode)
If you prefer running a local server to serve `index.html` via ES modules:
```powershell
# Using Python (if available):
python -m http.server 3000

# Using Node / npx (if available):
npx serve .
```
Then navigate to `http://localhost:3000/`.

---

## 🛡️ The Seven Core Pillars of TrustLens 2.0

### 1. Screenshot OCR & Multilingual Analysis (`#/analyze`)
- **Drag-and-Drop Upload**: Supports PNG, JPEG, and WebP screenshots of SMS, WhatsApp, and Telegram messages.
- **Side-by-Side Verification**: Displays the original screenshot alongside editable extracted text.
- **Multilingual Support**: Tailored for English, Hindi (Devanagari), Hinglish (Roman Hindi colloquialisms), Marathi, Tamil, and Telugu.
- **PII Redaction Guard**: Scrambles Indian mobile numbers (`+91 98*** ****0`), Aadhaar numbers, PAN cards, and UPI virtual addresses before storage or sharing.

### 2. Safe Link Investigation & Sandboxed Webpage Previews (`#/investigate`)
- **"Investigate Before You Click"**: Analyzes malicious or shortened links without opening them on personal devices.
- **Multi-Hop Redirect Chain**: Traces initial shortened link → cloaking/redirect hops → final destination server.
- **WHOIS & Domain Telemetry**: Surfaces domain registration age (e.g., registered 3 days ago in Seychelles), registrar, and ASN risk.
- **Lookalike Brand Detection**: Flags typo-squatting against SBI, HDFC, ICICI, Mahavitaran, India Post, Income Tax, and FedEx.
- **DOM Harvester Audit**: Scans for fraudulent password fields, credential exfiltration endpoints, and APK download links.
- **Defanged Links**: Automatically displays suspicious URLs in safe format (`hxxps[://]...`).

### 3. Personalized “What Should I Do Next?” Safety Recommendations
- **Strictly 3 Prioritized Actions**: Contextualized based on threat category (Bank/KYC, UPI PIN Reverse Trap, Utility Disconnection, Digital Arrest).
- **Indian National Helpline Integration**: Direct one-tap access to dial **1930** (Citizen Financial Cyber Fraud Helpline) and link to `cybercrime.gov.in`.
- **Reviewable Cybercrime Report Draft**: Formats an official incident report ready for copying to the National Cyber Crime Reporting Portal.
- **Never Auto-Submits**: Users retain complete editorial review and consent before copying.

### 4. Community Scam Campaign Intelligence (`#/intelligence`)
- **Threat Indicator Clustering**: Clusters reports by phone numbers, UPI handles, shortened links, and lookalike domains.
- **Active Campaign Deep-Dives**:
  - *Maharashtra Electricity Disconnection Surge* (urgent power cut at 9:30 PM demand)
  - *SBI YONO APK Phishing* (fake PAN/Aadhaar update delivering SMS-stealing RAT)
  - *YouTube Like / Telegram Task Scam* (advance fee fraud)
  - *FedEx / Digital Arrest Extortion* (fake police video interrogations)
- **7-Day Surge Timelines**: Interactive trend charts showing report spikes.
- **Regional State Breakdown**: Maps threat densities across Indian states.

### 5. WhatsApp & Telegram Warning Bot Integration (`#/` & In-App Simulator)
- **"Protection Where the Scam Happens"**: Simulates forwarding suspicious messages to TrustLens bot.
- **Interactive Simulator**: Switch between WhatsApp and Telegram interface mockups with real-time NLP analysis.
- **Production Architecture**: Documented HMAC-SHA256 signature verification (`X-Hub-Signature-256`), Token-Bucket rate limiting (10 req/min per MSISDN), and ephemeral memory handling.

### 6. Consent-Based Family Protection (`#/family`)
- **"Help Protect the People You Love"**: Care circle connecting aging parents with tech-savvy adult children.
- **Second-Opinion Review Inbox**: When an elder receives a high-risk SMS, children can send a 1-tap "DO NOT PAY" alert.
- **"Call Before Paying" Reminders**: High-contrast warning screen prompted when unverified UPI payment requests appear.
- **Senior-Friendly Mode**: High-contrast, large text, simplified buttons, and plain-language DO / DO NOT advice.

### 7. Evidence-Backed Explainable AI (`TrapMap.js` & `RedFlagCard.js`)
- **Explainable Red Flags**: Every detected flag expands to reveal:
  1. Directly observed text token
  2. Why it is suspicious (manipulation tactic)
  3. Relevant scam pattern
  4. Detection method (NLP, Regex, WHOIS)
  5. Regulatory evidence source (RBI, CERT-In, NPCI, TRAI, MERC)
  6. Independent verification instructions
- **Interactive 5-Stage Trap Map**:
  $$\text{Entry Message} \longrightarrow \text{Impersonated Entity} \longrightarrow \text{Suspicious Link/ID} \longrightarrow \text{Demanded Action} \longrightarrow \text{Target Harm}$$

---

## 🔒 Privacy & Data Protection (DPDP Act, 2023)

- **Local Storage Sandbox**: Reports and settings are stored strictly in client-side browser memory (`localStorage`).
- **User-Controlled Retention**: Choose between 30 days, 7 days, or Ephemeral Mode (zero retention).
- **Clear All Data**: 1-click erasure of stored reports and caches in `#/settings`.
- **No Fabricated Claims**: Demo data and samples are clearly marked as educational demonstrations.

---

## 📂 File Architecture

```text
trustlens/
├── index.html                 # Modular SPA entry point (Tailwind + ES Modules)
├── standalone.html            # Standalone single-file bundle (zero-dependency double-click)
├── README.md                  # System documentation & Indian cyber guidelines
└── src/
    ├── css/
    │   └── app.css            # Dark cyber theme, animations, Senior Mode styling
    ├── data/
    │   ├── presets.js         # Realistic Indian scam vectors (SBI, Mahavitaran, Tasks)
    │   ├── intelligenceData.js# Clustered threat campaigns, 7-day timelines, Indian states
    │   └── mockWhoisData.js   # Multi-hop redirects, WHOIS age, DOM input indicators
    ├── services/
    │   ├── analyzer.js        # Multilingual NLP detection & Explainable AI engine
    │   ├── urlScanner.js      # Link defanging, lookalike detection & sandbox queries
    │   ├── piiMasker.js       # Indian PII detection (Phone, Aadhaar, PAN, UPI)
    │   ├── reportGenerator.js # 1930 Cybercrime Portal incident draft builder
    │   └── storageService.js  # Local encrypted storage & privacy retention
    ├── components/
    │   ├── Navbar.js          # Responsive nav, Senior Mode switch, 1930 hotline pill
    │   ├── Footer.js          # CERT-In, Chakshu, RBI Kehta Hai links & disclosures
    │   ├── TrapMap.js         # Interactive 5-stage attack chain diagram
    │   ├── RedFlagCard.js     # Clickable, evidence-backed red flag drawer
    │   ├── NextActionCard.js  # Prioritized 3-step action protocol
    │   ├── CybercrimeModal.js # Reviewable cybercrime report draft modal
    │   ├── SandboxedPreview.js# Isolated DOM viewer & redirect chain sequence
    │   ├── BotSimulator.js    # WhatsApp/Telegram bot simulator & webhook specs
    │   └── SeniorBanner.js    # Accessible Senior Safety Mode banner
    ├── pages/
    │   ├── LandingPage.js     # Hero ("Spot the Scam"), KYC Demo, 7 Pillars
    │   ├── AnalyzePage.js     # Drag-and-drop OCR, side-by-side view, Trap Map
    │   ├── InvestigatePage.js # Safe link sandbox, WHOIS age, DOM audit
    │   ├── IntelligencePage.js# Threat campaign clustering & report scam modal
    │   ├── FamilyPage.js      # Family protection circle & second-opinion inbox
    │   ├── ReportsPage.js     # Saved incident reports & JSON export
    │   └── SettingsPage.js    # DPDP Act privacy controls & data retention
    └── app.js                 # SPA router & application bootstrap
```

---

## 🇮🇳 Official Emergency Cyber Contacts
- **National Cyber Crime Helpline**: `1930` (Toll-Free 24x7)
- **Official Reporting Portal**: [cybercrime.gov.in](https://cybercrime.gov.in)
- **Department of Telecom Chakshu Portal**: [sancharsaathi.gov.in](https://sancharsaathi.gov.in)
- **National Power Helpline**: `1912`
- **RBI Consumer Awareness**: [rbikehtahai.rbi.org.in](https://rbikehtahai.rbi.org.in)
