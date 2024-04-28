# Configuración de Aplicaciones con AndroidX Preference

La configuración permite que los usuarios cambien la funcionalidad y el comportamiento de una app. Pueden afectar el comportamiento en segundo plano, como la frecuencia con la que la app sincroniza datos con la nube, o pueden ser de mayor alcance, como cambiar el contenido y la presentación de la interfaz de usuario.

Un `Preference` es el componente básico básico de la biblioteca de Preference. Una pantalla de configuración contiene una jerarquía de Preference.

### Como incluir preferences en el app
```groovy
dependencies {
    implementation "androidx.preference:preference-ktx:1.2.0"
}
```

### Cómo crear una jerarquía

En tu proyecto, navega a la carpeta `res/xml`, crea un archivo `preferences.xml` y agrégale el siguiente código:

```xml
<PreferenceScreen
    xmlns:app="http://schemas.android.com/apk/res-auto">

    <SwitchPreferenceCompat
        app:key="notifications"
        app:title="Enable message notifications"/>

    <Preference
        app:key="feedback"
        app:title="Send feedback"
        app:summary="Report technical issues or suggest new features"/>

</PreferenceScreen>
```

**_NOTE:_** `SwitchPreferenceCompat` que permite a los usuarios activar y desactivar una configuración, y un Preference básico sin widgets.

**_NOTE:_** Cuando se compila una jerarquía, cada `Preference` debe tener una clave única.

**_NOTE:_** Para aumentar una jerarquía a partir de un atributo XML, crea un `PreferenceFragmentCompat`

**_NOTE:_** `PreferenceFragmentCompat` oculta gran parte de la maquinaria necesaria para guardar y leer las preferencias.  todo se almacena con `SharedPreferences`