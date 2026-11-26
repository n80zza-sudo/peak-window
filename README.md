# Peak Window native app (Capacitor)

Wraps the web app as a real iOS and Android app. Reminders are scheduled on the phone itself, so no server is needed.

## One-time setup
1. Install Node.js. For Android install Android Studio. For iOS you need a Mac with Xcode.
2. Edit `appId` in `capacitor.config.json` to your own reverse-domain id (for example `com.janedoe.streetgym`).
3. `npm install`
4. `npm run icons` (makes app icons and splash screens from the `assets` folder)
5. `npx cap add android` and/or `npx cap add ios`
6. `npm run sync`

## Run it
- Android: `npm run android`, then press Run in Android Studio with your phone plugged in.
- iOS: `npm run ios`, set your Team under Signing in Xcode, then Run on your iPhone.

## Android extras
- Android 13+ asks for notification permission when you tap "Allow notifications".
- Android 12+ may need exact alarms. If reminders arrive late, add
  `<uses-permission android:name="android.permission.SCHEDULE_EXACT_ALARM"/>` to
  `android/app/src/main/AndroidManifest.xml` and allow "Alarms and reminders" for the app in system settings.

## Publishing
- Apple Developer Program: about $99 per year. Google Play Console: one-time $25.
- Both stores want a privacy policy URL, screenshots and a content rating.

## How reminders work
The app schedules your next ~58 prompts plus window-closing alerts on the device, respecting your interval,
quiet hours, rest day and enabled drills. It reschedules whenever you change something, finish a workout or open the app.
iPhone allows 64 pending local notifications, so open the app at least once per day or two to refresh the schedule.
Decay is applied when you next open the app.

## Free automatic Android builds (GitHub Actions)
1. Put this folder in a GitHub repository (public repos get free build minutes).
2. Push to the `main` branch, or run "Build Android APK" from the Actions tab.
3. When it finishes, download `street-gym-debug-apk` from the run page, unzip it and install the APK on your phone
   (allow installs from unknown sources). Debug APKs are fine for personal use but cannot go on Google Play.
