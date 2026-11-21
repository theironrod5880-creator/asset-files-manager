# Mastercore Video — starter

A new repo to start from: a home page, a video screen that plays, storage
access, a JSON catalog, and an assets folder. Nothing else yet — this is
the floor to build on.

## Files

| File | What it is |
| --- | --- |
| `index.html` | Home page. Lists the videos from `videos.json`, plus a "Choose videos from this phone" button (storage access). |
| `video.html` | The video screen. Big player, plays on open, sound button, and its own "Choose a different video" picker. |
| `videos.json` | The catalog. One entry per video: title, file, note. |
| `assets/` | Video files live here. `sample.mp4` is a 5-second test pattern — delete it when your own videos are in place. |
| `termux-setup.md` | The Termux steps: install, clone, preview, push. |

## How storage access works here

A web page cannot ask Android for storage permission the way an app does.
Access comes from the file picker: when you tap "Choose videos from this
phone", your phone asks which files to share, and only those files are
shared. Nothing is uploaded anywhere — picked videos play on your device,
and only their titles and sizes are remembered. If you close the tab, pick
the videos again and they relink by name and size.

## Add a video

1. Put the file in `assets/` (for example `assets/my-clip.mp4`).
2. Add one line to `videos.json`:
   `{"title": "My Clip", "file": "assets/my-clip.mp4", "note": ""}`
3. Push. It shows up on the home page.

## Put it on GitHub (new repo)

1. On github.com, New repository. Name it whatever you like —
   `Mastercore-Video-Studio` is a good fit. Public or private, your call.
2. Upload these files (drag them all in at once), or push from Termux —
   see `termux-setup.md`.
3. Settings → Pages → Source: **Deploy from a branch** → Branch: **main**,
   Folder: **/(root)** → Save.
4. Your live address will be
   `https://<your-github-name>.github.io/<repo-name>/`

## Preview on your phone first

Do not open `index.html` straight from the file — the catalog
(`videos.json`) will not load that way. Use a tiny server instead:

```sh
cd <repo-folder>
python3 -m http.server 8000
```

Then open `http://localhost:8000` in Chrome. Same on Termux, same on a
computer. Full steps in `termux-setup.md`.

## What's next (not in this starter)

- Google Drive sync for the catalog (the Video Studio app already has
  this — it can be added once the starter is live).
- An Android wrapper (APK) with real storage permissions in the manifest.
  On the web, the file picker is the permission.
