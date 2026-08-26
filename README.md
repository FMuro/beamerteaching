# beamerteaching

Tema ligero de Beamer para presentaciones de docencia universitaria en
matemáticas. Esta primera versión está pensada para docencia en español en la
Universidad de Sevilla; la arquitectura permite añadir más adelante variantes
para la UNED y otros idiomas.

## Características

- formato panorámico compatible con Beamer;
- tipografía romana estándar de LaTeX tanto para el texto como para las
  matemáticas;
- paleta US basada en PANTONE 123 CVC, PANTONE 201 CVC y negro;
- portada, títulos de diapositiva y separadores de sección, sin barra inferior;
- logotipo de la Universidad de Sevilla en la portada;
- entornos matemáticos en español: teorema, proposición, lema, corolario,
  definición, ejemplo, ejercicio, demostración y solución, sin fondos
  coloreados;
- demostraciones y soluciones divisibles automáticamente entre diapositivas;
- dependencias limitadas a Beamer y los paquetes estándar `amsmath` y
  `amssymb`;
- compatible con pdfLaTeX y pensado para TeX Live en macOS y Texifier en iOS.

## Uso

Copia `beamerthemeTeaching.sty` y el directorio `assets/` junto al fichero
principal de la presentación y escribe en el preámbulo:

```tex
\documentclass[aspectratio=169,11pt]{beamer}
\usepackage[utf8]{inputenc}
\usepackage[T1]{fontenc}
\usepackage[spanish]{babel}
\usetheme{Teaching}
```

El tema utiliza `assets/logo-us.png` como logotipo de portada. Puede sustituirse
con `\titlegraphic{...}` o suprimirse con `\titlegraphic{}` después de cargar el
tema.

El separador automático al comienzo de cada sección está activado por defecto.
Puede desactivarse con:

```tex
\usetheme[nosectionpages]{Teaching}
```

## Demostraciones en varias diapositivas

Los entornos `proof` y `solution` tienen una presentación ligera, sin cajas, y
pueden dividirse automáticamente mediante la opción `allowframebreaks`. El
cuadrado de cierre queda al final del entorno y aparece únicamente en la última
diapositiva:

```tex
\begin{frame}[allowframebreaks]{Teorema fundamental}
  \begin{theorem}
    % Enunciado
  \end{theorem}

  \begin{proof}
    % Demostración completa
  \end{proof}
\end{frame}
```

Beamer escoge los puntos de división. Puede indicarse un punto preferido o
forzar un salto con `\framebreak` sin cerrar el entorno `proof`. Los entornos
`proofpart` y `solutionpart` se conservan como alternativa cuando se quieran
diseñar las diapositivas por separado.

## Ejercicios y soluciones

El entorno `exercise` contiene el enunciado y usa letra redonda. El entorno
`solution` contiene la solución y se comporta como una demostración:

```tex
\begin{frame}{Ejercicio}
  \begin{exercise}
    % Enunciado
  \end{exercise}
\end{frame}

\begin{frame}[allowframebreaks]{Solución}
  \begin{solution}
    % Solución completa; puede contener \framebreak
  \end{solution}
\end{frame}
```

No es necesario dividir la solución manualmente. El título de la diapositiva
recibe en las continuaciones la marca que proporciona Beamer, y el cuadrado se
mantiene en la última.

## Ejemplo

Desde la raíz del repositorio:

```sh
latexmk -pdf examples/ejemplo.tex
```

También puede compilarse directamente desde `examples/`, como suele hacer
Texifier. El ejemplo añade las rutas `../` y `./` a la búsqueda de ficheros
para localizar `beamerthemeTeaching.sty` en ambos casos.

Para eliminar los ficheros auxiliares:

```sh
latexmk -C examples/ejemplo.tex
```

## Próximos pasos

- separar el núcleo del tema de las variantes US y UNED;
- añadir soporte explícito para inglés;
- preparar plantillas para asignaturas completas y tutorías.
