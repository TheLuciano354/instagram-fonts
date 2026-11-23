# Instagram Directional

Estilo de texto **Directional** de las historias de Instagram.

| | |
|---|---|
| Fuente | Instagram Directional Bold |
| Tipo | Reconstruida desde capturas |
| Coincidencia con las capturas (IoU) | 0,964 |
| Archivos | `InstagramDirectional-Bold.otf`, `InstagramDirectional-Bold.ttf`, `InstagramDirectional-Bold.woff2` |

![Muestra](InstagramDirectional-Bold_muestra.png)

## Origen

Ninguna de las versiones de la app revisadas (9 IPA de iOS y 3 APK de Android) contiene esta fuente; Instagram la descarga al usar el estilo y la guarda en almacenamiento privado. Se reconstruyó a partir de 49 capturas 1440×2560 generadas automáticamente vía ADB en Android: cada grupo de caracteres se escribió en el editor de historias y se guardó la imagen. Los glifos se aislaron, vectorizaron (potrace) y montaron con fontTools; el espaciado y el kerning se ajustaron midiendo líneas de texto reales.

## Verificación

- Anchura de líneas de texto: ±0,4 % (19 líneas).
- Kerning medido (p. ej. LT −72, WA −55).

## Notas

- Solo mayúsculas, igual que en Instagram: las minúsculas se mapean a las mayúsculas, ß → SS e ı → I.

_La coincidencia se mide superponiendo el texto renderizado sobre la captura y calculando la intersección sobre unión (IoU) de la tinta, de 0 a 1. Una fuente idéntica da 0,94–0,98._

## Licencia

Reconstrucción a partir de capturas de una fuente propietaria de Meta. Uso personal y no comercial; no redistribuir.
