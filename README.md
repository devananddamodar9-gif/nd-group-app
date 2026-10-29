# ND Group - Android Application (APK)

**ND Group** हे ताजी भाजीपाला (Vegetables) आणि किराणा माल (Groceries) खरेदी करण्यासाठी बनवलेले आधुनिक Android ऍप आहे. यात dynamic weight multiplier pricing, wallet points withdrawal system, आणि सुरक्षित admin dashboard समाविष्ट आहे.

---

## 📁 Android Studio प्रोजेक्ट स्ट्रक्चर (Project Structure)

```text
NDGroup-Android/
├── .github/
│   └── workflows/
│       └── build-apk.yml          # GitHub Actions द्वारे स्वयंचलित (Automatic) APK बिल्ड
├── app/
│   ├── src/
│   │   ├── main/
│   │   │   ├── AndroidManifest.xml # Permissions (Internet) आणि ॲप कॉन्फिगरेशन
│   │   │   ├── java/com/example/
│   │   │   │   ├── MainActivity.kt # Navigation (Shop, Vegetables, Grocery, Wallet, Admin)
│   │   │   │   ├── data/
│   │   │   │   │   ├── local/      # Room Database, DAO (AppDao.kt) & Entities
│   │   │   │   │   ├── model/      # Product, WeightOption, User, WithdrawalRequest
│   │   │   │   │   └── repository/ # NdGroupRepository (Business logic & Admin restrictions)
│   │   │   │   └── ui/
│   │   │   │       ├── components/ # NdTopBar, ProductCard, AdVideoCard
│   │   │   │       ├── screens/    # HomeScreen, CartScreen, WalletScreen, AdminDashboardScreen
│   │   │   │       ├── theme/      # Color.kt, Theme.kt, Type.kt (ND Group Brand Theme)
│   │   │   │       └── viewmodel/  # NdGroupViewModel.kt
│   │   │   └── res/
│   │   │       ├── drawable/       # ND Group official logo & vector icons
│   │   │       ├── mipmap-*/       # Adaptive Launcher Icons (HDPI to XXXHDPI)
│   │   │       └── values/         # strings.xml, colors.xml
│   │   └── test/                   # Robolectric आणि Unit Tests
│   ├── build.gradle.kts            # App-level dependencies (Compose, Room, Coil)
│   └── proguard-rules.pro
├── gradle/
│   ├── libs.versions.toml          # Centralized dependency catalog
│   └── wrapper/
│       ├── gradle-wrapper.jar      # Gradle Wrapper JAR
│       └── gradle-wrapper.properties
├── .env.example
├── build.gradle.kts                # Project-level Gradle build file
├── gradlew                         # Linux/macOS Gradle executable
├── gradlew.bat                     # Windows Gradle executable
├── settings.gradle.kts             # Project settings (ND Group)
└── metadata.json
```

---

## 🚀 GitHub Actions द्वारे Automatic APK कसा मिळवायचा?

1. हा कोड तुमच्या **GitHub Repository** वर Push करा:
   ```bash
   git add .
   git commit -m "Add ND Group Android App and GitHub Actions workflow"
   git push origin main
   ```
2. GitHub वर तुमच्या repository च्या **"Actions"** टॅब मध्ये जा.
3. तिथे **"Build ND Group Android APK"** हा workflow आपोआप सुरू होईल.
4. बिल्ड पूर्ण झाल्यावर **"Artifacts"** सेक्शन मधून `ndgroup-debug-apk.zip` डाउनलोड करा.
5. झिप फाईल Unzip करून तुमच्या मोबाईलवर APK Install करा!

---

## 💻 Android Studio मध्ये कसे चालवायचे (How to run locally)

1. **Android Studio** (Ladybug किंवा त्यापुढील आवृत्ती) उघडा.
2. **File -> Open** वर क्लिक करून हा फोल्डर निवडा.
3. Gradle Sync पूर्ण होण्याची वाट पहा.
4. **Build -> Build Bundle(s) / APK(s) -> Build APK(s)** निवडून मॅन्युअल APK तयार करा.
5. किंवा **Run (Shift + F10)** दाबून Emulator किंवा खऱ्या मोबाईलवर ऍप चालू करा.

---

## 🔑 मुख्य फिचर्स आणि Admin लॉगिन (Key Features)

1. **Admin Dashboard (admin@ndgroup.com)**:
   - फक्त `admin@ndgroup.com` या खात्याला ॲडमिन डॅशबोर्डचा ऍक्सेस आहे.
   - **Customer Care Number**: थेट ॲपमधून सपोर्ट नंबर अपडेट करा.
   - **Product Prices**: बेस प्राईस बदलल्यावर 250g, 500g, 1kg, 2kg चे दर आपोआप बदलतात.
   - **Promotional Ad Video**: होम स्क्रीनवरील जाहिरात व्हिडिओ चालू/बंद (Toggle) करा.
   - **Approve Withdrawals**: ग्राहकांच्या बँक खात्यात पॉईंट्स विथड्रॉ करण्यासाठी एका क्लिकवर "Approve" करा.
2. **Dynamic Weight Dropdown**:
   - ग्राहक 250g, 500g, 1kg इत्यादी वजन निवडू शकतात. Multiplier मुळे प्राईस लगेच कॅल्क्युलेट होते.
3. **Wallet System (1 Point = ₹1 Rupee)**:
   - ग्राहक बँकेचे डिटेल्स (Bank Name, A/C No, IFSC, Name) भरून विथड्रॉवल रिक्वेस्ट पाठवू शकतात.
