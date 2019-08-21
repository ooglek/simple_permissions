# Simple Permissions

**IMPORTANT: This is based on the Simple Permissions plugin from Ethras ([https://pub.dartlang.org/packages/simple_permissions](https://pub.dartlang.org/packages/simple_permissions)). The plugin repository has since been deleted, so commit history cannot be retained.**

**This is a maintained fork from [tamcy/simple_permissions](https://github.com/tamcy/simple_permissions)**

A flutter plugin for checking and requesting permissions on iOs and Android.

## Installation

This plugin is currently not published to [pub.dev](https://pub.dev).

To install add the path to the git repo to your pubspec.yaml:

```yaml
dependencies:
  simple_permissions:
    git:
      url: https://github.com/tq-systems/simple_permissions.git
```

## Getting Started

Make sure you add the needed permissions to your Android Manifest  [Permission](https://developer.android.com/reference/android/Manifest.permission.html)
and Info.plist.

```xml
<uses-permission android:name="android.permission.RECORD_AUDIO" />
<uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE" />
```

## API
### List of currently available permissions

```dart
enum Permission {
  // Microphone
  RecordAudio,

  // Camera
  Camera,

  // Read External Storage (Android)
  ReadExternalStorage

  // Write External Storage (Android)
  WriteExternalStorage,

  // Access Coarse Location (Android) / When In Use iOS
  AccessCoarseLocation,

  // Access Fine Location (Android) / When In Use iOS
  AccessFineLocation,

  // Access Fine Location (Android) / When In Use iOS
  WhenInUseLocation,

  // Access Fine Location (Android) / Always Location iOS
  AlwaysLocation

  // Write contacts (Android) / Contacts iOS
  WriteContacts

  // Read contacts (Android) / Contacts iOS
  ReadContacts
}
```

```dart
/// Permissions status enum (iOS)
enum PermissionStatus { notDetermined, restricted, denied, authorized }
```

### Methods
```dart
  /// Check a [permission] and return a [Future] with the result
  static Future<bool> checkPermission(Permission permission);

  /// Request a [permission] and return a [Future] with the result
  static Future<PermissionStatus> requestPermission(Permission permission);

  /// Open app settings on Android and iOS
  static Future<bool> openSettings();
  
  /// Get iOs permission status 
  static Future<PermissionStatus> getPermissionStatus(Permission permission)
```
