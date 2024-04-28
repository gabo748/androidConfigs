# CLASE FRAGMENTO ESTATICO 2

```kotlin
import android.os.Bundle
import androidx.fragment.app.Fragment
import android.view.LayoutInflater
import android.view.View
import android.view.ViewGroup
import android.widget.TextView

class SegundoFragmento : Fragment() {
    // se declara la referencia del TextView que mostrara la informacion recibida
    lateinit var mensaje: TextView

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)

        // se obtiene el valor de la "key" con el dato que sostiene la variable
        // "valor campo"
        parentFragmentManager.setFragmentResultListener("key", this) {requestKey, bundle ->

            val resultReceived = bundle.getString("valor_campo").toString()
            mensaje.setText(resultReceived)

        }

    }

    override fun onCreateView(
        inflater: LayoutInflater, container: ViewGroup?,
        savedInstanceState: Bundle?
    ): View? {
        // Inflate the layout for this fragment
        return inflater.inflate(R.layout.fragment_segundo_fragmento, container, false)
    }


    override fun onViewCreated(view: View, savedInstanceState: Bundle?) {
        super.onViewCreated(view, savedInstanceState)
        // se muestra el valor recibido en el mensaje que viene del fragment 1
        mensaje = view.findViewById(R.id.tct_texto_recibido)
    }
}
```