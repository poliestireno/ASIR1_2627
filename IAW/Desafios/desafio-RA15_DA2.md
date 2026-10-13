# RA15_DA2

## ENUNCIADO

Ver vídeo

https://youtu.be/UrsxojWLVTA

ENTREGA:
Enlace a github con el código fuente y
Video de la ejecución de menos de 1 min.

**FIN ENUNCIADO**

---

## DESAFÍO NCA

**Desafío Nº:** `RA15_DA2`

# Tira los dados: un juego de azar en PHP a dos páginas

Construir en PHP un pequeño juego de dados a dos páginas: un formulario que configura la tirada y una página que la resuelve y declara el resultado.

### Objetivos técnicos

- Construir un formulario HTML/PHP con varios combos (`<select>`) y un campo de entrada, para capturar los parámetros de la tirada.
- Enviar los datos del formulario a una segunda página PHP y recogerlos en el servidor.
- Generar números aleatorios en PHP para simular la tirada de N dados de M caras cada uno.
- Sumar los resultados de la tirada y compararlos con un valor dado para determinar si se gana o se pierde.
- Mostrar visualmente el resultado (dados obtenidos, puntos, veredicto), opcionalmente con CSS propio.
- Documentar el proyecto en GitHub y grabar un vídeo de demostración de menos de 1 minuto.

### Módulos implicados

- (CFGS Administración de Sistemas Informáticos en Red – ASIR, módulo IAW)

### Resultados de aprendizaje

- **RA1.** Prepara el entorno de desarrollo y los servidores de aplicaciones Web instalando e integrando las funcionalidades necesarias.
- **RA5.** Genera documentos Web utilizando lenguajes de guiones de servidor.

### Elementos transversales / competencias

Lógica de programación, manejo de formularios HTML, generación de números aleatorios, comunicación técnica (vídeo de demostración)

### Principios pedagógicos

Aprendizaje por proyectos, Construcción del pensamiento, Autonomía

### Sesiones

Acogida 1 · Explorar 1 · Idear 1 · Materializar 3 · Cierre 1 — **Total: 7 sesiones en 7 días**

---

### Fases

**Acogida** — 1 sesión
- Presentación del desafío: programar un pequeño juego de dados en PHP, jugando contra un oponente cuyos puntos ya se conocen de antemano.

Observación: se plantea como primer proyecto PHP completo que encadena formulario, procesamiento en servidor y resultado.

**Explorar** — 1 sesión
- Repasar cómo crear formularios HTML con `<select>` e inputs, y cómo recoger esos datos en PHP (`$_GET`/`$_POST`) — pond. 2
- Repasar cómo generar números aleatorios en PHP (`rand()`/`mt_rand()`) dentro de un rango concreto — pond. 2

Observación: son los dos únicos ingredientes técnicos nuevos que hacen falta para todo el desafío.

**Idear** — 1 sesión
- Diseñar el formulario de `a01.php`: qué combos y valores exactos lleva (número de dados 1-3, número de caras 4/6/8/10/12/20, campo de puntos del oponente) y cómo se pasan los datos a `a02.php` — pond. 2
- Bocetar cómo se mostrará el resultado en `a02.php` (dados obtenidos, suma, veredicto) y qué estilo CSS se aplicará — pond. 1

Observación: se piensa el flujo completo entre las dos páginas antes de escribir ningún PHP.

**Materializar** — 3 sesiones
- Construir `a01.php` con el formulario completo (los dos combos y el campo de puntos del oponente) y el botón de envío — pond. 2
- Construir `a02.php`: recoger los datos enviados y tirar los dados aleatoriamente según el número y las caras elegidos, mostrando cada resultado obtenido — pond. 3
- Calcular la suma de puntos obtenidos, compararla con los puntos del oponente y mostrar el veredicto (gana/pierde) — pond. 2
- Dar estilo con CSS a ambas páginas y grabar el vídeo de ejecución de menos de 1 minuto — pond. 2

Observación: es la fase central — se evalúa tanto que el cálculo y la comparación sean correctos como que el flujo entre las dos páginas funcione de principio a fin.

**Cierre** — 1 sesión
- Puesta en común mostrando el vídeo de cada alumno y comparando las distintas formas de representar los dados y el veredicto en pantalla.

Observación: cierre centrado en comparar soluciones distintas al mismo juego, no solo en comprobar que funciona.
