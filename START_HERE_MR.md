# RAVAN AI — ZIP उघडल्यानंतर आधी हे वाचा

## 1. ही कोणती फाईल आहे?

ही **Android Source Project ZIP** आहे; तयार APK नाही. APK GitHub Actions मधून build करायची आहे. या development environment मध्ये Android SDK/Gradle उपलब्ध नसल्यामुळे compiled APK देणे शक्य झालेले नाही.

## 2. ZIP मध्ये काय आहे?

- `app/` — RAVAN AI Android अॅपचा Kotlin code.
- `backend/` — पर्यायी Node.js AI/Call backend आणि mock tests.
- `.github/workflows/build-apk.yml` — GitHub वर APK build करण्याची workflow.
- `CREATOR_STUDIO_MR.md` — video creation/editing माहिती.
- `YOUTUBE_CHANNEL_MR.md` — YouTube upload व monetization मार्गदर्शक.
- `BUILD_APK_ON_GITHUB_MR.md` — GitHub build करण्याची पायरी-पायरीची माहिती.

## 3. कोणत्या Android फोनवर?

`minSdk = 30`, म्हणजे Android 11 किंवा त्यापुढील आवृत्ती. Android 11 फोनवर install compatibility असू शकते; प्रत्यक्ष performance device hardware, memory, codec आणि available storage वर अवलंबून असेल.

## 4. ₹0 मोड कसा वापरायचा?

- Backend URL रिकामा ठेवल्यास local commands, local video creator, photo labels/face count आणि device speech features वापरता येतात.
- पूर्ण मुक्त-संवाद AI किंवा remote generative image/video साठी external model/server लागतो. या ZIP मध्ये unlimited free generative AI समाविष्ट नाही.
- Video rendering फोनवर होते; लांब किंवा मोठे videos render करताना वेळ, storage आणि battery लागेल.

## 5. ZIP मधून APK कशी तयार करायची?

1. Android File Manager मधून ZIP Extract करा.
2. Extract झालेला `RavanAI` folder उघडा.
3. GitHub वर private repository तयार करा.
4. `RavanAI` मधील सर्व contents repository च्या root मध्ये upload करा. `app`, `backend`, `gradle.properties`, `settings.gradle.kts`, `.gitignore`, `.github` हे सगळे जतन झाले पाहिजे.
5. GitHub मध्ये `Actions` उघडा.
6. `Build RAVAN AI APK and test backend` workflow निवडा.
7. `Run workflow` दाबा.
8. `android-apk` job हिरवा/Success झाल्यावर `RAVAN-AI-debug-apk` artifact download करा.
9. Artifact ZIP Extract करा. त्यातील `app-debug.apk` install करा.

GitHub मध्ये `.github` folder दिसत नसेल तर repository मध्ये `Add file → Create new file` वापरून path `.github/workflows/build-apk.yml` तयार करा आणि ZIP मधील त्या फाईलचा पूर्ण मजकूर paste करा.

## 6. साधारण किती वेळ?

पहिला GitHub build साधारण **8–20 मिनिटे** लागू शकतो; कधी runner किंवा downloads मुळे जास्तही लागू शकतो. पुढील builds अनेकदा कमी वेळात होतात. ही अंदाजित वेळ आहे, हमी नाही. Build fail झाला तर Actions → failed job → log मध्ये पहिला लाल/error message पाहा.

## 7. प्रथम Install नंतर

- Microphone परवानगी फक्त voice वापरायचा असल्यास द्या.
- Notifications परवानगी reminders साठी द्या.
- Media picker मधून फक्त वापरायचे photo/video निवडा.
- Android ने दाखवलेल्या प्रत्येक permission चा अर्थ समजून मगच allow करा.

## 8. अजून कोणत्या मर्यादा आहेत?

- WhatsApp message draft उघडता येतो; Send user ने करायचा.
- कोणतेही app उघडणे किंवा website URL browser मध्ये उघडणे शक्य; पण प्रत्येक app च्या आत पूर्ण remote control नाही.
- Play Store मधून app install करण्यासाठी user ने Install करायचा.
- YouTube Studio उघडता येते आणि upload details copy करता येतात; प्रत्येक channel setting किंवा monetization approval RAVAN स्वतः बदलू शकत नाही.
- Full prompt-to-video, CapCut-class VFX आणि unrestricted device access या build मध्ये नाहीत.

अचूक यादीसाठी `LEVEL3_CAPABILITIES_MR.md` वाचा.
