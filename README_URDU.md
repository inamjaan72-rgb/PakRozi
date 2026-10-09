# Pak Rozi — Flutter/Firebase starter

یہ ایک ابتدائی source project ہے، تیار شدہ APK نہیں۔ Firebase project config کے بغیر یہ چل نہیں سکے گا، اور اس starter میں خودکار ترجمہ، نجی chats، voice/video calls یا production-grade security ابھی شامل نہیں۔

## Windows پر استعمال
1. Flutter SDK اور Android Studio انسٹال کریں:
   https://docs.flutter.dev/get-started/install/windows/mobile
2. PowerShell میں:
   ```powershell
   flutter create pak_rozi
   cd pak_rozi
   flutter pub add firebase_core firebase_auth cloud_firestore
   ```
3. اس archive کی `lib/main.dart` کو نئے پروجیکٹ کی `lib/main.dart` سے بدلیں۔
4. Firebase Console میں Android app بنائیں، Email/Password Authentication اور Firestore فعال کریں۔
5. Firebase CLI اور FlutterFire CLI انسٹال کریں:
   ```powershell
   npm install -g firebase-tools
   firebase login
   dart pub global activate flutterfire_cli
   flutterfire configure
   ```
   اس سے `lib/firebase_options.dart` بننی چاہیے۔
6. Firebase Console > Firestore > Rules میں `firestore/firestore.rules` کے قواعد لگائیں۔ یہ صرف demo shared chat کے لیے ہیں، production private messaging کے لیے نہیں۔
7. فون USB debugging کے ساتھ جوڑیں اور چلائیں:
   ```powershell
   flutter pub get
   flutter devices
   flutter run
   ```

## APK بنانے کے لیے
Firebase configuration مکمل اور ٹیسٹ ہونے کے بعد:
```powershell
flutter build apk --release
```
APK عام طور پر `build\app\outputs\flutter-apk\app-release.apk` میں ہوگا۔

## اہم حدود
- موجودہ کوڈ صرف مشترکہ demo chat ہے، نجی one-to-one messaging نہیں۔
- خودکار ترجمہ ابھی implement نہیں کیا گیا۔
- اسے عوامی طور پر لانچ کرنے سے پہلے participant-based Firestore rules، abuse controls، privacy policy، account deletion اور translation backend درکار ہیں۔
