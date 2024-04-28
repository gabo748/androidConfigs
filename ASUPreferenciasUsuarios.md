# PREFERENCIAS DE USUARIOS.

Las aplicaciones de Android a menudo necesitan configuraciones que permitan a los usuarios modificar las preferencias en la aplicación.
Veamos en este tutorial cómo integrar el marco de preferencias de Android (`PreferenceActivity`)

El marco de preferencias viene con una clase de actividad `android.preference.PreferenceActivity` que debe anularse con nuestra propia clase. Cree una clase  `UserSettingsActivity` en el paquete  `net.viralpatel.android` donde se almacenan todas las actividades para esta aplicación.

```java
package net.viralpatel.android;

import android.os.Bundle;
import android.preference.PreferenceActivity;

public class UserSettingActivity extends PreferenceActivity {

	@Override
	public void onCreate(Bundle savedInstanceState) {
		super.onCreate(savedInstanceState);

		addPreferencesFromResource(R.xml.settings);

	}
}
```
- Agregamos preferencias a la aplicación usando el método `addPreferencesFromResource`. Especificamos una identificación de archivo xml con este método.

```xml
<?xml version="1.0" encoding="utf-8"?>
<PreferenceScreen xmlns:android="http://schemas.android.com/apk/res/android" >

    <PreferenceCategory android:title="@string/pref_user_profile" >
        <EditTextPreference 
            	android:title="@string/pref_user_name" 
            	android:summary="@string/pref_user_name_summary" 
            	android:key="prefUsername"/>
    </PreferenceCategory>
    
    <PreferenceCategory android:title="@string/pref_update_setting" >
        <CheckBoxPreference
            android:defaultValue="false"
            android:key="prefSendReport"
            android:summary="@string/pref_send_report_summary"
            android:title="@string/pref_send_report" >
        </CheckBoxPreference>

        <ListPreference
            android:key="prefSyncFrequency"
            android:entries="@array/syncFrequency"
            android:summary="@string/pref_sync_frequency_summary" 
            android:entryValues="@array/syncFrequencyValues"
            android:title="@string/pref_sync_frequency" />
    </PreferenceCategory>

</PreferenceScreen>
```

### La página de configuración tiene 3 componentes diferentes para especificar la configuración del usuario.

- `EditTextPreference` se utiliza para definir una propiedad de texto editable. En este ejemplo, el nombre de usuario es una propiedad editable.
- `CheckBoxPreference` le permite definir un valor booleano en la pantalla de preferencias. En este ejemplo, definimos una propiedad para verificar el clima y enviar un informe de fallas o no.
- `ListPreference` Como sugiere su nombre, permite al usuario seleccionar cualquier elemento de una lista determinada. En este ejemplo, dejamos que el usuario decida cuál debería ser la frecuencia de sincronización de datos.


La lista que definimos en el archivo de configuración de preferencias anterior se declarará como una matriz en `arrays.xml` en `res/values`.
```xml
<?xml version="1.0" encoding="utf-8"?>
<resources>
   <string-array name="syncFrequency">
      <item name="1">Once a day</item>
      <item name="7">Once a week</item>
      <item name="3">Once a year</item>
      <item name="0">Never (Update manually)</item>
   </string-array>
   <string-array name="syncFrequencyValues">
      <item name="1">1</item>
      <item name="7">7</item>
      <item name="30">30</item>
      <item name="0">0</item>
   </string-array>
</resources>
```

Además de `arrays.xml`, también necesitaremos algunos valores de cadena para nuestra aplicación. A continuación se muestra la lista de constantes de cadena que agregaremos en  `strings.xml`

```xml
<resources>
   <string name="app_name">Android_Preferences_example</string>
   <string name="hello_world">Hello world!</string>
   <string name="menu_settings">Settings</string>
   <string name="title_activity_main">MainActivity</string>

   <string name="pref_send_report">Send crash reports</string>
   <string name="pref_send_report_summary">Helps to fix bugs</string>
   <string name="pref_sync_frequency">Sync frequency</string>
   <string name="pref_sync_frequency_summary">Set the sync frequency</string>
   <string name="pref_user_name">Set username</string>
   <string name="pref_user_name_summary">Set your username</string>

   <string name="pref_user_profile">User Profile</string>
   <string name="pref_update_setting">Update Settings</string>
</resources>
```

Ahora hemos creado la configuración básica de Preferencias en nuestra aplicación. Ahora necesitamos integrarlo con nuestra `Activity`.


- Primero necesitamos crear un menú que se mostrará cuando el usuario haga clic en el botón de `menú`. Este `menú` tendrá solo un elemento de menú,  Configuración

```xml
<menu xmlns:android="http://schemas.android.com/apk/res/android" >

    <item
        android:id="@+id/menu_settings"
        ic_menu_preferences=""
        android:orderInCategory="100"
        android:showAsAction="never"
        android:title="@string/menu_settings"
        android:icon="@android:drawable/ic_menu_preferences"/>

</menu>
```

- Cree una nueva clase de Actividad  `MainActivity`

```java
public class MainActivity extends Activity {

    private static final int RESULT_SETTINGS = 1;

    @Override
    public void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        showUserSettings();
    }

    private void showUserSettings() {
        SharedPreferences sharedPrefs = PreferenceManager
            .getDefaultSharedPreferences(this);

        StringBuilder builder = new StringBuilder();

        builder.append("\n Username: " +
            sharedPrefs.getString("prefUsername", "NULL"));

        builder.append("\n Send report:" +
            sharedPrefs.getBoolean("prefSendReport", false));

        builder.append("\n Sync Frequency: " +
            sharedPrefs.getString("prefSyncFrequency", "NULL"));

        TextView settingsTextView = (TextView) findViewById(R.id.textUserSettings);

        settingsTextView.setText(builder.toString());
    }

}
```

En `MainActivity`,  `showUserSettings` el método recupera los valores almacenados en `Preferencia`s y los muestra en la pantalla. ejemplo:

```java
SharedPreferences sharedPrefs = PreferenceManager
                .getDefaultSharedPreferences(this);

sharedPrefs.getString("prefUsername", "NULL");
sharedPrefs.getBoolean("prefSendReport", false);
```