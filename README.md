EyMIETeX
========================

> Template de Tesis para la Especialización y Maestría en Ingeniería Estructural de la Universidad Tecnológica Nacional (UTN)

[![License MIT](http://img.shields.io/badge/license-MIT-brightgreen.svg)](license.md)

## Autor
*   Ing. Mihdí Caballero

--------------------------------------------------------------------------------
## Características

* Cumple con las pautas de tesis de maestría de la [Circular 2/2003](https://www.frbb.utn.edu.ar/frbb/info/secretarias/academica/carreras/posgrado/man/normativa/circular-2-2003.pdf) y [Circular 2/2020](https://www.frd.utn.edu.ar/circular-2-2020/) del Rectorado de la Universidad Tecnológica Nacional.

* Página de título con escudos universitario.

* Versión impresa / en línea: Distintos estilos de diseño e hiperreferenciación para cada caso.

* Fuentes predefinidas.

* Soporte de estilo de bibliografía predefinido para APA 6 en español.

* Estilos de página predefinido.

* Tamaño de margen predefinido.

* Opción para generar solo capítulos y referencias específicas sin portada ni portada. Útil para revisión y correcciones.

* Modo borrador: Borrador de marca de agua, marca de tiempo, numeración de versión y numeración de línea

-------------------------------------------------------------------------------

## Detalles de uso

La información de la tesis, como título, autor, año, grado, etc., y otros metadatos se pueden modificar en `tesis-info.tex`

### Opciones de clase

El archivo de clase, `EyMIETeX`, se basa en la clase estándar `book`.

Admite las siguientes opciones personalizadas en la clase de documento en `tesis.tex`:

*   `index`: Incluyendo esta opción se construye el índice, que se coloca al final de la tesis.

    Las instrucciones sobre cómo usar el índice se pueden encontrar [aquí](http://en.wikibooks.org/wiki/LaTeX/Indexing#Using_makeidx).

*   `chapter`: Esta opción habilita solo el capítulo especificado y sus referencias. Útil para revisión y correcciones.

*   `draft`: El modo de borrador predeterminado admite algunas funciones especiales, como números de línea, imágenes y marca de agua con
     marca de tiempo y texto personalizado. La posición del texto se puede modificar en `_settings/preamble.tex`.

*	`oneside` o `twoside`: Alterna la impresión de las hojas en simple fazo en doble faz, respectivamente.

*	`print`: Para imprimir en papel, sin hiperreferencias y todas las referencias en negro.     

### Página de título

La página principal (página de título) cambia de tamaño para adaptarse a la longitud de su título y cantidad de directores y co-directores. Puede modificar las opciones en `tesis-info.tex`.

### Modo capítulo

*  El modo de capítulo permite al usuario imprimir solo capítulos específicos junto con las referencias. De forma predeterminada, excluye todo lo demás en la parte delantera y los apéndices. Esto se puede hacer usando la opción `chapter` en la clase de documento en `tesis.tex`. Ignore las advertencias posteriores sobre la omisión de secciones (si las hay).

* Para generar el resumen y la portada por separado, asegúrese de que los siguientes comandos estén en la sección de preámbulo del archivo `tesis.tex`:

		\ifdefineChapter
			\includeonly{Capitulos/capitulo1}
		\fi

### Borrador

`draft` agrega la marca de agua con el texto `borrador` con marca de tiempo y número de versión en la parte inferior de la página. La numeración de línea por página se agrega en cada página. La configuración del `draft` se puede modificar en `preamble.tex`.

* Para agregar figuras en modo borrador (habilitado por defecto), en el preámbulo establezca `\setkeys{Gin}{draft=false}`. `draft=true` deshabilita las figuras.

* Para cambiar el texto de la marca de agua:
      \SetDraftText{Borrador}

* Para cambiar la posición del texto de la marca de agua. La posición predeterminada de la marca de agua es superior. La ubicación se puede cambiar a (top / bottom)
      \SetDraftWMPosition{bottom}

* Para cambiar la versión de borrador. La versión de borrador predeterminada es v1.0.
      \SetDraftVersion{v1.1}

### Referencias bibliográficas
* Para poder procesar correctamente la bilbiografía en LaTeX hay que ajustar el orden de compilación por defecto que viene en cualquier programa que trabaje con archivos .tex. En este caso, se muestra el ejemplo con TeXstudio.

Lo que hay que hacer es ir a `Opciones > Configurar TeXstudio` y dentro de la pestaña `Compilar` se debe ajustar los comandos de Compilador por defecto y Herramienta
bibliográfica por defecto. Para el primer caso, se hace clic en el botón `Configurar` y se debe dejar la siguiente secuencia de órdenes:

`PdfLaTeX > Biber > PdfLaTeX > PdfLaTeX`

Para el caso de configuraciones de bibliografía solo debe tener la órden de Biber. 

Para más información sobre referencias bibliográficas en LaTeX y la configuración ir a este [link.]{https://github.com/mihdicaballero/LaTeX-Projects/tree/main/BibLaTeX_guide_ES}


### Definición de nomenclatura

* Para usar la nomenclatura en sus capítulos:

        \nomenclature[g-pi]{$\pi$}{ $\simeq 3.14\ldots$}

    Las claves de clasificación tienen un prefijo. En este caso, se usa un prefijo de `g` para indicar símbolos griegos, seguido de `-pi` o `-sort_key`. Use un `-` para separar la clave de clasificación de los prefijos. Los prefijos estándar definidos en esta clase son:
    
	 * `A` o `a`: Símbolos Romanos

     * `G` o `g`: Símbolos Griegos

     * `Z` o `z`: Acrónimos/Abreviaturas

     * `R` o `r`: Superíndices

     * `S` o `s`: Subíndices

     * `X` o `x`: Otros Símbolos


 La opción de compilación predeterminada de TexStudio no incluye `nomenclature`, para compilar su documento con la nomenclatura, haga doble clic en el archivo 
`compile-thesis-windows.bat` en la carpeta de la tesis (tener el PDF cerrado) en Windows  sino ejecute `make` en Unix / Linux / MacOS.

## To-do Notes

Para incluir notas de tareas personalizadas en su documento pdf, use `\mynote{Tengo una nota}` en cualquier parte de sus capítulos. Para activar esta función, debe descomentar las siguientes líneas en `preamble.tex`. Las notas de tareas estarán disponibles solo en el "borrador" y no en la tesis final.

	\ifsetDraft
		\usepackage[colorinlistoftodos]{todonotes}\setlength{\marginparwidth}{3cm}\reversemarginpar
		\newcommand{\mynote}[1]{\todo[author=Nombre,size=\small,inline,color=green!40]{#1}}
	\else
		\newcommand{\mynote}[1]{}
		\newcommand{\listoftodos}{}
	\fi

--------------------------------------------------------------------------------

## Bugs o sugerencias de mejora

*   Open issues se pueden ver en [https://github.com/mihdicaballero/EyMIETeX/issues](https://github.com/mihdicaballero/EyMIETeX/issues). Si desea agregar una nueva característica a la plantilla, cree un problema y etiquételo como una mejora.
*   Por favor [hacer un fork en github](https://github.com/mihdicaballero/EyMIETeX/fork) y cree una "pull request", si desea contribuir al repositorio.

--------------------------------------------------------------------------------

## Aprender LaTeX

* Podés aprender LaTeX viendo los tutoriales que tengo en mi canal de YouTube llamado [Me lo dijo un ingeniero.](https://www.youtube.com/channel/UCqglEznvF-ZnrmDbwQjVpIg)
* Si querés aprender de manera más completa y seria LaTeX, podés ver mi curso online en Udemy llamado [LaTeX - El curso definitivo.](https://www.udemy.com/course/latex-el-curso-definitivo/)
--------------------------------------------------------------------------------

## Basado en

*   Cambridge PhD Thesis Template [https://github.com/kks32/phd-thesis-template](https://github.com/kks32/phd-thesis-template) por Krishna Kumar
