# UPSC PYQ Tracker

Single-file web app (`index.html`) to browse ~8,700 Mains questions, filter by paper / syllabus / microtheme / keyword,
open the topper's answer at the right page, mark questions done or for review, and see an activity chart.
Progress can sync to a Google Sheet (`Code.gs`).

## Files to upload to the GitHub repo (all in the same folder)
`index.html`, `sociology.html`, `dashboard.html`, `prelims.html`, `recall.html`, `writing.html` (+ this README).
Each page is a single self-contained file; no other data files are needed.
`Code.gs` is not uploaded to GitHub; it is pasted into Google Apps Script.

## 1. Host on GitHub Pages
1. Create a **public** repo (e.g. `upsc-tracker`), upload `index.html` (+ this README), commit.
2. **Settings > Pages > Deploy from a branch > main / (root) > Save**.
3. Live at `https://<username>.github.io/upsc-tracker/` after a minute.

## 2. Set up Google Sheets sync
1. Create a new Google Sheet. Open **Extensions > Apps Script**.
2. Replace the default code with `Code.gs`. Change `TOKEN` to a long random string and save.
3. **Deploy > New deployment > type: Web app**. Execute as: **Me**. Who has access: **Anyone**. Deploy, authorise when asked.
4. Copy the **Web app URL** (ends with `/exec`).
5. In the app click **Sheets sync**, paste the URL and your token, then **Save & connect**. Repeat once on each device.

A `Progress` tab is created automatically. Each mark/unmark or microtheme change updates one row.
If you edit `Code.gs` later, use **Deploy > Manage deployments > edit > New version**.

## Notes
- The URL and token are stored only in your browser, never in the repo.
- Anyone who has both the URL and token can read or write your progress, so keep the token private.
- If you are offline, changes queue locally and are sent on the next action or page load.
- Do not edit the `id` column in the sheet; deleting a row resets that question.

## Sociology tracker (`sociology.html`)
- Upload `sociology.html` next to `index.html`; it appears at `https://<username>.github.io/upsc-tracker/sociology.html`. The two pages link to each other.
- Replace the Apps Script code with the new `Code.gs` (keep your own `TOKEN`) and **Deploy > Manage deployments > edit > New version**. The same URL keeps working.
- The sociology page writes to a separate `Sociology` tab; the GS app keeps using `Progress`. Because both pages are on the same site, connecting sync in one connects the other.
- Model answers are included in the page; they stay hidden until you press **Show answer**.

## Dashboard (`dashboard.html`)
- Upload `dashboard.html` next to the other pages. All three pages link to each other.
- Shows combined GS + Sociology progress (click a tile for the subject/theme breakdown), a Prelims placeholder, countdowns to your Prelims/Mains dates, a "questions per day needed" figure, a study-session timer, a Pomodoro timer, a daily goal bar, and heatmaps for questions done and study minutes.
- Replace `Code.gs` again (keep your `TOKEN`) and create a **New version** under Deploy > Manage deployments. It adds two tabs: `Sessions` (one row per study session) and `Settings` (exam dates, goal, pomodoro lengths).
- A running session is remembered if you close the tab; stop it manually when you finish.

## New pages
- **prelims.html**: 1,760 Prelims MCQs (2009-2025, 183 microthemes). Practice by subject / microtheme / year, mark for review, wrong answers go to the mistake notebook automatically and return on a 1-3-7-14-30 day schedule ("Due today"). Timed mocks with optional negative marking, and per-subject / per-microtheme accuracy.
- **recall.html**: active recall cards. Subject cards (name all microthemes) and microtheme cards (what was asked) for Prelims, GS Mains and Sociology, with spaced scheduling.
- **writing.html**: Mains answer-writing timer. Pick questions by set / paper / subject / marks, run a strict exam or a practice session (10 marks = 7 min, 15 = 10, 20 = 15; editable), and mark each question as attempted in exam, practised, skipped or not attempted. Shows coverage so you can see what is left.
- Re-paste `Code.gs` and create a **New version** (Deploy > Manage deployments). It adds tabs `Prelims`, `Mocks`, `Recall` and `Writing`.
