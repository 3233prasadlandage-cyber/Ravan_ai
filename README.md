# RAVAN AI — Free-first Android assistant (source project)

**Version:** 1.4.0  
**Project:** Android app + optional Node.js AI/call backend  
**Important:** this ZIP is source code, not a pre-built APK. The Android APK has not been compiled in this environment because Android SDK/Gradle are unavailable here. Use the included GitHub Actions workflow to build it, then inspect the result and build logs.

## What this build actually includes

- Android app built with Kotlin + Jetpack Compose (minimum Android 11 / API 30).
- Marathi/Hindi/English speech input/output when the device's speech service and TTS voices support those languages.
- Limited offline command routing for supported Android actions.
- Optional AI backend that returns a reviewed plan of up to five allow-listed actions. Steps stop on failure or when the user must finish an external-app hand-off.
- Launch an installed app, open supported Android settings screens, open YouTube search, search the Play Store, and open an explicit HTTP(S) URL in the default browser.
- Alarm/reminder screens, notifications, and a scheduled WhatsApp draft reminder. WhatsApp itself still requires the user to review and tap Send.
- On-device photo analysis: visible face count plus general object/scene labels. It does not identify real people by name or match identities.
- Built-in local video creator using AndroidX Media3 Transformer: sequentially combine up to 20 selected photos/videos, set still-photo duration, use a background music track, add a static text title, choose YouTube 16:9 or Shorts 9:16, apply simple colour presets (cinematic, grayscale, bright, inverted), optionally mute source audio, export MP4 to `Movies/RAVAN AI`.
- Single-clip editor: trim, rotate, optional mute, and export MP4.
- YouTube Channel Toolkit: prepare title, description, tags, copy the upload details, open YouTube Studio, and share the finished MP4 for manual upload.
- Optional cloud call-receptionist backend, which requires compatible telephony/provider access and may cost money.

## What it does not claim to do

- This is **not** a prompt-to-realistic-video generator. The local creator composes user-selected photos/clips into a video; it does not invent new moving scenes from a text prompt.
- It is not a full CapCut-class editor: professional multi-track timeline controls, keyframes, chroma key, animated VFX packs, crossfade transitions, and complex audio automation are not included in this build. Media3 Composition currently documents crossfading as unsupported.
- It does not control every screen in every installed app. Android app sandboxing and third-party app protections prevent unrestricted app control. It uses Android intents and approved APIs; a hand-off means the user takes over in that app.
- It does not silently install apps, send WhatsApp messages, secretly listen to normal SIM calls, identify people in photos, or change every YouTube channel/monetization setting automatically.
- It cannot guarantee that YouTube will approve a channel for monetization or that the channel will grow.

## Free-first costs

The local Android features can run without paid AI API credentials. Android's speech service, phone storage, device performance, and network availability can still affect operation. Natural-language cloud reasoning, text/image/video generation from remote AI models, a hosted backend, and cloud telephony may cost money or have limited free quotas. This project does not contain an unlimited free text-to-video model.

## Project structure

- `app/` — Android source code.
- `backend/` — optional Node.js backend, local mock tests, call webhook flow.
- `.github/workflows/build-apk.yml` — GitHub Actions build workflow.
- `START_HERE_MR.md` — Marathi setup guide.
- `BUILD_APK_ON_GITHUB_MR.md` — GitHub build steps and expected time.
- `CREATOR_STUDIO_MR.md` — actual local video/photo capabilities and limitations.
- `YOUTUBE_CHANNEL_MR.md` — YouTube upload and monetization workflow.
- `LEVEL3_CAPABILITIES_MR.md` — feature and permission matrix.

## Build the debug APK on GitHub

1. Extract this ZIP. Open the `RavanAI` folder.
2. Create a **private** GitHub repository.
3. Upload the contents of `RavanAI` to the repository root (not the outer `RavanAI` folder as a nested directory). Preserve `.github/workflows/build-apk.yml`.
4. Open **Actions** and run **Build RAVAN AI APK and test backend**.
5. When the `android-apk` job succeeds, download the `RAVAN-AI-debug-apk` artifact ZIP. It contains `app-debug.apk`.
6. Extract the APK and install it on a compatible Android phone you own or are allowed to use. Review each permission prompt.

The first CI build commonly takes around 8–20 minutes because the Android SDK and Gradle dependencies need to download. Later builds are often faster. Actual time depends on GitHub runner load, dependency downloads, and build status; this is an estimate, not a promise. If the job fails, open the failed job log and read the first Gradle/Kotlin error.

## Build configuration

- `compileSdk = 36`, `targetSdk = 36`, `minSdk = 30` (Android 11+).
- Java 17, Android Gradle Plugin 8.13.2, Gradle 8.13, Kotlin 2.4.21, KSP 2.3.12.
- AndroidX Media3 1.11.1.

## Backend tests

From `backend/`:

```bash
node --check server.js
node --check test.js
npm test
```

The tests use mock endpoints. They do not verify live AI billing, real telephone provider settings, Android runtime behaviour, or a real YouTube channel.

## Security

- Never commit `.env`, API keys, app tokens, OAuth client secrets, Twilio tokens, or call data to a public repository.
- Keep the GitHub repository private while developing.
- Do not give RAVAN your Google password. Use Google's official sign-in and permission prompts.
- Keep external communications and uploads under your review. Ask a parent/guardian to review account, privacy, and payment settings.

## Official technical references

- Android Media3 Transformer editor guide: https://developer.android.com/media/implement/editing-app
- Media3 composition guide and current limitations: https://developer.android.com/media/media3/transformer/composition
- YouTube video upload API: https://developers.google.com/youtube/v3/guides/uploading_a_video
- YouTube Partner Program eligibility: https://support.google.com/youtube/answer/72851
- Google Play Accessibility API policy: https://support.google.com/googleplay/android-developer/answer/10964491
