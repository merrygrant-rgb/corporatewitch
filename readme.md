# Corporate Witch — Website Repository

**Welcome, bestie.** This is the repo for [corporatewitch.media](https://corporatewitch.media). Everything you need to deploy, update, and maintain the site is in here. Written assuming you've never touched Git or Netlify before. No gatekeeping.

> ✦ If you get stuck anywhere, the specific error message + Googling `site:stackoverflow.com [error]` will get you unstuck 90% of the time. For the other 10%, email me.

---

## 📁 What's In This Repo?

```
corporatewitch/
├── index.html                  ← Your landing page (corporatewitch.media)
├── ritual/
│   └── index.html              ← The AI Readiness Ritual funnel
├── grimoire/
│   └── index.html              ← The Starter Grimoire (interactive web version)
├── spell-bank/
│   └── index.html              ← Your PRIVATE 30-hook content library (hidden from Google)
├── assets/
│   └── pdf/
│       └── starter-grimoire.pdf ← The lead magnet PDF emailed to subscribers
├── _redirects                  ← Netlify URL rules (clean URLs like /ritual)
├── netlify.toml                ← Netlify config (security, caching)
└── README.md                   ← This file
```

**Important architecture note:** Each HTML file is **completely self-contained** — all CSS and JavaScript lives inside the file. This means:
- ✓ You can open any HTML file by double-clicking it (no server required)
- ✓ Editing one page never breaks another page
- ✗ If you change brand colors, you edit them in each file separately (the price of independence)

---

## 🎯 The Big Picture — How Everything Connects

```
  Someone clicks a TikTok link
          ↓
  Lands on corporatewitch.media (index.html)
          ↓
  Clicks "Take The Ritual"
          ↓
  Answers 8 questions (ritual/index.html)
          ↓
  Sees personalized results + Quick Win plan (step 3 is BLURRED)
          ↓
  Enters email to unlock step 3
          ↓
  beehiiv receives the email → sends welcome email with PDF
          ↓
  Visitor gets the Grimoire PDF + joins your newsletter list
          ↓
  Every Sunday: they get your weekly "spell"
```

Three tools do the work:
1. **Netlify** hosts the site (free)
2. **beehiiv** handles emails + the newsletter (free up to 2,500 subscribers)
3. **Git/GitHub** stores your code + gives you one-click updates

---

## 🚀 FIRST-TIME SETUP (do this once)

### Step 1 — Install the tools

**Git** (a tool that tracks changes to your files):
- Mac: Open Terminal, type `git --version`. If you see a version number, you're done. If not, it will prompt you to install.
- Windows: Download from [git-scm.com/download/win](https://git-scm.com/download/win). Install with default options.

**A code editor** — optional but helpful:
- Free + easy: [VS Code](https://code.visualstudio.com/)
- You can also edit files in any text editor (even Notepad)

### Step 2 — Create a GitHub account

Go to [github.com](https://github.com) and sign up. Free. Choose a username you won't be embarrassed by.

### Step 3 — Create your repo (on GitHub)

1. Click the **+** icon in the top-right of GitHub → **New repository**
2. Name it: `corporatewitch`
3. Description: "Corporate Witch — AI fluency for mid-career professionals"
4. Set it to **Private** (so randoms can't see your Spell Bank hooks)
5. **Don't** check any of the "initialize with README" boxes — leave it empty
6. Click **Create repository**

### Step 4 — Upload this folder to GitHub

Open Terminal (Mac) or PowerShell/Git Bash (Windows). Navigate to wherever you saved this folder:

```bash
cd path/to/corporatewitch
```

Then run these commands one at a time:

```bash
# 1. Initialize Git in this folder
git init

# 2. Add all the files
git add .

# 3. Save the first snapshot
git commit -m "Initial commit — Corporate Witch launch"

# 4. Rename the default branch to 'main'
git branch -M main

# 5. Connect to your GitHub repo
# REPLACE "YOURUSERNAME" with your actual GitHub username!
git remote add origin https://github.com/YOURUSERNAME/corporatewitch.git

# 6. Upload everything to GitHub
git push -u origin main
```

On step 6, GitHub may ask for a "password." **Don't type your GitHub password** — GitHub doesn't accept those anymore. Instead:

1. GitHub → click profile pic → **Settings**
2. Scroll way down → **Developer settings** → **Personal access tokens** → **Tokens (classic)**
3. Click **Generate new token (classic)**
4. Name it: "My laptop"
5. Expiration: 90 days
6. Scopes: check `repo` (the whole section)
7. Click **Generate token** and **copy the token immediately** (it won't show again)
8. When Git asks for a password, paste the token

Refresh your GitHub repo page — you'll see all your files.

### Step 5 — Connect to Netlify

1. Go to [netlify.com](https://netlify.com) → **Sign up** (use "Sign up with GitHub" for easy mode)
2. Click **Add new site** → **Import an existing project**
3. Click **GitHub** as the Git provider
4. Authorize Netlify
5. Select your `corporatewitch` repo
6. Leave the build settings as-is:
   - Build command: *(leave empty)*
   - Publish directory: `.`
7. Click **Deploy**

Netlify will publish in ~60 seconds. You'll get a random URL like `glowing-witch-a7b2f.netlify.app`. Your site is LIVE.

### Step 6 — Add your real domain

1. In Netlify, click your site → **Domain settings** → **Add a domain**
2. Enter: `corporatewitch.media`
3. Follow the instructions based on your registrar:

**Option A — Let Netlify manage DNS (easiest)**
- Netlify gives you 4 nameservers (like `dns1.p04.nsone.net`)
- Log into your domain registrar
- Find the "nameservers" setting for corporatewitch.media
- Replace the existing nameservers with Netlify's 4
- Save. Wait 10 min to 24 hours for DNS propagation
- ✓ Done. Netlify handles everything including SSL.

**Option B — Keep DNS at your registrar**
- In your registrar's DNS settings, add:
  - **A record**: Name `@` (or blank) → Value `75.2.60.5`
  - **CNAME record**: Name `www` → Value `<your-site>.netlify.app`
- Wait 10 min to 24 hours
- Back in Netlify, click **Verify DNS configuration**

Either way, Netlify auto-creates a free SSL certificate within minutes.

---

## 📧 CONFIGURE BEEHIIV (the email engine)

Right now, emails submitted through your site go nowhere — the code is in "simulate mode" (you'll see a fake success but no real email capture). Let's wire it up.

### Step 1 — Create your beehiiv account

1. [beehiiv.com](https://beehiiv.com) → **Sign up free**
2. Create your publication:
   - Name: `The Coven`
   - URL: `corporate-witch` (becomes `corporate-witch.beehiiv.com`)
   - Category: "Marketing"

### Step 2 — Find your Publication ID and Embed URL

1. In beehiiv → **Settings** → **Publication Settings**
2. Copy your "Publication ID" (looks like `pub_xxxxxxxxxx`)
3. Go to **Grow** → **Subscribe Forms**
4. Click **Create Form** → choose **Embed**
5. Give it a name like "Site forms"
6. beehiiv gives you HTML code. Find the `action="https://..."` URL inside the `<form>` tag. Looks like: `https://embeds.beehiiv.com/xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx`
7. Copy that URL

### Step 3 — Paste them into your HTML files

**Because each page is self-contained, you need to update THREE files.** In each file, find this block near the bottom (search for `CW_CONFIG`):

```js
window.CW_CONFIG = {
  BEEHIIV_PUB_ID: 'REPLACE_WITH_PUB_ID',
  BEEHIIV_FORM_URL: 'REPLACE_WITH_EMBED_URL'
};
```

Replace the two placeholders with your real values, in these three files:

1. `index.html` (landing page)
2. `ritual/index.html`
3. `grimoire/index.html`

(The Spell Bank is private and has no email capture, so no update needed there.)

**Pro tip:** Use VS Code's Find & Replace (Cmd/Ctrl+Shift+F) to find `REPLACE_WITH_PUB_ID` across all files at once.

### Step 4 — Upload the PDF to beehiiv

1. In beehiiv → **Content** (top) → **Assets** (or **Files**)
2. Upload `assets/pdf/starter-grimoire.pdf`
3. Copy the public URL beehiiv gives you — you'll use it in the welcome email

### Step 5 — Set up the Welcome Email (delivers the Grimoire)

1. beehiiv → **Automations** (left menu) → **Welcome Email**
   - Free plan gets one welcome email, which is exactly what we need
2. Subject: `✦ Your Starter Grimoire, as promised`
3. Body (adapt the tone):

   > Hey bestie,
   >
   > Welcome to The Coven. You just made the single fastest move a corporate professional can make in 2026 — you started learning the tools instead of waiting for someone to teach them to you.
   >
   > As promised — your **Starter Grimoire**: [Download PDF](URL_FROM_STEP_4)
   >
   > Print it. Stick it to your second monitor. Screenshot the Safety Card to your phone. Don't let it live in your downloads folder with the other PDFs you forgot about.
   >
   > **What happens next:**
   > - Every Sunday: one real AI workflow you can use Monday morning
   > - Nothing else — no pitches, no webinars, no "bundles"
   > - Reply to any email to talk to me directly. I read every one.
   >
   > Now go cast something.
   >
   > — Merry

4. Activate.

### Step 6 — Push the update to your site

Back in Terminal (from inside your `corporatewitch` folder):

```bash
git add .
git commit -m "Configure beehiiv integration"
git push
```

Netlify auto-detects the push and rebuilds your site within 60 seconds. **That's it — emails now flow to beehiiv.**

---

## ✏️ MAKING UPDATES (everyday workflow)

```bash
# 1. Edit whatever file you want (in VS Code or any editor)

# 2. In Terminal, from the corporatewitch folder:
git add .
git commit -m "Brief description of what you changed"
git push

# 3. Netlify auto-deploys. Visit your site in 60 seconds to see changes.
```

### Common edits:

**Change the hero headline:**
- Open `index.html`
- Find `<h1 class="hero-title">`
- Change the text
- Save → push

**Change brand colors:**
- Since each file is self-contained, colors are defined in each file's `:root` CSS block at the top
- Use VS Code Find & Replace across all files to change `#e91e8c` (magenta bright) to whatever new color

**Add a new Spell Bank hook:**
- Open `spell-bank/index.html`
- Find the `const hooks = [` array in the `<script>` section
- Copy an existing hook object, paste, modify
- Save → push

---

## 🔧 TROUBLESHOOTING

**"My site isn't updating after push"**
- Check Netlify dashboard → **Deploys**. If "Failed," click to see the error.
- Usually a typo in `netlify.toml` or `_redirects`.

**"The Ritual's AI analysis isn't working"**
- The ritual calls Claude's API directly from the browser. This works in development but hits CORS errors in production.
- **Solution:** Add a Netlify Function as a proxy. This is a Phase 2 task (~1 hour). For now the ritual scoring + Quick Win plan works perfectly; only the AI-generated "Witch's Reading" block needs the proxy.

**"Emails aren't showing up in beehiiv"**
- Did you update all 3 files? (index.html, ritual/index.html, grimoire/index.html)
- Open your live site, open browser DevTools (F12) → **Console**. Submit a test email. Look for `[CW]` logs — they'll tell you exactly what happened.
- If you see `simulating success`, the config isn't saved/pushed yet in that file.

**"My domain isn't working"**
- DNS can take up to 24 hours. Be patient.
- Check propagation at [dnschecker.org](https://dnschecker.org).

**"I broke something and want to go back"**
```bash
git log --oneline          # shows your history
git revert HEAD            # undoes the last commit safely
git push
```

**"The pages won't open on my laptop by double-clicking"**
- They should! That's the whole point of self-contained files.
- If they don't, it's a file association issue — right-click the file → Open With → Chrome/Firefox/Safari.

---

## 📊 ONGOING MAINTENANCE

**Weekly (10 min):**
- Check beehiiv → **Audience** → new subscribers + where they came from (UTMs)
- Write the Sunday spell in beehiiv's editor → Send

**Monthly (1 hour):**
- Batch-film TikToks using the Spell Bank (open `spell-bank/index.html` locally)
- Review Netlify analytics (built-in basic view, or add Plausible/Fathom for more)
- Check if PDF needs updating

**Quarterly:**
- Update the PDF with new tools/formulas and re-upload to beehiiv
- Review which stage is converting best on the Ritual → refine copy

---

## 💸 COST SUMMARY

| Service | Cost | When to upgrade |
|---|---|---|
| GitHub (private repo) | Free | Never for your needs |
| Netlify (site hosting) | Free | At ~400GB/mo bandwidth |
| beehiiv (email) | Free until 2,500 subs | When you hit 2k → Scale ($39/mo) |
| Domain | ~$30-60/year | Already paid |
| Anthropic API (Ritual analysis) | Pay-per-use | ~$0.01 per ritual. 1000/month → ~$10/mo |

**Total to launch: $0 + your domain renewal.**

---

## ✦ One Last Thing

You don't need to understand every line of code in here. You need to understand the **flow** — what points to what, where emails go, where edits happen. Bookmark this README. Everything else becomes muscle memory after the third push.

Now go cast something.

— Built with the Witch for the Witch
