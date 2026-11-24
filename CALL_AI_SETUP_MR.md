# RAVAN AI कॉल असिस्टंट — मराठी मार्गदर्शक (मोफत व Cloud पर्याय)

## दोन वेगळे मोड समजून घ्या

### A. ₹0 SIM Call Companion (या ZIP मध्ये Android बाजूने उपलब्ध)
- सामान्य SIM कॉल आल्यावर Android ची Call Screening सेवा caller नंबर ओळखून notification दाखवते.
- Busy mode आणि SMS permission दिल्यास RAVAN स्वतःची AI ओळख करून देणारा SMS पाठवू शकतो.
- हा मोड कॉल उचलत नाही, caller चे बोलणे ऐकत नाही आणि caller ला AI आवाजात उत्तर देत नाही. Android च्या सामान्य third-party app मर्यादेमुळे हे करता येत नाही.
- SMS पाठवण्यास मोबाइल ऑपरेटरचे SMS शुल्क/प्लॅन लागू होऊ शकतात. SMS auto-reply बंद ठेवणे हा सर्वात कमी खर्चाचा पर्याय आहे.

### B. App मधील Voice Assistant (₹0 मध्ये वापरता येणारा मर्यादित मोड)
- RAVAN अॅप उघडून mic वापरा; Android speech recognizer तुमचे बोलणे मजकुरात बदलतो.
- इंटरनेट/backend नसतानाही मूलभूत फोन commands आणि काही पूर्वनिश्चित मराठी/हिंदी/इंग्रजी उत्तरे उपलब्ध आहेत.
- Speech recognition सेवा काही फोनवर इंटरनेट वापरू शकते. TTS साठी फोनमध्ये भाषेचा voice pack उपलब्ध असणे आवश्यक आहे.
- हा पूर्ण offline ChatGPT-सारखा model नाही. मुक्त स्वरूपातील AI उत्तरांसाठी cloud AI किंवा फोनवर चालणारा मोठा local model लागतो.

## हा Cloud Phone AI कसा काम करतो? (पर्यायी, खर्च लागू शकतो)

1. समोरची व्यक्ती cloud voice नंबरवर कॉल करते.
2. सर्व्हर कॉल उचलतो आणि सुरुवातीलाच सांगतो की तो RAVAN AI आहे.
3. कॉलर जे बोलतो ते speech recognition मजकुरात बदलते.
4. मजकूर AI कडे जातो. AI आधीचे संभाषण लक्षात घेऊन उत्तर तयार करतो.
5. उत्तर फोनवर आवाजात ऐकवले जाते आणि पुन्हा कॉलरचे बोलणे घेतले जाते.
6. कॉल संपल्यावर कॉलरचा नंबर आणि छोटा सारांश अॅपच्या Calls विभागात Sync होऊ शकतो.

## महत्त्वाची मर्यादा आणि खर्च

- Android मधील सामान्य अॅपला साध्या SIM कॉलचा दोन्ही बाजूंचा आवाज थेट ऐकता येत नाही. त्यामुळे RAVAN फोनमधील SIM कॉल गुपचूप उचलत नाही.
- खरे कॉल AI संभाषण करण्यासाठी तुमच्या मोबाईल कंपनीकडून आणि cloud voice provider कडून समर्थित call forwarding/voice number लागतो. या सेवांसाठी कॉल, speech recognition आणि AI model वापराचे शुल्क लागू होऊ शकते; त्यामुळे ₹0 ची हमी नाही.
- या ZIP मधील backend Twilio-compatible webhook वापरतो. भारतात कोणता नंबर प्रकार आणि forwarding चालेल हे आधी provider आणि carrier कडून तपासावे लागते. Twilio च्या भारतासाठीच्या voice मार्गदर्शकात सामान्य domestic inbound voice `N/A` दाखवले आहे; toll-free साठी वेगळ्या अटी आहेत. त्यामुळे भारतात हे थेट चालेल असे गृहीत धरू नका.
- या आवृत्तीत Twilio Gather 2.0 चे `language=multi` + `speechModel=deepgram_nova-3` वापरले आहे. Deepgram Nova-3 च्या सध्याच्या multilingual यादीत Marathi, Hindi आणि English आहेत. त्यामुळे AI प्रतिसाद त्या भाषेत देण्याचा प्रयत्न करतो. तरीही प्रत्यक्ष provider account, region आणि Gather 2.0 वर test call करणे आवश्यक आहे.
- कॉल ऑडिओ RAVAN backend स्वतः साठवत नाही. मात्र caller number आणि छोटा text सारांश backend मध्ये राहतो; voice provider स्वतःच्या सेवेत कॉल डेटा process करू शकतो.

## Cloud Phone AI साठी काय लागेल? (पर्यायी)

- HTTPS असलेला Node.js 20+ server.
- Anthropic API key आणि लांब, random APP_TOKEN. हे फक्त private server settings मध्ये ठेवा.
- Phone conversation साठी Twilio-compatible webhook असलेला voice provider. नंबर उपलब्धता, forwarding नियम आणि खर्च आधी तपासा.
- सेवा खाते तयार करणे, खर्च किंवा privacy settings बदलणे यासाठी पालक/विश्वासू मोठ्या व्यक्तीची मदत घ्या.

## Backend सुरू करणे (Cloud AI वापरायचा असल्यासच)

1. `backend/.env.example` ची private copy करा.
2. `ANTHROPIC_API_KEY` मध्ये server key टाका.
3. `APP_TOKEN` साठी लांब random secret ठेवा.
4. `PUBLIC_URL` मध्ये HTTPS backend URL द्या. शेवटी `/` देऊ नका.
5. `TWILIO_AUTH_TOKEN` मध्ये voice provider चा auth token द्या.
6. `CALL_LANG=multi`, `CALL_SPEECH_MODEL=deepgram_nova-3` आणि `CALL_SPEECH_TIMEOUT=5` ठेवा. हा multilingual mode Marathi/Hindi/English input साठी आहे. फक्त Hindi वापरायचे असल्यास `CALL_LANG=hi-IN` करा. `GREETING` आणि `DISCLOSURE` caller ला समजणाऱ्या भाषेत ठेवा.
7. `backend` फोल्डरमधून `npm start` चालवा. या backend ला external npm packages लागत नाहीत.
8. `/health` उघडून सेवा चालू आहे का तपासा.

## Voice provider webhook सेटिंग

- Incoming call webhook: `POST https://YOUR_HOST/voice/incoming`
- Caller speech साठी action webhook TwiML मधून आपोआप `/voice/turn` वापरतो.
- Call status callback: `POST https://YOUR_HOST/voice/status`
- Provider चे webhook signatures verify होण्यासाठी `PUBLIC_URL` आणि `TWILIO_AUTH_TOKEN` अगदी अचूक असावेत.

सुरुवातीला फक्त test call वापरा. आधी पूर्ण greeting, AI disclosure, caller speech, AI reply, follow-up आणि summary तपासा. मगच मुख्य नंबरचे forwarding विचारात घ्या. कोणताही खर्च/forwarding सुरू करण्यापूर्वी provider च्या अटी तपासा.

## ₹0 मोड वापरणे आणि APK बनवणे

- फक्त app-based voice आणि local commands वापरण्यासाठी backend URL/token रिकामे ठेवा.
- Settings मध्ये Speak replies सुरू करा. Android Settings मध्ये Marathi/Hindi/English speech recognition व text-to-speech voices उपलब्ध आहेत का तपासा.
- SIM call companion साठी Calls/Busy mode permission वापरता येईल; SMS auto-reply ऐच्छिक आहे आणि operator शुल्क लागू होऊ शकते.
- प्रत्यक्ष SIM call AI receptionist साठी Cloud Phone AI विभागातील सेवा लागतात; त्या मोफत आहेत असे गृहीत धरू नका.

## APK बनवणे

या ZIP मधील `RavanAI` फोल्डरमधील सर्व contents GitHub repository मध्ये folder structure जपून upload करा. Hidden `.github` फोल्डर सुद्धा upload झाला पाहिजे. मग Actions → Build RAVAN AI APK चालवा. Build green झाल्यावर Artifacts मधील `RAVAN-AI-debug-apk` ZIP डाउनलोड करा. त्या ZIP मध्ये `app-debug.apk` असेल.

## अधिकृत भाषा/कॉल संदर्भ

- Twilio Gather 2.0 भाषानिवड आणि `multi` + `deepgram_nova-3`: https://www.twilio.com/docs/voice/twiml/gather
- Deepgram Nova-3 समर्थित भाषा (Marathi/Hindi/English यासह): https://developers.deepgram.com/docs/models-languages-overview/
- Twilio भारत Voice नियम व उपलब्धता: https://static1.twilio.com/en-us/guidelines/in/voice
- Anthropic Claude model ID: https://platform.claude.com/docs/en/models/sonnet-5-5/overview
