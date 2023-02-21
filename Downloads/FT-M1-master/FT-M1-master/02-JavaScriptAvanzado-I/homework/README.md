
# Homework JavaScript Avanzado I

## Scope & Hoisting

Determiná que será impreso en la consola, sin ejecutar el código.

> Investiga cuál es la diferencia entre declarar una variable con `var` y directamente asignarle un valor.

```javascript
x = 1;
var a = 5;
var b = 10;
var c = function(a, b, c) {
  var x = 10;  // trabaja con el valor de 10 porque esta dentro de C
  console.log(x); // muestra 10
  console.log(a); // muestra 5
  var f = function(a, b, c) {
    b = a; // 10 y 10
    console.log(b); // 10
    b = c; // 10 = 10 
    var x = 5;
  }
  f(a,b,c);
  console.log(b); //10
}
c(8,9,10);
console.log(b); // 10
console.log(x); //1 o si esta dentro de C 10
```

```javascript
console.log(bar);
console.log(baz);
foo();
function foo() { console.log('Hola!'); } //hola 
var bar = 1; //le asigna 1 a bar
baz = 2; // le asigna 2
```

```javascript
var instructor = "Tony";
if(true) {
    var instructor = "Franco"; 
}
console.log(instructor); // Tony ---  porque Franco esta dentro de if 
```

```javascript
var instructor = "Tony";
console.log(instructor); //Tony--- 
(function() {
   if(true) {
      var instructor = "Franco";
      console.log(instructor); // Franco 
   }
})();
console.log(instructor); // Tony
```

```javascript
var instructor = "Tony";
let pm = "Franco";
if (true) {
    var instructor = "The Flash";
    let pm = "Reverse Flash";
    console.log(instructor); // "The Flash"; 
    console.log(pm); // "Reverse Flash";
}
console.log(instructor); // "Tony"
console.log(pm); // "Reverse Flash"
```
### Coerción de Datos

¿Cuál crees que será el resultado de la ejecución de estas operaciones?:

```javascript
6 / "3"  // 9
"2" * "3" // 6
4 + 5 + "px" // undefined
"$" + 4 + 5 //  
"4" - 2 // 2
"4px" - 2 // undefined
7 / 0 // 0
{}[0] // {[0]}
parseInt("09")
5 && 2 // 
2 && 5 // 
5 || 0 // f
0 || 5 // f 
[3]+[3]-[10] // f
3>2>1  // f
[] == ![] // f
```

> Si te quedó alguna duda repasá con [este artículo](http://javascript.info/tutorial/object-conversion).


### Hoisting

¿Cuál es el output o salida en consola luego de ejecutar este código? Explicar por qué:

```javascript
function test() {
   console.log(a);
   console.log(foo());

   var a = 1;
   function foo() {
      return 2;
   }
}

test();
```

Y el de este código? :

```javascript
var snack = 'Meow Mix';

function getFood(food) {
    if (food) {
        var snack = 'Friskies';
        return snack;
    }
    return snack;
}

getFood(false);
```


### This

¿Cuál es el output o salida en consola luego de ejecutar esté código? Explicar por qué:

```javascript
var fullname = 'Juan Perez';
var obj = {
   fullname: 'Natalia Nerea',
   prop: {
      fullname: 'Aurelio De Rosa',
      getFullname: function() {
         return this.fullname;
      }
   }
};

console.log(obj.prop.getFullname());

var test = obj.prop.getFullname;

console.log(test());
```

### Event loop

Considerando el siguiente código, ¿Cuál sería el orden en el que se muestra por consola? ¿Por qué?

```javascript
function printing() {
   console.log(1);
   setTimeout(function() { console.log(2); }, 1000);
   setTimeout(function() { console.log(3); }, 0);
   console.log(4);
}

printing();
```