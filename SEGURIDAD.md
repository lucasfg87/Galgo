# Seguridad

Galgo es un único archivo HTML que corre en tu navegador. No hay servidor, no hay cuenta y no se
envía nada a ninguna parte. Esta página explica qué protege Galgo, qué no, y cómo avisarme si
encontrás un problema.

## Cómo reportar un problema

Escribime por LinkedIn: [linkedin.com/in/lucas-gomez-data](https://linkedin.com/in/lucas-gomez-data).
Contame qué encontraste y, si podés, cómo reproducirlo. Si es algo que puede afectar a otras
personas, avisame en privado antes de publicarlo y te respondo lo antes que pueda. Galgo es un
proyecto personal que mantengo en mis ratos libres, así que no puedo prometer plazos, pero sí que
lo voy a tomar en serio.

## Qué hace Galgo con tus datos

Nada que salga de tu computadora. La planilla se lee en el navegador, el tablero se arma en el
navegador y el informe se guarda como un archivo en tu disco. Galgo no tiene servidor propio, no
hace llamadas a internet mientras trabajás y no tiene telemetría: no sé cuántas personas lo usan ni
qué datos cargan.

Si abrís Galgo desde [galgo.net.ar](https://galgo.net.ar), el archivo se descarga una vez y después
funciona igual que si lo tuvieras en el escritorio. Podés desconectarte de internet y seguir
trabajando.

## Lo que tenés que saber antes de abrir un informe que te mandaron

**Un informe de Galgo es un archivo HTML, es decir, código que se ejecuta cuando lo abrís.** Es la
misma situación que un Excel con macros: abrilo si confiás en quien te lo mandó. Galgo no puede
garantizarte que un archivo con extensión `.html` que recibiste por mail sea un informe de Galgo
legítimo y no otra cosa con el mismo nombre.

Si querés mirar antes de abrir, un informe de Galgo real tiene en su encabezado la línea
`<meta name="generator" content="Galgo ...">` y se puede leer con cualquier editor de texto.

## Qué protege Galgo

- **Los datos de tu planilla se tratan siempre como texto.** Si una celda o un nombre de columna
  contiene algo que parece código HTML, se muestra como texto y no se ejecuta, tanto en el editor
  como en el informe exportado.
- **Los datos del informe van en un bloque aislado**, codificados de forma que no puedan cerrar ese
  bloque y empezar a ejecutarse.
- **Galgo no ejecuta código que venga de un archivo.** No usa `eval` ni construye funciones a partir
  de texto. Las fórmulas de las medidas calculadas las interpreta un analizador propio que solo
  entiende operaciones matemáticas y nombres de columna.
- **Al abrir un proyecto se descartan las claves peligrosas** (`__proto__`, `constructor`,
  `prototype`) y se verifica la estructura y el tamaño antes de usarlo. Un archivo dañado o
  preparado a propósito da un mensaje claro en vez de dejar el editor en un estado raro.
- **Las librerías de terceros van sin modificar**, con su huella digital registrada y verificada en
  cada compilación. Ver `AVISOS-DE-TERCEROS.md`.

## Qué no protege Galgo

- No te protege de un archivo HTML malicioso que alguien te mande diciendo que es un informe de
  Galgo. Esa decisión es tuya, igual que con cualquier adjunto.
- No cifra nada. Si guardás un informe con datos sensibles en una carpeta compartida, lo ve
  cualquiera que tenga acceso a esa carpeta.
- No controla quién abre un informe que ya enviaste. Una vez que el archivo salió, viaja solo.
- No valida los datos por vos. Si la planilla está mal, el tablero va a estar mal.

## Versiones

Las correcciones de seguridad salen en la versión siguiente y se anuncian en el historial del
[README](README.md). Usá siempre la última versión publicada en
[galgo.net.ar](https://galgo.net.ar).
