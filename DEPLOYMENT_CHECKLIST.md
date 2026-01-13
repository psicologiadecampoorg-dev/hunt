# 📋 Production Deployment Checklist

## Pre-Launch Verification

### 1. Configuration ✅
- [ ] Add Gemini API Key to `lib/main.dart`
- [ ] Update app name in `pubspec.yaml` if needed
- [ ] Update version number (currently: 1.0.0+1)

### 2. Dependencies ✅
- [ ] Run `flutter pub get`
- [ ] Verify all packages installed: `flutter pub list`
- [ ] Check for dependency conflicts: `flutter pub outdated`

### 3. Platform Setup

#### Android
- [ ] Add permissions to `android/app/src/main/AndroidManifest.xml`
- [ ] Update `android/build.gradle` (minSdkVersion ≥ 21 recommended)
- [ ] Test on Android device/emulator

#### iOS
- [ ] Add keys to `ios/Runner/Info.plist`
- [ ] Run `cd ios && pod install`
- [ ] Test on physical iOS device (camera needs real device)

### 4. Testing Checklist

#### Core Features
- [ ] App launches without crashes
- [ ] Archetype quiz completes and saves selection
- [ ] Dashboard displays correctly
- [ ] Navigation between tabs works

#### Chat/AI
- [ ] Gemini API responds to messages
- [ ] Text-to-speech works (Portuguese)
- [ ] Microphone input activates

#### Camera Features
- [ ] Camera permission request appears
- [ ] Video call screen shows camera preview
- [ ] Face analysis feature captures photos

#### Storage
- [ ] User data persists after app restart
- [ ] Journal entries save correctly
- [ ] Mission progress is retained

#### Missions
- [ ] Timer-based missions count down correctly
- [ ] Form missions save reflection data
- [ ] Week advancement works

### 5. Performance & Security
- [ ] No obvious memory leaks (monitor 5+ minutes)
- [ ] API key is NOT hardcoded (use environment variables in production)
- [ ] No console errors or warnings
- [ ] Response times acceptable (<2s for API calls)

### 6. UI/UX
- [ ] All text displays correctly (Portuguese)
- [ ] Images load from URLs
- [ ] Bottom navigation is responsive
- [ ] Back button works on all screens

### 7. Error Handling
- [ ] App handles network disconnect gracefully
- [ ] Missing API key shows error (not crash)
- [ ] Denied permissions don't crash app
- [ ] Invalid inputs are handled

### 8. Documentation
- [ ] PRODUCTION_SETUP.md is complete
- [ ] ANDROID_SETUP.md added to repo
- [ ] IOS_SETUP.md added to repo
- [ ] README.md mentions production setup

## Deployment Steps

### iOS App Store
```bash
# 1. Update version in pubspec.yaml
# 2. Build for release
flutter build ios --release

# 3. In Xcode:
# - Product → Scheme → Runner (Release)
# - Product → Archive
# - Distribute App → App Store Connect
# - Follow Xcode's prompts
```

### Android Play Store
```bash
# 1. Generate keystore (first time only)
keytool -genkey -v -keystore ~/key.jks -keyalg RSA -keysize 2048 -validity 10000

# 2. Create/update android/key.properties
storeFile=~/key.jks
storePassword=your_password
keyPassword=your_password
keyAlias=key

# 3. Build release APK
flutter build apk --release

# 4. Build app bundle for Play Store
flutter build appbundle --release

# 5. Upload to Play Store Console
```

## Post-Launch Monitoring

- [ ] Monitor crash reports (Firebase Crashlytics recommended)
- [ ] Track user retention metrics
- [ ] Collect feedback from beta users
- [ ] Monitor API usage (Gemini quota)
- [ ] Check device compatibility reports

## Known Limitations

1. **Speech-to-Text**: Currently Portuguese only (pt-PT)
2. **Camera**: Requires real device on iOS
3. **Background Execution**: TTS/STT don't work in background
4. **Storage**: Uses local SharedPreferences (consider cloud sync later)

## Future Enhancements

- [ ] Cloud backup of journal entries
- [ ] Multi-language support
- [ ] Push notifications for missions
- [ ] Analytics dashboard
- [ ] Social sharing features
- [ ] Video tutorials integration
- [ ] Offline mode

## Quick Fixes

If issues arise:

```bash
# Nuclear option - reset everything
flutter clean
rm -rf ios/Pods ios/Podfile.lock
flutter pub cache clean
flutter pub get
cd ios && pod install && cd ..
flutter run
```

## Support Resources

- Issues with camera: Check Info.plist/AndroidManifest.xml permissions
- API errors: Verify API key in main.dart
- Build failures: Run `flutter doctor` and resolve issues
- Performance: Profile with DevTools: `flutter run --profile`

---

**Last Updated**: January 2026  
**Status**: Ready for Production  
**Next Review**: After first 100 users
