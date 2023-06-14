# PUG

## Sintáxis Básica

### Declarar elementos
- Se declara el elemento, solamente con el nombre.
- Se deja un espacio de separación para el contenido
    - `h1 Hola mundo` en lugar de <h1>Hola mundo</h1>

### Anidamiento
- Se indenta el elemento hijo
    ```javascript
    h1 Hola
        span Mundo!!
    ```
### Atributos
- Similar a HTML
- Más de un atributo => Separación por comas o espacios.
    ```javascript
    a(href="#") Soy un enlace
    img(src="logo.png", alt="El logo no existe")
    img(src="logo.png" alt="El logo no existe")
    ```
### Clases y id's
- Similar a los selectores CSS
- Varias clases separadas con punto
    - `p#text párrafo con ID`
    - `p.text párrafo con clase`
    - `p.text.text_rojo párrafo con clases`
    - `p.text#text párrafo con clasey id`

### Intercalar hijos dentro de elementos
- Para declarar una etiqueta cuyo contenido es texto dentro de otra etiqueta de texto, se debe separar con saltos de línea y un pipe `|`.

`padre` 1er_texto_padre `salto de línea` 

`indentación` `hijo` texto_hijo `salto de línea`

`|` `indentación` 2do_texto_padre

```p Lorem ipsum dolor, sit amet consectetur adipisicing elit. Dolore vero quis 
    a(href='#') dolorum
    | Dicta veniam culpa nisi dolor sequi ea aliquid mollitia sapiente natus consectetur, recusandae ducimus tempora officia cupiditate nostrum?
```

La segunda parte del texto del párrafo (padre) queda al mismo nivel de indentación del link.

Es importante tener en ceunta los espacios en blanco.

Pug considera que el 2do fragmento del pàrrafo, está al mismo nivel del link.

### Elementos en una misma línea

En lugar de salto + indentación, se puede usar el caracter `:`

```html
ul: li: a(href="") Estamos en una misma línea
```

## Scripts, styles y variables

- CSS => Etiqueta link
- JS => Etiqueta script src
- style y script en línea con un (.)
    - style.
        - propiedades
    - script.
        - scripts

## Variables JS en pug
- Se declaran de la misma forma qué en js, pero con un guión (-) antes.

`- let name = 'Fer'`

- Utilizar variable.
    - elemento seguido de el operador `(=)` más la variable o template strings en caso de formatear string.

    ```javascript
    h1= `Hola ${name}`
    h2= name
    ```
- Funciona igual con los arrays
- Para utilizar objetos se debe hacer después del guión un salto de línea e indentar.

```javascript
// Salto e indentación > (-)
- 
        let obj = {
            key1 : 'asdfasd',
            key2 : '2sdfasd'            
        }
```
## Condicionales

- Se declaran con if + condición sin ()
- Instrucción cond => Salto, indentación.
- Igual para el else
- Tambien se puede usar else if como en js

```javascript
if dato 
    p Se cumple la condición
else 
    p No se cumple la condición
```

### Operador ternarios
- Se usa para establecer atributos, clases y id's.
- Hay que escribir las clases y id's como en html

```javascript
        p(class= dato ? 'active' : 'inactive') Lorem, ipsum dolor sit amet
```

## Bucles

- each => Funciona igual for in
- each elm in iterable => salto, ind
    - Instrucción
- Cualquier código js es válido

```javascript
each name in names
    // p= name
    p= `${name.charAt(0).toUpperCase()}${name.substring(1)}`
```

### Validación de array vacio

- Utilizar else como en condicional
    - No vacio => Se ejecuta la instrucción de each
    - Vacio => Se ejecuta la instrucción del else

```js
each name in names
    p= `${name.charAt(0).toUpperCase()}${name.substring(1)}`
else 
    p= 'El array está vacio'
```
### Recorrer objetos

- Se un 2do parámetro
- Par 1 => Value
- Par 2 => Key

```js
each v, k in user
    p= `la key es ${k} el value es ${v}`
```

- El 2do parámetro también funciona con arrays, pero en este caso sería el índice.

```js
each name, i in names
    p= `${i+1}: ${name}`
```

## Templates
Código común a varias páginas

### Importar plantillas
- extends => ruta

`extends ../templates/template`

###Blocks

Marcas que se definen en las plantillas, para que en las instancias se pueda añadir código en el lugar deseado.

Extends no érmite añadir código sin usar blocks o mixins.

## Sintáxis

- template => `block name`
- instancia => `block name` => salto indentación => código


