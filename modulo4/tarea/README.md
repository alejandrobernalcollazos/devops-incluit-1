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
            
