# Peak Gains (Android app project)

Workout reminders with Strength, Stamina and Focus windows. Reminders are scheduled on the phone itself, so no server is needed.

## Option A: build the APK with GitHub (nothing to install)
1. Create a free GitHub account and a new **public** repository.
2. Upload everything inside this folder (not the folder itself) with "uploading an existing file".
   Files you should see in the repository root: `www`, `assets`, `package.json`, `capacitor.config.json`, `privacy.html`, `README.md`, `.gitignore`.
3. Hidden folders are often skipped by uploads. If the repository has no `.github` folder, click **Add file > Create new file**,
   type `.github/workflows/android.yml` as the name, and paste in the contents of that file from this project. Commit it.
4. Open the **Actions** tab and run **Build Android APK** (it also starts by itself after a commit to `main`).
5. When it turns green, open the run and download the artifact named **peak-window-debug-apk**. Unzip it to get `app-debug.apk`.
6. Copy the APK to your phone, open it, and allow installs from that source.
7. Open the app and tap **Allow notifications** in Settings. Android 13+ will ask for permission.

## Option B: build on your own computer
1. Install Node.js and Android Studio.
2. `npm install`
3. `npm run icons`
4. `npx cap add android`
5. `npm run sync`
6. `npm run android`, then press Run with your phone plugged in.

## Notes
- Android 12+ may need exact alarms. The GitHub workflow adds the permission for you. If reminders arrive late,
  allow "Alarms & reminders" for the app in system settings and turn off battery optimisation for it.
- The app schedules about 58 reminders ahead. Open it every day or two to refresh the schedule.
- Debug APKs are for personal testing and cannot be uploaded to Google Play.
- Before publishing, change `appId` in `capacitor.config.json`, host `privacy.html` and add your contact email to it.

## If the build says it cannot find ./www
The workflow now builds the `www` folder itself. Make sure `index.html`, `manifest.json` and `icon.svg` (the files from the `www` folder)
sit at the top level of the repository next to `package.json`. Icons are optional: without the `assets` folder the app just uses a default icon.
