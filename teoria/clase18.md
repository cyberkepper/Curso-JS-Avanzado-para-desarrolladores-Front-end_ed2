# Clase 18

### Drag & Drop
- [Documentación](https://developer.mozilla.org/es/docs/DragDrop/Drag_and_Drop)
- [Tutorial](https://www.html5rocks.com/es/tutorials/dnd/basics/)
- [Demo](http://html5demos.com/drag)


### Canvas
- [Documentación](https://developer.mozilla.org/es/docs/Web/HTML/Canvas)
- [Integrating Canvas into your Web App](https://www.html5rocks.com/en/tutorials/canvas/integrating/)
- [Canvas tutorial](https://developer.mozilla.org/en-US/docs/Web/API/Canvas_API/Tutorial?redirectlocale=en-US&redirectslug=Canvas_tutorial)
- [Dive Into HTML5 > Canvas](http://diveintohtml5.info/canvas.html)
- [HTML5 Canvas — the Basics](https://dev.opera.com/articles/html5-canvas-basics/)
- [Tutorial](https://billmill.org/static/canvastutorial/index.html)


### indexedDB
- [Documentación](https://developer.mozilla.org/en-US/docs/Web/API/IndexedDB_API)
- [diveintohtml5 - Storage](http://diveintohtml5.info/storage.html)
- [Soporte](http://caniuse.com/#feat=indexeddb)
- [Tutorialspoint - indexedDB ](https://www.tutorialspoint.com/html5/html5_indexeddb.htm)
- [Storing images and files in IndexedDB](https://hacks.mozilla.org/2012/02/storing-images-and-files-in-indexeddb/)
- [Building A Simple Cross-Browser Offline To-Do List With IndexedDB And WebSQL By Matt Andrews](https://www.smashingmagazine.com/2014/09/building-simple-cross-browser-offline-todo-list-indexeddb-websql/)


### Expresiones Regulares

![Regular Expression XKCD](http://imgs.xkcd.com/comics/regular_expressions.png "RegEx save the day")
<sup>http://xkcd.com/208/</sup>


![email regex](http://i.imgur.com/7rV4c56.jpg "email regex")



**Creación**
```javascript
var expresionRegular = /fictizia/;
var expresionRegular = new RegExp("fictizia");
```

**[Trabajando con Flags](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/RegExp/flags)**

- Flags disponibles:
    - [g](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/RegExp/global), *Buscar en todo el texto*
    - [i](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/RegExp/ignoreCase), *Case-insensitive*
    - [m](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/RegExp/multiline), *Multilineal*
    - [y](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/RegExp/sticky), *Sticky, recordando la última búsqueda*

- Usando Flags:
```javascript
var expresionRegular = /fictizia/gi;
var expresionRegular = new RegExp("fictizia", "gi");
```

**Métodos**
- [exec](https://developer.mozilla.org/en-US/docs/JavaScript/Reference/Global_Objects/RegExp/exec)
    Método RegExp que devuelve un array de información.
    ```javascript
    var coincidencias = /Fictizia/.exec('Hola desde Fictizia! Que te cuentas?');
    var coincidencias2 = /dato/.exec('Hola desde Fictizia! Que te cuentas?');
    console.log(coincidencias[0]); // Fictizia
    console.log(coincidencias2);   // null
    ```

- [test](https://developer.mozilla.org/en-US/docs/JavaScript/Reference/Global_Objects/RegExp/test)
    Método RegExp que verifica una coincidencia en una cadena. Devuelve true o false.
    ```javascript
    var coincidencias = /Fictizia/.test('Hola desde Fictizia! Que te cuentas?');
    var coincidencias2 = /dato/.test('Hola desde Fictizia! Que te cuentas?');
    console.log(coincidencias);  // true
    console.log(coincidencias2); // false
    ```

- [match](https://developer.mozilla.org/en-US/docs/JavaScript/Reference/Global_Objects/String/match)
    Método String que retorna un array de información o null si no existe coincidencia alguna.
    ```javascript
    var cadena = 'Hola desde Fictizia! Que te cuentas?';
    var erFictizia = /Fictizia/;
    var erDato = /dato/;
    var coincidencias = cadena.match(erFictizia);
    var coincidencias2 = cadena.match(erDato)
    console.log(coincidencias[0]); // Fictizia
    console.log(coincidencias2);   // null
    ```

- [search](https://developer.mozilla.org/en-US/docs/JavaScript/Reference/Global_Objects/String/search)
    Método String que devuelve el índice de la coincidencia, o -1 si la búsqueda falla.
    ```javascript
    var cadena = 'Hola desde Fictizia! Que te cuentas?';
    var erFictizia = /Fictizia/;
    var erDato = /dato/;
    var coincidencias = cadena.search(erFictizia);
    var coincidencias2 = cadena.search(erDato)
    console.log(coincidencias);   // 11
    console.log(coincidencias2);  // -1
    ```

- [replace](https://developer.mozilla.org/en-US/docs/JavaScript/Reference/Global_Objects/String/replace)
    Método String que reemplaza la subcadena encontrada con una subcadena de reemplazo.
    ```javascript
    var cadena = 'Hola desde Fictizia! Que te cuentas?';
    var erFictizia = /Fictizia/;
    var erDato = /dato/;
    var coincidencias = cadena.replace(erFictizia, "Cambiazo");
    var coincidencias2 = cadena.replace(erDato, "Cambiazo")
    console.log(coincidencias);   // Hola desde Cambiazo! Que te cuentas?
    console.log(coincidencias2);  // Hola desde Fictizia! Que te cuentas?
    ```

- [split](https://developer.mozilla.org/en-US/docs/JavaScript/Reference/Global_Objects/String/split)
    Un método String que retorna un array de subcadenas partiendo de un patrón dado.
    ```javascript
    var cadena = 'Hola desde Fictizia! Que te cuentas?';
    var erFictizia = /Fictizia/;
    var erDato = /dato/;
    var coincidencias = cadena.split(erFictizia);
    var coincidencias2 = cadena.split(erDato)
    console.log(coincidencias);   // ["Hola desde ", "! Que te cuentas?"]
    console.log(coincidencias2);  // ["Hola desde Fictizia! Que te cuentas?"]
    ```

###  Regex: Patrones complejos

Se utilizan los caracteres a, b, c y d para ilustrar los ejemplos.

**Básicos**

- ab
    Cualquier caracter o conjunto de caracteres. La busqueda se realiza de forma literal
    ```javascript
    //Encuentra solo el Lunes
    /Lunes/.test("Lunes")
    ```

**Anclajes**

- ^ab
    Coincide con el principio de la cadena o línea.
    ```javascript
    /^000/g.test("0001 es un id básico");
    ```

- ab$
    Coincide con el final de la cadena o línea.
    ```javascript
    /on$/.test("cancion")
    ```

**Metacaracteres**

Deberían ser escapados.

- .
    El metacaracter punto que coincide con cualquier carácter excepto *\n \r \u2028* o *\u2029*.
    ```javascript
    "That's hot!".match(/h.t/g);
    // [hat, hot]
    ```

- a|b
    Coincide con uno o con otro.
    ```javascript
    //Encuentra Lunes o Martes pero no Miercoles, jueves...
    /Lunes|Martes/.test("Martes")
    ```

- \
    Escapa un carácter específico.
    ```javascript
    /\*/.test("*")
    ```

**Cuantificadores**

- *
    Coincide con cero o más ocurrencias de la subexpresión que le precede al asterisco.
    ```javascript
    //Encuentra A, Ahhh, Ah, etc...
    /Ah*/.test("Ahhhhhhhh!")
    ```

- +
    El metacaracter suma coincide con una o más ocurrencias de la subexpresión que lo precede.
    ```javascript
    //Encuentra Ahhh, Ah, etc... pero no A.
    /Ah+/.test("Ahhhhhhhh!")
    ```

- ?
    Coincide con cero o un caracter.
    ```javascript
    //Encuentra A, Ahhh, An, Al, etc...
    /Ah?/.test("Ahhhhhhhh!")
    ```

- {X,y}
    Coincide un número determinado de veces.
    ```javascript
    // {2} Exactamente 2. Encuentra 11, 99, pero no 9, 987, etc...
    /[1-9]{2}/.test(12);

    // {2, 5} Exactametne entre 2 y 5. Encuentra 11, 666, 74511 pero no 1, 123456, etc...
    /[1-9]{2, 5}/.test(12345);

    // {2,} Exactamente 2 o más. Encuentra 11, 666, 74511 pero no 1,
    /[1-9]{2}/.test(123);
    ```



**Clases de caracteres**

- \d
    numérico (incluyendo _)
    ```javascript
    "Hola u_123! *.*".match(/\d/g);
    //["1", "2", "3"]
    ```

- \D
    No-numérico (incluyendo _)
    ```javascript
    "Hola u_123! *.*".match(/\D/g);
    // ["H", "o", "l", "a", " ", "u", "_", "!", " ", "*", ".", "*"]
    ```

- \s
    Busca un espacios en blanco
    ```javascript
    "Hola u_123! *.*".match(/\s/g);
    // [" ", " "]
    ```

- \S
    Busca que no coincida con un espacios en blanco
    ```javascript
    "Hola u_123! *.*".match(/\S/g);
    // ["H", "o", "l", "a", "u", "_", "1", "2", "3", "!", "*", ".", "*"]
    ```

- \w
    Busca caracteres alfanuméricos (_ incluido)
    ```javascript
    "Hola u_123! *.*".match(/\w/g);
    // ["H", "o", "l", "a", "u", "_", "1", "2", "3"]
    ```

- \W
    Busca que no coincida con un caracteres alfanuméricos (_ incluido)
    ```javascript
    "Hola u_123! *.*".match(/\W/g);
    // [" ", "!", " ", "*", ".", "*"]
    ```

- \b
    Busca la coincidencia al principio o fin de la palabra.
    ```javascript
    /\bme/g.test("menos")
    ```

- \B
    Busca la coincidencia evitando el principio o fin de la palabra.
    ```javascript
    /\Bte/g.test("bateria")
    ```

- \n
    Busca el salto de línea
    ```javascript
    /\n/.test("Hola!\nHola de nuevo...")
    ```

- \r
    Busca el retorno de carro
    ```javascript
    /\r/.test("Hola!\rHola de nuevo...")
    ```

- \t
    Busca la tabulación
    ```javascript
    /\t/.test("Hola!\tHola de nuevo...")
    ```


- \xxx
    Busca un caracter especificando el octal
    ```javascript
    // W -> 127
    /\127/g.test("Me gusta la Web")
    ```

- \uxxxx
    Busca un caracter unicode especificando en hexadecimal.
    ```javascript
    // W -> u0057
    /\u0057/g.test("Me gusta la Web")
    ```


**Agrupadores y Rangos**


- [ab]
    Coincide con al menos uno de los caracteres.
    ```javascript
    "hola... y de nuevo hola".match(/[hol]/g)
    // ["h", "o", "l", "o", "h", "o", "l"]
    ```

- [1-9]
    Rango entre 1 y 9
    ```javascript
    "172635172312312352451234...".match(/[1-4]/g)
    // ["1", "2", "3", "1", "2", "3", "1", "2", "3", "1", "2", "3", "2", "4", "1", "2", "3", "4"]
    ```

- [a-f]
    Rango alfabetico entre a y f.
    ```javascript
    "am3s5bdnd,ABCvm2naw8perjascm<lcmqPWD...".match(/[5-8q-zA-C]/g)
    // ["s", "5", "A", "B", "C", "v", "w", "8", "r", "s", "q"]
    ```

- [^ab]
    No debe coincidir con ningun de estos carácteres.
    ```javascript
    "hola... y de..".match(/[^hol]/g)
    // ["a", ".", ".", ".", " ", "y", " ", "d", "e", ".", "."]
    ```

- (ab)
    Agrupadores, permite crear un grupo
    ```javascript
    "Hola _quien seas_".replace(/_(.*?)_/, "<strong>$1</strong>")
    ```

- (?:ab)
    Grupo no capturado
    ```javascript
    "foo".match(/(foo){1,2}/) // ["foo", "foo"]
    "foo".match(/(?:foo){1,2}/) //["foo"]
    ```

- a(?=b)
    Encuentra *a* solo si *a* es seguido de *b*.
    ```javascript
    //Encuentra Metacaracter o Metacaracteres pero no Metadato.
    /Meta(?=caracter|caracteres)/.test("Metacaracter");
    ```

- a(?!y)
    Encuentra *a* solo si *a* no va seguido de *b*.
    ```javascript
    // Encuentra 141 pero no 3.141.
    /\d+(?!\.)/.test("3.141")
    ```


### Ejercicios

**1 -** Captura los emails del siguiente texto.
```
demo@demo.com, demo_demo@demo.com.ar, demo-demo12312@sub.dom.com.ar, demo@novalido, novalido>@demo.com, demo@novalido-.com, demo@-novalido.com
```

```javascript
var email = /[a-z0-9!#$%&'*+\/=?^_`{|}~-]+(?:\.[a-z0-9!#$%&'*+\/=?^_`{|}~-]+)*@(?:[a-z0-9](?:[a-z0-9-]*[a-z0-9])?\.)+[a-z0-9](?:[a-z0-9-]*[a-z0-9])?/g;
var emails = "demo@demo.com, demo_demo@demo.com.ar, demo-demo12312@sub.dom.com.ar, ,demo@novalido, novalido>@demo.com, demo@novalido-.com, demo@-novalido.com".match(email);
console.log(emails);
// ["demo@demo.com", "demo_demo@demo.com.ar", "demo-demo12312@sub.dom.com.ar"]
```


**2 -** Captura el DNI y NIE
- Formato DNI: 11223344-A (Guión opcional).

```
Válidos: 12345678-A, 11223344A,
No válidos: A11223344, 1234567K
```

- Formato para el NIE: X-1223344-A (Guión opcional).
    - El inicio puede ser X, Y o Z.

```
Válidos: X-1234567-A, X1234567A, Z1234567M
No válidos: X-1233456, 1234567
```

```javascript
var NIE = /([X-Z]{1})([-]?)(\d{7})([-]?)([A-Z]{1})/g;
var DNI = /(\d{8})([-]?)([A-Z]{1})/g;
var todosRegex = /(([X-Z]{1})([-]?)(\d{7})([-]?)([A-Z]{1}))|((\d{8})([-]?)([A-Z]{1}))/g;

var dniText = "Válidos: 12345678-A, 11223344A. No válidos: A11223344, 1234567K."
var nieText = "Válidos: X-1234567-A, X1234567A, Z1234567M. No válidos: X-1233456, 1234567."
var todosTexto = dniText + nieText

var DNIs = dniText.match(DNI);
var NIEs = nieText.match(NIE);
var todos = todosTexto.match(todosRegex)

console.log("Solo DNIs:", DNIs); // ["12345678-A", "11223344A"]
console.log("Solo NIEs:", NIEs); // ["X-1234567-A", "X1234567A", "Z1234567M"]
console.log("TODOS:", todos); // ["12345678-A", "11223344A", "X-1234567-A", "X1234567A", "Z1234567M"]
```

**3 -** Comprobar la seguridad de una contraseña

De esta forma comprobaremos:
- Contraseñas que contengan al menos una letra mayúscula.
- Contraseñas que contengan al menos una letra minúscula.
- Contraseñas que contengan al menos un número
- Contraseñas que contengan al menos un caracter especial @#$%.
- Contraseñas cuya longitud sea como mínimo 6 caracteres.
- Contraseñas cuya longitud máxima sea 20 caracteres.

```javascript
var test = `Válidas:
Z%C2Uacgw_4weL@Q
QZ6UttU-&r4t%R+J
KK8a%K^9seQ$Qc8X
*Q#*9-CP%?JkXQSs
#1234abCD@

No válidas:
?mT6JmKpTu6m_=g=
=G4T!v-J2_6aS^EW
perrito
perrito123
Perrito1234`;

var exp = /((?=.*\d)(?=.*[a-z])(?=.*[A-Z])(?=.*[@#$%]).{6,20})/gm;
var validas = test.match(exp);
// ["Z%C2Uacgw_4weL@Q", "QZ6UttU-&r4t%R+J", "KK8a%K^9seQ$Qc8X", "*Q#*9-CP%?JkXQSs", "#1234abCD@"]
```


**4 -** Incorpora el patron *Chain of responsability* al cajero automatico para indicar los billetes y monedas facilitadas por la maquina cuando se retira efectivo

- [Solución](http://codepen.io/ulisesgascon/pen/91487e2ccdab7a1064516e3693547733)

**5 -** Refactoriza la aplicación de las películas:
- Objetivos:
  - Encapsular todo el código
  - Controlar la interacción con eventos
  - Estructurar el código de una manera eficiente

- [Solución](http://codepen.io/ulisesgascon/pen/48b774d3d0ffefe1bfb079f79bc8686a/)