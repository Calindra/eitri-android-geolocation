# eitri-android-geolocation

Geolocation module for the [`Eitri Android framework`](https://github.com/Calindra/eitri-android). This module provides a standardized interface for handling geolocation permissions and retrieving the device's location, integrating seamlessly with the Eitri runtime.

## Requirements

- Android 5.0 (API level 21) or later
- Google Play Services available on the target device

## Installation

The `eitri-android-geolocation` artifact is available on Maven Central.

### Gradle Kotlin DSL (`build.gradle.kts`)

```kotlin
dependencies {
    implementation("tech.eitri:eitri-android-geolocation:$version")
}
```

Make sure to replace `$version` or `${version}` with the desired version of the module. You can find the latest version on [Maven Central](https://central.sonatype.com/artifact/tech.eitri/eitri-android-geolocation).

## Registering geolocation module

```kotlin
    import tech.eitri.android.geolocation.GeolocationModule
    
    // [...]

    val machineContext = EitriMachineInstanceManager.start()
    val mainEitriMachine = machineContext.mainMachine

    // configure eitri-machine [...]

    // register modules
    mainEitriMachine.modules.register(GeolocationModule())
```

## Background Location Permission (Optional)

If your app needs to access location when running in the background, you must add the background location permission to your app's `AndroidManifest.xml`:

```xml
<manifest xmlns:android="http://schemas.android.com/apk/res/android">
    <!-- Other permissions -->

    <!-- Required only if using upgradeToBackgroundPermission() method -->
    <uses-permission android:name="android.permission.ACCESS_BACKGROUND_LOCATION" />

    <!-- Application configuration -->
</manifest>
```

**Important Notes:**
- This permission is **only required** if you use the `upgradeToBackgroundPermission()` method from Bifrost
- Only available on Android 10 (API 29) and later
- On Android 10+, background location requires a separate permission request after foreground location permission is granted
- The module does not include this permission by default to avoid unnecessary permission declarations

## Core Concepts

- `GeolocationModule`: The entry point for the module, implementing the `EitriModule` protocol. It registers the available geolocation methods with the Eitri runtime.

### Methods

The module exposes its functionality under the `geolocation` namespace.
Examples of what methods are avaliable and how they can be used can be consulted on the [`Eitri Bifrost documentation page`](https://cdn.83io.com.br/library/eitri-bifrost/doc/latest/classes/_internal_.Geolocation.html)
