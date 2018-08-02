# Curso CSS Grid Layout


## Tabla de Contenido
  - [Introducción](#introducción)

  - [Primeros Pasos](#primeros-pasos)

  - [Displays](#displays)
  
  - [Espaciado entre columnas](#espaciado-entre-columnas)
  - [Repetidores, unidades de medida y funciones](#Repetidores,-unidades-de-medida-y-funciones)

  - [Areas de contenido](#areas-de-contenido)

  - [Definir tamaños de las columnas](#definir-tamaños-de-las-columnas)

  - [Definir tamaños de las filas](#definir-tamaños-de-las-filas)

  - [Definir el nombre de las lineas](#definir-el-nombre-de-las-lineas)

  - [Manejando el Grid Implicito](#manejando-el-grid-implicito)

  - [Alineación de items](#alineación-de-items)

  - [Alineación de contenido](#alineación-de-contenido)

## Introducción

En esta sección explicaremos las conceptos más importantes:

#### `Layout:`
  Son los recuadros principales donde se encierra o se envuelve todo el contenido y componentes de nuestro sitio web.

#### `Grid Container:`
  Es el elemento padre principal que va a tener puesto un nuevo tipo de display llamado `grid` , el cual nos va a permitir que le podamos poner otras propiedades para manipular nuestro Layout. Los hijos directos de dicho contenedor serán `Grid Items`.
  > Ejemplo :
```html
  <div class="container">
    <div class="item item-1"></div>
    <div class="item item-2"></div>
    <div class="item item-3">
      <div>
      <!-- Este no es un Grid Item porque no es hijo directo -->
      </div>
    </div>
</div>
```
#### `Grid Line:`
  Son líneas divisorias horizontales y verticales.
  Divisiones invisibles dentro de nuestro web site.
  También serán las que van a contornear nuestro grid.

#### `Grid Track:`
  Es el espacio entre dos lineas adyacentes o mas bien conocido como filas y columnas.

#### `Grid Cell:`
  Es el espacio entre dos filas adyacentes y dos columnas adyacentes.

#### `Grid Area:`
  Es el espacio que es rodeado por 4 grid lines (Cabe destacar que se puede ampliar a N cantidades)

#### *Sobre su soporte en los navegadores:*
  CSS Grid Layout es soportada en un gran
  porcentaje puedes mirar el siguiente
  enlace [css-grid-support](https://caniuse.com/#feat=css-grid)


<div align="right">
  <small><a href="#tabla-de-contenido">🡡 volver al inicio</a></small>
</div>

## Primeros Pasos


#### `Columnas:`
1. Primero se crea la estructura básica del html `index.html`

```html
<html>
  <head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Columnas</title>
    <link rel="stylesheet" href="style.css">
  </head>
  <body>
    <div class="container">
      <div class="item">
        contenido #1
      </div>
      <div class="item">
        contenido #2
      </div>
      <div class="item">
        contenido #3
      </div>
    </div>
  </body>
</html>
```

2. Escribimos el css `style.css`

```css
  body {
    font-family: arial;
  }
  .container{
    display: grid;
    grid-template-columns: 25% 50% 25%;
  }
  .item{
    background: lightblue;
    padding: 10px;
    border: 1px solid red;
  }
```

Con esto hemos definido el `Grid Container` y sus columnas que en
este caso son 3 (25% 50% 25%) respectivamente.
Para definir las columnas se realiza de la siguiente manera:
```css
    grid-template-columns: valores;
```

#### `Filas:`
  Para definir filas tenemos que aumentar
  el siguiente codigo en nuestro `style.css`

```css
  .container{
    display: grid;
    grid-template-columns: 25% 50% 25%;
    grid-template-rows: 300px 300px; /*linea agregada*/
  }
```

Podemos definir las filas de la siguiente manera:
```css
    grid-template-rows: valores;
```
Tambien filas y columnas a la vez:
```css
    grid-template: filas / columnas;
```
> Ejemplo:
```css
  .container{
    display: grid;
    grid-template: 300px 300px / 25% 50% 25%;
  }
```
`(*) Tomar muy en cuenta los siguientes conceptos:`

#### `Grid Explicito:`
  (Explicit Grid) es cuando nosotros definimos
  el número de filas o columnas.

#### `Grid Implicito:`
  (Implicit Grid) es cuando filas o columnas
  que no definimos pero son parte de nuestro grid.

  Para más información: [Implicit/Explicit Grid](https://www.quackit.com/css/grid/tutorial/explicit_vs_implicit_grid.)


<div align="right">
  <small><a href="#tabla-de-contenido">🡡 volver al inicio</a></small>
</div>

## Displays
  Entre los displays disponibles de Grid Css Layout
  tenemos:

#### `subgrid:`

  Este display es para heredar la configuración del grid padre
  (cuando se esten anidando los grids)

  ```css
    display: subgrid; /*No disponible aun*/
  ```

#### `inline-grid:`

  Este display es para mostrar el grid en una sola linea

  ```css
    display: inline-grid; /*No disponible aun*/
  ```

<div align="right">
  <small><a href="#tabla-de-contenido">🡡 volver al inicio</a></small>
</div>

## Espaciado entre columnas
  Para el espaciado entre columnas tenemos las
  siguientes propiedades:

  ```css
    grid-column-gap: value; /*Espaciado entre columnas*/
  ```

  ```css
    grid-row-gap: value; /*Espaciado entre filas*/
  ```

  ```css
    grid-gap: rows columns; /*Espaciado filas y columnas*/
  ```

#### `(*)Importante Actualización Chrome 66`

  Se retira la inicial `grid-`
  
  ```css
    column-gap: value; /*Espaciado entre columnas*/
  ```

  ```css
    row-gap: value; /*Espaciado entre filas*/
  ```

  ```css
    gap: rows columns; /*Espaciado filas y columnas*/
  ```

  <div align="right">
    <small><a href="#tabla-de-contenido">🡡 volver al inicio</a></small>
  </div>

## Repetidores, unidades de medida y funciones

  Dentro de las unidades de medida tenemos las siguientes:

#### `Fracciones:`
  `(fr)` distribuye el espacio en formas iguales, este
  solo se puede utilizar dentro de un `display:grid`.

  > Ejemplo

  ```css
    grid-template: 300px 100px 100px / 1fr 1fr 1fr;
  ```

#### `Auto:`
  `(auto)` distribuye el tamaño respecto al contenido.

  > Ejemplo

  ```css
    grid-template: 300px 100px 100px / auto auto auto;
  ```

#### `Funciones:`

##### `(repeat)`
  Es una función para usar un mismo valor
   de manera repetida: `repeat(cantidad,valor)`

  > Ejemplo

  ```css
    grid-template: 300px 100px 100px / repeat(3, 1fr);
  ```

##### `(minmax)`
  Es una función para usar agregar un valor minimo y maximo para el tamaño
  al hacer responsive `minmax(min,max)`

  > Ejemplo A

  ```css
    grid-template: 300px 100px 100px / repeat(3, minmax(200px,1fr)));
  ```

   > Ejemplo B

  ```css
    grid-template: 300px 100px 100px / minmax(200px,1fr) 1fr 1fr;
  ```


  <div align="right">
    <small><a href="#tabla-de-contenido">🡡 volver al inicio</a></small>
  </div>

## Areas de contenido
  Para definir las areas debemos hacer lo
  siguiente:

  1. Definir nuestro contenedor.

  ![Contenedor](https://raw.githubusercontent.com/JoseChirinos/curso-css-grid/master/static/layout.png)

  2. Agregar la propiedad:
     `grid-template-areas` de la siguiente manera:

  ```css
    .container{
      display: grid;
      /* filas / columas = 3/2 */
      grid-template: repeat(3,1fr) / 200px 1fr;
      gap: 10px;
      height: 100vh;
      grid-template-areas: "header header"
                "left content"
                "footer footer";
    }
  ```

  3. Agregar el markup necesario con clases.

  ```html
    <div class="container">
      <div class="item header">header</div>
      <div class="item left">left</div>
      <div class="item content">contenido</div>
      <div class="item footer">footer</div>
    </div>
  ```

  4. Agregar la propiedad:
    `grid-area` para definir a que area pertenece:
  
  ```css
  .header{
    grid-area: header;
  }
  .left{
    grid-area: left;
  }
  .content{
    grid-area: content;
  }
  .footer{
    grid-area: footer;
  }
  ```

  5. Nuestra Area esta correctamente configurada,   para cambiar tamaños solo modificar el
     `grid-template`

  ```css
    grid-template: 100px 1fr 150px / 200px 1fr;
  ```

  <div align="right">
    <small><a href="#tabla-de-contenido">🡡 volver al inicio</a></small>
  </div>

## Definir tamaños de las columnas

  Los tamaños de columnas se definen dependiendo
  el numero de `Grid Lines`

> Sintaxis sin resumir grid-lines

  ```css
    grid-column-start: 1; /*linea 1*/
    grid-column-end: 3; /*linea 3*/
  ```

> Sintaxis resumida por grid-lines

  ```css
    grid-column: 1 / 3; 
    grid-column: start/end;
  ```
> (*)Caso especial, sintaxis definida por cantidad de columnas
  ```css
    grid-column: 1 / span 2; /*2 columnas*/
  ```

##### Resultado:

![Contenedor](https://raw.githubusercontent.com/JoseChirinos/curso-css-grid/master/static/grid-lines.png)

> Sintaxis para ocupar todo el ancho dinamicamente

  ```css
    grid-column: 2 / -1; /*ocupa del 2 hasta n*/
  ```

##### Resultado:

![Contenedor](https://raw.githubusercontent.com/JoseChirinos/curso-css-grid/master/static/grid-line-end.png)

  <div align="right">
    <small><a href="#tabla-de-contenido">🡡 volver al inicio</a></small>
  </div>

## Definir tamaños de las filas
  Los tamaños de filas se definen dependiendo
  el numero de `Grid Lines`

> Sintaxis sin resumir grid-lines

  ```css
    grid-row-start: 1; /*linea 1*/
    grid-row-end: 3; /*linea 3*/
  ```

> Sintaxis resumida por grid-lines

  ```css
    grid-row: 1 / 3; 
    grid-row: start/end;
  ```
> (*)Caso especial, sintaxis definida por cantidad de filas
  ```css
    grid-row: 1 / span 2; /*2 filas*/
  ```

##### Resultado:

![Contenedor](https://raw.githubusercontent.com/JoseChirinos/curso-css-grid/master/static/grid-row.png)

<div align="right">
  <small><a href="#tabla-de-contenido">🡡 volver al inicio</a></small>
</div>


## Definir el nombre de las lineas
  Podemos usar nombres para darle tamaño a las celdas definiendo de que linea a que linea vamos.

  Lo que hacemos es confeccionar manualmente (sin repeat) las filas y columnas y luego entre 
  corchetes le ponemos el nombre a cada linea que componen el `grid`.
  
  `[nombre de la linea]`

> Ejemplo de uso

  ```css
    grid-template-columns: [start-col] 1fr [line2] 1fr [end-col];
    grid-template-rows: [start-row] 1fr [line2] 1fr [end-row];
  ```

##### Resultado:

![Contenedor](https://raw.githubusercontent.com/JoseChirinos/curso-css-grid/master/static/grid-named-lines-official.png)

<div align="right">
  <small><a href="#tabla-de-contenido">🡡 volver al inicio</a></small>
</div>


## Manejando el Grid Implicito

  El grid implicito es cuando tenemos filas o columnas
  que no definimos pero son parte de nuestro grid.

  Para manejar las `columnas`, lo podemos
  realizar de la siguiente manera:

  ```css
    grid-auto-flow: column; /*establece el manejo de los implicit grid*/
    grid-auto-columns: 200px; /*valores al igual que grid-template-columns*/
  ```
  ##### (*) En firefox el `grid-auto-columns:valor` solo recibe un valor

  Para manejar las `filas`, lo podemos
  realizar de la siguiente manera:

  ```css
    grid-auto-flow: row; /*establece el manejo de los implicit grid*/
    grid-auto-rows: 50px 100px; /*valores al igual que grid-template-rows*/
  ```

  <div align="right">
    <small><a href="#tabla-de-contenido">🡡 volver al inicio</a></small>
  </div>

## Alineación de items

  La alineación se realiza de la siguiente manera:

#### justify-items (Horizontal)


```css
justify-items: value;
```

> VALUES:

`start` : contenido hacia la izquierda

`end` : contenido hacia la derecha

`center` : contenido al medio

`stretch` : estira el contenido al espacio 
que nos de el grid

#### align-items (Vertical)

```css
align-items: value;
```

> VALUES:

`start` : contenido hacia arriba

`end` : contenido hacia abajo

`center` : contenido al medio

`stretch` : estira el contenido al espacio 
que nos de el grid

#### Alineación Individual

  `justify-self` : Alineación Horizontal

  `align-self` : Alineación Vertical

  <div align="right">
    <small><a href="#tabla-de-contenido">🡡 volver al inicio</a></small>
  </div>

## Alineación de contenido

  La alineación se realiza de la siguiente manera:

#### justify-content (Alineado Horizontal)


```css
justify-content: value;
```

> VALUES:

`start` : contenido hacia la izquierda

`end` : contenido hacia la derecha

`center` : contenido al medio

`stretch` : estira el contenido al espacio 
que nos de el grid

`space-around` : Espacios alrededor de cada columna

`space-between` : Espaciado interno

`space-evenly` : distribución homogenea del espacio

#### justify-items (Alineado Vertical)

```css
align-items: value;
```

> VALUES:

`start` : contenido hacia la arriba

`end` : contenido hacia la abajo

`center` : contenido al medio

`stretch` : estira el contenido al espacio 
que nos de el grid

`space-around` : Espacios alrededor de cada fila

`space-between` : Espaciado interno

`space-evenly` : distribución homogenea del espacio


  <div align="right">
    <small><a href="#tabla-de-contenido">🡡 volver al inicio</a></small>
  </div>

## Great!!
> Resumido por josechirinos 2018