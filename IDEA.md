# CoachMe — Product Idea & Feature Summary

> Working name: **CoachMe**. Status: idea / pre-POC. This document records the concept, features, and decisions agreed so far. It is the source of truth we plan the POC from.

---

## 1. The Core Insight

People are much better at holding *others* accountable than holding *themselves* accountable.

- I can easily lecture my brother for skipping the gym, or push him for "5 more minutes" on the treadmill.
- If I were in his shoes telling *myself* that, I'd usually stop.
- If I were in his shoes and *someone else* told me, I'd actually do it.

Self-discipline is weak; **external expectation** is strong. CoachMe turns that into a product: someone else (a friend, relative, or stranger) becomes your coach and is *expecting* you to follow through.

### What CoachMe is NOT
The motivation engine is **a real person expecting you to do it** — not streaks, points, badges, or checklists. Gamification may exist as supporting UI, but it is never the core loop. The core loop is human accountability.

---

## 2. Dual Role: Everyone Is Both Coach and Coachee

- Every user can be **both** a coach (to others) and a coachee/client (of others) at the same time.
- Users *may* choose to only use one side, but the app **encourages doing both**.
- Rationale: there's a psychological effect in lecturing someone else and then feeling accountable yourself — holding others to a standard makes you hold yourself to it too.
- This is a single account with two "hats", not two account types.

---

## 3. Key Concepts / Glossary

| Term | Meaning |
|---|---|
| **User** | Anyone with an account. Can act as coach, coachee, or both. |
| **Coach** | The person holding someone accountable within a specific contract. |
| **Coachee / Client** | The person who committed to a goal within a specific contract. |
| **Contract** | The formal, signed agreement between a coachee and a coach: goal, tasks, duration, coach permissions, signatures. |
| **Task / Habit** | The concrete recurring or one-off actions the coachee promised to do under a contract (e.g., "gym 4x/week", "study 2h/day"). |
| **Check-in** | The coach checking whether a task was done; a nudge, motivation, or reprimand. |
| **Proof** | Evidence (e.g., a photo) a coach requests and then approves/rejects. |
| **Coaching style / personality** | How a coach talks to you when you're slacking. |
| **Enforcement strengths** | What a user is *good at enforcing on others* (e.g., studying, productivity) — used for matching. |

---

## 4. Features

### 4.1 Coaches: Friends, Relatives, or Strangers
- A coachee can invite a **known person** (friend/relative) as their coach.
- Or get matched with / pick a **stranger** who role-plays as their coach.
- A coach can:
  - Ping/remind the coachee to start a task ("start your workout now").
  - Send motivating, strict, or funny messages.
  - Track whether tasks were done.
  - Do periodic calls (e.g., weekly), if the contract allows it and the contract is long enough.
  - Request proof.

### 4.2 Coach Personalities / Styles
Coachees choose the type of coach they vibe with; coaches advertise their style.

**Preset archetypes** (initial list, extendable):
- **Drill Sergeant** — tough, strict, yells at you.
- **Supportive Best Friend** — warm, gentle, understanding.
- **Motivational Speaker** — hype, inspiring, big-picture.
- **Competitive Rival** — challenges you, "bet you can't".
- (more can be added later: e.g. Calm Mentor, Sarcastic Roaster…)

**Style sliders** — "How should someone talk to you when you're slacking?"
- Gentle ⟷ Brutal
- Encouraging ⟷ Challenging
- Serious ⟷ Funny

**Free-text description** — coaches can also describe their style in their own words.

Both sides use this: coachees state what they *want*, coaches state what they *offer*. Useful for matching and filtering.

### 4.3 Mini Contracts (signature feature)
The contract should feel **official and binding** — the act of signing is part of the motivation.

A contract contains:
- **Parties**: coachee and assigned coach.
- **Goal**: the expected end result (e.g., "Lose 5kg", "Finish chapter 1–6 of the course").
- **Expectations / tasks**: what the coachee must do and how often.
- **Dates**: start date, end date / duration, date signed.
- **Coach responsibilities**: e.g. daily check-in, weekly review call.
- **Coach privileges / permissions**, granted by the coachee, e.g.:
  - App notifications only
  - Text/chat messages
  - Voice/video calls
  - Request proof
  - (possibly: quiet hours, max pings per day)
- **Signatures**: both coachee and coach "sign" by squiggling a signature on screen (canvas). Simulated, not legally binding — it's about the feeling.
- **Final rendered contract**: once both sign, the app shows a nicely styled "official" contract document.

**Duration is flexible**: from **30 minutes** (a single focus session) up to **1 year**.

Contract lifecycle:
`Draft → Open (in pool) → Matched (coach accepted) → Signed by both (Active) → Verdict pending → Completed / Failed / Disputed`
plus `Cancelled` (by the coachee before signing), `Coach fired`, `Coach resigned` and `Blocked`.

**Verdict (who decides success/fail):**
- When the contract ends, **the coach proposes the verdict** (success or fail) with an optional note.
- **The coachee confirms or disputes it.**
- If the coachee doesn't respond within a set window (e.g. 72h), the coach's verdict stands.
- If they disagree, the contract is marked **Disputed**. Disputed contracts are shown separately and don't count towards either person's success rate. Both people can still leave a review.
- For very short contracts (e.g. a 30-minute focus session), the window can be much shorter.
- Note on incentives: the coach's success rate pushes them towards declaring **success** rather than unfairly declaring failure. That's why the coachee's confirmation matters, and why the coachee's review of the coach is the check on a coach who just approves everything.

### 4.4 Proof Requests
- The coach can request proof: "Send me a pic of you at the gym / on the treadmill / studying."
- The coachee uploads a photo (later possibly video, screenshot, etc.).
- The coach **approves** or **rejects** it.
- Proof results feed into contract progress and the coachee's reliability rating.

### 4.5 Matching
**Primary flow: Uber-style "open contract" pool** (no friend request, no Tinder-style mutual swipe — that extra step would mean fewer matches and fewer contracts).

1. The coachee writes the goal, tasks, duration, preferred coaching style and coach permissions. This becomes an **open contract request**.
2. The request is shown to suitable coaches: those whose **enforcement strengths** match the goal category (and preferably the style).
3. **The first coach to accept gets it** and is put forward to the coachee.
4. The coachee looks at that coach's profile and either **signs** or **refuses**. If they refuse, the request goes back to the pool.
5. Once both have signed, the contract is active.

**Match by enforcement strength (not by goal)**: users list what they're **good at enforcing on others**, which can differ from their own goals.
- Example: my goal is fitness (I'm bad at committing to exercise), but I'm good at enforcing *studying* and *productivity*. My coach profile says "good at coaching: studying, productivity".
- A fitness request is shown to people who are good at enforcing fitness.

**Secondary flows:**
- **Search & filter**: browse coaches by strengths, style, rating, success rate, language/timezone and send a contract directly to one person.
- **Invite a friend/relative**: send a contract by link or code to someone you know.

### 4.5.1 Firing & Leaving
- A coachee can **fire** their coach at any time, for example because the coach stopped responding.
- After firing, the coachee can **leave a review** ("stopped responding" etc.) and can **put the same contract back in the pool** to get a new coach.
- (Suggested) A coach can also **resign** from a contract, which affects their record less than being fired but is still visible.

### 4.5.2 Communication & Safety
**All contact happens inside the app by default.** The app never shows anyone's phone number.

Communication channels, each one a **permission the coachee grants per contract**:
| Channel | Notes |
|---|---|
| **Predefined buttons** | Safest tier. The coach can only send preset prompts such as "Do it now!", "Nudge 👊", "How's it going?", "Proof please 📸". Good for coachees who don't want to give a stranger free-text access. |
| **Push notifications** | The coach can trigger a notification (a preset or custom text). |
| **Free-text messages** | Normal chat. |
| **Voice notes** | Recorded audio messages. |
| **Photos** | Proof photos and photos in chat. |
| **In-app calls** | Undecided; later phase. |

- Users may share outside contact details (a phone number, socials) **at their own discretion**. The app shows a warning/disclaimer when they do and is not responsible for it.
- **Disclaimers** cover harsh coaching styles (the coachee asked for them), interaction with strangers, and contact outside the app.
- **Report**: either party can report the other. The report saves the **most recent messages, voice notes and photos** as evidence for moderation.
- **Block**: either party can block the other. Blocking ends the contract and stops all contact.
- We accept that edge cases will happen. Permissions + report + block are the safety net, not perfect prevention.

### 4.6 Ratings & Reputation (two-sided)
**Coach reputation:**
- Average rating (out of 5) from clients.
- Written reviews.
- Number of contracts coached.
- Number of *successful* contracts (client completed the goal).
- Success rate.

**Coachee/client reputation:**
- Rating from coaches (did they show up, honest, responsive).
- Contracts taken / completed / success rate.
- Proof approval rate (possible).

Rating happens at the end of a contract (both sides rate each other).

---

## 5. Monetization Ideas (later — not in POC)
Both ideas exist mainly to **deepen the feeling of commitment**, and secondarily as revenue.

**Option A — Stake / deposit**
- Coachee puts money into the contract (e.g., $10).
- Completed → get it back. Failed → lose it to the studio.
- Known weakness: can't truly be enforced, people can lie about completion. Still has psychological value. Proof + coach approval partially mitigates.

**Option B — Fixed small fee per contract**
- Signing a contract costs a small fixed amount (e.g., $1).
- Paying makes it feel real; also justifies the impact on coaches' ratings.
- Possibly only for contracts above a minimum length (e.g., ≥ 1 month).

Decision: **deferred**. Not part of the POC, but the data model should not make it hard to add later (e.g., contracts can later have a `stake_amount` / `fee` / payment status).

---

## 6. Decisions So Far

| # | Decision |
|---|---|
| D1 | Core motivation = a person expecting you to follow through. No streaks/points as the core loop. |
| D2 | One account type; every user can be coach and coachee simultaneously. Doing both is encouraged, not forced. |
| D3 | Coaches can be friends/relatives (invite) or strangers (match/search). |
| D4 | Coach personality = presets + sliders (gentle–brutal, encouraging–challenging, serious–funny) + free text. |
| D5 | Contracts are formal: goal, tasks, dates, coach responsibilities & permissions, simulated hand-drawn signatures from both parties, and a rendered "official" view. |
| D6 | Contract duration ranges from 30 minutes to 1 year. |
| D7 | Coachee controls coach permissions (notifications / text / calls / proof requests). |
| D8 | Coaches can request photo proof; they approve or reject it. |
| D9 | Matching supports both manual search/filter and matching by enforcement strengths (not by goals). |
| D10 | Two-sided ratings: coach (stars, reviews, contracts, success rate) and coachee. |
| D11 | Monetization (stake or per-contract fee) is deferred until after the POC. |
| D12 | Verdict: the coach proposes success/fail, the coachee confirms or disputes it. Silence means the coach's verdict stands. A disputed contract doesn't count towards either person's success rate. |
| D13 | The coachee can fire the coach at any time, review them, and put the contract back in the pool. |
| D14 | Matching is Uber-style: the coachee posts an open contract, coaches with matching enforcement strengths see it, and the first to accept gets it. The coachee then signs or refuses. No mutual swipe. |
| D15 | Search/filter and inviting a friend are secondary ways to assign a coach. |
| D16 | All contact is in the app. Each channel (predefined buttons, notifications, text, voice notes, photos, later calls) is a permission the coachee grants. |
| D17 | Phone numbers are never shown by the app. Users can share outside contact at their own discretion, with a warning. |
| D18 | Report (saves recent messages/media as evidence) + block are available to both sides. Disclaimers cover strangers, harsh styles and outside contact. |
| D19 | Stack: **Flutter** (mobile) + **Supabase** (Postgres, auth, storage, realtime, edge functions). |
| D20 | A coachee can have several coaches at once (one per contract). Coaches have a cap on active clients (value to be tuned). |
| D21 | An open contract stays in the pool for **1 week** before it expires. |
| D22 | Proof photos are **deleted by default when the contract ends**, unless the coachee chooses at the end to keep/download them. Later idea: a "progress & proofs" recap view. |
| D23 | Approach: stop theorizing and build step by step. Remaining open questions get answered by trying things in the app. |

---

## 7. Open Questions (to resolve during POC planning)

**Product**
- Can a coachee have several coaches at once (one per contract)? Should coaches have a cap on active clients?
- How long does an open contract stay in the pool before expiring? What happens if nobody accepts?
- How do short contracts (30-minute focus session) differ in flow from long ones (calls, weekly reviews)?
- Privacy of proof photos (only the coach can see them? deleted after the contract ends?).
- Rate limits on nudges/notifications so a "brutal" coach can't spam (quiet hours, max per day).

**POC scope**
- In-app calls: left out of the POC (likely).
- Push notifications in the POC (needed for nudges), via FCM.
- Final list of must-have POC features (section 8).

---

## 8. Candidate POC Feature Set (draft — to be finalized together)

**Likely in:**
- Auth + profile (both coach and coachee sides on one profile)
- Coach style: presets + sliders + free text; enforcement strengths
- Contract creation → open pool → a coach accepts → the coachee signs or refuses
- Signature canvas (both parties) → rendered official contract
- Tasks within a contract + the coachee marks them done
- Coach dashboard: my clients, today's tasks, check-in
- Permission-gated communication: predefined buttons, notifications, text chat, photos (voice notes possibly)
- Proof request → photo upload → approve/reject
- Verdict flow (the coach proposes, the coachee confirms/disputes) → two-sided rating & review
- Fire coach, report (with saved evidence), block
- Basic reputation stats on the profile

**Likely out (later):**
- Payments / stakes / fees
- In-app voice/video calls
- Search/filter and friend invite (possibly in, if time allows)
- Advanced moderation tooling (admin dashboard can just be the Supabase table editor at first)
