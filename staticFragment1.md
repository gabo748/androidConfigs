# XML FRAGMENTO 1 

- Este fragmento tienen un `EditText` que obtiene el valor que escribe el usuario, tambien tienen un boton que se encarga de mandar la info al 
`fragmento 2`

```xml
<?xml version="1.0" encoding="utf-8"?>
<FrameLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:background="@color/verde"
    tools:context=".PrimerFragmento">

    <!-- TODO: Update blank fragment layout -->
    <TextView
        android:id="@+id/txt_bienvenida"
        android:textColor="@color/white"
        android:textStyle="bold"
        android:textSize="18sp"
        android:gravity="center_horizontal"
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:text="@string/text_fragmento_1" />

    <ImageView
        android:id="@+id/imgufg"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:src="@drawable/iconogarantiaufg"
        android:adjustViewBounds="true"
        android:scaleType="fitXY"
        android:maxHeight="150dp"
        android:layout_marginTop="25dp"
        android:layout_gravity="center_horizontal"
        />

    <TextView
        android:id="@+id/txt_indicacion_texto"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:textColor="@color/white"
        android:layout_marginTop="170dp"
        android:layout_marginLeft="20dp"
        android:text="@string/text_indicacion_campo"
        android:layout_below="@id/imgufg"/>


    <EditText
        android:id="@+id/txt_text_fragmento1"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:inputType="text"
        android:textSize="13sp"
        android:hint="@string/text_placeholder"
        android:layout_marginLeft="48dp"
        android:layout_marginTop="190dp"
        android:textColor="@color/white"
        android:textColorHint="@color/white"
        android:layout_below="@id/txt_indicacion_texto"/>

    <Button
        android:id="@+id/btn_boton"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_gravity="center_horizontal"
        android:layout_marginTop="230dp"
        android:text="@string/text_btn_enviar"
        android:layout_below="@id/txt_text_fragmento1"/>

</FrameLayout>
```