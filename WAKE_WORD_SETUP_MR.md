# RAVAN Wake Word — setup and limitations (Marathi)

## काय जोडले आहे
- Settings मध्ये `Wake word: RAVAN` switch.
- Switch ON केल्यावर Android microphone permission घेऊन foreground microphone service सुरू होते.
- कायम दिसणाऱ्या notification मध्ये RAVAN listening असल्याचे दाखवले जाते.
- Android speech recognition मधील partial/final results मध्ये `RAVAN` शब्द आढळल्यास wake event पाठवला जातो.
- App समोर उघडे असेल तर voice input सुरू होते. App background मध्ये असेल तर notification tap करून app उघडल्यावर voice input सुरू होते.
- Conversation दरम्यान microphone clash टाळण्यासाठी wake listener थांबतो. Conversation नंतर Settings मधील switch OFF/ON करून पुन्हा arm करा.

## महत्त्वाच्या मर्यादा
- हा offline acoustic keyword model नाही. हा Android च्या उपलब्ध SpeechRecognizer provider वर आधारित prototype आहे; provider इंटरनेट वापरू शकतो आणि त्याचे audio/privacy नियम लागू होतात.
- Android/फोन निर्माता battery management, speech provider किंवा OS policy मुळे सतत recognition थांबवू शकतात. म्हणून screen-off आणि दीर्घकाळ चालण्याची हमी नाही.
- App background मध्ये असताना Android चे background-activity नियम लागू होतात. त्यामुळे शब्द ओळखला तरी app आपोआप समोर आणण्याऐवजी notification tap करून conversation सुरू करावी लागू शकते.
- Wake word नंतर speech conversation सुरू होते; हे पूर्ण hands-free continuous multi-turn assistant नाही. Conversation संपल्यावर Settings मधून Wake word पुन्हा ON करा.
- प्रत्यक्ष OPPO/Android 11 device test या build environment मध्ये करता आलेली नाही.

## फोनवर चाचणी
1. APK install करून RAVAN AI उघडा.
2. Settings → Wake word: RAVAN ON करा.
3. Microphone permission द्या आणि RAVAN listening notification दिसते का पाहा.
4. App समोर असताना `RAVAN` म्हणा; voice input सुरू होणे अपेक्षित आहे.
5. App background मध्ये ठेवल्यावर wake word म्हणा; notification tap करून बोलणे सुरू करा.
6. आवाज ओळखत नसेल तर Google app / Speech Recognition service उपलब्ध आहे का आणि इंटरनेट/भाषा सेटिंग तपासा.
7. थांबवण्यासाठी Settings switch OFF करा.

## Build status
Backend tests pass. Android APK compilation is not verified in this environment because Gradle and Android SDK are not installed here. Use the included GitHub Actions workflow to compile the debug APK, then test on the target phone.
