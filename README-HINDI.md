# Notebook Hisab Calculator — Native Android APK

यह **native Android app project** है (वेबसाइट/PWA नहीं)। APK GitHub Actions के cloud Android builder से बनेगा।

## APK बनाने का सबसे आसान तरीका (मोबाइल से)
1. ZIP को extract करें।
2. GitHub पर नया खाली repository बनाएँ।
3. इस ZIP के अंदर की सभी files repository में upload करें (ZIP को repository में अकेली file की तरह नहीं)।
4. GitHub repository में **Actions** खोलें। `Build Android APK` workflow चुनें और **Run workflow** दबाएँ।
5. Build पूरा होने पर नीचे **Artifacts** में `Notebook-Hisab-Calculator-APK` डाउनलोड करें।
6. ZIP artifact खोलें, `app-debug.apk` को Vivo फोन में install करें। Android पूछे तो उस source से install की अनुमति दें।

## Gemini Vision server
1. `backend` folder को Node.js hosting पर deploy करें (HTTPS जरूरी)।
2. `backend/.env.example` की कॉपी `.env` नाम से बनाएँ और `GEMINI_API_KEY` भरें।
3. `GEMINI_MODEL` default `gemini-2.5-flash` है; जरूरत पर बदलें।
4. App खोलकर server URL field में API का HTTPS base URL डालें, जैसे `https://your-api.example`।
5. फोटो चुनें → Gemini से अंक पढ़ें → पीले चेतावनी वाले अंक खुद जाँचें/सुधारें → हिसाब सेव/एक्सपोर्ट करें।

## महत्वपूर्ण सीमाएँ / सुरक्षा
- API key Android APK में नहीं रखी जाती; केवल backend environment variable में रहती है।
- Gemini स्कैनिंग के लिए इंटरनेट और deployed HTTPS backend चाहिए।
- Local history फोन के app storage में रहती है; app uninstall करने पर हट सकती है।
- Unreadable entries are returned blank/uncertain. Always review OCR before using financial totals.
- यह initial native build है; release signing, cloud backend deployment और device QA अलग चरण हैं।
