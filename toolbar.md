## Como crear menu superior (tool bar)
### En el activity main (XML) se debe declarar este elemento de UI

```xml
    <androidx.appcompat.widget.Toolbar
        android:id="@+id/toolbal"
        android:layout_width="match_parent"
        android:layout_height="?actionBarSize"
        android:background="#DDDDDD"
        android:theme="@style/Theme.AppCompat.DayNight.DarkActionBar"
        tools:ignore="MissingConstraints"
        app:popupTheme="@style/MenuStyle"
        />
```
- `app:popupTheme`:  Este esta definido en el paquete themes como un `<style></style>` agregado asi:
```xml
    <style name="MenuStyle" parent="Theme.MaterialComponents.Light" >
        <item name="popupMenuBackground">@color/rojoPasion</item>
        <item name="android:textColor">@color/white</item>
    </style>
```

### En el activit main (kt) se debe de llamar al toolbar asi:
```Kotlin
import android.annotation.SuppressLint
import android.content.Intent
import androidx.appcompat.app.AppCompatActivity
import android.os.Bundle
import android.view.Menu
import android.view.MenuItem
import android.widget.Button
import android.widget.Toast
import androidx.appcompat.widget.Toolbar

class MainActivity : AppCompatActivity() {
    @SuppressLint("MissingInflatedId")
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)
        
        // llamada al toolbar por el id 
        var toolbar = findViewById<Toolbar>(R.id.toolbal)
        setSupportActionBar(toolbar)

        supportActionBar?.title = "Campos Lopez"
        supportActionBar?.subtitle = "Universidad Francisco Gavidia"
        supportActionBar?.setIcon(R.drawable.ic_launcher_foreground)
    }

    // metodo del toolbar
    override fun onCreateOptionsMenu(menu: Menu?): Boolean {
        menuInflater.inflate(R.menu.ufg_toolbar, menu)
        return true
    }

    // metodo para ejecutar acciones del toolbar
    override fun onOptionsItemSelected(item: MenuItem): Boolean {

        return when(item.itemId) {
            R.id.congifuracion -> {
                Toast.makeText(this, "USTED A SELECCIONADO LA OPCION DE: CONFIGURACION", Toast.LENGTH_SHORT).show()
                true
            }
            R.id.user -> {
                Toast.makeText(this, "USTED A SELECCIONADO LA OPCION DE: PERFIL", Toast.LENGTH_SHORT).show()
                true
            }
            R.id.mapa -> {
                Toast.makeText(this, "USTED A SELECCIONADO LA OPCION DE: UBICACION", Toast.LENGTH_SHORT).show()
                true
            }
            R.id.nueva_cuenta -> {
                Toast.makeText(this, "USTED A SELECCIONADO LA OPCION DE: AGREGAR CUENTA", Toast.LENGTH_SHORT).show()
                true
            }
            R.id.salir -> {
                Toast.makeText(this, "USTED A SELECCIONADO LA OPCION DE: SALIR", Toast.LENGTH_SHORT)
                    .show()
                true
            }
            else -> false
        }
    }
}
```