# CLASE DEL FRAGMENTO ESTATICO 1 

```kotlin
import android.os.Bundle
import androidx.fragment.app.Fragment
import android.view.LayoutInflater
import android.view.View
import android.view.ViewGroup
import android.widget.Button
import android.widget.EditText


class PrimerFragmento : Fragment() {
    // se declara la referencia del EditText
    private lateinit var editText: EditText

    override fun onCreateView(
        inflater: LayoutInflater, container: ViewGroup?,
        savedInstanceState: Bundle?
    ): View? {
        // Inflate the layout for this fragment
        return inflater.inflate(R.layout.fragment_primer_fragmento, container, false)
    }

    override fun onViewCreated(view: View, savedInstanceState: Bundle?) {
        super.onViewCreated(view, savedInstanceState)

        // se inicializa la referencia con los id declarados en el XML
        val boton = view.findViewById<Button>(R.id.btn_boton)
        editText = view.findViewById(R.id.txt_text_fragmento1)

        // se define una accion al dar tap en el boton
        boton.setOnClickListener(View.OnClickListener {view ->
            var message: String = editText.text.toString()
            val bundle = Bundle()

            // se declara una variable con el nombre "valor_campo" que sera usada 
            // en el fragment 2 para mostrar el valor
            bundle.putString("valor_campo", message)

            arguments = bundle
            parentFragmentManager.setFragmentResult("key", bundle)

        })
    }
}
```