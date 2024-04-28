# Como crear un menu.
Seleccionar el paquete res y hacer lo siguiente: 
```sh
Click derecho -> new -> android resource file -> Resource type -> menu
```

## Ejemplo de menu basico:
```xml
<?xml version="1.0" encoding="utf-8"?>
<menu xmlns:android="http://schemas.android.com/apk/res/android">

    <item
        android:id="@+id/fragmento1"
        android:title="@string/item_primer_fragmento"/>

    <item
        android:id="@+id/fragmento2"
        android:title="@string/item_segundo_fragmento"/>

    <item
        android:id="@+id/fragmento3"
        android:title="@string/item_tercer_fragmento"/>
        
    <item
        android:id="@+id/fragmento4"
        android:title="@string/item_cuarto_fragmento"/>
</menu>
```