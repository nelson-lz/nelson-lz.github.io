---
layout: single
title: Scraping básico con BeautifulSoup4
date: 2021-11-24
classes: wide
header:
  teaser: https://avatars.githubusercontent.com/u/3083652?s=200&v=4
categories:
  - python
tags:
  - python
  - BeautifulSoup4
---
## En este mini tutorial trataré de explicar cómo extraer algunos datos de una página web, en este caso será de la página web de un supermercado.

<br>

**Qué es SCRAPING** Durante el web scraping (del inglés scraping = arañar/raspar) se extraen y almacenan datos de páginas web para analizarlos o utilizarlos en otra parte. Por medio de este raspado web se almacenan diversos tipos de información: por ejemplo, datos de contacto, tales como direcciones de correo electrónico o números de teléfono, o también términos de búsqueda o URL. Estos se almacenan en bases de datos locales, tablas o texto plano.

**BeautifulSoup4** es un paquete de Python para analizar documentos HTML y XML (incluido el marcado con formato incorrecto, es decir, etiquetas no cerradas). Crea un árbol de análisis para las páginas analizadas que se puede utilizar para extraer datos de HTML, lo que es útil para el web scraping.


Recursos:
---
1. [Pycharm](https://www.jetbrains.com/pycharm/)
2. [BeautifulSoup4](https://pypi.org/project/beautifulsoup4/)
3. [Python3](https://www.python.org/)
4. [Anaconda](https://www.anaconda.com/)

---

### Comenzemos
---
Para comenzar debemos tener instalado en nuestro ordenador python ya que con este lenguaje programaremos. Recomiendo tener instalado `Anaconda`, ésta herramienta nos facilitará mucho la vida. Nos ayudará para que podamos entornos virtuales para cada proyecto con sus respectivas librerías y versiones específicas. Con anaconda podemos crear varios entornos virtuales de desarrollo y en cada virtual_env podremos tener una librería con una versión diferente de acuerdo a los requisitos de cada proyecto. Para más información ver la documentación [AnacondaDoc](https://docs.anaconda.com/).

### `Requeriments.txt`
---
En el directorio de nuestro proyecto podemos tener un archivo de texto con el nombre de requirements.txt en donde definiremos las librerías que necesitamos con la versión correspondiente. *Es opcional*.
```txt
requests~=2.26.0
beautifulsoup4~=4.10.0
```
Luego en cualquier ordenador podremos ejecutar nuestra aplicación sin problemas con las librerias. Instalamos las dependecias con el siguiente comando:
```
$ pip install -r requirements.txt
```

### BeautifulSoup4 y requests
---
Con la librería `requests` haremos la petición a la web deseada y con `BeautifulSoup4` analizaremos y buscaremos en el html obtenido los datos que necesitamos. Con `requests` hacemos una petición a la url para obtener el html, luego con `BeautifulSoup4` analizamos la respuesta que recibimos al hacer la petición get() y el html devuelto lo guardamos en la variable soup, para luego buscar los datos que necesitamos:
```python
req = requests.get(url)

if req.status_code == 200:
    soup = BeautifulSoup(req.text,'html.parser')
    for elem in soup.find_all('li',attrs={'class':'level3'}):
        arrreglo_json = {
            'tipo': 'categoria',
            'descripcion': elem.a.string,
            'link' : elem.a['href'],
        }
        enlaces_categorias['links'].append(arrreglo_json)
    soup.clear()

```
> Con soup.find_all() obtenemos una lista da todas las etiquetas que cumplen con el filtro que hemos puesto, en este caso el tag `li` con el atributo de `class=level3`. En el parámetro `attrs` puede ir una lista de atributos por ejemplo `{'class':'level3 fontbold','id':'123'}`.
---
```html
<li class="inactive level3">
  <a class="collapsed" href="https://superseis.com.py/category/3-almacen-aderezoscondimentos-aceites.aspx">
    Aceites
  </a>
  <ul></ul>
</li>
```
> Al recorrer la lista de elementos encontrados podemos capturar los datos que nos interesan, como en este caso son el nombre y el link de la categoría. Un ejemplo de un elemento de la lista resultante de la búsqueda es el html que esta arriba y vemos que el tag `<li>` tiene como hijos a los tags `<a>` y `<ul>`. Viendo esto podemos capturar el link con `elem.a['href']` y también la descripción con `elem.a.string` utilizamos string al final para obtener solo el texto del tag `<a>`. Para mas información de como utilizar los métodos de BeautifulSoup4 consulta la [documentación](https://beautiful-soup-4.readthedocs.io/en/latest/).
---
---

Pueden tener un ejemplo simple de scraping a una web en mi repositorio [collect-price](git@github.com:nelson-lz/collect-prices.git). Todas las criticas constructivas son bienvenidas. <br>
### Muchas gracias por pasarte por aquí, Saludos. 