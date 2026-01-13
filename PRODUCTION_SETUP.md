# 🚀 Treasure Hunt 2.0 - Production Setup Guide

## Overview
This is the **production-ready version** of Treasure Hunt with native Flutter features for camera, audio, and AI integration.

## 🔧 Prerequisites

### 1. **API Key Configuration**
- Get your **Gemini API Key** from [Google AI Studio](https://makersuite.google.com/app/apikey)
- Open `lib/main.dart` and replace the empty string in:
  ```dart
  const String _apiKey = ""; // Insert your Gemini API key here
  ```

### 2. **Install Dependencies**
```bash
flutter pub get
```

## 📱 Platform-Specific Setup

### **Android Setup** (`android/app/AndroidManifest.xml`)
Add these permissions:
```xml
<uses-permission android:name="android.permission.CAMERA" />
<uses-permission android:name="android.permission.RECORD_AUDIO" />
<uses-permission android:name="android.permission.INTERNET" />
```

### **iOS Setup** (`ios/Runner/Info.plist`)
Add these keys:
```xml
<key>NSCameraUsageDescription</key>
<string>We need camera access for video calls and face analysis.</string>
<key>NSMicrophoneUsageDescription</key>
<string>We need microphone access for voice dictation and audio.</string>
<key>NSSpeechRecognitionUsageDescription</key>
<string>We need speech recognition for voice commands.</string>
```

## 🎯 Key Features

### 1. **Chat with Voice & Video**
- ✅ Real-time text-to-speech (Portuguese)
- ✅ Speech-to-text dictation
- ✅ Video preview with front camera
- ✅ Multi-turn conversation with Gemini

### 2. **Mission System**
- ✅ 8-week journey with 3 tracks: Fundamentos, Relacionamentos, Profissional
- ✅ Timer-based missions (e.g., 5-min meditation)
- ✅ Reflection forms with journaling
- ✅ Progress tracking

### 3. **Resonance Tab**
- ✅ Face analysis with camera
- ✅ AI-powered insights on expressions
- ✅ Archetype correlation

### 4. **Journal Tab**
- ✅ Free-form writing
- ✅ AI-powered text refinement ("Editor Literário")
- ✅ Auto-save to local storage

### 5. **State Management**
- ✅ Provider for reactive UI
- ✅ SharedPreferences for persistence
- ✅ User profile with archetype selection

## 🎮 Usage Flow

1. **Launch App** → Archetype Quiz (5 questions)
2. **Dashboard** → View current week, quick actions
3. **Jornada (Journey)** → Expand missions, complete challenges
4. **Guia (Chat)** → Talk with AI, use mic icon for dictation
5. **Ressonância** → Take selfies, analyze expressions
6. **Diário (Journal)** → Write and improve entries

## 📝 Project Structure

```
lib/
├── main.dart                 # Main app entry, all widgets in one file
├── dashboard_screen.dart     # (old - can be deleted)
├── glass_theme.dart          # (old - can be deleted)
└── ...

pubspec.yaml                  # Dependencies
```

## 🔐 Important Notes

### API Keys
- **Never commit** your API key to version control
- Use `.env` files or environment variables in production
- Consider using Firebase Remote Config for key rotation

### Permissions
- Request permissions at runtime (permission_handler is included)
- Users can deny access; handle gracefully

### Privacy
- Audio/video data is NOT saved by default
- Journal entries are stored locally (SharedPreferences)
- Messages are sent to Google Gemini servers

## 🛠️ Troubleshooting

### Camera not working
```bash
flutter clean
flutter pub get
flutter run
```

### Microphone not recognized
- Check permissions in device settings
- Ensure `speech_to_text` package is initialized

### TTS (Text-to-Speech) not working
- Verify language is set to "pt-PT" (Portuguese - Portugal)
- Check device TTS engine in system settings

### Build errors
```bash
flutter pub cache clean
flutter pub get
flutter clean
flutter pub get
```

## 📊 Data Flow

```
User Input (Text/Voice/Image)
    ↓
AppState (Provider)
    ↓
Gemini API
    ↓
Response Processing
    ↓
UI Update (Chat bubbles, etc.)
    ↓
LocalStorage (SharedPreferences)
```

## 🚀 Deployment

### iOS
```bash
flutter build ios --release
# Follow Xcode instructions for App Store submission
```

### Android
```bash
flutter build apk --release
flutter build appbundle --release
# Upload to Play Store
```

## 📚 API Reference

### `AppState` (Main State Class)
```dart
// Send message to AI
context.read<AppState>().sendMessage("Your message");

// Text-to-Speech
context.read<AppState>().speak("Text to speak");

// Analyze input with image
await context.read<AppState>().analyzeInput(
  "Analyze this", 
  "Analyst persona",
  imageBytes  // optional
);

// Set archetype (from quiz)
context.read<AppState>().setArchetype("Dom", "Tesouro");

// Advance week
context.read<AppState>().advanceWeek();
```

## 🎨 Customization

### Change Language
In `_initTTS()`:
```dart
await _flutterTts.setLanguage("en-US");  // or your language code
```

### Modify System Prompt
Edit `_systemPrompt` constant to change AI behavior

### Add New Missions
Edit `allMissionsData` map in `main.dart`

## 📞 Support & Resources

- [Flutter Docs](https://flutter.dev/docs)
- [Google Generative AI](https://ai.google.dev/)
- [Camera Plugin](https://pub.dev/packages/camera)
- [Speech-to-Text](https://pub.dev/packages/speech_to_text)

---

**Version**: 2.0 Production  
**Last Updated**: January 2026  
**Status**: ✅ Ready for deployment
