## Dependencias

### Paso 1: Las dependencias
```
implementation 'androidx.lifecycle:lifecycle-runtime-ktx:2.5.1'
implementation 'androidx.lifecycle:lifecycle-viewmodel-ktx:2.5.1'
implementation 'androidx.lifecycle:lifecycle-livedata-ktx:2.5.1'
implementation 'androidx.fragment:fragment-ktx:1.5.2'
implementation 'com.google.code.gson:gson:2.9.0'
implementation "org.jetbrains.kotlinx:kotlinx-coroutines-play-services:1.6.4"
```
Esta dependencia nos permite usar awaits para las operaciones de Google Play y Firebase

### Paso2: Activar los bindings
```
android{
...
    viewBinding{
        enabled = true
    }
...
}
```
