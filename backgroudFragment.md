# Como cambiar el color de fondo de un fragment
1. Selecciona el archivo `.xml` del fragmento deseado, en este caso:
```xml
<?xml version="1.0" encoding="utf-8"?>
<FrameLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:background="@color/gris"
    tools:context=".cuarto_fragmento">

    <!-- TODO: Update blank fragment layout -->
    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="@string/saludo_cuarto_fragmento"
        android:textSize="20sp"
        android:textColor="@color/white"
        android:textStyle="bold"
        android:layout_gravity="center"

        />

</FrameLayout>
```
2. `android:background:` es quien define el color del background del fragmento