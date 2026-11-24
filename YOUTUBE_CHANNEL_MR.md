# RAVAN AI — YouTube Channel Toolkit

## अॅपमध्ये सध्या काय आहे?

- Title, Description आणि comma-separated Tags भरण्यासाठी fields.
- `Copy upload details` दाबल्यावर हे तीन भाग clipboard मध्ये copy होतात.
- `Open YouTube Studio` अधिकृत YouTube Studio उघडते.
- तयार केलेला RAVAN MP4 Android share sheet द्वारे YouTube app/योग्य upload app कडे share करता येतो; user ने upload details व settings तपासून publish करायचे.

## काय स्वयंचलित नाही?

RAVAN या build मध्ये channel च्या सर्व private settings, audience controls, monetization modules, payout details किंवा channel ownership settings स्वतः बदलत नाही. YouTube/Google account मध्ये sign-in आणि final review तुझ्याकडेच राहतात.

Direct upload integration करायची असल्यास Google Cloud project, YouTube Data API, OAuth Android client आणि user-granted `youtube.upload` scope लागेल. OAuth secrets/token सुरक्षितपणे सांभाळावे लागतात. अधिकृत API video upload आणि काही metadata सेट करू शकतो; पण प्रत्येक YouTube Studio setting बदलण्याचा API पर्याय नाही.

Official guide: https://developers.google.com/youtube/v3/guides/uploading_a_video

## YouTube वर व्हिडिओ अपलोड करण्याची सुरक्षित प्रक्रिया

1. RAVAN Creator Studio मधून MP4 तयार करा.
2. YouTube Channel Toolkit मध्ये Title, Description आणि Tags भरा.
3. `Copy upload details` दाबा.
4. `Open YouTube Studio` दाबा आणि तुझ्या स्वतःच्या Google account मध्ये login करा.
5. Upload video उघडा, MP4 निवडा, copied title/description/tags paste करा.
6. Thumbnail, playlist, audience, visibility, subtitles, checks आणि schedule तपासा.
7. Copyright checks व audience settings तपासून मग Publish/Schedule स्वतः निवडा.

## Monetization checklist

YouTube च्या जाहिरात महसूलासाठी सध्याचे मुख्य YPP thresholds:

- 1,000 subscribers आणि मागील 12 महिन्यांत 4,000 पात्र public watch hours, किंवा
- 1,000 subscribers आणि मागील 90 दिवसांत 10 million पात्र public Shorts views.

Shorts Feed मधील views चे watch hours 4,000 long-form watch hours मध्ये मोजले जात नाहीत. Threshold पूर्ण झाले तरी YouTube channel policy review करतो; approval हमखास नाही.

Official eligibility page: https://support.google.com/youtube/answer/72851

जर creator 18 वर्षांखालील असेल, तर AdSense for YouTube payments हाताळण्यासाठी 18+ parent/legal guardian ची मदत लागू शकते. Payment/tax/account details पालक/guardian सोबत अधिकृत पद्धतीने हाताळा.

## RAVAN काय सुचवू शकतो?

AI backend उपलब्ध असल्यास chat मध्ये RAVAN ला `माझ्या पुढील हॉरर व्हिडिओसाठी title, description, tags, thumbnail concept आणि upload checklist तयार कर` असे विचारू शकतो. Backend नसल्यास offline मोडमध्ये पूर्ण creative generation मर्यादित असेल. तयार मजकूर YouTube fields मध्ये copy करून अंतिम तपासणी स्वतः करा.
