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
- entornos matemáticos en español: teorema, proposición, lema, corolario,
  definición, ejemplo, ejercicio, demostración y solución, sin fondos
  coloreados;
- segmentos para demostraciones y soluciones que ocupan varias diapositivas;
- dependencias limitadas a Beamer y los paquetes estándar `amsmath` y
  `amssymb`;
- compatible con pdfLaTeX y pensado para TeX Live en macOS y Texifier en iOS.

## Uso

Copia `beamerthemeTeaching.sty` junto al fichero principal de la presentación y
escribe en el preámbulo:

```tex
\documentclass[aspectratio=169,11pt]{beamer}
\usepackage[T1]{fontenc}
\usepackage[spanish]{babel}
\usetheme{Teaching}
```

El separador automático al comienzo de cada sección está activado por defecto.
Puede desactivarse con:

```tex
\usetheme[nosectionpages]{Teaching}
```

## Demostraciones en varias diapositivas

Los entornos de LaTeX no deben permanecer abiertos entre dos entornos `frame`.
Para una demostración larga, se usa `proofpart` en todos los segmentos salvo el
último. Solo el último segmento, escrito con `proof`, muestra el cuadrado final:

```tex
\begin{frame}{Teorema fundamental}
  \begin{theorem}
    % Enunciado
  \end{theorem}
  \begin{proofpart}
    % Primera parte de la demostración
  \end{proofpart}
\end{frame}

\begin{frame}{Teorema fundamental}
  \begin{proof}[\proofcontinuationname]
    % Última parte de la demostración
  \end{proof}
\end{frame}
```

Si hacen falta más de dos diapositivas, los segmentos intermedios también usan
`proofpart`, opcionalmente con el título
`[\proofcontinuationname]`.

## Ejercicios y soluciones

El entorno `exercise` contiene el enunciado y usa letra redonda. El entorno
`solution` contiene la solución y se comporta como una demostración:

```tex
\begin{frame}{Ejercicio}
  \begin{exercise}
    % Enunciado
  \end{exercise}
\end{frame}

\begin{frame}{Solución}
  \begin{solutionpart}
    % Primera parte de la solución
  \end{solutionpart}
\end{frame}

\begin{frame}{Solución}
  \begin{solution}[\solutioncontinuationname]
    % Última parte de la solución
  \end{solution}
\end{frame}
```

Como en las demostraciones, se usa `solutionpart` en todos los segmentos no
finales. Puede escribirse
`\begin{solutionpart}[\solutioncontinuationname]` para marcar expresamente las
continuaciones.

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
