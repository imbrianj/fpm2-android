Provides access to FPM2 password database on Android. FPM2 is Linux/GTK+ password manager. ACCESS IS READ-ONLY, so if you're not already managing passwords on your PC using FPM2 this software is probably useless.

## Modernized Android build
This repository was originally an Eclipse/Ant Android project. It now includes a Gradle/Android-Gradle-Plugin build so it can be opened directly in current Android Studio versions.

### Current Android targets
- `compileSdk`: 34
- `targetSdk`: 34
- `minSdk`: 21

### File access on modern Android
- On Android 10+ you should select your database with **Settings → Pick FPM2 file**.
- The file picker stores a persisted `content://` URI permission so the app can continue to open the chosen file after reboot.
- Legacy path-based external storage permissions are retained only for older Android versions (`READ_EXTERNAL_STORAGE` up to API 32 and `WRITE_EXTERNAL_STORAGE` up to API 28).

### Security notes
- FPM2 format compatibility is preserved; cryptographic parameters are defined by the original FPM2 file format and are not changed by this app.
- Prefer **Use Internal Storage** in settings to copy the file into app-private storage when possible.
- Clipboard copy behavior is supported for compatibility, but clipboard contents may be visible to other apps; clear clipboard after use.

### Building
Use JDK 17+ and run:

```bash
./gradlew assembleDebug
```

If your environment blocks access to Maven/Google repositories, Gradle dependency resolution will fail until repository access is available.
