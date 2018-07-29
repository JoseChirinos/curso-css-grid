# Curso CSS Grid Layout 

## Curso Oficial de Grid Css Layout 2018

> Instalar Browser-Sync para cambios en tiempo real
```sh
    npm install -g browser-sync
```
> Para ejecutar el proyecto modo desarrollo
```sh
    npm start
```

## Tabla de Contenido
  - [Introducción](#introducción)
  - [Ejemplo Básico](#ejemplo-basico)

## Introducción

### `Qué es un Layout?`:
  Son esos recuadros principales donde se encierra o se envuelve todo el contenido y componentes de nuestro sitio web.

#### `Grid Container`
  Elemento padre principal que va a tener puesto un nuevo tipo de display llamado `grid` , el cual nos va a permitir que le podamos poner otras propiedades para manipular nuestro Layout. Los hijos directos de dicho contenedor serán `Grid Items`.
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
#### `Grid Line`
  Líneas divisorias horizontales y verticales.
  Divisiones invisibles dentro de nuestro web site.
  También serán las que van a contornear nuestro grid.

#### `Grid Track`
  Es el espacio entre dos lineas adyacentes o mas bien conocido como filas y columnas.

#### `Grid Cell`
  Espacio entre dos filas adyacentes y dos columnas adyacentes.

#### `Grid Area`
  Espacio que rodeado por 4 grid lines (Cabe destacar que se puede ampliar a N cantidades)

#### `Soporte`
  CSS Grid Layout es soportada en un gran
  porcentaje puedes mirar el siguiente
  enlace [css-grid-support](https://caniuse.com/#feat=css-grid)


<div align="right">
  <small><a href="#tabla-de-contenido">Contenido 🡡</a></small>
</div>

## Ejemplo Básico


#### `Columas`
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

#### `Filas`
  Para definir filas tenemos que aumentar
  el siguiente codigo en nuestro `style.css`

```css
  .container{
    display: grid;
    grid-template-columns: 25% 50% 25%;
    grid-template-rows: 300px 300px; //linea agregada
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
- Ejemplo:
```css
  .container{
    display: grid;
    grid-template: 300px 300px / 25% 50% 25%;
  }
```
`(*) Tomar muy en cuenta los siguientes conceptos:`

#### `Grid Explicito`
  (Explicit Grid) es cuando nosotros definimos
  el número de filas o columnas.

#### `Grid Implicito`
  (Implicit Grid) es cuando filas o columnas
  que no definimos pero son parte de nuestro grid.

  Para más información: [Implicit/Explicit Grid](https://www.quackit.com/css/grid/tutorial/explicit_vs_implicit_grid.)


<div align="right">
  <small><a href="#tabla-de-contenido">Contenido 🡡</a></small>
</div>