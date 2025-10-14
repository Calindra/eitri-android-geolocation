# eitri-android-geolocation

Geolocation module for the [`Eitri Android framework`](https://github.com/Calindra/eitri-android). This module provides a standardized interface for handling geolocation permissions and retrieving the device's location, integrating seamlessly with the Eitri runtime.

## Requirements

- Android 5.0 (API level 21) or later
- Google Play Services available on the target device

## Instalation

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

## Core Concepts

- `GeolocationModule`: The entry point for the module, implementing the `EitriModule` protocol. It registers the available geolocation methods with the Eitri runtime.

### Methods

The module exposes its functionality under the `geolocation` namespace.
Examples of what methods are avaliable and how they can be used can be consulted on the [`Eitri Bifrost documentation page`](https://cdn.83io.com.br/library/eitri-bifrost/doc/latest/classes/_internal_.Geolocation.html)
