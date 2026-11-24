# RAVAN AI 1.4.0 — Level 3 Capability Matrix

| विभाग | या source build मधील क्षमता | मर्यादा |
|---|---|---|
| Voice | Device speech recognizer/TTS मधून Marathi, Hindi, English (device support वर अवलंबून) | प्रत्येक फोनवर प्रत्येक भाषा उपलब्ध असेलच असे नाही |
| Offline chat | ठरावीक keyword-based commands व मर्यादित offline replies | Full offline LLM/complex reasoning नाही |
| AI planner | optional backend वरून जास्तीत जास्त 5 allow-listed actions; review आणि run | Unrestricted GUI control नाही; actions failure/hand-off वर थांबतात |
| Apps | Launcher intent ने installed app उघडणे; Play Store search उघडणे | App install user करतो; third-party UI वर सार्वत्रिक नियंत्रण नाही |
| Web | स्पष्ट HTTP(S) URL default browser/Chrome मध्ये उघडणे | Website च्या login/settings/purchase स्वतः क्लिक करून बदलत नाही |
| Reminders | Android reminders/notification; scheduled WhatsApp draft notification | Android battery settings/notification permission लागू; WhatsApp Send user करतो |
| Photo AI | ML Kit face count आणि general object/scene labels | व्यक्तीची ओळख/नाव/face matching नाही |
| Multi-clip Creator | 20 पर्यंत user-selected photos/videos क्रमाने जोडणे, still duration, music, title overlay, 16:9/9:16, simple colour presets, mute, MP4 export | Text-to-video generation, pro multi-track/keyframes, chroma key, crossfade आणि advanced VFX नाही |
| Single-clip editor | Trim, rotate, mute, scale/720p export | Full professional editor नाही |
| YouTube | Metadata draft fields, clipboard copy, official Studio open, manual video share | सर्व channel settings/monetization स्वतः बदलत नाही; upload user reviews/publishes |
| SIM calls | Optional call screening/number metadata; optional cloud receptionist backend | Normal SIM call audio Android app ला थेट उपलब्ध नाही; provider/Cloud खर्च होऊ शकतो |

## Level 3 कसे काम करते?

1. User बोलून किंवा लिहून आदेश देतो.
2. Backend configured असल्यास AI supported actions मधून जास्तीत जास्त पाच steps सुचवतो.
3. अनेक actions किंवा external hand-off असतील तर review dialog दिसतो.
4. User `Run plan` मान्य केल्यावर supported actions क्रमाने चालतात.
5. अयशस्वी action किंवा दुसऱ्या app ला hand-off झाल्यास plan थांबतो. Action log मध्ये निकाल दाखवला जातो.
6. हा workflow unrestricted smartphone access नाही; प्रत्येक सुविधा Android आणि destination app च्या API/permissions पुरतीच.

## ₹0 बद्दल

Local commands, photo analysis, built-in video export आणि phone speech features बाह्य AI key शिवाय वापरता येऊ शकतात. Full natural-language AI, remote image/video generation, backend hosting आणि telephony साठी provider quotas/charges लागू शकतात. Unlimited free cloud AI/video generation या ZIP मध्ये नाही.

## Build status

Backend Node syntax आणि mock tests चालवले आहेत. Android Manifest XML parse validation केले आहे. Android SDK/Gradle या container मध्ये उपलब्ध नसल्याने Android APK compile/device test केलेले नाही. GitHub Actions workflow ने actual build करून logs तपासणे आवश्यक आहे.
