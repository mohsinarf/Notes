# JavaScript CheatSheet

## Sources
https://www.youtube.com/watch?v=Zi-Q0t4gMC8


### Data Types
```
let firstName = 'John';
console.log(typeof firstName);
                               
let num1 = 10;
console.log(typeof num1);

let pi = 3.14;
console.log(typeof pi);

let status = true;
console.log(typeof status);

let bigNum = 100000000n;
console.log(typeof bigNum);

let favouiteFood;
console.log(typeof favouiteFood);

const uniqueId = Symbol('id');
console.log(typeof uniqueId);

let user = { name: 'John', age: 30 };
user.name = 'Doe';
console.log(user);
console.log(user['name']);
console.log(typeof user);

let fruits = ['Apple', 'Banana', 'Orange'];
console.log(fruits);
```

### Functions
```
function greet(name) {
  console.log('Hello ' + name);
}

greet('John');
```

### Comparison operators
```
console.log(1 > 2); // false
console.log(1 < 2); // true
console.log(1 >= 2); // false
console.log(1 <= 2); // true
console.log(1 == 2); // false
console.log(1 != 2); // true
```

```
// Lose equality vs strict equality
console.log(1 == '1'); // true
console.log(1 === '1'); // false
```

```
// falsy values
console.log(0 == false); // true
console.log('' == false); // true
console.log(null == false); // false
console.log(undefined == false); // false
console.log(NaN == false); // false
```
### Conditional statements
```
// Conditional Statements
let hour = 10;

if(hour >= 6 && hour < 12)
    console.log('Good morning');
else if(hour >= 12 && hour < 18)
    console.log('Good afternoon');
else
    console.log('Good evening');
```

### Switch statements
```
let job = 'developer';

switch (job) {
  case 'developer':
    console.log('You will be a developer');
    break;
  case 'designer':
    console.log('You will be a designer');
    break;
  default:
    console.log('You will be something else');
}
```
### Loops in Javascript
```
let numbers = [1, 2, 3, 4, 5];
for (let id=0; id <numbers.length; id++) {
    console.log(numbers[id]);
}
```

```
let numbers = [1, 2, 3, 4, 5];

let id = 0;
while (numbers.length > id) {
  console.log(numbers[id]);
  ++id; 
}
```
```
let numbers = [1, 2, 3, 4, 5];
let id = 0;
do{
  console.log(numbers[id]);
  ++id; 
}while (numbers.length > id)
```

```
let course = {
  title: "Learn JavaScript",
  level: 1,
  topics: ["variables", "functions", "objects"]
};

for (let key in course) {
  console.log(key + ": " + course[key]);
}
```

```
let numbers = [1, 2, 3, 4, 5];
for (const element of numbers) {
  console.log(element);
}
```

### javascript object literal
```
const dog = {
  name: 'Buddy',
  breed: 'Golden Retriever',
  bark() {
    console.log('Woof!');
  }
};

dog.bark(); // Output: Woof!
```

### Factory Functions
```
function getDog(name, breed) {
  return {
    name: name,
    breed: breed,
    bark() {
      console.log('Woof!');
    }
  };
}

const anotherDog = getDog('Buddy', 'Golden Retriever');
console.log(anotherDog); // Output: Buddy
```

### Constructor Functions
```
 function Dog(name, breed, weight){
    this.name = name;
    this.breed = breed;
    this.weight = weight;
    this.bark = function(){
        if(this.weight > 25){
            alert(this.name + " says Woof!");
        } else {
            alert(this.name + " says Yip!");
        }
    };
 }

  var fido = new Dog("Fido", "Mixed", 38);
  console.log(fido);
```

### Objects Dynamics
```
const person = {
  name: 'John'
};
console.log(person); 

person.age = 25;
console.log(person);

person['surname'] = 'Doe';
console.log(person);

person.job = function() {
  console.log('I am a developer');
}
console.log(person);

delete person.age;
console.log(person);
```

### Functions are objects
```
const Programmer = function(name) {
  this.name = name;
  this.sayHello = function() {
      console.log(`Hello, ${this.name}`);
  };
};

const newProgrammer = new Programmer('John');
newProgrammer.sayHello(); // Outputs: Hello, John
```

### Primitive vs objects values
#### Primitive data types
Primitive data types are data types that are not objects. They do not have methods or properties.
There are 7 primitive data types: string, number, bigint, boolean, undefined, symbol, and null.
#### Object data types
Objects are complex data types that are made up of key-value pairs.
Objects can contain primitive data types, other objects, and functions.

Primitive values are passed by values while objects are passed by reference.

## Enumerating objects in javascript
```
const dog = {
  name: 'dog',
  age: 3,
  breed: 'Golden Retriever'};

  const keys = Object.keys(dog);
  const values = Object.values(dog);
  const entries = Object.entries(dog);
  console.log(keys);
  console.log(values);
  console.log(entries);
  
```

### Clonning object data types
```
const dog = {
  name: 'dog',
  age: 3,
  breed: 'Golden Retriever'
};

let dog2 = {};
Object.assign(dog2, dog);

let dog3 = { ...dog };

```

### Template literals
```
// Template literals
let firstName = 'John';
let lastName = 'Doe';

let fullName = `${firstName} ${lastName}`;
console.log(fullName); // John Doe
```

### Functions declration 
```
// Function declaration vs function expression
let greet = function() {
  console.log("Hello, World!");
};

greet(); // Hello, World!

// Function declaration
function greet() {
  console.log("Hello, World!");
}

greet(); // Hello, World!
```

### Hoisting in javascript
```
// What is hoisting?
// Hoisting is a JavaScript mechanism where variables and function declarations are moved to the top of their scope before code execution.
// Inevitably, this means that no matter where functions and variables are declared, they are moved to the top of their scope regardless of whether their scope is global or local.
// Hoisting is JavaScript's default behavior of moving declarations to the top.
// However, only the declarations are hoisted, not the initializations.
console.log(x); // undefined
var x = 5;

// let and const are not hoisted
console.log(y); // ReferenceError: Cannot access 'y' before initialization
let y = 5;
```
### Function Arguments 
```
// function arguments
function multiply(a, b) {
    let product = 1;

    for (let number of arguments) {
        product *= number;
    }
    return product;
}

console.log(multiply(1, 2, 3, 4, 5)); // 120
```

### Rest operator
```
// rest operator
function multiply(multiplier, ...theArgs) {
  return theArgs.map(x => multiplier * x);
}   

var arr = multiply(2, 1, 2, 3);
console.log(arr); // [2, 4, 6]
```

### Default paramters
```
// Function default parameters
function greet(name = 'World') {
    console.log(`Hello, ${name}!`);
    }
    greet(); // Hello, World!
```

### Getters and Setters 
```
// Getters and Setters
let user = {
    name: "John",
    surname: "Smith",
    
    get fullName() {
        return `${this.name} ${this.surname}`;
    },
    
    set fullName(value) {
        [this.name, this.surname] = value.split(" ");
    }
    };
```

### Try and catch 
```
// Getters and Setters
let user = {
    name: "John",
    surname: "Smith",
    
    get fullName() {
        return `${this.name} ${this.surname}`;
    },
    
    set fullName(value) {
        if(typeof value !== "string") {
            throw new Error("Value must be a string");
        }
        [this.name, this.surname] = value.split(" ");
    }
};

try{
    user.fullName = 42;
    console.log(user); // Alice Cooper
}
catch(e) {
    console.log(`Caught an error , ${e.message}`);
}
```
### let vs var keyword   
- let is block scoped and var is function scoped
### this keyword

