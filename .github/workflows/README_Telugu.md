# Farm Motion Alarm — Android starter project

ఈ ప్రాజెక్ట్ ఒక **starter prototype** మాత్రమే. ఇది కెమెరా ఫ్రేముల మధ్య మార్పును చూసి కదలిక గుర్తించినప్పుడు అలారం టోన్ ప్లే చేస్తుంది.

## Activation key (డెమో)
`FARM-ALARM-2026`

`app/src/main/java/com/example/farmmotionalarm/MainActivity.kt` లో `activationKey` విలువను మార్చవచ్చు.

**భద్రత:** APK లో hard-code చేసిన activation key నిజమైన రహస్య key కాదు; APK ను పరిశీలిస్తే దాన్ని కనుగొనవచ్చు. వాణిజ్య యాప్‌కు server-side activation అవసరం.

## పరిమితులు
- ఇది కోతులు/లంగూర్లను ప్రత్యేకంగా గుర్తించదు. ఏ కదలికైనా (ఆకులు, నీడ, మనుషులు, వాహనాలు) అలారం రావచ్చు.
- కెమెరా ప్రివ్యూ తెరిచి ఉండాలి; ఫోన్ స్క్రీన్ ఆఫ్ చేసినప్పుడు/బ్యాటరీ ఆప్టిమైజేషన్ వల్ల పని ఆగవచ్చు.
- Bluetooth స్పీకర్‌ను Android Bluetooth సెట్టింగ్స్‌లో ముందుగా జత చేయండి. ఫోన్‌లో media outputగా స్పీకర్ ఎంపికైతే అలారం దానికి వెళ్లవచ్చు.
- నిరంతర కెమెరా వినియోగం వల్ల వేడి/బ్యాటరీ వినియోగం ఉంటుంది. ఫోన్‌ను నీరు, ప్రత్యక్ష ఎండ నుంచి రక్షించండి.
- ఫీల్డ్‌లో పరీక్షించకుండా కోతులను తరిమే విశ్వసనీయ వ్యవస్థగా భావించవద్దు.

## APK build చేయడానికి
అవసరం: Android Studio, JDK 17, Android SDK Platform 35.

1. Android Studioలో `FarmMotionAlarm` ఫోల్డర్‌ను Open చేయండి.
2. Gradle sync పూర్తయ్యే వరకు వేచి ఉండండి.
3. `Build > Build Bundle(s) / APK(s) > Build APK(s)` ఎంచుకోండి.
4. APK సాధారణంగా `app/build/outputs/apk/debug/app-debug.apk` లో ఉంటుంది.

## Release APK signing key తయారు చేయడం
Android Studioలో:
`Build > Generate Signed Bundle / APK > APK > Create new`

- Key store path: మీ కంప్యూటర్‌లో సురక్షితమైన స్థలం
- Password: బలమైన ప్రత్యేక పాస్‌వర్డ్
- Key alias: `farmalarm`
- Validity: 25 సంవత్సరాలు లేదా అంతకంటే ఎక్కువ
- Key password: ప్రత్యేక పాస్‌వర్డ్

Key store (`.jks`) మరియు పాస్‌వర్డ్‌లను సురక్షితంగా బ్యాకప్ చేయండి. ఎవరికీ పంపవద్దు. Key పోతే అదే signing identityతో తదుపరి updates విడుదల చేయడం కష్టమవుతుంది.

## నిజమైన activation system
ఈ starterలో local demo key మాత్రమే ఉంది. నిజమైన activation keys కోసం backend/server, unique codes, validation, revocation మరియు privacy handling అవసరం.
