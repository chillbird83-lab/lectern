# Lectern

Record your lectures on your phone, bookmark the moments that matter, take notes, and find everything again by course, week or search. Recordings stay on your phone and it works offline.

- **Recorder** – one big button; pause/resume; live waveform and timer. The screen stays on while recording (Wake Lock) and **Dim** turns it black to save battery. Audio is written to storage every 5 seconds, so if the app is closed, the browser crashes or the phone restarts, the recording is **recovered** on the next launch. A warning appears if the input is very quiet.
- **Bookmarks** – tap ⭐ Important, 🎯 Exam, ❓ Question or 📌 Note (with a label) while recording or listening; they show as ticks on the player and jump straight there (starting 3 s early).
- **Notes** – type notes during the lecture or afterwards; ⏱ inserts the current time as `[12:34]`, and every timestamp in your notes becomes a jump button.
- **Organiser** – courses with colour, emoji, lecturer, room and weekly times. Lectern uses the timetable to pre-select the class you are in and titles recordings "Lecture 1, 2, 3…". *Today* shows the class happening now, *Continue listening* and a *To review* list; *Week* shows your timetable with ✓ for every class you recorded; *Library* has full-text search across titles, notes and bookmark labels plus *To review* / *Starred* filters. Archive courses at the end of a semester.
- **Player** – keeps playing while you browse the app or lock the phone (lock-screen controls), remembers where you stopped, 0.75×–2× speed, ±15/30 s.
- **Your files** – share a recording to Drive/WhatsApp/e-mail, save it to Downloads, copy notes, remove audio but keep notes to free space, and download a **full backup** (.zip of all recordings + `lectern.json`) that you can restore on a new phone.
- Three quality levels: Saver (≈7 MB/h), Standard (≈14 MB/h, default), High (≈29 MB/h) — Opus audio, clear for speech.

### Put it on your Android phone

1. Open **https://chillbird83-lab.github.io/lectern/** in **Chrome**.
2. Chrome menu (⋮) → **Install app** / **Add to Home screen**. Lectern opens full screen like a normal app, works offline, and Chrome protects its storage from automatic clean-up.
3. The first time you record, allow the microphone.

Tips: keep Lectern open while recording (use **Dim** instead of locking the phone — browsers may pause the microphone for apps in the background), put the phone face up near the speaker, and make a backup from *Settings* now and then: recordings live only on the phone, and clearing Chrome's site data deletes them.

| Path | Purpose |
| --- | --- |
| `js/logic.js` | Pure logic — timetable matching, search, titles, formatting, validation — fully unit-tested |
| `js/recorder.js` | Microphone recording, crash-safe chunk saving, bookmarks, wake lock, level meter |
| `js/store.js`, `js/db.js` | State, IndexedDB storage (audio as Blobs), crash recovery, backup/restore |
| `js/player.js` | Shared audio player, resume position, lock-screen controls |
| `js/zip.js` | Minimal ZIP writer/reader for backups (unit-tested) |
| `js/views.js`, `js/sheets.js`, `js/app.js` | Screens, forms, navigation (Android back button) |

## Run it locally

```bash
npm start        # http://localhost:8080
npm test         # unit tests (Node's built-in test runner)
```

There is no build step: it is plain HTML, CSS and ES modules, with no dependencies. Recording needs HTTPS (or `localhost`).

## Deploy

`.github/workflows/pages.yml` runs the tests and publishes the site to GitHub Pages on every push to `main`. One-time setup: **Settings → Pages → Build and deployment → Source: GitHub Actions**.

`scripts/make-icons.mjs` regenerates the PNG icons from the SVGs (needs `playwright`; development only).
