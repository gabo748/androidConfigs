# UI Responsive con ConstraintLayout


**_NOTE:_**  `ConstraintLayout` te permite crear diseños grandes y complejos con una jerarquía de vistas plana (sin grupos de vistas anidados). Es similar a `RelativeLayout`

### Descripción general de las restricciones

Para definir la posición de una vista en `ConstraintLayout`, agrega al menos una restricción horizontal y una vertical para la vista. Cada restricción representa una conexión o alineación con otra vista, el diseño de nivel superior o un lineamiento invisible. Cada restricción define la posición de la vista a lo largo del eje horizontal o vertical.

### Cómo agregar ConstraintLayout a tu proyecto
Para usar ConstraintLayout en tu proyecto, haz lo siguiente:
1. Asegúrate de tener el repositorio `maven.google.com` declarado en tu archivo `settings.gradle`

```groovy
    dependencyResolutionManagement {
      ...
      repositories {
          google()
      }
    )
    
```

2. Agrega la biblioteca como una dependencia en el archivo build.gradle de nivel de módulo, como se muestra en el siguiente ejemplo. La última versión puede ser diferente a la que se muestra en el ejemplo.

```groovy
dependencies {
    implementation "androidx.constraintlayout:constraintlayout:2.2.0-alpha13"
    // To use constraintlayout in compose
    implementation "androidx.constraintlayout:constraintlayout-compose:1.1.0-alpha13"
}
```

### Cuando crees restricciones, recuerda las siguientes reglas:

- Cada vista debe tener al menos dos restricciones: una horizontal y una vertical.
- Solo puedes crear restricciones entre un controlador de restricción y un punto de anclaje que compartan el mismo plano. Un plano vertical (el lado izquierdo y el derecho) de una vista puede restringirse solo a otro plano vertical, y las líneas de base pueden restringirse solo a otras líneas de base.
- Cada controlador de restricción se puede usar para una sola restricción, pero puedes crear varias restricciones desde diferentes vistas hasta el mismo punto de anclaje.

### Descripciones importantes:

 - `Fixed`: Especifica una dimensión específica en el siguiente cuadro de texto o cambia el tamaño de la vista en el editor.
 Wrap Content: La vista se expande solo lo necesario para ajustarse al contenido.

- `layout_restrictedWidth` Configúralo como `true` para permitir que la dimensión horizontal cambie y respete las restricciones. De forma predeterminada, un widget configurado como WRAP_CONTENT no está limitado por restricciones.

- `Match Constraints`: La vista se expande tanto como sea posible para cumplir con las restricciones de cada lado, después de tener en cuenta los márgenes. Sin embargo, puedes modificar ese comportamiento con los siguientes atributos y valores. Estos atributos solo se aplican cuando estableces el ancho de la vista para que "coincide con las restricciones"

- `layout_constraintWidth_min`Toma una dimensión en dp para el ancho mínimo de la vista.

- `layout_constraintWidth_max` Toma una dimensión en dp para el ancho máximo de la vista.