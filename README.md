# 🩺 MediAssist - Smart Health Telemetry & Automated Emergency Escalation

MediAssist is an IoT-connected telemedicine and emergency response web application. It connects to a wearable health monitoring device (`MediAssist PulseGuard Pro`) to continuously collect vitals—including **Blood Pressure (BP)**, **Blood Sugar (Glucose)**, and **Body Temperature** (plus Heart Rate and SpO2)—evaluates deviations in real time, and executes an automated multi-tier escalation protocol.

---

## 🌟 Key Features

### 1. 📡 Device Telemetry & Continuous Health Collection
- **Connected IoT Device:** Real-time pairing with `MediAssist PulseGuard Pro` via BLE 5.3 telemetry.
- **Biometric Parameters Monitored:**
  - **Blood Pressure (BP):** Systolic & Diastolic (mmHg), Pulse Pressure, Mean Arterial Pressure (MAP).
  - **Blood Sugar / Glucose:** Fasting and post-meal glucose level (mg/dL and mmol/L).
  - **Body Temperature:** Core thermal sensor in °F and °C.
  - **Cardiopulmonary:** Heart Rate (BPM) & Blood Oxygen Saturation (SpO2 %).
- **Device Simulator & Calibration:** Interactive sliders and one-click clinical presets to inject and test any physiological condition on the fly.

### 2. ⚡ Intelligent Abnormality Detection & Escalation Matrix
- **Minor Abnormality Detection:**
  - *Triggers:* Pre-hypertensive BP (130-139 / 85-89 mmHg), mild hyperglycemia (135-240 mg/dL), low-grade fever (99.5°F - 101.4°F).
  - *Automated Action:* Dispatches an in-app **minor notification alert** and pleasant audio chime with actionable medical advice (hydration, posture rest, re-check schedule) without disturbing emergency services.
- **Major Problem (Critical Emergency Escalation):**
  - *Triggers:* Hypertensive Crisis (BP ≥ 180/120 mmHg or ≤ 85/50 mmHg), Severe Hypoglycemia (Sugar ≤ 54 mg/dL) or Hyperglycemia (≥ 250 mg/dL), Hyperpyrexia (Temp ≥ 103.5°F) or Hypothermia (≤ 95.0°F).
  - *Step 1 — Urgent Automated SMS:* Dispatches an SMS alert with real-time vitals and GPS coordinates to the designated Primary Emergency Contact.
  - *Step 2 — Automated Voice Call to Person:* Rings the primary contact with an audible phone ringtone and speaks the emergency situation using Web Speech synthesis.
  - *Step 3 — Automated Ambulance Escalation ("if not, call to the ambulance"):* If the primary contact is unreachable or fails to answer within the 20-second countdown, MediAssist **automatically escalates and calls 911 / EMS Ambulance Services**, dispatches an ambulance unit (Unit #402 ALS), and transmits live biometrics to the responding paramedic crew!

### 3. 📈 Dual Tracing System
- **Real-Time ECG Telemetry Oscilloscope:**
  - High-frequency 250Hz canvas rendering P-Q-R-S-T cardiac waveform synchronized with heart rate.
  - Audible telemetry blip option, sweep speed adjustor (1x, 2x, 4x), and medical grid overlay.
- **Multi-Parameter Vital Sign Trend Tracing:**
  - Comparative historical graph tracing BP, Blood Glucose, and Body Temperature with threshold tolerance corridors.
- **Geographic Emergency Route Tracing (GPS Map):**
  - Live interactive map displaying the patient's GPS beacon, dispatched ambulance vehicle tracking along streets in real time, moving distance/ETA countdown, and trauma center route.

### 4. 👥 Emergency Contacts & Ambulance Dispatch Center
- Add, edit, and remove responders.
- Designate the **Primary Emergency Contact** (receives first automated SMS & voice call).
- Interactive **Test Call** and **Test SMS** buttons.
- Emergency Services Hotlines (911 / 112 / 108) and hospital profile configurations.

### 5. 📋 Historical Health Records Ledger
- Searchable and filterable chronological table of all device readings.
- Clinical status classification: Normal, Minor Alert, Critical Emergency.
- Audit trail of actions taken (Notification Sent, Automated Voice Call, EMS Ambulance Dispatched).
- One-click export to **CSV** and **JSON** for physician review.
- Manual entry form for offline readings.

### 6. 🤖 MediAssist AI (ChatGPT-like Health Companion)
- ChatGPT-style conversational assistant equipped with medical triage intelligence.
- **Live Vitals Context:** Can analyze current device readings instantly.
- Prompt pills for quick answers.
- **Voice Dictation (Speech-to-Text)** and **Voice Playback (Text-to-Speech)**.
- Full markdown formatting with actionable clinical disclaimers.

---

## 🚀 Running the Application

### Prerequisites
- Node.js (v18+ or v24+)
- npm

### Development Server
```bash
cd C:\Users\chill\.gemini\antigravity\scratch\mediassist
npm run dev
```
Open **`http://localhost:5173/`** in your browser.

### Production Build
```bash
npm run build
npm run preview
```

---

## 🧪 Quick Testing Guide

1. **Test Normal Condition:** Click **"All Normal"** in the bottom preset bar. Status will display green "All Vitals Optimal".
2. **Test Minor Abnormality:** Click **"Minor Abnormal (Notify)"**. Notice the amber notification chime, toast, and Notification Center badge.
3. **Test Major Emergency Escalation:**
   - Click **"Major BP Crisis"**, **"Severe Hypoglycemia"**, or **"104.2°F High Fever"**.
   - Notice the emergency siren/ringtone, automated SMS dispatch card, automated phone call to Dr. Sarah Jenkins, and the 20s countdown.
   - Click **"Unanswered • Call Ambulance Immediately"** or let the countdown expire.
   - Observe the automatic ambulance dispatch and click **"Open Live Ambulance Tracing Map"** to see real-time vehicle route tracking!
4. **Test AI Chatbot:** Navigate to the **AI Chatbot** tab or click the floating **"Ask MediAssist AI"** button. Click **"Analyze my live vitals"** to see instant telemetry clinical feedback.
