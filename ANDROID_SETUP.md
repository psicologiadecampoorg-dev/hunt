# Android Permissions Setup

## Required Permissions for `android/app/src/main/AndroidManifest.xml`

Add these permissions inside the `<manifest>` tag (before the `<application>` tag):

```xml
<!-- Camera for video calls and face analysis -->
<uses-permission android:name="android.permission.CAMERA" />

<!-- Microphone for voice input and dictation -->
<uses-permission android:name="android.permission.RECORD_AUDIO" />

<!-- Internet for API calls -->
<uses-permission android:name="android.permission.INTERNET" />

<!-- Storage (if saving files) -->
<uses-permission android:name="android.permission.READ_EXTERNAL_STORAGE" />
<uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE" />
```

## Runtime Permission Handling

The `permission_handler` package is included and will request permissions at runtime when needed.

## Testing

To verify permissions are working:

```bash
adb shell am start -n com.uview360.treasure_hunt/.MainActivity
adb logcat | grep PERMISSION
```

## Troubleshooting

- If permissions dialog doesn't appear, rebuild: `flutter clean && flutter pub get && flutter run`
- Check device Settings → Apps → Treasure Hunt → Permissions
- Grant Camera and Microphone permissions
