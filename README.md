# Chem Lab Sketchbook

A gamified chemistry app: 15 missions across 3 worlds (Kitchen Chemistry, Titanic
Engine Room, Pixel Power Lab), each walking through a 6-step Lab Ticket
(Notice → Guess → Watch → Sketch → Explain → Label). Includes a drawing canvas,
XP/badges, a "Cookbook" revision view, and CSV export for Anki.

Single static file, no build step, no backend. Progress is saved in the
browser's `localStorage` under the key `chem-lab-v1`, so it's private to
whichever device/browser it's opened on.

## Deploy to Vercel

**Option A — Vercel CLI** (fastest if you've done this before):
```bash
cd chem-lab-sketchbook
npx vercel --prod
```
Follow the prompts (link to your Vercel account, accept defaults). It'll give
you a live URL like `chem-lab-sketchbook.vercel.app` when done.

**Option B — Vercel dashboard, no CLI:**
1. Go to vercel.com → **Add New... → Project**
2. Choose **"Deploy without Git"** / drag-and-drop, and drop this whole folder
   (`index.html` + `vercel.json`) onto the upload area
3. Vercel auto-detects it as a static site — click **Deploy**
4. You'll get a `.vercel.app` URL; rename the project in Settings if you want
   a nicer subdomain (e.g. `jjchemlabsketchbook.vercel.app`)

**Option C — GitHub import** (best if you want future edits to auto-deploy):
1. Push this folder to a new GitHub repo
2. In Vercel: **Add New... → Project → Import Git Repository**
3. Select the repo, leave build settings blank (no framework, no build
   command needed), click **Deploy**

## After deploying

Once you have the live URL, send it back and I'll help you add a matching
card to the `jjsketchbookcollection.vercel.app` collection page, styled the
same way as Science Quest / Astro Sketchbook / Thematic Sketchbook.

## Notes for future edits

- Everything lives in `index.html` — missions data, styling, and app logic
  are all in that one file, same pattern as the other apps in this project.
- To add a new mission: add an entry to the `MISSIONS` array (copy an
  existing one as a template) with a unique `id` and the right `zone`.
- To add a new zone/world: add an entry to `ZONES`, tag its missions with a
  matching `zone` value, and (optionally) add a badge in `BADGES` and a
  `--zone-accent` color in the CSS.
- XP, progress bars, and the "Full Steam Ahead" badge are all computed from
  `MISSIONS.length` dynamically — no totals to update by hand when you add
  content.
