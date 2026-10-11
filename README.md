# UPSC PYQ Tracker

Single-file web app (`index.html`) to browse ~8,700 Mains questions, filter by paper / syllabus / microtheme / keyword,
open the topper's answer at the right page, mark questions done or for review, and see an activity chart.
Progress can sync to a Google Sheet (`Code.gs`).

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
