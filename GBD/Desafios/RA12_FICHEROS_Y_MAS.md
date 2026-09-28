# RA12_FICHEROS_Y_MAS

## ENUNCIADO

Dos fases: primero los ejercicios clásicos de ficheros secuenciales, aleatorios e indexados; después, un recorrido práctico por lo que de verdad hay dentro de un archivo — su extensión, sus metadatos, y cómo manipularlos.

Teoría de referencia (pública): `teoria-ficheros.html`.


### Fase 1 · Ficheros clásicos

Repasa antes la teoría de *Sistemas de archivos* si te hace falta — en concreto, secuenciales, aleatorios e indexados.

1. **Agenda secuencial.** Crea un fichero de texto secuencial `agenda_secuencial.txt` con una agenda de teléfonos. Cada contacto debe incluir: Nombre, Apellidos, Dirección, Ciudad, Teléfono. Incluye un mínimo de diez contactos, de al menos cuatro ciudades distintas.
2. **La misma agenda, en aleatorio.** Partiendo de los datos del ejercicio anterior, crea un fichero de texto aleatorio `agenda_aleatorio.txt`. Presenta una justificación del número de caracteres que has elegido para cada campo — recuerda que, a diferencia del secuencial, aquí cada campo necesita un tamaño fijo.
3. **Indexar la agenda.** Copia `agenda_aleatorio.txt` a un nuevo fichero llamado `agenda_indexada.txt`. Crea un fichero de índice `agenda_apellidos_nombre.txt` que lo ordene por apellidos y nombre, y otro `agenda_ciudad.txt` que lo ordene por ciudad. Para cada fichero indexado, dibuja el árbol binario correspondiente — el de menor valor siempre a la izquierda, el de mayor a la derecha.
4. **Borrar e insertar.** Borra un contacto cualquiera de `agenda_indexada.txt` e inserta un contacto nuevo, actualizando a la vez los ficheros de índice asociados (los árboles de los dos apartados anteriores).
5. **SGBD actuales.** Consulta en internet información sobre las prestaciones de los SGBD comerciales y libres más utilizados hoy en día, y resúmelo brevemente.

### Fase 2 · La verdadera naturaleza de un archivo

Tres partes para entender que la extensión de un archivo es solo una etiqueta, el peso real de sus metadatos, y cómo controlarlos con una herramienta de línea de comandos. Documenta cada respuesta con capturas de pantalla y un comentario propio.

> **Paso 0 · antes de empezar:** necesitas dos cosas: una **imagen** cualquiera (una foto hecha con el móvil sirve), guardada como `mi_foto_disney.jpg`; y **ExifTool** instalado (descárgalo desde `exiftool.org` y sigue las instrucciones para Windows). Abre después una terminal y navega hasta la carpeta donde vayas a guardar los archivos de prueba.

#### Parte 1 · La extensión es solo un disfraz

**1.1 Un cuento con extensión falsa.** Abre un editor de texto plano y escribe: *"Érase una vez, en un lejano reino, vivía un príncipe que se enamoró de una misteriosa princesa. Al amanecer, ella se marchó, dejando tras de sí solo un zapato de cristal."* Guárdalo como `cuento_cenicienta.txt`. Cambia el nombre del archivo a `cuento_cenicienta.jpg` e intenta abrirlo con tu visualizador de imágenes. ¿Qué pasa? Coméntalo.

**1.2 Descubrir la verdad con TrID.** Una herramienta como **TrID** analiza el contenido real del archivo, sin fiarse de su extensión. Utilízala sobre `cuento_cenicienta.jpg`. ¿Qué resultado da, y por qué?

#### Parte 2 · Por qué un .docx pesa más que un .txt

**2.1 Comparar tamaños.** Crea un archivo de texto con la frase *"Los personajes de Disney son mágicos."*, guárdalo como `frase_magica.txt` y anota su tamaño (serán muy pocos bytes). Ahora escribe exactamente la misma frase en Word o LibreOffice y guárdala como `frase_magica.docx` (o `.odt`). Compara los dos tamaños — el `.docx` es mucho mayor, aunque el texto sea idéntico. ¿Por qué pasa esto? Coméntalo.

**2.2 Un .docx es, en realidad, un .zip.** Cambia la extensión de `frase_magica.docx` a `.zip` y descomprímelo. Dentro encontrarás varias carpetas (`_rels`, `docProps`, `word`) y archivos XML. Abre `word/document.xml` con un editor de texto. ¿Qué puedes identificar ahí dentro? Explícalo.

#### Parte 3 · Metadatos con ExifTool

**3.1 Buscar pistas en la imagen.** Desde la terminal, en la carpeta de tu foto, ejecuta:

```bash
exiftool mi_foto_disney.jpg
```

Busca etiquetas que revelen información sobre la foto — modelo de cámara, fecha de creación, coordenadas GPS si las hay… Saca todas las que puedas y coméntalas.

**3.2 Escribir tus propios metadatos.** Con ExifTool también puedes añadir o modificar metadatos, con la sintaxis `-[Etiqueta]="[Valor]"`:

```bash
exiftool -Comment="Esta foto fue tomada en el Castillo de la Bella Durmiente" mi_foto_disney.jpg
exiftool -Comment mi_foto_disney.jpg
```

La segunda línea comprueba que el comentario se ha guardado correctamente.

**3.3 Borrando el rastro.** Para eliminar solo la posición GPS (si la hay):

```bash
exiftool -GPSPosition= mi_foto_disney.jpg
```

Para eliminar **todos** los metadatos de golpe (muy potente, úsalo con cuidado):

```bash
exiftool -all= mi_foto_disney.jpg
exiftool mi_foto_disney.jpg
```

La segunda ejecución debería mostrar la lista de metadatos casi vacía. Comenta qué ha pasado.

> **Trabaja siempre sobre una copia:** ExifTool crea automáticamente una copia de seguridad (`.jpg_original`) antes de modificar un archivo, pero sigue siendo buena práctica trabajar sobre una copia propia si no estás seguro del resultado.

### Entrega

Documento con capturas de pantalla de cada paso (Fase 1 y Fase 2) y tus comentarios propios sobre cada pregunta.

**FIN ENUNCIADO**

---

## DESAFÍO NCA

**Desafío Nº:** `RA12_FICHEROS_Y_MAS`

# Ficheros y más: de la agenda en papel al verdadero contenido de un archivo

Reconstruir a mano los sistemas de almacenamiento previos al SGBD con una agenda de teléfonos, y después desmontar la idea de que la extensión o el tamaño de un archivo cuentan toda la verdad sobre lo que contiene.

### Objetivos técnicos

- Crear y comparar tres organizaciones de fichero (secuencial, aleatorio e indexado) sobre los mismos datos de una agenda.
- Diseñar y justificar la longitud fija de cada campo en el fichero aleatorio.
- Construir los árboles binarios de índice correspondientes, y mantenerlos sincronizados tras un borrado e inserción.
- Investigar las prestaciones de los SGBD comerciales y libres más usados actualmente.
- Comprobar experimentalmente que la extensión de un archivo es solo una etiqueta, no su contenido real (con TrID).
- Entender por qué un `.docx` pesa más que un `.txt` equivalente, e inspeccionar su estructura interna como ZIP + XML.
- Leer, escribir y borrar metadatos EXIF de una imagen con ExifTool.

### Módulos implicados

- (CFGS Administración de Sistemas Informáticos en Red – ASIR, módulo GBD)

### Resultados de aprendizaje

- **RA1.** Reconoce los elementos de las bases de datos analizando sus funciones y valorando la utilidad de los sistemas gestores.
- **RA2.** Diseña modelos lógicos normalizados interpretando diagramas entidad/relación.

### Elementos transversales / competencias

Organización de la información, atención al detalle, investigación autónoma, documentación técnica

### Principios pedagógicos

Descubrimiento guiado, Construcción del pensamiento, Autonomía

### Sesiones

Acogida 1 · Explorar 1 · Idear 1 · Materializar 4 · Cierre 1 — **Total: 8 sesiones en 8 días**

---

### Fases

**Acogida** — 1 sesión
- Presentación del desafío en dos actos: primero reconstruir a mano los sistemas de fichero que existían antes de un SGBD, después descubrir que ni la extensión ni el peso de un archivo cuentan la verdad completa sobre lo que contiene.

Observación: sirve de puente directo hacia "por qué hace falta un SGBD", que es el tema de la siguiente unidad.

**Explorar** — 1 sesión
- Repasar la teoría de ficheros secuenciales, aleatorios e indexados, y cómo se dibuja el árbol binario de un índice — pond. 2
- Familiarizarse con las herramientas de la Fase 2 antes de usarlas: qué hace TrID, qué es ExifTool y qué son los metadatos EXIF — pond. 1

Observación: apoyado en la teoría de referencia del módulo sobre sistemas de archivos.

**Idear** — 1 sesión
- Diseñar los datos de la agenda (mínimo 10 contactos, 4 ciudades distintas) y decidir la longitud fija de cada campo para la versión aleatoria, justificando cada tamaño — pond. 2
- Antes de tocar la imagen y el `.docx`, anotar qué metadatos y qué contenido interno se espera encontrar, para poder comparar después con lo real — pond. 1

Observación: se piensa y se justifica antes de crear ningún archivo.

**Materializar** — 4 sesiones
- Crear la agenda secuencial y su versión aleatoria con los campos ya diseñados — pond. 2
- Indexar la agenda por apellidos+nombre y por ciudad, dibujando el árbol binario de cada índice; borrar un contacto e insertar uno nuevo, actualizando ambos árboles — pond. 3
- Investigar y resumir las prestaciones de los SGBD comerciales y libres más usados actualmente — pond. 1
- Fase 2 completa: extensión falsa comprobada con TrID; comparar `.txt` frente a `.docx` y examinar su interior como ZIP; leer, escribir y borrar metadatos EXIF de una foto con ExifTool — pond. 4

Observación: es la fase central — se evalúa tanto la corrección técnica de cada fichero/árbol como la evidencia (capturas) y el comentario propio de cada resultado.

**Cierre** — 1 sesión
- Presentar el documento final con todas las capturas y comentarios, destacando qué resultado de la Fase 2 resultó más sorprendente y por qué.

Observación: puesta en común comparando qué metadatos encontró cada alumno en su propia foto.
