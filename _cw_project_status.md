# CORPORATE WITCH — PROJECT STATUS & BRAIN DUMP
*Last updated: April 20, 2026*
*Save this file. Read this first at the start of every session.*

---

## THE BIG IDEA (don't lose this)

Corporate Witch is NOT a TikTok AI channel.
It is a **consulting pipeline with a content engine on top.**

Merry is the Corporate Witch — a mid-career professional who used AI to beat 
the #1 salesperson on her team by $100K, in a non-tech role, as the only person 
on the team using AI. That is the hook. That is what nobody else can say.

**Target audience:** Mid-to-late career corporate professionals who feel left 
behind by AI. Directors, Managers, VPs, Business Owners. People who've tried 
AI, got garbage, and quietly gave up.

**The differentiator:** She's not 22. She didn't grow up digital. She chose it. 
And she has measurable proof it works.

---

## THE FUNNEL (how it's supposed to work)

```
TikTok / LinkedIn content
        ↓
corporatewitch.media (landing page)
        ↓
The AI Readiness Ritual (intake form disguised as a quiz)
        ↓
Score + Stage generated (0-32, 5 witchy stages)
        ↓
Merry gets AUTO-NOTIFIED with their full profile
(Stage, score, role, industry, blocker, priority, context)
        ↓
They book a call via Calendly
        ↓
Merry shows up already knowing their level — zero prep time
        ↓
beehiiv nurtures non-bookers with weekly "spells" (The Coven newsletter)
```

---

## WHAT'S BUILT (all files in this folder)

| File | Status | Notes |
|------|--------|-------|
| `index.html` | ✅ Complete | Landing page. Beautiful. Ready. |
| `ritual/index.html` | ✅ Complete | 8-question quiz, 5-stage scoring, AI analysis via Claude API, email capture with blurred step 3 |
| `grimoire/index.html` | ✅ Complete | Interactive web version of the cheat sheet |
| `spell-bank/index.html` | ✅ Complete | Private 30-hook TikTok content library. Open locally, don't push to public. |
| `assets/pdf/starter-grimoire.pdf` | ✅ Complete | Lead magnet PDF for welcome email |
| `netlify.toml` | ✅ Complete | Security headers, caching config |
| `_redirects` | ✅ Complete | Netlify clean URLs |
| `README.md` | ✅ Complete | Full beginner-friendly deployment guide |

**Total cost to run: $0 + domain renewal**

---

## THE 5 WITCHY STAGES (Ritual scoring)

| Score | Stage | Icon | Color | Consultation Type |
|-------|-------|------|-------|-------------------|
| 0–5 | The Sleeping Company | 💤 | Red | AI Emergency Session |
| 6–11 | Awareness Without Action | 👁️ | Orange | AI Wake-Up Call |
| 12–19 | The Dabbling Stage | 🧪 | Gold | AI Strategy Intensive |
| 20–27 | Emerging Fluency | ⚡ | Green | AI Scale & Systematize |
| 28–32 | AI-Fluent Culture | ✦ | Magenta | AI Competitive Edge |

The score tells Merry: how much hand-holding they need, what consultation 
to offer, and how to open the first call.

---

## WHAT'S NOT DONE YET (priority order)

### 🔴 BLOCKING LAUNCH

**1. GitHub + Netlify setup**
Site is not live yet. Follow README.md step by step.
~20 minutes. Everything is already written out.

**2. beehiiv configuration**
Email capture is in "simulate mode" — no real emails being captured.
Need: Publication ID + Embed Form URL from beehiiv.com
Update 3 files: `index.html`, `ritual/index.html`, `grimoire/index.html`
Search for `REPLACE_WITH_PUB_ID` across all three.

**3. Calendly booking link**
Replace the `mailto:corporatewitchadmin@gmail.com` CTA in `ritual/index.html` 
results section with a real Calendly link.
Add 3-4 intake questions to Calendly that mirror the Ritual 
(for people who skip the quiz and go straight to booking).

### 🟠 HIGH PRIORITY (do after launch)

**4. Auto-notification to Merry when Ritual is completed**
Right now Merry only gets notified if the person clicks "Book" and sends 
the email manually. Most won't.
Solution: Add Netlify Forms to the ritual so every completion 
auto-emails Merry with the full profile — stage, score, role, industry, 
blocker, priority, context. ~20 min to implement.

**5. Real LinkedIn + Instagram URLs in index.html**
Both social buttons currently point to generic linkedin.com / instagram.com.
Find in `index.html` and replace with actual profile URLs.
TikTok: @corporatewitch05 ✅ already correct.

**6. LinkedIn content strategy**
LinkedIn = where the BUYERS are (Directors, VPs, Business Owners).
TikTok = where the AUDIENCE is.
Different tone, different content cadence, same core story.
LinkedIn posts should drive to the Ritual as a "free assessment."

### 🟡 PHASE 2 (after first paying client)

**7. Netlify Function proxy for Claude API**
The Ritual's "Witch's Reading" AI analysis calls Claude directly from 
the browser — hits CORS errors in production. README documents this.
Workaround: fallback static analysis already built in. Works fine for now.

**8. Shareable score card**
A screenshot-worthy result card people would share on TikTok/LinkedIn.
"I'm a Stage 2 Dabbling Apprentice 🧪 — what's your witch level?"
Drives viral referral traffic back to the Ritual.

---

## CONTENT STRATEGY — TIKTOK LAUNCH

**The hook that works:**
"I'm the one in the office using AI while everyone else is still in a 
meeting ABOUT AI."

**Merry's proof point (use this in launch video):**
Beat the #1 salesperson on the team by $100K in February 2026. 
Only rep using AI. On a team that cherry-picks leads against her.
This is not a claim — it's a documented result.

**Content pillars:**
- "Today's Spell" — one AI trick, 60 seconds, show the actual screen
- "Corporate Autopsy" — why your company is behind (emotional hook)
- "The Witch at Work" — real day-in-the-life, no names, just results
- "Spell vs. Search" — side by side: how most people use AI vs. how she does
- "What your IT department isn't telling you" — this one will blow up

**Batch filming guide:** Open `spell-bank/index.html` locally (double-click). 
30 pre-written hooks ready to film. Do a monthly batch session.

---

## KEY ACCOUNTS & CONTACTS

| What | Detail |
|------|--------|
| TikTok | @corporatewitch05 |
| Domain | corporatewitch.media |
| Email | corporatewitchadmin@gmail.com |
| beehiiv pub name | The Coven |
| Parent LLC | Rebel Herd Media |

---

## MERRY'S CONSULTING POSITIONING

She is not selling AI tools. She is selling **what she already did.**

The pitch:
"I took a job that was already working and used AI to make my numbers 
measurably better — in a role where nobody else was doing it, against 
people with better leads and more tenure. I'm going to show you how 
to do the same thing in your job."

She is the proof of concept. That's the whole brand.

---

*Next session: read this file first, then pick up from the BLOCKING LAUNCH section.*
*To resume: ask Claude to read _CW_PROJECT_STATUS.md from the Corporate Witch folder.*
