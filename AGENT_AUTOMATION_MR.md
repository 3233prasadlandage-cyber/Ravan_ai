# RAVAN Android Automation — permissions व मर्यादा

RAVAN official Android intents/API वापरून supported actions करतो. तो hidden unrestricted access वापरत नाही.

- Installed app उघडणे: हो, app launcher मध्ये दिसत असल्यास.
- Website URL उघडणे: पूर्ण `https://` किंवा `http://` URL दिल्यास default browser उघडतो.
- Play Store: search खोलतो; install user confirm करतो.
- WhatsApp: scheduled reminder + pre-filled draft; WhatsApp मध्ये Send user दाबतो.
- Photo: on-device face count + image labels; real identity/name recognition नाही.
- Video: built-in multi-clip local creator व single-clip editor उपलब्ध; advanced VFX / text-to-video नाही.
- Third-party apps: CapCut, VN, KineMaster इ. उघडणे/फाइल share करणे शक्य; त्यांच्या private UI timeline वर पूर्ण automation नाही.
- YouTube: Studio उघडणे, metadata clipboard copy, MP4 share. सर्व settings auto-change किंवा monetization approval नाही.
- Calls: normal SIM call audio app ला थेट ऐकता येत नाही; cloud telephony flow वेगळा.

Sensitive action, external browser hand-off, file access, Play Store search किंवा multi-step action साठी app confirmation मागतो. Android permission prompt समजूनच स्वीकारा.

Google Play Accessibility API policy: https://support.google.com/googleplay/android-developer/answer/10964491
