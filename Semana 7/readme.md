## Dependencias necesarias

```
implementation 'androidx.lifecycle:lifecycle-runtime-ktx:2.5.1'
implementation 'androidx.lifecycle:lifecycle-viewmodel-ktx:2.5.1'
implementation 'androidx.lifecycle:lifecycle-livedata-ktx:2.5.1'
implementation 'androidx.fragment:fragment-ktx:1.5.2'
implementation 'com.google.code.gson:gson:2.9.0'
```

## Permisos necesarios
```
<uses-permission android:name="android.permission.INTERNET"/>
```

## Ejemplo de una corutina
```
 lifecycleScope.launch(Dispatchers.IO) {
            val url = URL("https://www.google.com")
            val client = url.openConnection() as HttpsURLConnection
            client.requestMethod = "GET"
            val response = client.inputStream.bufferedReader().readText()
            withContext(Dispatchers.Main){
                Toast.makeText(this@MainActivity, response, Toast.LENGTH_LONG).show()
            }
 }
 ```
