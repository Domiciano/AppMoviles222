# Configurar servicio de mensajería

## Dependencias

Para esta sección necesita las dependencias de mensajería
```
implementation 'com.google.firebase:firebase-messaging-ktx:23.0.4'
```

## Cree una clase de servicio
```
class FCMService : FirebaseMessagingService() {

    override fun onMessageReceived(message: RemoteMessage) {
        ...
    }
}
```

## Registre el servicio en el manifest
```
<application>
    ...
    <service
        android:name=".services.FCMService"
        android:exported="false">
        <intent-filter>
            <action android:name="com.google.firebase.MESSAGING_EVENT"/>
        </intent-filter>
    </service>
    ...
</application>
```


## Ahora puede suscribirse
```
Firebase.messaging.subscribeToTopic("noti").addOnSuccessListener {
    Log.e(">>>","Suscrito")
}
```

## Notificaciones
Para obtener JSON del mensaje recibido
```
val obj = JSONObject(message.data as Map<*, *>)
val json = obj.toString()
```

## Crear notificaciones UI
Generar notificaciones visualmente
```
import android.app.Notification
import android.app.NotificationChannel
import android.app.NotificationManager
import android.app.PendingIntent
import android.content.Context
import android.content.Intent
import android.os.Build
import androidx.core.app.NotificationCompat
import edu.co.icesi.claseauth.ProfileActivity
import edu.co.icesi.claseauth.R

object NotificationUtil {

    private val CHANNEL_ID = "messages";
    private val CHANNEL_NAME = "Messages";
    private var id = 0;

    fun showNotification(context: Context, title:String, message:String){
        val notificationManager = context.getSystemService(Context.NOTIFICATION_SERVICE) as NotificationManager
        if(Build.VERSION.SDK_INT >= Build.VERSION_CODES.O) {
            val channel = NotificationChannel(CHANNEL_ID, CHANNEL_NAME, NotificationManager.IMPORTANCE_HIGH)
            notificationManager.createNotificationChannel(channel)
        }
        val builder = NotificationCompat.Builder(context, CHANNEL_ID)
            .setDefaults(Notification.DEFAULT_ALL)
            .setContentText(message)
            .setContentTitle(title)
            .setSmallIcon(R.drawable.ic_launcher_foreground)
        val notification = builder.build()
        notificationManager.notify(id, notification)
        id++
    }

}
```

## Hacer el POST Request desde Android

```
    fun POSTtoFCM(json: String): String {
        val url = URL("https://fcm.googleapis.com/fcm/send")
        val client = url.openConnection() as HttpsURLConnection
        client.requestMethod = "POST"
        client.setRequestProperty("Content-Type", "application/json")
        client.setRequestProperty("Authorization", "key=$FCM_KEY")
        client.doOutput = true
        client.outputStream.bufferedWriter().use {
            it.write(json)
            it.flush()
        }
        return client.inputStream.bufferedReader().readText()
    }
```


## Referencias
1. https://firebase.google.com/docs/cloud-messaging/fcm-architecture?hl=es-419
2. https://firebase.google.com/docs/cloud-messaging/migrate-v1?hl=es-419#java

