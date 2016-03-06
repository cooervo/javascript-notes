# Javascript Inheritance

JS does NOt have classical OOP inheritance. It uses **prototype-based OO**. [Stackoverflow link](http://stackoverflow.com/a/389390/4031815) for further info.


```
// =============== Super prototype ===============
function Mammal() {}
//properties
Mammal.prototype.legs = 4;
Mammal.prototype.characteristics = ["makes milk", "has fur"];
//methods
Mammal.prototype.noise = function(){
    console.log("...")
}

// =============== Sub prototype ===============
function Dog() {}
//set dog to inherit from Mammal
Dog.prototype = Object.create(Mammal.prototype);
// New properties
Dog.prototype.howls = true;

// Override Superclass methods
Dog.prototype.noise = function(){
    console.log("Woof")
}


var mammal = new Mammal(); //Notice constructor we can pass parameters
console.log(mammal.legs); //4
console.log(mammal.howls); //undefined  (mammal does NOT inherit from Dog
console.log(mammal.noise()); //"..."

// Now initialize an instance of Dog and try it
var pluto = new Dog();
console.log(pluto.legs)// 4
console.log(pluto.howls)// true
pluto.noise(); //"Woof"

// =============== Sub prototype ===============
function Kangaroo(){}
Kangaroo.prototype = Object.create(Mammal.prototype);

var kangaroo = new Kangaroo();
console.log(kangaroo.legs)// 4
//Override property
Kangaroo.prototype.legs = 2;
console.log(kangaroo.legs)// 2

console.log(mammal.legs)// 4

/**
 * JAVASCRIPT DOES NOT HAVE OOP CLASSES, IT HAS PROTOTYPAL INHERITANCE
 */
console.log(mammal.characteristics)// ["makes milk", "has fur"]
kangaroo.characteristics.push("jumps!!!")
console.log(kangaroo.characteristics)// ["makes milk", "has fur", "jumps!!!"]
//Notice that when pushing to kangaroo.characteristics, it was also pushed to mammal.characteristics
console.log(mammal.characteristics)// ["makes milk", "has fur", "jumps!!!"]```
