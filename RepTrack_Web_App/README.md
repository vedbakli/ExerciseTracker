# RepTrack — six-day intermediate workout tracker

RepTrack is an offline-first tracker for the exact six-day 45-minute Push/Pull/Legs program: Monday Push A, Tuesday Pull A, Wednesday Legs A, Thursday Push B, Friday Pull B, Saturday Legs B, Sunday rest.

## Features
- All 30 exercise slots across six training days, with sets and rep ranges preloaded
- Set-by-set weight/repetition logging (lb or kg), done toggles, auto-saved drafts
- Previous-set recall, rest timer, warm-up and cardio reminders
- Cardio mode, duration and intensity logging
- Weekly consistency, cardio totals, best-set strength charts and exercise history
- Optional body-weight measurements and trend
- JSON backup/restore and CSV export
- Fully local: no login, cloud, advertisements, analytics or network permissions

## Using RepTrack right away

**Desktop:** Extract `reptrack_web.zip`, then open `index.html` in a modern browser. Or open the standalone `RepTrack_Offline.html` provided separately. Both work without a server.

**Android browser:** Upload the contents of `reptrack_web.zip` to any HTTPS static host (such as GitHub Pages), open that URL in Android Chrome, and choose the browser's "Install app" / "Add to Home screen" command. Once installed, the PWA opens offline. HTTPS hosting is required for PWA installation; opening the HTML file from Android's Files app is for preview only and may not retain data reliably.

## Building the Android app (APK)

1. Install Android Studio with Android SDK Platform 35 and a Java 17-compatible toolchain.
2. Open the `android` directory as an Android Studio project and allow Gradle synchronization (AGP 8.7.3).
3. Select **Build > Build App Bundle(s) / APK(s) > Build APK(s)**. The project includes Gradle wrapper settings for Gradle 8.9; if Android Studio requests a Gradle executable or wrapper JAR, use your local Gradle 8.9 installation (or run `gradle wrapper --gradle-version 8.9` once).
4. Install the resulting `app-debug.apk` on your Android phone, or run directly from Android Studio with USB debugging.

The compiled `.apk` is **not** bundled because the tool environment did not have an Android SDK or access to Android build dependencies. The source project is included and needs no paid services or code changes to compile in Android Studio.

## Data and units

Logs are stored in the app's WebView / browser local storage. Use Settings > Backup JSON regularly, especially before changing phones. Import replaces existing data after confirmation. Each dumbbell entry should consistently represent the weight of **one dumbbell**; barbell entries represent the total weight including the bar. Unilateral reps are per side. The app's volume summary is a proxy and should not be interpreted as physiological work or direct tonnage.

## Technical notes

- Frontend uses plain HTML, CSS and JavaScript; no web libraries or remote assets.
- Web build includes a service worker and web app manifest; the Android app embeds the exact same files.
- The Android wrapper uses a local `file:///android_asset/` WebView and a minimal Java bridge for the native Android document pickers used in backup/restore. No INTERNET permission.
- WebView data is device-local and can be lost when app data is cleared/uninstalled. Users should export backups.
