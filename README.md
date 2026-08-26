# beamerteaching

Tema ligero de Beamer para presentaciones de docencia universitaria en
matemáticas. Esta primera versión está pensada para docencia en español en la
Universidad de Sevilla; la arquitectura permite añadir más adelante variantes
para la UNED y otros idiomas.

## Características

- formato panorámico compatible con Beamer;
- paleta sobria y fácilmente sustituible por variantes institucionales;
- portada, títulos de diapositiva, pie con numeración y separadores de sección;
- entornos matemáticos en español: teorema, proposición, lema, corolario,
  definición, ejemplo y demostración;
- dependencias limitadas a Beamer y los paquetes estándar `amsmath` y
  `amssymb`;
- compatible con pdfLaTeX y pensado para TeX Live en macOS y Texifier en iOS.

## Uso

Copia `beamerthemeTeaching.sty` junto al fichero principal de la presentación y
escribe en el preámbulo:

```tex
\documentclass[aspectratio=169,11pt]{beamer}
\usepackage[T1]{fontenc}
\usepackage[provide=*,spanish]{babel}
\usetheme{Teaching}
```

El separador automático al comienzo de cada sección está activado por defecto.
Puede desactivarse con:

```tex
\usetheme[nosectionpages]{Teaching}
```

## Ejemplo

Desde la raíz del repositorio:

```sh
latexmk -pdf examples/ejemplo.tex
```

Para eliminar los ficheros auxiliares:

```sh
latexmk -C examples/ejemplo.tex
```

## Próximos pasos

- afinar la identidad visual para la Universidad de Sevilla;
- separar el núcleo del tema de las variantes US y UNED;
- añadir soporte explícito para inglés;
- preparar plantillas para asignaturas completas y tutorías.
