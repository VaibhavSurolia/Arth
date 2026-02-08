# Story-Driven Financial Game (Design Doc)

## Vision
Create a story-driven financial game where players live through a virtual life and learn money concepts only when the story demands them. The game emphasizes situational learning (decision → outcome → explanation) rather than lectures, using historical market events to teach behavior and long-term thinking.

## Core Experience
- **Narrative-first gameplay**: The player lives through a life story, making choices that impact their finances.
- **Just-in-time learning**: Concepts appear only when needed.
- **Visual explanations**: Graphs, comparisons, and outcomes teach more than definitions.

## Learning Loop
1. **Situation**: Story moment presents a financial decision.
2. **Decision**: Player makes a choice.
3. **Outcome**: Portfolio changes are shown visually.
4. **Explanation**: Mentor provides a short lesson.

## Game Flow (High-Level)
1. Start with a new graduate receiving their first salary.
2. Introduce saving vs investing.
3. Introduce SIP through a personal goal.
4. Introduce mutual funds through guidance.
5. Simulate market events (crashes, recoveries, bull runs).
6. Teach diversification and compounding.
7. Conclude with a long-term wealth snapshot.

## Story Arc: “Zero to Investor”
**Main Character**: Aarav (22, first job, no finance knowledge)

**Mentor**: Friendly senior/AI guide who explains concepts simply.

### Chapter Outline
1. **First Salary**
   - Salary arrives: ₹30,000
   - Choices: spend, save, ask about investing
   - Lesson: saving vs investing, inflation
2. **Bike Goal (SIP Introduction)**
   - Goal: buy a bike in 3 years
   - Choices: save monthly vs invest monthly
   - Lesson: SIP + compounding basics
3. **First Investment (Mutual Funds)**
   - Choices: one stock vs mutual fund
   - Lesson: risk vs stability
4. **2016 Demonetization (Event)**
   - Choices: panic sell vs hold
   - Lesson: policy impact, long-term mindset
5. **Diversification**
   - Sector drop triggers mini-game
   - Lesson: asset allocation
6. **2018 Market Correction (Event)**
   - Lesson: short-term volatility
7. **Compounding Time Skip**
   - 5-year jump comparison
   - Lesson: time + compounding
8. **2020 COVID Crash (Major Event)**
   - Choices: sell, hold, invest more
   - Lesson: recovery + behavior
9. **2021 Bull Run (Event)**
   - Lesson: greed vs discipline
10. **2022 Inflation & Rates (Event)**
    - Lesson: inflation, interest rates
11. **Futures & Options (Advanced)**
    - Simple hedge analogy
    - Lesson: risk protection
12. **Life Events Simulation**
    - Emergencies, job loss, marriage
    - Lesson: liquidity + planning
13. **Final Wealth Snapshot (15 Years)**
    - Net worth summary
    - Lesson recap + free-play unlock

## Core Data Models
### Character
```json
{
  "name": "Aman",
  "age": 22,
  "profession": "Graduate",
  "salary": 30000,
  "savings": 5000,
  "portfolio": [],
  "risk_level": "low"
}
```

### Portfolio Item
```json
{
  "asset_name": "Index Fund",
  "type": "mutual_fund",
  "invested_amount": 10000,
  "current_value": 10500,
  "risk_level": "medium"
}
```

### Story Scene
```json
{
  "id": "scene_01",
  "dialogue": "You got your first salary of ₹30,000.",
  "choices": [
    "Save in bank",
    "Invest in SIP",
    "Spend all"
  ],
  "outcomes": {
    "Save in bank": "Savings increase",
    "Invest in SIP": "SIP explained + portfolio updated",
    "Spend all": "No savings, lesson on opportunity cost"
  },
  "next_scene": "scene_02"
}
```

## Portfolio Growth Logic (Backend)
- **Simple growth**: `current_value = invested_amount × (1 + return_rate)`
- **SIP formula** (internal): `future_value = P × [((1+r)^n -1)/r]`

## Historical Event Model
```json
{
  "name": "COVID Crash",
  "effect": -0.35,
  "duration_turns": 3,
  "recovery_turns": 5
}
```

## UI Screens (Minimum)
- **Story Screen**: character avatar, dialogue box, choice buttons
- **Portfolio Screen**: pie chart + growth graph
- **Simulation Screen**: market up/down animation
- **Progress Screen**: badges, levels, XP

## Gamification
- **XP**: +50 per lesson, +100 per market event survival
- **Levels**: Beginner → Investor → Pro Investor
- **Badges**: SIP Starter, Diversification Master, Market Survivor

## MVP Scope (First Demo)
- 1 story arc
- 3 scenes
- 1 portfolio
- 1 chart
- 1 market crash event

## Suggested Tech Stack
### Frontend
- React Native / Flutter (mobile-first)
- If web: React + Tailwind

### Backend
- Node.js or Firebase

### Database
- Firebase Firestore or MongoDB

### Charts & Animations
- Chart.js or Recharts
- Lottie / Spline

## Core Loop (State Updates)
1. User logs in
2. Load character
3. Load current scene
4. User makes decision
5. Update portfolio
6. Show result & mentor lesson
7. Move to next scene

---

This document is the baseline design for the story-driven financial game. It can be used to scope MVP features, define data models, and guide UI/UX flows.
