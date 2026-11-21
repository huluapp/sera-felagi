# Sera Felagi — Android-ready upgrade

This project preserves the original Amharic job search and Telegram announcement flow, and adds:
- A refreshed, responsive mobile interface and dark-mode support.
- Saved jobs stored locally on the device.
- Refresh, clear-search, saved-jobs view, and loading/empty/error states.
- Last successful search cache for a matching query when offline.
- Safer handling of announcement links.

## Build an Android APK with GitHub Actions
1. Upload the contents of this folder to the root of `huluapp/sera-felagi` on the `main` branch (replace the old `index.html`; add the other files and workflow).
2. Open the repository's **Actions** tab.
3. Select **Build Android APK** and run the workflow, or push a commit to `main`.
4. When it finishes, open the workflow run and scroll to **Artifacts**. Download `sera-felagi-debug-apk`.
5. Extract the artifact ZIP and install `app-debug.apk` on your Android phone. You may need to allow installation from your browser/files app.

The workflow builds a debug APK for testing. A Play Store release needs a separately configured signing key and release build.

## Local Android build
Requires Node.js 20+, Java 17, Android SDK, and Android platform tools:
```bash
npm install
npx cap add android
npx cap sync android
cd android
./gradlew assembleDebug
```
APK output: `android/app/build/outputs/apk/debug/app-debug.apk`.

## Backend
The app continues to use the existing public API endpoint configured in `index.html`:
`https://job-api.huliyay4.workers.dev`
