# Compatibilidad de pantalla en Android

Android es compatible con una amplia gama de dispositivos que varían en tamaño de pantalla y densidad de píxeles. El sistema realiza ajustes automáticos para adaptar la interfaz de usuario a diferentes pantallas, pero hay estrategias para mejorar la adaptación de la interfaz a cada tipo de pantalla.

## Tamaños de pantalla

El tamaño de la pantalla se refiere al espacio visible para la interfaz de usuario de la app. No es el tamaño físico real de la pantalla del dispositivo, ya que incluye consideraciones como la orientación de la pantalla y las decoraciones del sistema. Las apps deben tener en cuenta estos aspectos y adaptarse en consecuencia.

### Diseños flexibles

Android ajusta automáticamente el tamaño del diseño de la app para adaptarse a la pantalla actual. Es importante diseñar con flexibilidad, evitando codificar posiciones o tamaños fijos para los componentes de la interfaz.

### Diseños alternativos

Se pueden crear diferentes diseños para optimizar la experiencia del usuario en dispositivos con diversos tamaños de pantalla. Android permite proporcionar archivos de diseño alternativos que se aplican en tiempo de ejecución según el tamaño de la pantalla del dispositivo.

### Imágenes estirables

Es crucial que las imágenes se estiren correctamente para adaptarse a la pantalla actual. Android admite mapas de bits de 9-patch, que especifican regiones de píxeles que se pueden estirar mientras el resto de la imagen permanece sin ajustar.

## Densidades de píxeles

La densidad de píxeles (DPI) es la cantidad de píxeles dentro de un área física de la pantalla. La independencia de la densidad es crucial para mantener el tamaño físico del diseño de la interfaz en pantallas con diferentes densidades de píxeles.

### Independencia de la densidad

Para lograr la independencia de la densidad, se utilizan píxeles independientes de la densidad (dp o dip) en lugar de píxeles absolutos (px) como unidad de medida.

### Mapas de bits alternativos

Proporcionar mapas de bits alternativos que coincidan con la densidad de cada pantalla ayuda a que las imágenes se vean mejor en todas las pantallas.

### Gráficos vectoriales

Para imágenes simples como íconos, se pueden utilizar gráficos vectoriales para evitar crear imágenes separadas para cada densidad, ya que se pueden redimensionar sin pérdida de calidad.

## Dispositivos específicos

Para dispositivos como Wear OS, Android TV, Android Auto, Android Automotive y ChromeOS, se deben considerar modelos de interacción de usuario específicos y seguir las pautas de desarrollo proporcionadas por Android.

## Dispositivos plegables

Los dispositivos plegables presentan desafíos únicos debido a sus múltiples pantallas y configuraciones cambiantes. Es crucial probar la app en una variedad de dispositivos y tamaños de pantalla para garantizar una experiencia óptima.

Para obtener más información sobre la compatibilidad con dispositivos plegables y otros dispositivos específicos, consulta la documentación relevante proporcionada por Android.
