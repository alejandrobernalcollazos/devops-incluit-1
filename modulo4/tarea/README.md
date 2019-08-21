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
    font-weight: 400;
}

h3 {
    margin-bottom: 5%;
}

h4 {
    margin-bottom: 2%;
}

.icon-big {
    font-size: 200%;
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
    height: 65vh;
    width: 65vh;
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
        height: 65vh;
        width: 65vh;
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
        height: 60vh;
        width: 60vh;
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
