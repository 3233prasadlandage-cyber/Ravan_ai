# RAVAN AI APK — GitHub वरून Build करण्याची प्रक्रिया

## अंदाजित वेळ

पहिला build साधारण **8–20 मिनिटे** लागू शकतो. Android SDK 36 व Gradle dependencies download होतात म्हणून पहिल्यांदा वेळ जास्त लागू शकतो. नंतरचे builds अनेकदा जलद होतात. ही फक्त अंदाजे वेळ आहे; GitHub runner, नेटवर्क आणि build errors मुळे बदलू शकते.

## फोनवरून प्रक्रिया

1. `RAVAN_AI_ULTIMATE_FREE_FIRST_FINAL.zip` Extract करा.
2. Extract मधील `RavanAI` folder उघडा.
3. Chrome मधून GitHub उघडा आणि private repository तयार करा.
4. Repository मध्ये `Add file → Upload files` निवडा.
5. `RavanAI` मधील files/folders repository च्या मुख्य root मध्ये upload करा. `app/`, `backend/`, `gradle.properties`, `settings.gradle.kts`, `build.gradle.kts` आणि `.github/` यांची रचना बदलू नका.
6. `.github` hidden असल्यामुळे दिसत नसेल, `Add file → Create new file` निवडा. File path म्हणून `.github/workflows/build-apk.yml` लिहा. ZIP मधील त्या workflow चा पूर्ण मजकूर copy/paste करून commit करा.
7. Upload/commit झाल्यावर repository च्या `Actions` tab मध्ये जा.
8. `Build RAVAN AI APK and test backend` workflow निवडा. `Run workflow` → branch `main` → `Run workflow` दाबा.
9. Run उघडा. `backend-tests` आणि `android-apk` हे jobs यशस्वी झाले पाहिजेत.
10. Run पेजच्या खाली `Artifacts` मध्ये `RAVAN-AI-debug-apk` डाउनलोड करा.
11. Artifact ZIP Extract करून `app-debug.apk` मिळवा.
12. APK स्वतःच्या/परवानगी असलेल्या Android फोनवर install करा. फोन विचारेल तेव्हा या source मधून install करण्याची परवानगी द्यायची का ते काळजीपूर्वक ठरवा.

## लक्षात ठेवा

- ZIP फाईल GitHub वर एकच फाईल म्हणून upload केली तर workflow चालणार नाही; आधी Extract करून त्यातील contents upload करायचे.
- `.github/workflows/build-apk.yml` योग्य path मध्ये नसल्यास Actions workflow दिसणार नाही.
- APK ही debug build आहे. ती Play Store release/signing package नाही.
- Build हिरवा झाला तरी फोनवर प्रत्यक्ष वापरून camera/voice/media export/permissions test करणे आवश्यक आहे.
- Android source या environment मध्ये compile केलेली नाही. GitHub build log मधून प्रत्यक्ष compile result तपासा.
- `.env`, AI keys, OAuth secrets किंवा Twilio secrets GitHub वर upload करू नका.

## Build fail झाल्यास

1. Failed workflow run उघडा.
2. `android-apk` job उघडा.
3. पहिला `FAILURE`, `e:` किंवा `Could not resolve` message शोधा.
4. त्या error चा screenshot किंवा पूर्ण error मजकूर ठेवा. त्यावरून नेमका code/dependency issue शोधता येईल.
