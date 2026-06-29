# Customers — Offline Contact Manager

A simple Android app to manage customers (name + phone), stored fully offline
in a local database on the device. Built with Kotlin, Jetpack Compose, and Room.

## What it does
- Add, edit, delete customers
- Search by name or phone
- Everything is stored locally on the device — no internet, no backend

## How to build the APK from your phone (no laptop needed)

This project includes a GitHub Actions workflow (`.github/workflows/build.yml`)
that builds the APK automatically on GitHub's servers. You just need a free
GitHub account and a phone browser.

1. **Unzip this file** on your phone (most file manager apps, like the stock
   Files app or MT Manager, can unzip — just don't try to "build" it there,
   only extract it).

2. **Create a free GitHub account** at https://github.com if you don't have one,
   using your phone browser.

3. **Create a new repository**:
   - Tap the **+** icon (top right) → **New repository**
   - Name it `CustomerManager` (or anything you like)
   - Keep it **Public** (required for unlimited free Actions minutes) or Private is fine too, just slower
   - Don't add a README/gitignore from GitHub's side — leave it empty
   - Tap **Create repository**

4. **Upload the project files**:
   - On the new repo's page, tap **uploading an existing file** (or **Add file** → **Upload files**)
   - From your file manager, select **all the files and folders** inside the unzipped `CustomerManager` folder (not the outer folder itself — its *contents*: `app`, `.github`, `build.gradle.kts`, `settings.gradle.kts`, `gradle.properties`, `README.md`)
   - GitHub's mobile upload may require selecting folders one at a time — if so, upload `app` first, then `.github`, then the loose files
   - Commit the changes (there's a "Commit changes" button after selecting files)

5. **Let it build**:
   - Go to the **Actions** tab of your repo
   - You should see a workflow run start automatically (triggered by your upload). If not, tap **Build APK** in the left sidebar → **Run workflow**
   - Tap into the running job and wait — first build takes about 3-5 minutes

6. **Download the APK**:
   - Once the run shows a green checkmark, open it
   - Scroll down to **Artifacts** → tap **app-debug-apk** to download a zip containing your APK
   - Unzip that on your phone, then tap the `.apk` file to install
     (you may need to allow "install from unknown sources" the first time — Android will prompt you)

That's it — APK built and installed, no laptop, no Android Studio.

## How to build the APK (once you have your laptop)

1. **Install Android Studio**: https://developer.android.com/studio
   Run the installer and accept the default setup (it downloads the Android SDK automatically).

2. **Open the project**:
   - Unzip `CustomerManager.zip` somewhere on your computer
   - Open Android Studio → "Open" → select the unzipped `CustomerManager` folder
   - Wait for Gradle to sync (first time can take a few minutes — it downloads dependencies)

3. **Build the APK**:
   - Menu bar → `Build` → `Build Bundle(s) / APK(s)` → `Build APK(s)`
   - When it finishes, click the "locate" link in the notification, or find the file at:
     `CustomerManager/app/build/outputs/apk/debug/app-debug.apk`

4. **Install it on your phone**:
   - Plug your phone into the laptop via USB, with USB debugging enabled
     (Settings → About phone → tap "Build number" 7 times → Developer options → USB debugging)
   - In Android Studio, click the green ▶ Run button with your phone selected as the target — this installs and launches it directly
   - OR copy the `app-debug.apk` file to your phone (e.g. via USB, email, or cloud storage) and tap it on the phone to install (you may need to allow "install from unknown sources" the first time)

That's it — no coding required, just those clicks.

## Project structure
```
CustomerManager/
├── app/
│   ├── build.gradle.kts          # dependencies (Compose, Room)
│   └── src/main/
│       ├── AndroidManifest.xml
│       └── java/com/example/customermanager/
│           ├── MainActivity.kt
│           ├── data/
│           │   ├── Customer.kt        # the data model
│           │   ├── CustomerDao.kt      # database queries
│           │   └── AppDatabase.kt      # Room database setup
│           └── ui/
│               ├── CustomerViewModel.kt   # app logic / state
│               └── CustomerListScreen.kt  # the UI
├── build.gradle.kts
└── settings.gradle.kts
```

## Want to change something later?
- Add a new field (e.g. email): add it to `Customer.kt`, bump the database `version`
  in `AppDatabase.kt`, and add a field to the dialog in `CustomerListScreen.kt`.
- Just ask me — paste in the file and I'll make the edit for you.
