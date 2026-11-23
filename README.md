# Instagram Fonts

Las fuentes de los **18 estilos de texto de las historias de Instagram**, en formato instalable (OTF/TTF, y WOFF2 en las reconstruidas), con la documentación de dónde sale cada una y cómo se verificó.

## Estilos

### Fuentes originales (11)

Extraídas de los paquetes de la app (IPA/APK) o identificadas con exactitud.

| Estilo | Fuente | Diseño | Verificación |
|---|---|---|---|
| [Modern](Modern/) | Instagram Sans Condensed Regular (+ Light, Medium, Bold) | Colophon Foundry para Meta | Grosor del trazo 0,5595 vs 0,5601 |
| [Squeeze](Squeeze/) | Instagram Squeeze Black | Colophon Foundry para Meta | IoU 0,845 |
| [Handwritten](Handwritten/) | Instagram Signature Regular | Colophon Foundry para Meta | IoU 0,881 con shaping |
| [Editor](Editor/) | Instagram Editor Regular | Colophon Foundry para Meta | Nombre del estilo + comparación |
| [Poster](Poster/) | Instagram Poster Black | Colophon Foundry para Meta | Nombre del estilo + comparación |
| [Bubble](Bubble/) | Instagram Bubble Black | Colophon Foundry para Meta | Nombre del estilo + comparación |
| [Deco](Deco/) | Instagram Deco Regular | Colophon Foundry para Meta | Nombre del estilo + comparación |
| [Headline](Headline/) | Advercase Regular | — | IoU 0,97–0,98 por letra |
| [Literature](Literature/) | Instagram Serif Regular | Colophon Foundry para Meta | IoU 0,970 por letra |
| [Strong (Android)](Strong%20Android/) | Montserrat ExtraBold Italic | Julieta Ulanovsky | Archivo idéntico al de la app |
| [Strong (iOS)](Strong%20iOS/) | Avenir Next Heavy Italic | Linotype | Ángulo 10,02° vs 10,04°, alturas ±1 px |

### Fuentes reconstruidas (7)

Instagram no las incluye en ninguna versión de la app revisada: las descarga al usar el estilo. Se han reconstruido a partir de capturas.

| Estilo | Fuente | IoU con las capturas | Limitaciones |
|---|---|---|---|
| [Classic](Classic/) | Instagram Classic Black | 0,983 | — |
| [Typewriter](Typewriter/) | Instagram Typewriter Bold | 0,976 | Sin ± ½ ¼ ¾ ¹ |
| [Directional](Directional/) | Instagram Directional Bold | 0,964 | Solo mayúsculas (como en la app) |
| [Meme](Meme/) | Instagram Meme Bold | 0,955 | — |
| [Arcade](Arcade/) | Instagram Arcade Regular | 0,953 | Sin ‰ ni fracciones |
| [Gothic](Gothic/) | Instagram Gothic Regular | 0,952 | Sin kerning |
| [Elegant](Elegant/) | Instagram Elegant Italic | 0,919 | — |

Cada carpeta tiene su propio `README.md` con el origen, la verificación y la licencia.

## Metodología

**Extracción.** Se analizaron 9 IPA de iOS y 3 APK de Android de distintas versiones de Instagram (oficiales y builds de terceros que conservan fuentes descargadas en caché) y se extrajeron las fuentes de cada paquete.

**Verificación.** Cada identificación se comprueba con medidas, no a ojo: se renderiza el mismo texto con la fuente candidata, se superpone sobre una captura de Instagram y se calcula la intersección sobre unión (IoU) de la tinta. Una fuente idéntica da 0,94–0,98; las candidatas parecidas se quedan en 0,6–0,85. Para las manuscritas enlazadas se aplica shaping OpenType (HarfBuzz) antes de comparar. Dos identificaciones iniciales hechas a ojo (Cosmopolitan Script y Georgia) se descartaron así.

**Reconstrucción.** Para los estilos sin fuente disponible:

1. Captura automatizada vía ADB en Android: cada grupo de caracteres se escribe en el editor de historias y se guarda la imagen (1440×2560), siempre al mismo tamaño.
2. Segmentación de glifos por componentes conexos, con separación de letras pegadas y acentos compuestos sobre la letra base.
3. Vectorización con potrace sobre el bitmap ampliado ×4 y simplificación con skia-pathops.
4. Montaje con fontTools (CFF y TrueType), con métricas calibradas a una altura de mayúscula de 700 unidades.
5. Espaciado y kerning ajustados por mínimos cuadrados con las líneas de texto reales.
6. Validación de la forma (IoU por glifo) y de la anchura de las líneas frente a las capturas.

## Nomenclatura

Se sigue la de las fuentes de estilo de Meta: nombre `Instagram <Estilo> <Peso>` y archivo `Instagram<Estilo>-<Peso>`. Así todas aparecen agrupadas en los menús de fuentes. Strong Android y Strong iOS son copias renombradas de Montserrat y Avenir Next, con los glifos sin modificar. Headline conserva su nombre original, Advercase.

## Licencia

Este repositorio **no** concede ninguna licencia sobre las fuentes.

- Las fuentes de Meta, Advercase y Avenir Next son propietarias y tienen licencia solo para su uso dentro de la app o del sistema. Las reconstruidas son calcos de diseños de Meta. Todas son para uso personal y no comercial, y no pueden redistribuirse.
- **Montserrat** (Strong Android) se distribuye bajo la [SIL Open Font License 1.1](https://openfontlicense.org) y es la única libre, también para uso comercial.

Instagram es una marca de Meta Platforms, Inc. Este proyecto no está afiliado a Meta ni cuenta con su respaldo.
