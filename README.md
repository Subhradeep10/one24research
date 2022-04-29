

->To get device location i used location package we can even get lat and long even when app is running in background
  but with some limitations.

-> Add this to your package's pubspec.yaml file:
    dependencies:
      location: ^4.2.0

-> Android configuration ::
       To use location background mode on Android, you have to use the enableBackgroundMode({bool enable}) API 
       before accessing location in the background and adding necessary permissions. You should place the required permissions in your applications
  <uses-permission android:name="android.permission.FOREGROUND_SERVICE" />
  <uses-permission android:name="android.permission.ACCESS_BACKGROUND_LOCATION"/>


   Remember that the user has to accept the location permission to always allow to use the background location. The Android 11 option to always allow 
    is not presented on the location permission dialog prompt. The user has to enable it manually from the app settings. This should be explained to the user on a separate UI that redirects the user to the app's location settings managed by the operating system. More on that topic can be found on 
    Android developer page(https://developer.android.com/training/location/permissions#request-background-location).
-> IOS configuration::
   you have to add this permission in Info.plist :
   // This is probably the only one you need. Background location is supported
   // by this -- the caveat is that a blue badge is shown in the status bar
   // when the app is using location service while in the background.
   NSLocationWhenInUseUsageDescription

   // Deprecated, use NSLocationAlwaysAndWhenInUseUsageDescription instead.
   NSLocationAlwaysUsageDescription

  // Use this very carefully. This key is required only if your iOS app
  // uses APIs that access the user’s location information at all times,
  // even if the app isn't running.
  NSLocationAlwaysAndWhenInUseUsageDescription
  
->To receive location when application is in background you have to enable it:
     location.enableBackgroundMode(enable: true)