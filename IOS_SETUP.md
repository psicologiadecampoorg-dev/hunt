# iOS Permissions Setup

## Required Keys for `ios/Runner/Info.plist`

Add these keys to enable camera, microphone, and speech recognition:

```xml
<!-- Camera Usage -->
<key>NSCameraUsageDescription</key>
<string>We need access to your camera for video calls and to analyze your facial expressions in the Ressonância feature.</string>

<!-- Microphone Usage -->
<key>NSMicrophoneUsageDescription</key>
<string>We need access to your microphone for voice dictation and real-time AI conversations.</string>

<!-- Speech Recognition -->
<key>NSSpeechRecognitionUsageDescription</key>
<string>We need speech recognition to convert your voice to text for hands-free interaction with your guide.</string>

<!-- Photo Library (optional, for image picker) -->
<key>NSPhotoLibraryUsageDescription</key>
<string>We need access to your photos for the Ressonância feature to analyze images.</string>
```

## Implementation Steps

1. Open `ios/Runner.xcworkspace` in Xcode
2. Select Runner → Info
3. Look for "Custom iOS Target Properties" or scroll to find the keys
4. Add the above permissions using the Xcode UI, or edit the XML directly

### Alternative: Direct XML Edit

If editing `ios/Runner/Info.plist` directly as XML:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
<dict>
    <!-- ... existing keys ... -->
    
    <key>NSCameraUsageDescription</key>
    <string>We need access to your camera for video calls and facial analysis.</string>
    
    <key>NSMicrophoneUsageDescription</key>
    <string>We need access to your microphone for voice interaction.</string>
    
    <key>NSSpeechRecognitionUsageDescription</key>
    <string>We need speech recognition for voice-to-text conversion.</string>
    
    <!-- ... rest of config ... -->
</dict>
</plist>
```

## Building for iOS

After adding permissions:

```bash
cd ios
pod install
cd ..
flutter clean
flutter pub get
flutter run
```

## Testing on Device

1. Build and run on physical device (simulator permissions are limited)
2. Go to Settings → [App Name] → Permissions
3. Toggle Camera, Microphone, and Speech Recognition ON

## Troubleshooting

- **Permission dialog doesn't appear**: Ensure you rebuilt after changing Info.plist
- **Runtime crash**: Check Xcode console for permission-related errors
- **Camera/Mic not working**: Verify Info.plist changes were saved and app was rebuilt
