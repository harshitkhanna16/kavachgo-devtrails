# KavachGo

> **Guidewire DEVTrails 2026 | Phase 1 — Seed Submission**
> Persona: Grocery / Q-Commerce Delivery (Zepto / Blinkit)

---

## Inspiration

*Kavach* (कवच) means armor in Hindi. Every Q-commerce delivery partner racing to fulfill Zepto's 10-minute and Blinkit's 15-minute promises deserves that armor.

India has millions of dark-store delivery partners whose entire livelihood depends on uninterrupted access to a single 3 km zone. When a flash flood hits, when AQI crosses 400, when a local bandh shuts the roads — they lose ₹300–600 in a single afternoon. No insurance. No safety net. No recourse.

**KavachGo** wraps every delivery partner in a digital armor — a fully automated, AI-powered parametric income insurance platform that detects disruptions via real-time APIs and sends a UPI payout within minutes. No forms. No waiting. Just protection, as fast as their deliveries.

---

## Persona & Scenario

### Target Persona: Q-Commerce Delivery Partner (Zepto / Blinkit)

| Attribute | Detail |
|---|---|
| **Name** | Suresh, 24, Bengaluru |
| **Platform** | Blinkit (full-time) |
| **Working Pattern** | 8–10 hrs/day, 6 days/week, shift-based |
| **Avg. Weekly Earnings** | ₹4,500 – ₹7,000 |
| **Delivery Radius** | 2–4 km from assigned dark store |
| **Risk Profile** | Extreme weather sensitivity due to hyperlocal, time-critical nature of Q-commerce |
| **Tech Literacy** | Android smartphone, UPI-native, Kannada/Hindi preferred |

### Why Q-Commerce Workers Are Uniquely Vulnerable

- **Dark store dependency**: Workers are tethered to a specific warehouse. If the zone around that store floods or goes under curfew, there is no alternative zone to shift to.
- **Volume-based earnings**: Q-commerce pay is per-delivery. A 3-hour disruption at peak hours (6–9 PM) can wipe out 30–40% of a day's earnings.
- **Hyperlocal exposure**: A storm may only affect a 3 km radius — but if that radius contains the worker's dark store, they are fully grounded.

### Persona-Based Scenarios

| Scenario | Trigger | Income Impact |
|---|---|---|
| Monsoon Flash Flood | Rainfall > 40mm/hr, roads waterlogged near dark store | Full shift lost (4–5 hrs) |
| Severe Air Pollution | AQI > 300 — Zepto/Blinkit suspends outdoor ops | 3–6 hrs lost |
| Extreme Heat Advisory | Temp > 44°C for 3+ hrs, platform reduces active slots | 2–4 hrs lost |
| Local Bandh / Curfew | Road blockage score > 80% in delivery zone | Entire shift inaccessible |
| Dark Store Zone Closure | Civic authority closes the micro-zone around dark store | All deliveries halted |

### Application Workflow

```
[Worker Onboarding]
        ↓
[Dark Store Zone Assignment + AI Risk Profiling]
        ↓
[KavachGo Calculates Weekly Premium → Worker Selects Plan]
        ↓
[Policy Activated for the Week]
        ↓
[24x7 Parametric Trigger Monitoring]
        ↓
[Disruption Detected → Auto Claim Initiated]
        ↓
[Fraud Validation Engine]
        ↓
[Instant UPI Payout → Worker Notified]
        ↓
[Dashboard Updated → Policy Auto-Renewed Sunday]
```

---

## Weekly Premium Model

KavachGo is structured entirely on a **weekly pricing basis**, matching the typical weekly payout cycle of Q-commerce platforms.

### Premium Tiers

| Plan | Weekly Premium | Max Weekly Payout | Best For |
|---|---|---|---|
| **Kavach Basic** | ₹25/week | ₹400 | Part-time / new workers |
| **Kavach Plus** | ₹45/week | ₹900 | Full-time, stable zone |
| **Kavach Max** | ₹75/week | ₹1,800 | Full-time, high-risk zone |

> Workers can upgrade or downgrade their plan each Sunday. Mid-week changes are not permitted to prevent adverse selection.

### AI-Driven Dynamic Premium Formula

The weekly premium is recalculated **every Sunday night** by our ML pricing engine:

```
Final Weekly Premium =
    Base Plan Rate
    × Dark Store Zone Risk Index     (0.75x – 1.50x)
    × 7-Day Weather Forecast Score   (0.90x – 1.35x)
    × Worker Claim History Factor    (0.80x – 1.25x)
    × Platform Activity Multiplier   (0.85x – 1.10x)
```

**Worked Example — Suresh in Bengaluru:**
- Base Plan: Kavach Plus (₹45)
- Zone: Koramangala dark store (moderate flood risk) → 1.15x
- IMD Forecast: Moderate rain alert for 3 days → 1.20x
- Claim History: 1 claim in past 60 days (clean) → 0.95x
- Platform Activity: High (top 20% delivery volume) → 0.90x
- **Calculated Premium: ₹45 × 1.15 × 1.20 × 0.95 × 0.90 ≈ ₹53/week**

Workers receive a Sunday evening notification showing next week's premium before auto-renewal.

---

## Parametric Triggers

All triggers are based on **objective, third-party verifiable data only**. Workers never need to file a manual claim.

| Trigger ID | Event | Data Source | Threshold | Payout Rate |
|---|---|---|---|---|
| T-01 | Heavy Rainfall / Flash Flood | OpenWeatherMap API | > 40mm/hr sustained 1.5 hrs | ₹90/hr lost |
| T-02 | Severe Air Pollution | CPCB AQI Open API | AQI > 300 (Severe Category) | ₹70/hr lost |
| T-03 | Extreme Heat | IMD / OpenWeatherMap | > 44°C for 3+ consecutive hrs | ₹70/hr lost |
| T-04 | Civic Disruption / Bandh | Google Maps Traffic API | Zone traffic score drop > 75% | ₹90/hr lost |
| T-05 | Dark Store Zone Closure | Zepto/Blinkit API (mock) | Active delivery slots = 0 in zone | ₹100/hr lost |

**Payout Calculation:**
```
Payout = Verified Lost Hours × Payout Rate per Trigger
         (capped at worker's plan Max Weekly Payout)
```

Working hours are defined as **9 AM – 9 PM only**. Disruptions outside this window do not generate payouts.

---

## AI/ML Integration Plan

### 1. Dynamic Weekly Premium Engine
- **Algorithm**: XGBoost Regressor
- **Input Features**: Dark store GPS + historical weather for that zone, IMD 7-day forecast, worker claim frequency (past 90 days), avg. weekly delivery volume, seasonal risk index
- **Output**: Weekly premium multiplier (0.75x – 1.5x) applied to base plan rate
- **Training Data**: Synthetic dataset of 60,000 Q-commerce worker profiles + 3 years of OpenWeatherMap historical data for 20 Indian cities

### 2. Intelligent Fraud Detection Engine
- **Model**: Isolation Forest (unsupervised anomaly detection)
- **Fraud Signals**:
  - Worker GPS not within 5 km of claimed dark store zone during disruption window
  - Delivery activity detected on platform during claimed disruption
  - Same device filing claims across multiple worker accounts
  - Trigger event confirmed by only 1 source (requires ≥ 2 independent APIs)
  - Claim pattern matches known fraud archetypes (e.g., claims always on Friday evening)
- **Output**: Fraud Risk Score (0–100). Score > 65 → auto-hold + manual review. Score > 85 → auto-reject + flag account.
- **Rule-Based Hard Layer**: Max 4 claims/week, 48-hr cooldown per trigger type

### 3. Predictive Risk Heatmap
- Every Monday, KavachGo generates a 7-day risk heatmap per dark store zone
- High-risk zones get push notifications nudging workers to upgrade their plan
- Helps the insurer pre-position payout reserves ahead of monsoon weeks

---

## Tech Stack

### Platform: Progressive Web App (PWA)

**Justification**: Q-commerce workers are entirely smartphone-based. A PWA delivers a native app experience — offline capability, push notifications, Hindi/Kannada support — without requiring Play Store installation. Critical for low-friction onboarding.

| Layer | Technology |
|---|---|
| Frontend | React.js + Next.js + Tailwind CSS (PWA) |
| Backend | Node.js + Express.js |
| Database | PostgreSQL + Redis |
| ML Service | Python + FastAPI (XGBoost + Isolation Forest) |
| Weather Data | OpenWeatherMap API (free tier) |
| AQI Data | CPCB Open Data API (free) |
| Traffic Data | Google Maps Platform (mock/free tier) |
| Payments | Razorpay Test Mode (UPI simulation) |
| Auth | Firebase Phone OTP |
| Notifications | Firebase Cloud Messaging |
| Hosting | Vercel (frontend) + Railway (backend + ML) |
| Version Control | GitHub |

---

## Development Roadmap

### Phase 1 (March 4–20) — Ideation & Foundation
- [x] Problem research & Q-commerce persona definition
- [x] Weekly premium model design
- [x] Parametric trigger identification & threshold calibration
- [x] Fraud detection strategy
- [x] Tech stack selection
- [x] README / Idea Document
- [ ] 2-minute strategy video

### Phase 2 (March 21 – April 4) — Automation & Protection
- [ ] Worker onboarding (OTP login, dark store zone, risk profile)
- [ ] Weekly plan selection + Razorpay test payment
- [ ] ML premium engine v1 (XGBoost, synthetic data)
- [ ] 5 parametric trigger monitors (OpenWeatherMap, CPCB, Traffic mock)
- [ ] Auto claim initiation pipeline
- [ ] Basic fraud rule layer
- [ ] Claims management dashboard

### Phase 3 (April 5–17) — Scale & Optimise
- [ ] Isolation Forest fraud detection (ML-based)
- [ ] Instant UPI mock payout flow (Razorpay sandbox)
- [ ] Worker dashboard: earnings protected, active coverage, claim history
- [ ] Insurer/admin dashboard: loss ratios, zone risk heatmap, predictive analytics
- [ ] Final pitch deck (PDF)
- [ ] 5-minute walkthrough demo video

---

## Out of Scope — Critical Constraints

Per problem statement rules, KavachGo **strictly excludes**:
- Health or medical coverage
- Life insurance
- Accident or injury coverage
- Vehicle damage or repair payouts
- Any manual, self-reported claim process

**KavachGo covers ONLY verifiable income lost due to external parametric disruptions.**

---

## What Makes KavachGo Different

1. **Dark Store Zone Intelligence**: Risk is mapped at the individual dark store level — the Koramangala Blinkit warehouse and the Whitefield warehouse face completely different monsoon risks. KavachGo treats them differently.

2. **Sunday Forecast Nudge**: Every Sunday evening, workers get a push notification: *"Heavy rain forecast near your dark store this week. Upgrade to Kavach Max for ₹75?"* — driving proactive coverage adoption.

3. **Shift-Based Payout Logic**: KavachGo understands shift schedules and pays out only for disrupted active-shift hours — precise and fraud-resistant.

4. **Earnings Protection Scorecard**: A lifetime metric showing each worker: *"KavachGo has protected ₹3,240 of your earnings so far."* — building loyalty and trust.

5. **Cross-Platform Policy**: One KavachGo policy covers a worker whether they're delivering for Zepto or Blinkit that week.

---

## Team

| Name | Role |
|---|---|
| Harshit Khanna | Full Stack + ML Lead |
| Swapnil Saini | Backend Development |
| Divyanshu Sharma | Frontend + UI/UX |

---
*KavachGo — Digital Armor for India's Q-Commerce Warriors.*
*Guidewire DEVTrails 2026 | In Partnership with EY*
