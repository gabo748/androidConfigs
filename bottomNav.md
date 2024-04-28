## Como crear menu inferior (bottom navigation)

### En el activity main (XML) se debe declarar este elemento de UI
```xml
<?xml version="1.0" encoding="utf-8"?>
<androidx.coordinatorlayout.widget.CoordinatorLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:id="@+id/main"
    tools:context=".MainActivity">
    
    // Contenedor de fragments
    <androidx.fragment.app.FragmentContainerView
        xmlns:android="http://schemas.android.com/apk/res/android"
        xmlns:app="http://schemas.android.com/apk/res-auto"
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:id="@+id/fragment_container_view"
        android:tag="my_tag"
        >
    </androidx.fragment.app.FragmentContainerView>

    // Este es el elemento necesario para el navigation bottom.
    <com.google.android.material.bottomnavigation.BottomNavigationView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:id="@+id/nav_menu"
        app:menu="@menu/menu"
        android:layout_gravity="bottom"
        android:background="@color/black"
        app:itemTextColor="@color/white"
        app:itemIconTint="@color/white"
        />

</androidx.coordinatorlayout.widget.CoordinatorLayout>
```
- `app:menu`: Este elemento es la referencia del id del menu creado con los items

### En el activit main (kt) se debe de llamar al bottom navigation asi:
- En este ejemplo el navigation menu sostiene fragments
```kotlin
import androidx.appcompat.app.AppCompatActivity
import android.os.Bundle
import androidx.fragment.app.commit
import androidx.fragment.app.replace
import com.google.android.material.bottomnavigation.BottomNavigationView

class MainActivity : AppCompatActivity() {
    lateinit var navegacion: BottomNavigationView

    private val opcionMenuSeleccionada = BottomNavigationView.OnNavigationItemSelectedListener {item ->
        when(item.itemId) {
            R.id.fragmento1 -> {
                supportFragmentManager.commit {
                    replace<primer_fragmento>(R.id.fragment_container_view)
                    setReorderingAllowed(true)
                    addToBackStack("replacement")
                }
                return@OnNavigationItemSelectedListener true
            }
            R.id.fragmento2 -> {
                supportFragmentManager.commit {
                    replace<segundo_fragmento>(R.id.fragment_container_view)
                    setReorderingAllowed(true)
                    addToBackStack("replacement")
                }
                return@OnNavigationItemSelectedListener true
            }
            R.id.fragmento3 -> {
                supportFragmentManager.commit {
                    replace<tercer_fragmento>(R.id.fragment_container_view)
                    setReorderingAllowed(true)
                    addToBackStack("replacement")
                }
                return@OnNavigationItemSelectedListener true
            }
            R.id.fragmento4 -> {
                supportFragmentManager.commit {
                    replace<cuarto_fragmento>(R.id.fragment_container_view)
                    setReorderingAllowed(true)
                    addToBackStack("replacement")
                }
                return@OnNavigationItemSelectedListener true
            }

        }
        false
    }
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        supportFragmentManager.commit {
            replace<primer_fragmento>(R.id.fragment_container_view)
            setReorderingAllowed(true)
            addToBackStack("replacement")
        }

        navegacion = findViewById(R.id.nav_menu)
        navegacion.setOnNavigationItemSelectedListener(opcionMenuSeleccionada)

    }

}
```