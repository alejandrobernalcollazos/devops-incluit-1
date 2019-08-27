# Tarea

## 1 COMO miembro del equipo de desarrollo PUEDO tener acceso al archivo index.html con las configuraciones iniciales PARA empezar a trabajar en nuevos requerimientos

### 1.1 Crear un feature branch con el nombre de la subtask, desde el branch de integración

Ejemplo

```
git checkout -b ALE-14
```

### 1.2 Crear el archivo index.html dentro del feature branch

Puedes hacer esto con tu editor de texto favorito

- Visual Studio Code
- Brackets

### 1.3 Crear la estructura principal del archivo

Con los siguientes tags de html

Puedes tomar este [archivo](https://github.com/alejandrobernalcollazos/abernal/blob/develop/index.html) como ejemplo

- DOCKTYPE
- html
- header
  - meta
    - [viewport meta tag](https://github.com/alejandrobernalcollazos/abernal/blob/develop/index.html)
  - links
    - [normalize.css](https://github.com/alejandrobernalcollazos/abernal/tree/develop/vendor/css)
    - [grid.css](https://github.com/alejandrobernalcollazos/abernal/tree/develop/vendor/css)
    - font "usa la fuente Lato desde [google fonts](https://fonts.google.com/)"
    - [icons](https://unpkg.com/ionicons@4.5.10-0/dist/css/ionicons.min.css)
    - [style.css](https://github.com/alejandrobernalcollazos/abernal/tree/develop/resources/css)
    - [queries.css](https://github.com/alejandrobernalcollazos/abernal/blob/develop/index.html)
- body

### 1.4 Crear la carpeta vendor y dentro la carpeta css

Puedes tomar de referencia esta estructura de [archivos](https://github.com/alejandrobernalcollazos/abernal/tree/develop)

### 1.5 Crear y Guardar los archivos normalize.css y grid.css dentro de vendor/css

Puedes tomar de referencia esta estructura de [archivos](https://github.com/alejandrobernalcollazos/abernal/tree/develop)

### 1.6 Crear la carpeta resources y dentro la carpeta css

Puedes tomar de referencia esta estructura de [archivos](https://github.com/alejandrobernalcollazos/abernal/tree/develop)

### 1.7 Crear y Guardar el archivo style.css dentro de resources/css

Puedes tomar de referencia esta estructura de [archivos](https://github.com/alejandrobernalcollazos/abernal/tree/develop)

### 1.8 Agregar los cambios al repositorio

```
git add .
```

### 1.9 Hacer commit de los cambios con la descripción de la user story

Tener en cuenta que el ticket ALE-14 es solo de ejemplo, debemos usar el número de ticket correspondiente

```
git commit -m "ALE-14 COMO miembro del equipo de desarrollo PUEDO tener acceso al archivo index.html con las configuraciones iniciales PARA empezar a trabajar en nuevos requerimientos"
```

### 1.10 Hacer push del branch al repositorio remoto

Tener en cuenta que el ticket ALE-14 es solo de ejemplo, debemos usar el número de ticket correspondiente

```
git push --set-upstream origin ALE-14
```

### 1.11 Crear un pull request y compartirlo con el instructor de la clase

El pull request debemos hacerlo desde el feature branch al branch de integración

### 1.12 Hacer un merge del pull request

### 1.13 Eliminar el feature branch en github (repositorio remoto) y el repositorio local

## 2 COMO una persona PUEDO ver en cualquier dispositivo, la sección principal del Curriculum Vitae PARA leer y visualizar todos sus componentes

### 2.1 Crear un feature branch con el nombre de la subtask, desde el branch de integración

Ejemplo

```
git checkout -b ALE-15
```

### 2.2 Modificar el archivo index.html 

Agregar el siguiente codigo dentro del tag header

```
<header>
    <nav>
        <div class="row">
            <div class="title">
                <h1>Alejandro</h1>
            </div>
            <ul class="main-nav">
                <li><a href="#">Valores</a></li>
                <li><a href="#">Experiencia</a></li>
                <li><a href="#">Testimonios</a></li>
                <li><a href="#">Contacto</a></li>
            </ul>        
        </div>
    </nav>
    <div class="row">
        <div class="motto">
            <h2>Por una humanidad sustentable</h2>
        </div>
        <div class="principal-image"></div>
    </div>
    <div class="motto-cell-phone">
        <h2>Por una humanidad sustentable</h2>
    </div>
</header>
```

### 2.3 Agregar el siguiente código dentro del archivo style.css

Este archivo debe estar dentro del siguiente path

- resources/css/style.css

```
/* --------------------------------*/
/* GENERAL SETTINGS */
/* --------------------------------*/

* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

html {
    background-color: #fff;
    color: #555;
    font-family: 'Lato', sans-serif;
    font-weight: 300;
    font-size: 20px;
    text-rendering: optimizeLegibility;
}

.row {
    max-width: 1140px;
    margin: 0 auto;
}

h1,
h2,
h3,
h4 {
    color: #535353;
}

h1 {
    margin: 0;
    font-size: 2.5em;
    font-weight: 700;
}

h2 {
    font-weight: 300;
}

h3 {
    margin-bottom: 5%;
}

h4 {
    margin-bottom: 2%;
}

.icon-big {
    font-size: 300%;
    display: block;
    color: #000;
    margin-bottom: 10px;
    text-align: center;
}

p {
    text-align: justify;
}

.box {
    padding: 1%;
    margin-bottom: 5%;
}

.center {
    text-align: center;
}

/* --------------------------------*/
/* PRINCIPAL SECTION */
/* --------------------------------*/

.title {
    display: inline-block;
    margin-left: 10px;
}

.title h1 {
    margin-top: 15px;
}

.main-nav {
    float: right;
    list-style: none;
    margin-top: 30px;
    margin-left: 10px;
}

.main-nav li {
    display: inline-block;
    margin-right: 40px;
}

.main-nav li a:link,
.main-nav li a:visited {
    color: #535353;
    text-decoration: none;
    font-weight: 100;
    font-size: 1.3em;
    border-bottom: 2px solid transparent;
    transition: border-bottom 0.8s;
}

.main-nav li a:hover,
.main-nav li a:active {
    border-bottom: 2px solid #181818;
}

.motto {
    display: inline-block;
    margin-left: 10px;
}

.motto h2 {
    margin-top: 50%;
}

.motto-cell-phone {
    display: none;
}

.principal-image {
    background-image: url(img/principal_section_image.jpg);
    background-size: contain;
    background-position: center;
    background-repeat: no-repeat;
    height: 60vh;
    width: 60vh;
    float: right;
}
```
            
### 2.4 Agregar el siguiente codigo dentro del archivo queries.css

Este archivo debe estar en el siguiente path

- resources/css/queries.css

```

/* --------------------------------*/
/* TABLETS LANDSCAPE */
/* --------------------------------*/

@media only screen and (max-width: 1024px) {

    /* --------------------------------*/
    /* General */
    /* --------------------------------*/
    
    body { font-size: 18px; }

    .icon-big {
        font-size: 300%;
    }

    /* --------------------------------*/
    /* Principal section */
    /* --------------------------------*/

    .title { 
        display: block; 
        margin-left: 20px;
    }

    .main-nav { 
        float: left; 
        margin-left: 20px;
    }

    .motto { margin-left: 20px; }   

    .motto h2 { font-size: 1.3em; }

    .principal-image { 
        height: 45vh;
        width: 45vh;
        margin-top: 5%;
    }  

}

/* --------------------------------*/
/* TABLETS PORTRAIT */
/* --------------------------------*/

@media only screen and (max-width: 768px) {

    /* --------------------------------*/
    /* General */
    /* --------------------------------*/
    
    body { font-size: 16px; }

    .icon-big { font-size: 400%; }

    /* --------------------------------*/
    /* Principal section */
    /* --------------------------------*/

    .title { 
        display: block; 
        margin-left: 10px;
    }

    .main-nav { 
        float: left; 
        margin-left: 10px;
    }

    .motto { display: none;  }   

    .motto-cell-phone {
        display: block;
        margin-left: auto;
        margin-right: auto;
        width: 70%;
    }

    .motto-cell-phone h2 {
        font-size: 1.5em;
        font-weight: 100;
        margin-top: 5%;
        margin-bottom: 5%;
        text-align: center;
    }

    .principal-image { 
        display: block;
        margin-left: auto;
        margin-right: auto;
        margin-top: 5%;
        height: 60vh;
        width: 60vh;
        float: unset;
    }    

}

/* --------------------------------*/
/* CELL PHONES */
/* --------------------------------*/

@media only screen and (max-width: 568px) {

    /* --------------------------------*/
    /* General */
    /* --------------------------------*/
    
    body { font-size: 14px; }

    /* --------------------------------*/
    /* Principal section */
    /* --------------------------------*/

    .title { 
        display: block; 
        margin-left: auto;
        margin-right: auto;
        width: 50%;
        text-align: center;
    }

    .main-nav { 
        display: block; 
        margin-left: auto;
        margin-right: auto;
        width: 90%;
        text-align: center;
        float: unset;
    }

    .main-nav li { margin-right: 20px; }

    .motto { display: none; }   

    .motto-cell-phone {
        display: block;
        margin-left: auto;
        margin-right: auto;
        width: 70%;
    }

    .motto-cell-phone h2 {
        font-size: 1.5em;
        font-weight: 100;
        margin-top: 6%;
        margin-bottom: 5%;
        text-align: center;
    }

    .principal-image { 
        display: block;
        margin-left: auto;
        margin-right: auto;
        margin-top: 5%;
        height: 40vh;
        width: 40vh;
        float: unset;
    }  

}
```
### 2.5 Agregar los cambios al repositorio

```
git add .
```

### 2.6 Hacer commit de los cambios con la descripción de la user story

Tener en cuenta que el ticket usado es solo de ejemplo, debemos usar el número de ticket correspondiente

```
git commit -m "ALE-15 COMO una persona PUEDO ver en cualquier dispositivo, la sección principal del Curriculum Vitae PARA leer y visualizar todos sus componentes"
```

### 2.7 Hacer push del branch al repositorio remoto

Tener en cuenta que el ticket usado es solo de ejemplo, debemos usar el número de ticket correspondiente

```
git push --set-upstream origin ALE-15
```

### 2.8 Crear un pull request y compartirlo con el instructor de la clase

El pull request debemos hacerlo desde el feature branch al branch de integración

### 2.9 Hacer un merge del pull request

### 2.10 Eliminar el feature branch en github (repositorio remoto) y el repositorio local

### 2.11 Hacer un fetch y un pull en el repositorio local para traer los cambios del pull request y merge del repositorio remoto


## 3 COMO una persona PUEDO ver en cualquier dispositivo la sección “Valores” del Curriculum Vitae PARA leer cada uno de ellos y su descripción

### 3.1 Crear un feature branch con el nombre de la subtask, desde el branch de integración

Ejemplo

```
git checkout -b ALE-16
```

### 3.2 Modificar el archivo index.html

Agregar el siguiente codigo, después del tag header

```
<section class="values">
    <div class="row">
        <div class="values-title">
            <h2>Valores</h2>
        </div>
    </div>
    <div class="row">
        <div class="col span-1-of-4 box">
            <i class="icon ion-md-heart icon-big"></i>
            <center><h3>Pasion</h3></center>
            <p class="text">Para mi la vida es un evento asombroso, si me pongo a pensar en todo lo necesario para que sea posible</p>
            <br/>
            <p class="text">Por eso trato de vivir con pasión cada momento y cada actividad que desarrollo, desde caminar hasta desarrollar un sistema de información</p>
        </div>
        <div class="col span-1-of-4 box">
            <i class="icon ion-md-star icon-big"></i>
            <center><h3>Honestidad</h3></center>
            <p class="text">Desde mi perspectiva la comunicación eficiente es un requisito para el exito de cualquier proyecto, tanto personal como profesional </p>
            <br/>
            <p class="text">Para que dicha comunicación sea posible, de mi parte trato de ser lo más honesto posible</p>
        </div>
        <div class="col span-1-of-4 box">
            <i class="icon ion-md-alarm icon-big"></i>
            <center><h3>Respeto</h3></center>
            <p class="text">Este valor es fundamental, respeto primero por mi mismo, por todos los humanos y la naturaleza</p>
            <br/>
            <p class="text">Respeto para mi es tener en cuenta y valorar, las necesidades, opiniones y diferencias de los seres vivos incluyendo a la naturaleza </p>
        </div>
        <div class="col span-1-of-4 box">
            <i class="icon ion-md-hand icon-big"></i>
            <center><h3>Tolerancia</h3></center>
            <p class="text">Si bien no me es fácil tolerar comportamientos no respetuosos, considero que es importante detenerse y observar antes de juzgar</p>
            <br/>
            <p class="text">Luego se vuelve evidente el porque nosotros en determinadas situaciones hacemos lo que hacemos </p>
        </div>
    </div>
</section>
```

### 3.3 Modificar el archivo style.css

Agregar el siguiente contenido al archivo

```
/* --------------------------------*/
/* VALUES SECTION */
/* --------------------------------*/

.values {
    background-color: #f4f4f4;
}

.values-title {
    margin-top: 5%;
    margin-bottom: 5%;
    margin-left: auto;
    margin-right: auto;
    width: 50%;
}

.values-title h2 {
    font-size: 2em;
    text-align: center;
}
```

### 3.4 Modificar el archivo queries.css

Agregar el siguiente contenido al archivo

```
@media only screen and (max-width: 1024px) {
.
.
.

    /* --------------------------------*/
    /* Values section */
    /* --------------------------------*/

    .box {
        width: 50%;
        margin-left: auto;
        margin-right: auto;
        height: 270px;
        padding: 4%;
    }
.
.
.
}

@media only screen and (max-width: 568px) {
.
.
.
    /* --------------------------------*/
    /* Values section */
    /* --------------------------------*/

    .box {
        width: 100%;
        padding: 4%;
        height: auto;
    }
.
.
.
}
```

### 3.5 Agregar los cambios al repositorio

```
git add .
```

### 3.6 Hacer commit de los cambios con la descripción de la user story

Tener en cuenta que el ticket usado es solo de ejemplo, debemos usar el número de ticket correspondiente

```
git commit -m "ALE-16 COMO una persona PUEDO ver en cualquier dispositivo la sección “Valores” del Curriculum Vitae PARA leer cada uno de ellos y su descripción"
```

### 3.7 Hacer push del branch al repositorio remoto

Tener en cuenta que el ticket usado es solo de ejemplo, debemos usar el número de ticket correspondiente

```
git push --set-upstream origin ALE-16
```

### 3.8 Crear un pull request y compartirlo con el instructor de la clase

El pull request debemos hacerlo desde el feature branch al branch de integración

### 3.9 Hacer un merge del pull request

### 3.10 Eliminar el feature branch en github (repositorio remoto) y el repositorio local

### 3.11 Hacer un fetch y un pull en el repositorio local para traer los cambios del pull request y merge del repositorio remoto


## 4 COMO una persona PUEDO ver en cualquier dispositivo la sección “Imágenes” del Curriculum Vitae PARA visualizar claramente las imágenes

### 4.1 Crear el feature branch correspondiente

```
git checkout -b ALE-17
```

### 4.2 Agregar el siguiente código al archivo index.html

Este código va después de la sección de valores

```
<section class="images">
    <ul class="images-gallery clearfix">
        <li>
            <figure class="photo">
                <img src="resources/img/alejandro_image_1_gallery_withe_background.jpg" alt="Alejandro Bernal Collazos">
            </figure>
        </li>
        <li>
            <figure class="photo">
                <img src="resources/img/alejandro_image_2_gallery_withe_background.jpg" alt="Alejandro Bernal Collazos">
            </figure>
        </li>
    </ul>
</section>
```

### 4.3 Agregar las imagenes en el file system

- Sacar las imagenes de este [repositorio](https://github.com/alejandrobernalcollazos/abernal/tree/develop/resources/img)
- Guardarlas en el siguiente path 

```
resources/img/
```

### 4.4 Modificar el archivo style.css

Agregar el siguiente código

```
/* --------------------------------*/
/* IMAGES SECTION */
/* --------------------------------*/

.images {

}

.images-gallery {
    list-style: none;
    width: 100%;
}

.images-gallery li {
    display: block;
    float: left;
    width: 50%;
}

.photo {
    width: 100%;
    overflow: hidden;
    background-color: #000;
}

.photo img {
    opacity: 0.7;
    width: 100%;
    height: auto;
    transform: scale(1.20);
    transition: transform 0.5s, opacity 0.5s;
}

.photo img:hover {
    opacity: 1;
    transform: scale(1.03);
}

.clearfix { zoom: 1 }

.clearfix:after {
    content: '.';
    clear: both;
    display: block;
    height: 0;
    visibility: hidden;
}
```

### 4.5 Modificar el archivo queries.css

Agregar el siguiente contenido

```
.
.
.
@media only screen and (max-width: 568px) {
.
.
.
    /* --------------------------------*/
    /* Images section */
    /* --------------------------------*/

    .images-gallery li {
        width: 100%;
    }
.
.
.
}
```

### 4.6 Agregar los cambios al repositorio

```
git add .
```

### 4.7 Hacer commit de los cambios con la descripción de la user story

Tener en cuenta que el ticket usado es solo de ejemplo, debemos usar el número de ticket correspondiente

```
git commit -m "ALE-17 COMO una persona PUEDO ver en cualquier dispositivo la sección “Imágenes” del Curriculum Vitae PARA visualizar claramente las imágenes"
```

### 4.8 Hacer push del branch al repositorio remoto

Tener en cuenta que el ticket usado es solo de ejemplo, debemos usar el número de ticket correspondiente

```
git push --set-upstream origin ALE-17
```

### 4.9 Crear un pull request y compartirlo con el instructor de la clase

El pull request debemos hacerlo desde el feature branch al branch de integración

### 4.10 Hacer un merge del pull request

### 4.11 Eliminar el feature branch en github (repositorio remoto) y el repositorio local

### 4.12 Hacer un fetch y un pull en el repositorio local para traer los cambios del pull request y merge del repositorio remoto

## 5 COMO una persona PUEDO ver en cualquier dispositivo la sección “Experiencia” del Curriculum Vitae PARA leerlas

### 5.1 Crear un feature branch con el número de la user story

Tener en cuenta que el ticket usado es solo de ejemplo, debemos usar el número de ticket correspondiente

```
git checkout -b ALE-18
```

### 5.2 Modificar el archivo index.html

Agregar el siguiente contenido

```
<section class="experience">
    <div class="row">
        <div class="experience-title">
            <h2>Experiencia</h2>
        </div>
    </div>
    <div class="row">
        <div class="col span-1-of-2 experience-box">
            <center><h3>Latam</h3></center>
            <center><h4>Enero 2014 - Junio 2016</h4></center>
            <p class="text">simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book. It has survived not only five centuries, but also the leap into electronic typesetting, remaining essentially unchanged. It was popularised in the 1960s with the release of Letraset sheets containing Lorem Ipsum passages, and more recently with desktop publishing software like Aldus PageMaker including versions of Lorem Ipsum</p>
            <br/>
            <i class="icon ion-md-airplane icon-big"></i>
        </div>
        <div class="col span-1-of-2 experience-box">
            <center><h3>American Airlines</h3></center>
            <center><h4>Enero 2012 - Enero 2014</h4></center>
            <p class="text">simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book. It has survived not only five centuries, but also the leap into electronic typesetting, remaining essentially unchanged. It was popularised in the 1960s with the release of Letraset sheets containing Lorem Ipsum passages, and more recently with desktop publishing software like Aldus PageMaker including versions of Lorem Ipsum</p>
            <br/>
            <i class="icon ion-md-airplane icon-big"></i>
        </div>
    </div>
</section>
```

### 5.3 Modificar el archivo style.css

Agregar el siguiente código al archivo

```
/* --------------------------------*/
/* EXPERIENCIE SECTION */
/* --------------------------------*/

.experience-title {
    margin-top: 5%;
    margin-bottom: 5%;
    margin-left: auto;
    margin-right: auto;
    width: 50%;
}

.experience-title h2 {
    font-size: 2em;
    text-align: center;
}

.experience-box {
    padding: 2%;
    margin-bottom: 5%;
}
```

### 5.4 Modificar el archivo queries.css

Agregar el siguiente código al archivo

```
.
.
.
@media only screen and (max-width: 568px) {
.
.
.
    /* --------------------------------*/
    /* Experience section */
    /* --------------------------------*/

    .experience-box {
        width: 100%;
        padding: 4%;
        height: auto;
    }
}
```


### 5.5 Agregar los cambios al repositorio

```
git add .
```

### 5.6 Hacer commit de los cambios con la descripción de la user story

Tener en cuenta que el ticket usado es solo de ejemplo, debemos usar el número de ticket correspondiente

```
git commit -m "ALE-18 COMO una persona PUEDO ver en cualquier dispositivo la sección “Experiencia” del Curriculum Vitae PARA leerlas"
```

### 5.7 Hacer push del branch al repositorio remoto

Tener en cuenta que el ticket usado es solo de ejemplo, debemos usar el número de ticket correspondiente

```
git push --set-upstream origin ALE-18
```

### 5.8 Crear un pull request y compartirlo con el instructor de la clase

El pull request debemos hacerlo desde el feature branch al branch de integración

### 5.9 Hacer un merge del pull request

### 5.10 Eliminar el feature branch en github (repositorio remoto) y el repositorio local

### 5.11 Hacer un fetch y un pull en el repositorio local para traer los cambios del pull request y merge del repositorio remoto


## 6 COMO una persona PUEDO ver en cualquier dispositivo la sección “Testimonios” del Curriculum Vitae PARA leerlos

### 6.1 Crear un feature branch con el número de la user story

Tener en cuenta que el ticket usado es solo de ejemplo, debemos usar el número de ticket correspondiente

```
git checkout -b ALE-19
```

### 6.2 Modificar el archivo index.html

Agregar el siguiente contenido al archivo

```
<section class="testimony">
    <div class="row">
        <div class="testimony-title">
            <h2>Testimonios</h2>
        </div>
    </div>
    <div class="row">
        <div class="col span-1-of-4 box">
            <blockquote>
                simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, 
                when an unknown printer took a galley of type and scrambled it to make a type specimen book.
                <cite><img src="resources/img/testimony-1.jpg">Andres Openhaimer</cite>
            </blockquote>
        </div>
        <div class="col span-1-of-4 box">
            <blockquote>
                simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, 
                when an unknown printer took a galley of type and scrambled it to make a type specimen book.
                <cite><img src="resources/img/testimony-2.jpg">Sandra Bullock</cite>
            </blockquote>
        </div>
        <div class="col span-1-of-4 box">
            <blockquote>
                simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, 
                when an unknown printer took a galley of type and scrambled it to make a type specimen book.
                <cite><img src="resources/img/testimony-3.jpg">Oscar Miretti</cite>
            </blockquote>
        </div>
        <div class="col span-1-of-4 box">
            <blockquote>
                simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, 
                when an unknown printer took a galley of type and scrambled it to make a type specimen book.
                <cite><img src="resources/img/testimony-4.jpg">Karen Palma</cite>
            </blockquote>
        </div>
    </div>
</section>
```

### 6.3 Modificar el archivo style.css

Agregar el siguiente contenido al archivo

```
.
.
.
/* --------------------------------*/
/* TESTIMONIES SECTION */
/* --------------------------------*/

.testimony {
    background-image: linear-gradient(rgba(0,0,0,0.8), rgba(0,0,0,0.8)), url(img/office-background.jpg);
    background-size: cover;
    color: #fff;
    background-attachment: fixed;
}

.testimony h2 {
    color: #fff;
}

.testimony-title {
    margin-top: 5%;
    margin-bottom: 5%;
    margin-left: auto;
    margin-right: auto;
    width: 50%;
}

.testimony-title h2 {
    font-size: 2em;
    text-align: center;
}

blockquote:before {
    content: "\201C";
    font-size: 400%;
}

blockquote {
    font-style: italic;
    line-height: 145%;
}

cite {
    font-size: 90%;
    margin-top: 25px;
    display: block;
}

cite img {
    height: 60px;
    border-radius: 50%;
    vertical-align: middle;
    margin-right: 10px;
}
.
.
.
```

### 6.4 Modificar el archivo queries.css

Agregar el siguiente código al archivo

```
.
.
.
@media only screen and (max-width: 568px) {
.
.
.
    /* --------------------------------*/
    /* Testimony section */
    /* --------------------------------*/

    blockquote {
        text-align: center;
    }

    cite {
        text-align: center;
    }
}
```

### 6.5 Agregar los cambios al repositorio

```
git add .
```

### 6.6 Hacer commit de los cambios con la descripción de la user story

Tener en cuenta que el ticket usado es solo de ejemplo, debemos usar el número de ticket correspondiente

```
git commit -m "ALE-19 COMO una persona PUEDO ver en cualquier dispositivo la sección “Testimonios” del Curriculum Vitae PARA leerlas"
```

### 6.7 Hacer push del branch al repositorio remoto

Tener en cuenta que el ticket usado es solo de ejemplo, debemos usar el número de ticket correspondiente

```
git push --set-upstream origin ALE-19
```

### 6.8 Crear un pull request y compartirlo con el instructor de la clase

El pull request debemos hacerlo desde el feature branch al branch de integración

### 6.9 Hacer un merge del pull request

### 6.10 Eliminar el feature branch en github (repositorio remoto) y el repositorio local

### 6.11 Hacer un fetch y un pull en el repositorio local para traer los cambios del pull request y merge del repositorio remoto

## 7 COMO una persona PUEDO ver en cualquier dispositivo la sección “Contacto” del Curriculum Vitae PARA leerlos

### 7.1 Crear el feature branch

```
git checkout -b ALE-20
```

### 7.2 Modificar el archivo index.html

Agregar el siguiente contenido

```
<section class="contact">
    <div class="row">
        <div class="contact-title">
            <h2>Contacto</h2>
        </div>
    </div>
    <div class="row">
        <div class="col span-1-of-4 box">
            <i class="icon ion-md-mail icon-big"></i>
            <center><h3>alejandro@alejandro.bio</h3></center>
        </div>
        <div class="col span-1-of-4 box">
            <i class="icon ion-md-call icon-big"></i>
            <center><h3>+54 9 351 2732 983</h3></center>
        </div>
        <div class="col span-1-of-4 box">
            <i class="icon ion-md-pin icon-big"></i>
            <center><h3>Av Velez Sarfield 576, Piso 4</h3></center>
        </div>
        <div class="col span-1-of-4 box">
            <i class="icon ion-md-browsers icon-big"></i>
            <center><h3>www.alejandro.bio</h3></center>
        </div>
    </div>
</section>
```

### 7.3 Modificar el archivo style.css

Agregar el siguiente contenido

```
.
.
.
/* --------------------------------*/
/* CONTACT SECTION */
/* --------------------------------*/

.contact-title {
    margin-top: 5%;
    margin-bottom: 5%;
    margin-left: auto;
    margin-right: auto;
    width: 50%;
}

.contact-title h2 {
    font-size: 2em;
    text-align: center;
}
.
.
.
```

### 7.4 Agregar los cambios al repositorio

```
git add .
```

### 7.5 Hacer commit de los cambios con la descripción de la user story

Tener en cuenta que el ticket usado es solo de ejemplo, debemos usar el número de ticket correspondiente

```
git commit -m "ALE-20 COMO una persona PUEDO ver en cualquier dispositivo la sección “Testimonios” del Curriculum Vitae PARA leerlas"
```

### 7.6 Hacer push del branch al repositorio remoto

Tener en cuenta que el ticket usado es solo de ejemplo, debemos usar el número de ticket correspondiente

```
git push --set-upstream origin ALE-20
```

### 7.7 Crear un pull request y compartirlo con el instructor de la clase

El pull request debemos hacerlo desde el feature branch al branch de integración

### 7.8 Hacer un merge del pull request

### 7.9 Eliminar el feature branch en github (repositorio remoto) y el repositorio local

### 7.10 Hacer un fetch y un pull en el repositorio local para traer los cambios del pull request y merge del repositorio remoto

## 8 COMO una persona PUEDO ver en cualquier dispositivo la sección “Footer” del Curriculum Vitae PARA leer y visualizar sus componentes

### 8.1 Crear el feature branch

```
git checkout -b ALE-21
```

### 8.2 Modificar el archivo index.html

Agregar el siguiente contenido al archivo

```
.
.
.
<section class="footer">
    <div class="row">
        <ul class="footer-main-nav">
            <li><a href="#">Valores</a></li>
            <li><a href="#">Experiencia</a></li>
            <li><a href="#">Testimonios</a></li>
            <li><a href="#">Contacto</a></li>
        </ul>
        <a href="#"><i class="icon ion-logo-facebook footer-icon"></i></a>
        <a href="#"><i class="icon ion-logo-instagram footer-icon"></i></a>
    </div>
    <div class="row">
        <p class="rights">Copyright © 2019 by Alejandro. All rights reserved</p>
    </div>
</section>
```

### 8.3 Modificar el archivo style.css

Agregar el siguiente contenido

```
.
.
.
/* --------------------------------*/
/* FOOTER SECTION */
/* --------------------------------*/

.footer {
    background-color: #393939;
}

.footer-main-nav {
    float: left;
    list-style: none;
    margin-top: 5%;
    margin-left: 10px;
    
}

.footer-main-nav li {
    display: inline-block;
    margin-right: 40px;
}

.footer-main-nav li a:link,
.footer-main-nav li a:visited {
    color: #fff;
    text-decoration: none;
    font-weight: 100;
    font-size: 1em;
}

.footer-icon {
    font-size: 300%;
    display: inline-block;
    color: #000;
    margin-top: 2.5%;
    margin-bottom: 10px;
    margin-right: 10%;
    text-align: center;
    float: right;
}

.rights {
    color: #fff;
    margin-top: 3%;
    margin-left: auto;
    margin-right: auto;
    display: block;
    text-align: center;
    margin-bottom: 3%;
}
```

### 8.4 Modificar el archivo queries.css

Agregar el siguiente contenido

```
@media only screen and (max-width: 1024px) {
.
.
.
    /* --------------------------------*/
    /* Footer section */
    /* --------------------------------*/

    .footer-main-nav {
        display: none;
    }

    .footer-icon {
        width: 50%;
        margin-left: auto;
        margin-right: auto;
        font-size: 400%;
    }
.
.
.
}
```

### 8.5 Agregar los cambios al repositorio

```
git add .
```

### 8.6 Hacer commit de los cambios con la descripción de la user story

Tener en cuenta que el ticket usado es solo de ejemplo, debemos usar el número de ticket correspondiente

```
git commit -m "ALE-21 COMO una persona PUEDO ver en cualquier dispositivo la sección “Footer” del Curriculum Vitae PARA leer y visualizar sus componentes"
```

### 8.7 Hacer push del branch al repositorio remoto

Tener en cuenta que el ticket usado es solo de ejemplo, debemos usar el número de ticket correspondiente

```
git push --set-upstream origin ALE-21
```

### 8.8 Crear un pull request y compartirlo con el instructor de la clase

El pull request debemos hacerlo desde el feature branch al branch de integración

### 8.9 Hacer un merge del pull request

### 8.10 Eliminar el feature branch en github (repositorio remoto) y el repositorio local

### 8.11 Hacer un fetch y un pull en el repositorio local para traer los cambios del pull request y merge del repositorio remoto
