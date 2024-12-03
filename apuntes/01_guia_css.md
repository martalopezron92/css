
# Guía inicial de CSS3.

## Introducción a CSS3

**CSS3** (Cascading Style Sheets Level 3) es la última versión de CSS, utilizada para describir la presentación de documentos HTML y XML. CSS3 introduce nuevas características y mejoras que facilitan la creación de diseños web más atractivos y funcionales.

### ¿Por qué usar CSS3?

*   **Modularidad:** CSS3 se divide en módulos, lo que facilita su uso y comprensión.
*   **Nuevas propiedades:** Permite efectos visuales avanzados como sombras, transiciones y animaciones.
*   **Responsive Design:** Facilita la creación de sitios web que se adaptan a diferentes tamaños de pantalla.
*   **Mejoras en el diseño:** Nuevas herramientas como Flexbox y Grid Layout para layouts más complejos y flexibles.


## Estructura Básica de CSS

Un archivo CSS está compuesto por reglas que definen cómo se deben mostrar los elementos HTML.

### Sintaxis Básica

```
selector {
    propiedad: valor;
}

```
### Ejemplo

```
body {
    background-color: #f0f0f0;
    font-family: Arial, sans-serif;
}

h1 {
    color: #333333;
    text-align: center;
}

```


## Selectores CSS

Los **selectores** son patrones utilizados para seleccionar los elementos HTML que deseas estilizar.

### Selectores Básicos

*   **Selector de Tipo:** Selecciona todos los elementos de un tipo específico.
    
    `css p { color: blue; }`
    
*   **Selector Universal:** Selecciona todos los elementos.
    
    `css * { margin: 0; padding: 0; }`
    

### Selectores de Clase y ID

*   **Clase:** Selecciona elementos con una clase específica.
    
    `css .mi-clase { background-color: yellow; }`
    
*   **ID:** Selecciona un elemento con un ID específico (debe ser único).
    
    `css **#**mi-id { border: 1px solid black; }`
    

### Selectores de Atributo

Seleccionan elementos basados en atributos o valores de atributos.

```
input[type="text"] {
    width: 200px;
    padding: 5px;
}

```

### Selectores de Pseudo-clases y Pseudo-elementos

*   **Pseudo-clases:** Seleccionan elementos en un estado específico.
    
    `css a:hover { color: red; }`
    
*   **Pseudo-elementos:** Seleccionan una parte específica de un elemento.
    
    `css p::first-line { font-weight: bold; }`
    

### Especificidad
Determina qué estilos se aplican cuando hay conflictos.  
- **Orden de importancia:**  
  1. Estilos inline (en el atributo `style` del HTML).  
  2. Selectores ID (`#id`).  
  3. Clases, atributos y pseudoclases (`.clase`, `[atributo]`, `:hover`).  
  4. Elementos y pseudoelementos (`div`, `::before`).  

**Ejemplo de especificidad:**  
```html
<div id="caja" class="rojo">
  Contenido
</div>
```
```css
#caja {
  color: blue; /* Más específico, gana */
}

.rojo {
  color: red;
}
```

## Jerarquía entre etiquetas en HTML y su uso en CSS

En HTML, los elementos están organizados jerárquicamente, lo que significa que algunos elementos contienen a otros (relaciones de **padre e hijo**) o están al mismo nivel (relaciones de **hermanos**). Esta jerarquía es fundamental para aplicar selectores en CSS de manera eficaz.

---

### Relaciones entre etiquetas
1. **Etiqueta padre:**  
   Un elemento que contiene a otros dentro de sí mismo.  
   Ejemplo:  
   ```html
   <div>
       <p>Texto</p>
   </div>
   ```
   En este caso, `<div>` es el **padre** de `<p>`.

2. **Etiqueta hijo:**  
   Un elemento contenido directamente dentro de otro.  
   Ejemplo:  
   ```html
   <ul>
       <li>Elemento 1</li>
       <li>Elemento 2</li>
   </ul>
   ```
   Aquí, cada `<li>` es un **hijo directo** de `<ul>`.

3. **Etiquetas hermanas:**  
   Elementos que comparten el mismo padre.  
   Ejemplo:  
   ```html
   <div>
       <h1>Título</h1>
       <p>Texto</p>
   </div>
   ```
   En este caso, `<h1>` y `<p>` son **hermanos**.

---

### Selectores CSS basados en la jerarquía
CSS permite seleccionar elementos según su relación jerárquica.

**1. Selector descendiente (`elemento1 elemento2`)**  
Selecciona **todos** los elementos `elemento2` que están dentro de `elemento1` (sin importar el nivel).  
Ejemplo:  
```css
div p {
  color: blue;
}
```
Selecciona todos los `<p>` dentro de un `<div>`.  

```html
<div>
  <p>Esto será azul</p>
</div>
```

**2. Selector hijo directo (`elemento1 > elemento2`)**  
Selecciona solo los elementos `elemento2` que son **hijos directos** de `elemento1`.  
Ejemplo:  
```css
div > p {
  color: red;
}
```
```html
<div>
  <p>Esto será rojo</p>
  <div>
    <p>Esto no será rojo</p>
  </div>
</div>
```

**3. Selector de hermanos adyacentes (`elemento1 + elemento2`)**  
Selecciona el primer `elemento2` que es **hermano inmediato** de `elemento1`.  
Ejemplo:  
```css
h1 + p {
  color: green;
}
```
```html
<h1>Título</h1>
<p>Esto será verde</p>
<p>Esto no será verde</p>
```

**4. Selector de hermanos generales (`elemento1 ~ elemento2`)**  
Selecciona **todos los hermanos** `elemento2` que están después de `elemento1`.  
Ejemplo:  
```css
h1 ~ p {
  color: orange;
}
```
```html
<h1>Título</h1>
<p>Esto será naranja</p>
<p>Esto también será naranja</p>
```

## Modelo BEM (Block, Element, Modifier)  
Es una metodología para nombrar clases y organizar CSS. Hace el código más fácil de entender y mantener.  
- **Block (Bloque):** Representa un componente independiente (`menu`).  
- **Element (Elemento):** Parte del bloque (`menu__item`).  
- **Modifier (Modificador):** Varía el estilo del bloque o elemento (`menu__item--activo`).  

**Ejemplo:**  
```html
<nav class="menu">
  <ul class="menu__lista">
    <li class="menu__item menu__item--activo">Inicio</li>
    <li class="menu__item">Servicios</li>
  </ul>
</nav>
```
```css
.menu {
  background-color: #eee;
}

.menu__item {
  list-style: none;
}

.menu__item--activo {
  font-weight: bold;
}
```


## Modelo de Caja (Box Model)

El **Box Model** de CSS describe cómo se calculan las dimensiones y el espacio alrededor de los elementos.

### Componentes del Box Model

1.  **Contenido:** Área donde se muestra el contenido (texto, imágenes, etc.).
2.  **Padding (Relleno):** Espacio entre el contenido y el borde.
3.  **Border (Borde):** Línea que rodea el padding y el contenido.
4.  **Margin (Margen):** Espacio fuera del borde.

**Propiedad `box-sizing`:**  
Controla cómo se calculan los tamaños.  
- `content-box`: El tamaño incluye solo el contenido (padding y bordes se suman).  
- `border-box`: El tamaño incluye el contenido, el padding y el borde.  

### Ejemplo

```
div {
    width: 300px;
    padding: 20px;
    border: 5px solid #333;
    margin: 15px;
}

```


### Visualización

```
+-----------------------------+
|          Margin             |
|  +-----------------------+  |
|  |        Border         |  |
|  |  +-----------------+  |  |
|  |  |     Padding     |  |  |
|  |  |  +-----------+  |  |  |
|  |  |  |  Content  |  |  |  |
|  |  |  +-----------+  |  |  |
|  |  +-----------------+  |  |
|  +-----------------------+  |
+-----------------------------+

```

## Propiedades de Texto y Fuente

CSS3 ofrece una amplia gama de propiedades para estilizar el texto.

### Tipografía

*   **font-family:** Define la familia de fuentes.
    
    `css body { font-family: 'Helvetica Neue', sans-serif; }`
    
*   **font-size:** Tamaño de la fuente.
    
    `css h1 { font-size: 2em; }`
    
*   **font-weight:** Grosor de la fuente.
    
    `css p { font-weight: bold; }`
    
*   **font-style:** Estilo de la fuente (normal, italic, oblique).
    
    `css em { font-style: italic; }`
    

### Propiedades de Texto

*   **color:** Color del texto.
    
    `css span { color: #ff5733; }`
    
*   **text-align:** Alineación del texto.
    
    `css .centrado { text-align: center; }`
    
*   **text-decoration:** Decoraciones del texto (subrayado, tachado, etc.).
    
    `css a { text-decoration: none; } a:hover { text-decoration: underline; }`
    
*   **line-height:** Altura de la línea.
    
    `css p { line-height: 1.6; }`
    



## Colores y Fondos

### Colores

Puedes definir colores usando nombres, códigos hexadecimales, RGB, RGBA, HSL y HSLA.

```
h2 {
    color: #3498db; /* Hexadecimal */
}

p {
    color: rgb(52, 152, 219); /* RGB */
}

div {
    background-color: rgba(52, 152, 219, 0.5); /* RGBA */
}

```


### Fondos

*   **background-color:** Color de fondo.
*   **background-image:** Imagen de fondo.
*   **background-repeat:** Repetición de la imagen.
*   **background-size:** Tamaño de la imagen de fondo.
*   **background-position:** Posición de la imagen de fondo.

```
body {
    background-color: #ecf0f1;
    background-image: url('fondo.jpg');
    background-repeat: no-repeat;
    background-size: cover;
    background-position: center;
}

```


## Diseño de Layout

### Flexbox

**Flexbox** es un modelo de diseño unidimensional que facilita la alineación y distribución de elementos dentro de un contenedor.

#### Contenedor Flex

```
.container {
    display: flex;
    flex-direction: row; /* column, row-reverse, column-reverse */
    justify-content: space-between; /* flex-start, flex-end, center, space-around, space-evenly */
    align-items: center; /* stretch, flex-start, flex-end, center, baseline */
}

```


#### Elementos Flex

```
.item {
    flex: 1; /* grow, shrink, basis */
    margin: 10px;
}

```


#### Ejemplo Completo

```
<div class="container">
    <div class="item">Elemento 1</div>
    <div class="item">Elemento 2</div>
    <div class="item">Elemento 3</div>
</div>

```


```
.container {
    display: flex;
    justify-content: space-around;
    align-items: center;
    height: 200px;
    background-color: #f8f9fa;
}

.item {
    background-color: #007bff;
    color: white;
    padding: 20px;
    border-radius: 5px;
}

```


### Grid Layout

**Grid Layout** es un sistema de diseño bidimensional que permite crear estructuras complejas con filas y columnas.

#### Contenedor Grid

```
.grid-container {
    display: grid;
    grid-template-columns: repeat(3, 1fr); /* 3 columnas de igual tamaño */
    grid-gap: 10px; /* Espacio entre filas y columnas */
}

```

#### Elementos Grid

```
.grid-item {
    background-color: #28a745;
    color: white;
    padding: 20px;
    text-align: center;
}

```

#### Ejemplo Completo

```
<div class="grid-container">
    <div class="grid-item">1</div>
    <div class="grid-item">2</div>
    <div class="grid-item">3</div>
    <div class="grid-item">4</div>
    <div class="grid-item">5</div>
    <div class="grid-item">6</div>
</div>

```

```
.grid-container {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    grid-gap: 15px;
    background-color: #f1f1f1;
    padding: 10px;
}

.grid-item {
    background-color: #28a745;
    color: white;
    padding: 30px 0;
    font-size: 30px;
    text-align: center;
}

```
