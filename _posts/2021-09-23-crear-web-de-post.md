---
layout: single
title: Cómo crear tu web de posts con jekyll
date: 2021-09-23
classes: wide
header:
  teaser: https://avatars.githubusercontent.com/u/3083652?s=200&v=4
categories:
  - github-pages
tags:
  - github-pages
  - jekyll
  - jekyll-theme
---
**Jekyll** es una herramienta hecha con ruby, con la cual podremos crear nuestra web de post simplemente utilizando el lenguaje de marcado(*markdown*) .

Otra herramienta que utilizaremos en **github**. Ésta nos estará hosteando nuestra web totalmente free.

Recursos:
---
1. JekyllThemes [JekyllThemes](http://jekyllthemes.org/)
2. Jekyll [Jekyll](https://jekyllrb.com/)
3. Tema el que yo he utilizado [slemire](https://github.com/slemire/slemire.github.io)
4. Tema el que yo he utilizado [s4vitar](https://github.com/s4vitar/s4vitar.github.io)
5. Video de s4vitar en youtube [video-s4vitar](https://www.youtube.com/watch?v=OZDKNqMXSxA)

---

### Comenzemos
---------------
Con `jekyll` podemos crear nuestra propia plantilla desde cero, pero en este caso se harán las cosas sencillas. Como ejemplo seleccionaremos un tema el que mas nos interese, como es el de [s4vitar](https://github.com/s4vitar/s4vitar.github.io). Siempre para apoyar al autor haremos un fork de su repositorio github y luego comenzamos a modificarlo a nuestro gusto. Ésto lo podemos realizar dentro de _github_ utilizando la herramienta de edición ubicado en la parte superior derecha.
<p align="center">
    <img src="/assets/images/crear-web-de-post/edit-config.png">
</p>
En el archivo `_config.yml` modificaremos las informaciones que deseemos, como ejemplo en el apartado de **Site Settings** los valores de locale, title, url y etc para dejar la pagina web con nuestros datos.

```yml
# theme                  : "minimal-mistakes-jekyll"
remote_theme             : "mmistakes/minimal-mistakes@4.15.1"
minimal_mistakes_skin    : "dark" #"haxor" "air", "aqua", "contrast", "dark", "dirt", "neon", "mint", "plum", "sunrise"

# Site Settings
locale                   : "es-PY"
title                    : "nelson-lz"
title_separator          : "-"
name                     : "nelson-lz"
description              : "Posts sobre TI y desarrollo de aplicaciones"
url                      : "https://nelson-lz.github.io" # the base hostname & protocol for your site e.g. "https://mmistakes.github.io"
baseurl                  : # the subpath of your site, e.g. "/blog"
repository               : "nelson-lz/nelson-lz.github.io" # GitHub username/repo-name e.g. "mmistakes/minimal-mistakes"
logo                     : "/assets/images/masthead.png"
teaser                   : # path of fallback teaser image, e.g. "/assets/images/500x300.png"
breadcrumbs              : true # true, false (default)
words_per_minute         : 200
```

### Github-Pages
---------------
Para que github hostee nuestra página únicamente debemos renombrar el repositorio con éste formato `nombre-usuario.github.io`.
<p align="center">
    <img src="/assets/images/crear-web-de-post/settings-rename.png">
</p>
Luego ingresando en el menú settings->Pages aquí podemos seleccionar la rama la cual github estará desplegando cada vez que haya algún cambio. Además si tuvieramos un dominio propio tambien podriamos indicarlo en este apartado. O tambien en el archivo `CNAME` dentro del proyecto.
<p align="center">
    <img src="/assets/images/crear-web-de-post/settings-pages.png">
</p>

### Estructura
---------------
<p align="center">
    <img src="/assets/images/crear-web-de-post/structure.png">
</p>
Ésta es la estructura del proyecto, los básicos a tener en cuenta son:
- Directorio `_pages`: es donde estan nuestras páginas con extensión .md (markdown). Tenemos los atributos title, layout, permalink y date donde layout indica cuál de los archivos del directorio `_layout` utilizará los datos de éste archivo. Este ejemplo sería `about.md`.

```markdown
---
title: "Información del autor"
layout: archive
permalink: /about/
date: 2021-09-23
---
```
- Archivo de configuración `_config.yml`: en éste archivo de tipo *yamel* es donde podemos configurar la mayor parte de la página, además de lo que ya habiamos mencionado mas arriba también podemos configurar nuestras `redes sociales, correo, google analytics, google site verifications, el tema` y etc.

```markdown
# Site Author
author:
  name             : "nelson-lz"
  avatar           : "https://avatars.githubusercontent.com/u/51168982?v=4"
  bio              : "Lic. en Análisis de Sistemas"
  location         : "Paraguay-Alto Paraná"
  email            : "mail@outlook.com"
  uri              : "nelsonlz.github.io"
  home             : # null (default), "absolute or relative url to link to author home"
  bitbucket        : "nelson-lz"
  codepen          :
  dribbble         :
  flickr           :
  facebook         :
  foursquare       :
  github           : "nelson-lz"
```
> Todo esto simplemente lo podemos editar desde la herramienta de edición de github al seleccionar uno de los archivos. Si consideran que algo de la información proporcionada esta equivocada por favor no dude en enviar un correo informandome les esteré muy agradecido. Saludos.
