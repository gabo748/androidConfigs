# XML DE ACTIVITY MAIN FRAGMENTS ESTATICOS

1. Denifir los fragmentos a utilizar en el ActivityMain `(xml)` 
- Notar que los fragmentos estaticos necesitan la propieda `name` 
- `name:` es la referencia hacia la `clase` que sostiene el fragment.
- Notar que el `LinearLayout` tiene un `showDividers="middle"`
- `showDividers="middle"`: Infiere que la pantalla estara divida en 2

```xml
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">

<LinearLayout
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:baselineAligned="false"
    android:divider="?android:attr/dividerHorizontal"
    android:orientation="vertical"
    android:weightSum="2"
    android:showDividers="middle">

    <fragment
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:id="@+id/fragment1"
        android:layout_weight="0.6"
        android:name="sv.edu.ufg.fis.amb.fragmentostaticoscamposlopez.PrimerFragmento"
    />

    <fragment
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:id="@+id/fragment2"
        android:layout_weight="1.4"
        android:name="sv.edu.ufg.fis.amb.fragmentostaticoscamposlopez.SegundoFragmento"
        />

</LinearLayout>

</androidx.constraintlayout.widget.ConstraintLayout>
```