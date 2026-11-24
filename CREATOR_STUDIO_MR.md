# RAVAN Creator Studio — प्रत्यक्ष क्षमता

## या build मध्ये phone वर काय render होते?

RAVAN Creator Studio निवडलेल्या media files वरून प्रत्यक्ष MP4 बनवते. ही फक्त CapCut उघडण्याची कृती नाही; Media3 Transformer फोनवर local render/export करतो.

### Multi-clip / photo video

- एकावेळी जास्तीत जास्त 20 फोटो आणि/किंवा व्हिडिओ निवडणे.
- निवडलेल्या क्रमाने clips/photos जोडणे.
- प्रत्येक फोटो 2 ते 12 सेकंद दाखवणे.
- निवडलेली background music/audio file स्वतंत्र audio sequence म्हणून जोडणे आणि video कालावधीपर्यंत loop करणे.
- Title/caption overlay लावणे.
- 16:9 YouTube landscape किंवा 9:16 Shorts output निवडणे.
- Presets: None, Cinematic, Black & White, Bright, Invert.
- Source clip audio mute करणे.
- MP4 output `Movies/RAVAN AI` मध्ये सेव्ह करणे.

### Single video editor

- Start/End वेळ सेकंदात देऊन trim.
- 90° increments मध्ये rotate.
- Source audio mute.
- 720p height output.
- MP4 export आणि share.

## वापरण्याची पद्धत

1. RAVAN उघडा → `Agent` tab.
2. `Add photos / videos` निवडा. जास्तीत जास्त 20 files निवडा.
3. `Choose background music` वापरून audio निवडा (ऐच्छिक).
4. Video वर दिसणारा title/caption लिहा.
5. YouTube 16:9 किंवा Shorts 9:16 निवडा.
6. Colour effect निवडा.
7. प्रत्येक फोटो किती सेकंद दिसावा ते ठरवा.
8. गरजेनुसार source video audio mute करा.
9. `Create / Export MP4` दाबा. Export दरम्यान RAVAN बंद करू नका.
10. Video `Movies/RAVAN AI` मध्ये save होईल. Share button वापरून तो YouTube किंवा इतर app मध्ये manually निवडा.

## प्रामाणिक मर्यादा

या आवृत्तीमध्ये prompt लिहून पूर्णपणे नवीन realistic moving video तयार करणारा text-to-video model नाही. ती user निवडलेल्या फोटो/व्हिडिओंचा sequence बनवते.

खालील advanced editing features या build मध्ये समाविष्ट नाहीत:

- Multi-track timeline वर स्वतंत्र layers move/trim करणे.
- Keyframes, motion tracking आणि animated camera paths.
- Green-screen/chroma-key compositing.
- Animated particle VFX, professional transitions आणि crossfade.
- Advanced audio ducking, beat sync, voice cleanup आणि automated sound design.
- Text prompt मधून नवीन AI-generated moving scene.

AndroidX Media3 Composition मध्ये sequential media, audio layers, effects आणि overlays समर्थित आहेत; अधिकृत दस्तऐवजात crossfading सध्या unsupported असल्याचे नमूद आहे. https://developer.android.com/media/media3/transformer/composition

पूर्ण AI text-to-video ला मॉडेल आणि मोठ्या compute/GPU ची गरज असते. हे unlimited free/offline उपलब्ध आहे असे या ZIP बद्दल सांगता येणार नाही.

## Photo understanding

Agent → `Choose photo and analyze`:
- चेहऱ्यांची संख्या मोजणे.
- ML Kit वापरून सामान्य objects/scenes चे labels देणे.
- निवडलेला फोटो फोनवरच process करणे.

ही सुविधा व्यक्तीचे नाव/ओळख सांगत नाही, faces वेगवेगळ्या फोटोंमध्ये match करत नाही आणि sensitive identity inference करत नाही.

## तांत्रिक आधार

AndroidX Media3 Transformer 1.11.1 वापरले आहे. अधिकृत editor guide मध्ये trimming, scaling, rotating, filters/effects, overlays आणि export ची उदाहरणे आहेत: https://developer.android.com/media/implement/editing-app
