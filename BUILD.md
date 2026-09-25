# Building your Plug Android app (.apk)

This folder is a small Android app project (using Capacitor) that wraps your
smart plug dashboard into a real installable app. You don't need Android
Studio — GitHub will build the actual .apk file for you, for free.

## 1. Create a new GitHub repository
Same as before: go to github.com → "+" → New repository. Name it e.g.
`plug-app`. Keep it Public.

## 2. Upload this whole folder
Upload everything in this `android-project` folder to that repo, keeping the
folder structure exactly as-is:
- `package.json`
- `capacitor.config.json`
- `www/` (with index.html, manifest.json, sw.js, icons/ inside it)
- `.github/workflows/build-apk.yml`

GitHub's drag-and-drop upload page preserves folder structure, including the
hidden `.github` folder — if it doesn't show up after upload, use "Add file"
→ "Create new file" and type the path `.github/workflows/build-apk.yml`
directly, pasting in the contents.

## 3. Let GitHub Actions build it
1. In your new repo, click the **Actions** tab.
2. You should see a workflow called "Build APK". If it hasn't run
   automatically, click into it and click **"Run workflow"**.
3. Wait 3–5 minutes while it builds (you can watch the progress live).

## 4. Download your APK
1. Once the run finishes with a green checkmark, click into that run.
2. Scroll down to **Artifacts** and click **plug-app-debug-apk** to download
   a zip containing your `app-debug.apk`.
3. Unzip it, transfer `app-debug.apk` to your Android phone (via USB, email
   to yourself, Google Drive, whatever's easiest).

## 5. Install it on your phone
1. Open the APK file on your phone. Android will warn about installing from
   an unknown source (normal for anything not from the Play Store) — allow it
   for this file.
2. It installs as a real app called "Plug", with the icon you saw earlier.
3. Open it — same password-protected dashboard as the webpage, just as a
   proper standalone app now.

## Notes
- This is a **debug build**, meaning it's unsigned/not optimized for
  distribution — perfectly fine for installing on your own phone, but if you
  ever want to share it with others or publish it, it would need to be signed
  as a "release" build. Let me know if you want that set up later.
- Any time you update the dashboard's code, just re-upload the changed files
  to this repo (or the `www` folder specifically) and re-run the workflow to
  get a fresh APK.
