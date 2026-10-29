# DayFlow — Personal Planner & Habit Tracker

A local-first, installable PWA starter for managing time-based tasks, recurring habits, monthly tracking, rescheduling reasons, focus sessions, and weekly insights.

## Important hosting limitation

This version is designed for **GitHub Pages only**. GitHub Pages hosts static files; it does not run a Python/FastAPI server or PostgreSQL database. To honor the GitHub-only hosting requirement, this edition runs in the browser and stores data in that browser's local storage.

That means:
- No account or backend server is required.
- Data stays in the current browser/device.
- Data does **not** automatically sync between your phone and laptop.
- Use **Settings → Download full backup (JSON)** regularly.
- Browser notifications are permission-based and schedule checks run while DayFlow is open. Browser/OS behaviour may delay or suppress background notifications.
- A native Android home-screen widget is not supported by a regular PWA. The website can be installed as an app; native widgets would require a separate Android implementation.
- Voice entry depends on browser speech-recognition support and may use the browser's speech service.

## Included

- Responsive dashboard and mobile bottom navigation
- Quick task capture
- Scheduled tasks, categories, priorities, repeat rules, edit/complete
- Rescheduling with reason and notes, with original schedule recorded in history
- Monthly habit grid with completed/missed/partial/excused statuses and notes
- Daily habit checklist
- Calendar/day schedule and tomorrow planner
- Focus timer with 15/25/45/60-minute presets
- Dark mode
- Voice task entry when supported by the browser
- Weekly insights and monthly habit statistics
- JSON backup/restore and CSV export
- PWA manifest, service worker, offline app shell cache

## Run locally

The easiest way to test the app is with Python installed:

```bash
python -m http.server 8000
```

Run that command from the `dayflow` folder, then open `http://localhost:8000`.

You can also use VS Code's Live Server extension. Opening `index.html` directly as a `file://` URL may prevent service-worker/PWA features from working.

## Publish with GitHub Pages

1. Create a new GitHub repository, for example `dayflow`.
2. Upload the **contents** of this folder to the repository root (`index.html`, `app.js`, `styles.css`, etc.).
3. In GitHub, open **Settings → Pages**.
4. Under Build and deployment, choose **Deploy from a branch**.
5. Choose branch `main` and folder `/ (root)`, then save.
6. Wait for the Pages deployment to finish and open the published URL.
7. On Android, open the URL in Chrome and use the browser menu → **Install app** or **Add to Home screen** (wording varies).

If you use a repository project path such as `https://username.github.io/dayflow/`, all app asset links are relative so they should work from that path.

## Data safety

The app does not send task data to a server. Browser local storage can be cleared by browser settings, private browsing, or device cleanup. Export backups before changing devices or clearing browser data. Importing a backup replaces current local data after confirmation.

## Development notes / current limitations

This is a functional front-end prototype, not a production multi-user full-stack service. For a real backend, the project would need an API server, database, authentication, migrations, secure deployment, and a push/local notification strategy. Those cannot be hosted on GitHub Pages alone.

The recurrence and reminder implementation is intentionally lightweight for a first release. Verify recurring task edge cases and notification delivery on the target browser before relying on it for critical reminders.
