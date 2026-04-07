# Forged — Deployment Guide

## Deploy to Vercel (Free, ~10 minutes)

### Step 1 — Install Node.js
If you don't have it: https://nodejs.org (download the LTS version)

### Step 2 — Set up the project locally
```bash
cd forged-deploy
npm install
npm run dev
```
Open http://localhost:5173 — the game should run locally.

### Step 3 — Push to GitHub
1. Go to https://github.com and create a new repository called `forged`
2. Run these commands in the `forged-deploy` folder:
```bash
git init
git add .
git commit -m "Initial deploy"
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/forged.git
git push -u origin main
```

### Step 4 — Deploy on Vercel
1. Go to https://vercel.com and sign up (free)
2. Click **"Add New Project"**
3. Import your `forged` GitHub repository
4. Vercel auto-detects Vite — click **Deploy**
5. Done! You get a URL like `forged-abc123.vercel.app`

### Step 5 — Enable AI Coach (optional)
The Morning Check-In AI coach needs an Anthropic API key.
1. Get a key at https://console.anthropic.com
2. In Vercel: go to your project → **Settings → Environment Variables**
3. Add: `VITE_ANTHROPIC_KEY` = your key
4. Redeploy

### Step 6 — Set up Supabase (for accounts + cloud saves)
Run the schema in your Supabase SQL Editor:
```sql
-- (paste contents of supabase_schema.sql)
```
The Supabase URL and anon key are already baked into the app.

---

## Making Updates
After editing `src/ForgedApp.jsx`:
```bash
git add .
git commit -m "Update"
git push
```
Vercel auto-deploys on every push.

## Custom Domain (optional)
In Vercel: Settings → Domains → Add your domain.
