---
layout: post
title: Cómo tomo mis notas de ingeniería utilizando Vim y GitHub pages
tag: Vim Neovim
reading_time: 15
date_shown: 14 Ago 2021
excerpt_separator: <!--intro-->
---

Soy el tipo de persona que gusta de tener buenos apuntes 🤓, porque sé que mi yo del futuro me lo va a agradecer. Sin embargo, al iniciar la pandemia por Covid 19 😷 y con eso, las clases en línea en la universidad, tomaba todas mis clases en la laptop mientras escribía mis apuntes en el cuaderno. Realmente era algo incómodo ☹, pues ocupaba mucho más espacio que antes y desde mi punto de vista no tenía sentido que siguiera haciéndolo de esa manera, teniendo la PC encendida.

<!--intro-->

## Qué es lo que busco en una herramienta de notas?
1. **Notas al ritmo de la clase** 👨‍🏫💨.
    Necesito ser capaz de escribir enunciados claros, ideas y palabras clave, pero al ser clase de ingeniería, debo de poder incluir ecuaciones matemáticas, gráficos y código en diferentes lenguajes.
2. **Temas estructurados, resaltar ideas y dejar notas para mi yo futuro** 🧱.
    Me refiero a que los temas estén bien delimitados y que de forma rápida pueda ojear los apuntes e identificar dónde está lo que busco. Esto lo hago usando títulos, diferentes tipos de letra y colores.
3. **Corrección de errores** 🚧.
    En una libreta, normalmente uso corrector para maquillar los errores, además, los errores más grandes implican realizar el apunte de nuevo. En este punto, las notas digitales ayudan muchísimo.
4. **Practicidad de uso** 🗸.
    Una de las ventajas que tiene un cuaderno frente a la computadora, es que sólo hay que abrirlo y buscar entre sus hojas, mientras que para la computadora hay que esperar a que encienda, luego buscar los archivos y abrirlos. Además una libreta se puede cargar donde sea y una laptop es mucho más pesada, por ende es más difícil de llevar a todos lados.
5. **Facilidad para compartir** 🔗.
    Muchas veces mis compañeros de clase me pedían mis notas para estudiar o ponerse al día con los temas. En ese sentido, es mejor tener apuntes digitales porque en el caso del cuaderno, se requiere tomar fotocopias o prestarlo 🥴. Y obviamente pasar un simple archivo sería más fácil... Claro!, siempre y cuando la otra persona no necesite instalar nada nuevo para verlo.

## Manos a la obra
Para encontrar la herramienta adecuada, comencé probando distintas alternativas, primero con [*Cherry Tree*](https://www.giuspen.com/cherrytree/) que tiene una muy buena organización de las notas, pero no tiene soporte para escribir matemáticas, luego con [*Word*](https://office.live.com/start/Word.aspx?ui=es%2DES) y aunque se pueden tomar notas con ecuaciones matemáticas, no es nada rápido y la organización de las notas tampoco lo es.

Así llegué a [*Joplin*](https://joplinapp.org/) donde encontré una gran herramienta que me permitió usar [markdown](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet), [KaTeX](https://katex.org/docs/supported.html), [Vim](https://missing.csail.mit.edu/2020/editors/), y tenía plugins muy interesantes que me convencieron de hacer mis notas ahí por dos semestres. Vim hacia que pudiera escribir todo muy rápido y es lo que más me gustaba.

Pero en ocasiones el profesor iba muy rápido, y por más que intentaba, tenía que concentrarme sólo en escribir ecuaciones y dejaba de comprender el tema 🥴, o incluso tenía que quedarme más tiempo ya concluida la clase, para terminar el apunte 😔.

## Snippets?

En `Vim`, yo ya estaba familiarizado con el uso de snippets, que utilizo mucho al momento de programar y hacen que todo sea más rápido, les recomiendo ver [este tutorial](https://missing.csail.mit.edu/2020/editors/).

Los snippets sirven para autocompletar al momento de escribir una palabra.

![snippets intro](/blogger/assets/snippetsIntro.gif)

Sólo tengo que escribir `intro` y `firma` , presionar `<TAB>` y luego `ENTER` para insertar un texto predefinido. Esto hace una diferencia enorme al momento de de escribir código $\KaTeX$.

![snippets con sin](/blogger/assets/snippetsComparison.gif)

A la izquierda se muestra el caso sin utilizar snippets y del lado derecho con snippets, que es más rápido. El snippet lo defino con anterioridad y está configurado para desplegarse de forma automática, **sin** tener que **oprimir nada**.

En Joplin no se puede hacer esto puesto que sólo tiene un emulador de `Vim` al escribir. Para implementar los plugins necesarios necesitamos `Vim` tal cual.

## Setup
Así se ve cuando tomo notas para mi clase:

![workflow](/blogger/assets/workflow.gif)

Al terminar la clase, dado que las notas están como archivos markdown `.md` en un repositorio `git`, sólo hago un commit y acto seguido, tengo el apunte listo en mi página web. [He aquí el apunte del ejemplo](https://danielhj.com/studious/notes/7mo%20Semestre/Control%20de%20Sistemas%20Mecatr%C3%B3nicos/Discretizaci%C3%B3n%20de%20ecuaciones%20en%20espacio%20de%20estado.html).

Me encanta este arreglo 🤩, puesto que puedo seguir el ritmo de la clase. Todo está a unos cuantos comandos de distancia y al final tengo un apunte bien organizado y muy limpio, al cual puedo acceder desde cualquier dispositivo y puedo compartirlo fácilmente.

### ¿Cómo funciona?

#### SO
Utilizo [WSL](https://docs.microsoft.com/en-us/windows/wsl/install-win10) que es el subsistema de Windows para Linux, así puedo tener una máquina virtual de Linux de forma nativa en Windows. En concreto uso [WSL 2](https://docs.microsoft.com/en-us/windows/wsl/install-win10#step-2---check-requirements-for-running-wsl-2) que permite tener prácticamente la mayoría de las funcionalidades de un sistema Linux, cosa que WSL 1 no puede dar.
Instalé [Ubuntu](https://www.microsoft.com/store/apps/9n6svws3rx71), pero cualquier [distribución](https://docs.microsoft.com/en-us/windows/wsl/install-win10#step-6---install-your-linux-distribution-of-choice) funciona.

#### Editor de texto
Lo siguiente y más importante es el editor de texto, en este caso [Neovim](https://neovim.io/), es básicamente un fork de [Vim](https://github.com/vim/vim), pero que mantiene la comunidad (ya que Vim es mantenido por su creador). Es un editor de texto desde la línea de comandos, es súper personalizable, tiene su propio lenguaje de programación y existen muchísimos plugins que permiten hacer de todo con él y de formas muy eficientes. De hecho está diseñado para utilizar únicamente el teclado.

##### Plugins
Los plugins que utilizo son los siguientes:
* [Vim-plug](https://github.com/junegunn/vim-plug): Este es el administrador de plugins, hace que sea mucho más rápidos instalarlos y desinstalarlos.
* [VimWiki](https://github.com/vimwiki/vimwiki): El administrador de notas que nos ayuda a crear notas de forma fácil, administrarlas y acceder a ellas de forma rápida.
    ![vimwiki navigation](/blogger/assets/vimwikiNav.gif)

    La creación de nuevas notas se hace de forma automática al crear un link:
    ![vimwiki creation](/blogger/assets/vimwikiNewNote.gif)

    En mi `.config/nvim/init.vim` (equivalente a `.vimrc`) tengo esta configuración. Primero para crear la vimwiki donde albergo mis notas escolares, utilizando sólo archivos tipo markdown:

    ```vim
    let studiousWiki = {}
    let studiousWiki.path = '/mnt/c/Users/Dani/Documents/Tareas/studious/'
    let studiousWiki.syntax = 'markdown'
    let studiousWiki.ext = '.md'
    let g:vimwiki_list = [studiousWiki]
    ```

    La siguiente configuración es necesaria para que no interfiera la funcionalidad de `<TAB>` en vimwiki para saltar entre links, con la de `coc-snippets` para navegar entre snippets:


    ```vim
    let g:vimwiki_global_ext = 0
    let g:vimwiki_key_mappings = { 'table_mappings': 0, }
    let g:vimwiki_table_mappings = 0
    ```

* [Markdown Preview](https://github.com/iamcco/markdown-preview.nvim): Permite generar una página web estática con base en archivos markdown (`.md`, `.markdown`), es el plugin que nos permite visualizar las notas en el navegador en tiempo real. Ya incluye soporte para renderizar varias cosas útiles como [KaTeX](https://katex.org/) y [mermaid](https://mermaid-js.github.io/mermaid/#/).

    ![markdown preview](/blogger/assets/markdownPreview.gif)

    Como configuración mapeo `<Ctrl-E>` como hotkey para abrir y cerrar la visualización previa. Defino como será el comportamiento de seguir el cursor y  los saltos de línea (↵ = `<br>`).

    ```vim
    nmap <C-e> <Plug>MarkdownPreviewToggle
    let g:mkdp_preview_options = {
        \ 'mkit': {"breaks": 1},
        \ 'sync_scroll_type': 'middle',
        \ }
    ```

* [Vim Markdown](https://github.com/plasticboy/vim-markdown): Es un *syntax highlighter* que pone de distintos colores lo que escribimos en un archivo markdown para poder identificar de qué se trata (títulos, cuerpo, listas, código, etc.). Aunque vimwiki ya hace esto por nosotros, a veces uno quiere escribir un archivo `.md` sin tener que adjuntarlo a la wiki.

    En la configuración sólo activo la extensión de matemáticas y desactivo el *folding*:
    ```vim
    let g:vim_markdown_folding_disabled = 1
    let g:vim_markdown_math = 1
    ```
* [coc-snippets](https://github.com/neoclide/coc-snippets): Este es el motivo por el cual elijo este setup. Permite crear nuestros propios snippets, esta extensión está basada en [UltiSnips](https://github.com/SirVer/ultisnips) y tiene la mayoría de sus funcionalidades. Es necesario instalar primero [coc](https://github.com/neoclide/coc.nvim), que es un plugin que permite añadir funcionalidades de completar texto, linters y highlighting en distintos lenguajes. Coc-snippets es una extensión de coc.

    Se configura este para darle a `<TAB>` la funcionalidad de pasar al siguiente snippet de la lista, y con `<ENTER>` se expande.

    ```vim
    inoremap <silent><expr> <TAB>
      \ pumvisible() ? coc#_select_confirm() :
      \ coc#expandableOrJumpable() ? "\<C-r>=coc#rpc#request('doKeymap',['snippets-expand-jump',''])\<CR>" :
      \ <SID>check_back_space() ? "\<TAB>" :
      \ coc#refresh()

    function! s:check_back_space() abort
      let col = col('.') - 1
      return !col || getline('.')[col - 1]  =~# '\s'
    endfunction

    let g:coc_snippet_next = '<tab>'
    xmap <Tab> <Plug>(coc-snippets-select)
    ```

#### Snippets!
Los snippets que más utilizo son para ecuaciones matemáticas, por ejemplo para agilizar las fracciones, matrices, estructuras de casos, etc. No pondré aquí todos para no alargar mucho el post y porque hay un [artículo](https://castel.dev/post/lecture-notes-1/#snippets) muy bueno de Gilles Castell (que fue fuente de inspiración para este post) donde explica qué son los snippets más a fondo y los que él usa. Les recomiendo ver [todos sus snippets](https://github.com/gillescastel/latex-snippets/blob/master/tex.snippets) para $\LaTeX$, yo uso algunos de ahí y los de UltiSnips de su artículo.

Sin embargo, él los usa para $\LaTeX$ en archivos `.tex`, nosotros usamos $\KaTeX$ en archivos `.md`, al ser diferentes lenguajes, el text highlighter que utilizan es diferente y los [snippets de contexto](https://castel.dev/post/lecture-notes-1/#context) no servirían.

El contexto hace que el snippet se expanda solamente si se encuentra bajo cierto *contexto*, es decir si ciertas **condiciones** se cumplen, en nuestro caso se puede usar a favor para expandir ciertos snippets sólo cuando se está en un entorno matemático:

![snippets context](/blogger/assets/snippetsContext.gif)

Como se puede ver, el snippet `bmatrix` sólo se expande cundo está entre `$$ $$` o `$ $`, es decir, sólo cuando está en un entorno matemático. De hecho se colorea de diferente color, esto es hecho por el highlighter, ya sea el de VimWiki o el de Vim Markdown.

Utilizando esta información, en el archivo de snippets para archivos markdown (que se abre con `:CocCommand snippets.editSnippets` en Neovim) se puede introducir el siguiente código para definir el contexto matemático:

```python
global !p
texMathZones = ['texMathZone' + x for x in ['X', 'Y']] + ['mkdMath'] + ["VimwikiMath", "VimwikiEqIn", "textSnipTEX", "texStatement"]
texIgnoreMathZones = ['texMathText']
texMathZoneIds = vim.eval('map('+str(texMathZones)+", 'hlID(v:val)')")
texIgnoreMathZoneIds = vim.eval('map('+str(texIgnoreMathZones)+", 'hlID(v:val)')")
ignore = texIgnoreMathZoneIds[0]

def math():
    synstackids = vim.eval("synstack(line('.'), col('.') - (col('.')>=2 ? 1 : 0))")
    try:
        first = next(i for i in reversed(synstackids) if i in
        texIgnoreMathZoneIds or i in texMathZoneIds)
        return first != ignore
    except StopIteration:
        return False
endglobal
```

Luego para definir el snippet de `bmatrix` bajo este contexto:

```python
context "math()"
snippet bmatrix "[matrix]" iAe
\begin{bmatrix}
	$0
\end{bmatrix}
endsnippet
```

> Para no definir doblemente todos los snippets (para vimwiki y para markdown), conviene importar los snippets en el archivo que menos se modifica, por ejemplo esto lo puse en el archivo de snippets de vimwiki:
>```python
>extends markdown
>```

## Página web de notas
Finalmente, explicaré como luego de tomar mis notas, puedo subirlas a mi página web, la cual pueden consultar [aquí](https://danielhj.com/studious/).

Utilizo [GitHub Pages](https://pages.github.com/) con [Jekyll](https://docs.github.com/en/pages/setting-up-a-github-pages-site-with-jekyll/about-github-pages-and-jekyll), así puedo armar una página web estática donde sólo tengo que subir un nuevo archivo markdown para tener una nueva nota, que tenga el formato que quiero.

Instalé Jekyll, creé un nuevo proyecto y siguiendo las indicaciones del `Gemfile` adapté el proyecto para GitHub pages:

``` ruby
#gem "jekyll", "~> 4.2.0"
# If you want to use GitHub Pages, remove the "gem "jekyll"" above and
# uncomment the line below. To upgrade, run `bundle update github-pages`.
gem "github-pages", group: :jekyll_plugins
```

Así pues, corrí `bundle install` seguido de `bundle update` que también actualiza el bundle `github-pages`.

No es la intención de este post describir como hice la página web como tal, pero hay algunas cosas que me parecen interesantes y tal vez les puedan ayudar.

> Jekyll tiene soporte para `Sass` integrado y por tanto sólo hay que hacer un `main.scss` para utilizarlo y así lo hice.

Jekyll permite crear plantillas de páginas html, basta con especificar en un archivo markdown o html, qué plantilla se quiere usar y al convertirse, tendrá la estructura general de ese plantilla. Así pues, creé el layout `_layouts/default.html` donde está el código para utilizar $\KaTeX$ y `mermaid`. Luego hice dos layouts que extienden a `default.html`: `notes.html` y `index.html` para las notas y los menús respectivamente. Creé un directorio donde se encuentran las notas y los menús correspondientes, que es el mismo donde está la vimwiki.

La estructura de directorios quedó de la siguiente manera (omitiendo los directorios ocultos):

```
 .
├── 404.html
├── _config.yml
├──  css
│   ├── code.css
│   └── main.scss
├── favicon.ico
├── Gemfile
├── Gemfile.lock
├──  _includes
│   └──  icons
├── index.md
├──  _layouts
│   ├── default.html
│   ├── index.html
│   └── note.html
├──  notes
│   ├──  6to Semestre
│   ├──  7mo Semestre
│   ├──  8vo Semestre
│   └──  img
├── README.md
└──  _site
```

### Integración de $\KaTeX$ en GitHub Pages con Jekyll

Para poder utilizar $\KaTeX$ en GitHub pages de la misma forma que lo implementa Markdown Preview, con `$$ $$` para bloques matemáticos y `$ $` para matemática en línea, es necesario configurarlo. Primero en `./_config.yml`:

```yml
markdown: kramdown

kramdown:
    input: GFM #Saltos de línea = 
    hard_wrap: true
    math_engine: katex
```

Se configura el interprete de markdown como `kramdown`, que tiene [soporte](https://kramdown.gettalong.org/math_engine/katex.html) para $\KaTeX$, luego se configura el input como `GFM` para que los saltos de línea sean igual que un `<br>` (si no, sería [así](https://gist.github.com/shaunlebron/746476e6e7a4d698b373)). El motor de matemáticas se configura como `katex`.

Ahora se manda a llamar a $\KaTeX$ en el `<head>`, en mi caso en el `./layouts/default.html`. Pero también se manda a llamar al método que cambia los delimitadores y desactiva el display, así se puede usar `$ $` para *in-line math*.

```html
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/katex@0.11.1/dist/katex.min.css" integrity="sha384-zB1R0rpPzHqg7Kpt0Aljp8JPLqbXI3bhnPWROx27a9N0Ll6ZP/+DiW/UqRcLbRjq" crossorigin="anonymous">

    <script defer src="https://cdn.jsdelivr.net/npm/katex@0.11.1/dist/katex.min.js" integrity="sha384-y23I5Q6l+B6vatafAwxRu/0oK/79VlbSz7Q9aiSZUvyWYIYsd+qj+o24G5ZU2zJz" crossorigin="anonymous"></script>
    <script defer src="https://cdn.jsdelivr.net/npm/katex@0.11.1/dist/contrib/auto-render.min.js" integrity="sha384-kWPLUVMOks5AQFrykwIup5lo0m3iMkkHrD0uJ4H5cjeGihAutqP0yW0J6dpFiVkI" crossorigin="anonymous" onload="renderMathInElement(document.body);"></script>
    <script defer src="https://cdn.jsdelivr.net/npm/katex@0.11.1/dist/contrib/auto-render.min.js"
        onload="renderMathInElement(document.body, { delimiters: [ {left: '$', right: '$', display: false} ], throwOnError: false });"></script>
```

### Integración de `mermaid` en GitHub Pages con Jekyll
Instalé también [mermaid](https://github.com/mermaid-js/mermaid/blob/develop/docs/usage.md) para renderizar los gráficos de flujo, estado, de Gantt, etc. y cambié el tema por uno de mi elección.

En el `<head>`:

```html
<script src="https://cdn.jsdelivr.net/npm/mermaid/dist/mermaid.min.js"></script>
```

Como tal, kramdown no detecta mermaid cuando se declara como bloque de código de la siguiente forma:

    ```mermaid

    ```

Para habilitar esto es necesario activar `htmlLabels`. También modifico el tema en el siguiente código que va después del `<body>`:

```html
<script>
    var config = {
        startOnLoad:true,
        theme: 'forest',
        flowchart:{
                useMaxWidth:false,
                htmlLabels:true
            }
    };
    mermaid.initialize(config);
    window.mermaid.init(undefined, document.querySelectorAll('.language-mermaid'));
</script>
```

### Workflow
Con este setup, lo único que tengo que hacer es agregar una entrada en el archivo `index.md` hacia la nota `<título de la nota>.md`, agregar el front matter al inicio del archivo creado para utilizar el layout de `note`:

```
---
layout: note
---
```

Escribo algo y hago un commit al repositorio en GitHub y automáticamente se despliega en la página.

Algo que ayuda bastante es que no necesito poner los títulos manualmente, pues en la página se muestran con el nombre del archivo como título de la nota. Además en los índices, se muestra un árbol de los directorios con links a los índices correspondientes. Todo esto se hace se forma automática y en este [artículo](/#) explico como se hace.


## Conclusiones
Este setup cumple con los requisitos que plantee sobre una buena herramienta para tomar mis notas y personalmente me encanta 🤩.

La única deficiencia que puede tener este arreglo es al momento de dibujar, pues no es muy cómodo hacerlo en la PC y aunque se pueden obtener dibujos incluso mejores, hacerlo implica mucho tiempo.

Quiero implementar más cosas a este setup, que pueden ayudar a corregir esto y me guiaré de este [artículo](https://castel.dev/post/lecture-notes-2/) para implementarlo en `WSL`. También me gustaría implementar búsqueda entre las notas en la página web.
