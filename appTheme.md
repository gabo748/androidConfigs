# Como cambiar el color de fondo del app.
Seleccionar el paquete `themes` 


```xml
<resources xmlns:tools="http://schemas.android.com/tools">
    <!-- Base application theme. -->
    <style name="Base.Theme.Camposlopez" parent="Theme.Material3.DayNight.NoActionBar">
        <item name="android:windowBackground">@color/amarillo</item>
    </style>

    <style name="Theme.Camposlopez" parent="Base.Theme.Camposlopez" />
</resources>
```
- `android:windowBackground`: Este elemento definira el color de fondo
