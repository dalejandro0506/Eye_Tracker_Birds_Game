# Avistamiento de Aves en la Selva

Juego de atención visual con seguimiento ocular (*eye-tracking*) para enseñar y practicar metodologías de investigación cognitiva. El participante explora escenas de selva buscando aves de colores para ganar puntos, mientras un eye tracker Gazepoint GP3HD registra hacia dónde mira. Está pensado para niños a partir de 7 años.

Este repositorio reúne el manual técnico-pedagógico, los estímulos visuales y el tablero de resultados del juego. Fue desarrollado en el Semillero de Cognición del Departamento de Psicología de la Universidad de los Andes (Colombia) como recurso para el Laboratorio de Psicología.

## Qué mide el juego

Cada escena tiene aves de tres categorías funcionales, con dos colores cada una. La más llamativa es la que resta puntos y la más valiosa es la más difícil de encontrar.

| Categoría | Colores | Puntos por segundo de fijación | Qué evalúa |
|---|---|:--:|---|
| Penalización | Rojo, magenta | −5 | Control inhibitorio: resistir lo que llama la atención |
| Recompensa | Amarillo, naranja | +5 | Búsqueda visual breve |
| Recompensa alta | Verde oliva, marrón | +10 | Búsqueda activa dirigida por metas (aves camufladas) |

El puntaje total es la suma de `tiempo de fijación × valor` sobre todas las aves. Solo cuentan las fijaciones de al menos 0,2 s. El juego tiene 10 escenas (E1–E10) en 5 niveles de dificultad creciente, con tiempos de exposición de 5,0 s a 3,0 s. El manual explica la fundamentación de cada parámetro.

## Contenido del repositorio

```
Eye_Tracker_Birds_Game/
├── manual_eyetracking_avistamiento.qmd   Manual (fuente en Quarto)
├── avistamiento_dashboard.html           Tablero de resultados (se abre en el navegador)
├── assets/                               Imágenes que usan el manual y el tablero
├── Diseño de estímulos/                  Ilustraciones de aves, escenas y pantallas auxiliares
├── Gazepoint/result/                     Dataset de prueba anonimizado para probar el tablero
├── Uso de Eye Tracker V1.pdf             Presentación de instalación y uso del equipo
└── Eye_Tracker_Birds_Game.Rproj          Proyecto de RStudio
```

## Cómo usarlo

### Tablero de resultados

1. Abre `avistamiento_dashboard.html` en el navegador. No necesita instalación ni servidor. Mantén la carpeta `assets/` junto al archivo, o no se verán las imágenes.
2. Al abrirlo muestra **datos de prueba** (8 jugadores ficticios).
3. Para ver resultados reales, pulsa **Cargar CSV** y elige el archivo *Data Summary* exportado desde Gazepoint Analysis. El procesamiento ocurre en tu navegador y no se envía nada.

El tablero tiene cuatro secciones: Introducción, Instrucciones de juego, Podio y Desempeño. El archivo CSV debe incluir la sección *AOI Statistics (for each user)*, que genera Gazepoint Analysis.

### Manual

El manual está escrito en [Quarto](https://quarto.org) y se renderiza a un HTML autocontenido:

```bash
quarto render manual_eyetracking_avistamiento.qmd
```

No requiere R. Cubre el marco teórico, la instalación y calibración del Gazepoint GP3HD, la configuración del experimento en Gazepoint Analysis, el sistema de puntuación, la extracción de datos y la operación en el laboratorio.

## Requisitos para aplicar el juego

- Eye tracker Gazepoint GP3HD con Gazepoint Control y Gazepoint Analysis (el manual usa la versión 7.1).
- Participante a unos 65 cm de la pantalla y el escáner unos 40 cm por debajo de los ojos.
- Calibración de 5 o 9 puntos, y *Fixation Filter* en 200 ms antes de cada sesión.

## Datos y ética

Este repositorio **no incluye datos de participantes reales**. La carpeta `Gazepoint/result/` contiene solo `Dataset prueba.csv`, un export *Data Summary* de prueba con ocho usuarios anonimizados (Usuario1 a Usuario8), pensado para probar el tablero. El resto del proyecto de Gazepoint Analysis (videos del rostro y de la pantalla, copias de respaldo, archivos de sesión y el archivo de proyecto) queda fuera del repositorio porque puede contener información personal de los participantes, que pueden ser menores de edad.

El uso de la herramienta debe seguir los lineamientos éticos institucionales para investigación con participantes humanos. Antes de aplicarla, los participantes y sus tutores legales, si son menores, deben recibir información clara y firmar consentimientos y asentimientos informados. El seguimiento ocular registra la dirección de la mirada, no pensamientos ni estados mentales.

## Estado del proyecto

Completado:

- Sistema de puntuación calibrado y documentado.
- Tablero de resultados con carga de CSV.
- Manual técnico con instalación, calibración y operación.
- Ilustraciones de las aves y escenas de ejemplo.

Pendiente:

- Finalizar las escenas E1–E10 y exportarlas a imágenes para Gazepoint.
- Definir las AOIs sobre las aves de cada escena en Gazepoint Analysis.
- Integración física en el laboratorio y pruebas de calibración con la distancia del espacio.
- Diseñar las pantallas auxiliares (bienvenida, instrucciones, interludios y resultados).

## Créditos

Diseñado por **Daniel Alejandro Socha Castelblanco**, Maestría en Psicología, Universidad de los Andes, con el apoyo de **Henry Armando Delgado Martínez** y **William Jiménez-Leal**. Desarrollado en el Semillero de Cognición del Departamento de Psicología, 2026.
