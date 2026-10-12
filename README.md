# Exam Reminder

An Android app that helps students keep track of upcoming exams and sends notifications before each one, so nothing gets forgotten.

<p align="center">
  <!-- Optional: add screenshots to a /screenshots folder and uncomment -->
  <!-- <img src="screenshots/home.png" width="250" /> <img src="screenshots/add-exam.png" width="250" /> -->
</p>

## Features

- **Add, edit and delete exams**: course name, topics/chapters, notes, exam date and time
- **Multiple reminders per exam**: choose any combination of:
  - 1 day before
  - 2 days before
  - 3 days before
  - 1 week before
  - Exam day morning
  - Custom time
- **Notifications at the exact time**: uses Android exact alarms
- **Survives phone restarts**: reminders are re-scheduled automatically after reboot
- **Works offline**: all data is stored on your phone (no account, no internet needed)
- **Modern look**: Material 3 design built with Jetpack Compose

## Tech stack

| Area | Technology |
|------|-----------|
| Language | Kotlin |
| UI | Jetpack Compose + Material 3 |
| Architecture | MVVM (ViewModel + Repository) |
| Storage | Room (local SQLite database) |
| Navigation | Navigation Compose |
| Reminders | AlarmManager + BroadcastReceivers + Notifications |
| Build | Gradle (Kotlin DSL, `.kts`) with a version catalog |

**Requirements on the phone:** Android 8.0 (API 26) or newer.

## Project structure

```
.
├── android/                  # The Android app (open this folder in Android Studio)
│   ├── app/src/main/java/com/example/examreminder/
│   │   ├── data/             # Room database, DAO, repository
│   │   ├── model/            # Reminder options
│   │   ├── notifications/    # Alarm scheduling, notifications, boot receiver
│   │   ├── ui/               # Screens, ViewModel, navigation, theme
│   │   └── MainActivity.kt
│   ├── app/src/main/res/     # Icons, strings, themes
│   └── gradle/libs.versions.toml   # Dependency versions
└── src/                      # Optional web preview of the app's design (React + Vite)
```

## Install on your phone (easiest)

If this repository includes a ready-made APK (see the **Releases** page or the `apk/` folder):

1. Download `app-debug.apk` to your phone.
2. Tap the file. If Android blocks it, tap **Settings** and enable **Allow from this source**, then go back and tap **Install**.
3. Open **Exam Reminder** from your home screen.

## Build it yourself

### What you need

- A computer (Windows, macOS or Linux)
- [Android Studio](https://developer.android.com/studio) (free). It includes everything else: the Android SDK and the right Java version.
- An internet connection for the first build

### Steps

1. **Clone or download** this repository:
   ```bash
   git clone https://github.com/<your-username>/<your-repo>.git
   ```
   (Or click **Code → Download ZIP** on GitHub and unzip it.)
2. In Android Studio choose **File → Open** and select the **`android`** folder (not the top-level folder).
3. Click **Trust Project** if asked, then **wait for the Gradle sync** to finish. The first sync downloads a lot and can take 5–20 minutes. If Android Studio offers to install a missing SDK platform, accept it.
4. Build the APK: **Build → Build Bundle(s) / APK(s) → Build APK(s)**.
5. When it finishes, click **locate** in the popup. The file is at:
   ```
   android/app/build/outputs/apk/debug/app-debug.apk
   ```
6. Copy that file to your phone and install it as described above.

### Run directly on a connected phone

1. On the phone: **Settings → About phone**, tap **Build number** 7 times to enable Developer options.
2. In **Developer options**, turn on **USB debugging**.
3. Plug the phone into the computer and allow the debugging prompt.
4. In Android Studio, pick your phone from the device list at the top and press the green ▶ **Run** button.

## First launch

- **Allow notifications** when asked (required on Android 13+).
- If the app opens a settings screen for **Alarms & reminders**, turn the switch on. Without it, reminders can't fire at the exact time.

## Troubleshooting

| Problem | Fix |
|---------|-----|
| Gradle sync fails or says SDK is missing | Open **Tools → SDK Manager**, install **Android 15 (API 35)**, then **File → Sync Project with Gradle Files** |
| "Install blocked" on the phone | Enable **Allow from this source** for the app you opened the APK from |
| Reminders don't appear | Check that notifications and the alarms permission are allowed in the phone's app settings, and that battery saver isn't restricting the app |
| Can't find `mipmap-anydpi-v26` or `strings.xml` | You opened an older copy of the project. Open the `android` folder from this repository |

## Optional: web design preview

The root of the repo also contains a small React + Vite page that shows how the app looks in a phone frame. It is not needed to build or use the Android app.

```bash
npm install
npm run dev
```

## Notes

- The APK built this way is a **debug build**, signed with Android's debug key. It's fine for personal use. Publishing to Google Play requires a release build signed with your own key.
- Build output (`build/`, `.gradle/`, `.idea/`) is not meant to be committed. See `.gitignore`.

## License

Ahmedaluraimi@gmail.com

