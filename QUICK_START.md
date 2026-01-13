# ⚡ Quick Start Guide - Treasure Hunt 2.0

## 🚀 5-Minute Setup

### Step 1: Get API Key (2 minutes)
1. Go to https://makersuite.google.com/app/apikey
2. Click "Create API Key"
3. Copy the key

### Step 2: Configure App (1 minute)
1. Open `lib/main.dart`
2. Find line: `const String _apiKey = "";`
3. Paste your key: `const String _apiKey = "your-key-here";`

### Step 3: Install & Run (2 minutes)
```bash
flutter pub get
flutter run
```

## 🎮 First Use

1. **Launch** → Answer 5 archetype questions
2. **Dashboard** → See your week & quick actions
3. **Chat** → Click 🎤 to speak, 📹 for video
4. **Missions** → Complete weekly challenges
5. **Journal** → Write reflections (AI can help refine)

## 📱 Platform-Specific Quick Setup

### Android (Easiest)
```bash
flutter run -d emulator-5554
# Permissions auto-request on first feature use
```

### iOS (Physical device recommended)
```bash
flutter run -d <device-id>
# Will ask permissions when needed
```

## 🔧 Troubleshooting

| Issue | Fix |
|-------|-----|
| **Camera not working** | Check: Settings → Treasure Hunt → Camera: ON |
| **Microphone no sound** | Verify: Settings → Treasure Hunt → Microphone: ON |
| **"No API key" error** | Add key to line 35 in `lib/main.dart` |
| **App won't start** | Run: `flutter clean && flutter pub get` |
| **Building takes forever** | First build is slow. Be patient! |

## 📍 Feature Locations

```
🏠 DASHBOARD
  ├─ Week indicator
  ├─ Quick Actions (Sessions, Change Track, Study, Anchors)
  └─ Current Archetype Card

🗺️ JOURNEY
  ├─ 8 weeks of missions
  ├─ Locked missions until you progress
  ├─ Timer missions
  └─ Reflection form missions

💬 CHAT (AI Guide)
  ├─ Text input
  ├─ 🎤 Voice dictation (Portuguese)
  ├─ 📹 Video call preview
  └─ AI responses with TTS

✨ RESONANCE
  ├─ 📸 Take selfie
  ├─ AI analyzes your expression
  └─ Archetype correlation

📖 JOURNAL
  ├─ Free writing
  ├─ ✨ AI text refinement
  └─ Auto-saves locally
```

## 💡 Pro Tips

1. **Voice Input**: Hold microphone button, speak in Portuguese
2. **Video Calls**: Shows your face in small preview (bottom-right)
3. **Missions**: Can't complete a week until previous is done
4. **Journal**: Click ✨ icon to have AI improve your writing
5. **Offline**: Limited; journal & settings work, chat needs internet

## 📊 File Structure

```
treasure_hunt/
├─ lib/main.dart                    ← ALL CODE HERE (production version)
├─ lib/main_old.dart               ← Original backup
├─ pubspec.yaml                    ← Dependencies (UPDATED)
├─ PRODUCTION_SETUP.md             ← Full docs
├─ ANDROID_SETUP.md                ← Android permissions
├─ IOS_SETUP.md                    ← iOS permissions
└─ DEPLOYMENT_CHECKLIST.md         ← Pre-launch checklist
```

## 🔐 Security Checklist

- ✅ API key in local file only (use env vars for production)
- ✅ No sensitive data logged
- ✅ Permissions requested at runtime
- ✅ Journal stored locally only
- ✅ Audio/video NOT saved

## 🎯 What's Included

✅ 8-week journey system  
✅ 3 tracks (Fundamentos, Relacionamentos, Profissional)  
✅ 24 total missions (8 per track)  
✅ Real camera + microphone  
✅ Text-to-speech in Portuguese  
✅ Speech-to-text dictation  
✅ AI-powered face analysis  
✅ Local journal with refinement  
✅ Persistent user data  

## ❌ What's NOT Included

❌ Push notifications (add Firebase if needed)  
❌ Cloud backup (local storage only)  
❌ Multi-language (Portuguese only)  
❌ Video storage (real-time preview only)  
❌ Social features (individual app)  

## 🆘 Help

```bash
# See all available commands
flutter --help

# Run tests
flutter test

# Check app health
flutter doctor

# Profile performance
flutter run --profile
```

## 🎬 Next Steps After Setup

1. **Customize AI prompt** in `_systemPrompt` variable
2. **Add your missions** by editing `allMissionsData` map
3. **Change language** from pt-PT to your language in `_initTTS()`
4. **Deploy** following DEPLOYMENT_CHECKLIST.md

## 📈 Analytics Recommendation

Add Google Analytics or Firebase (optional):
```dart
// In pubspec.yaml:
// firebase_analytics: ^10.0.0
// firebase_core: ^2.0.0
```

---

**Ready to launch?** Check `DEPLOYMENT_CHECKLIST.md` before going live!

**Questions?** See `PRODUCTION_SETUP.md` for detailed docs.

**Version**: 2.0 Production  
**Status**: ✅ Ready to Deploy  
**Last Update**: January 2026
