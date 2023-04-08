
---
### Big 8 Data Types of Java Script
Big 8 data type of Java Script are:
- Number
- String
- Boolean
- Object
- Function
- Undefined
- BigInt
- Symbol
All number values are stored as 64-bit floating point
---
### Typeof

To determine the datatype of a variable, you use `typeof`

---
### String Manipulation
| Function    | Syntax                                                           |                
|-------------|------------------------------------------------------------------|
| `charAt(0)` | Character at a specific location.                                | 
| `.concat`   | Concatenates string e.g. `firstName.concat(" ").concat(lastName)` |
 
---
### Falsey Values
Other types can be converted to boolean and evaluatedd

The seven falsey values are:
- ""
- 0
- NaN
- 0n
- null
- undefined
- false
---
### JavaScript Objects

`let person = {
	name: "Jane",
	age: 35,
	eyeColor: "brown"
};`

<b>Accessing Object Properties</b>

`person.name` OR `person["name"]`

Objects are assigned by reference

Short-handed syntax for creating objects instead of verbose redeclaration

`let name = 'bob';`
`let age = 23;`
`let person = {name, age};`

---
### 3 Ways to define a function in JavaScript

Ways defining functions in JavaScript:
<b>Approach 1:</b>

 `function add(x, y){
    return x+y;
 }`

 When function are defined with `function`, they are hoisted.
It means it can be call prior to the function definition.
`myFunc();
function myFunc(){
 }`

<b>Approach 2</b>

`let add = function(x, y){
 return x+y;
 }`

<b> Approach 3</b>

 `let add=(x,y)=>{
 return x+y;}`
 
 


---
### "Undefined" vs. "null"
Undefined - variable/property haven't been declared. 
"null" - a piece of data has been declared, but the data has not been assigned yet.

| Description | Undefined             | Null               |
|-------------|-----------------------|--------------------|
| Type        | This is its own type. | Object             |
| Default     | Uses default          | Do not use default |
 
---
### === vs ==

`===` checks for same type and same value
`==` checks for type only

- `0 == "0"` true
- `0 == ''` true
- `0 == []` true
- `0 == null` false
- `0 == undefined` false
- `true` == true false
- `false` == false false
- `"" == false` true
- `0 == false` true
- `0n == false` true
- `NaN = false` false
- `null = false` false
- `undefined = false` false
- Explicitly convert it to compare `5 === Number("5")` true
- Do deep equality for objects
- `myArr1 === myArr2` false for `myArr1 = [1,2,3]` and `myArr2 = [1,2,3]`

---
### For Loops

<b>Choice 1:</b>
`for(let x = 0; x < 10; x++)`

<b>Choice 2:</b>
`for(let x of arr)`

<b>Choice 3:</b>
Loop through an object
People = {"name": Paul, "age": 24}

`for(let key in person){
}`

<b>Choice 4:</b>
Looping through arrays
`arr.forEach(function(x){console.log(x);});`

---

### Block Scope vs Function Scope

`var t = 99;` function scope
`let t = 99;` block scope

Stick to block scope

---
### Prototypical Inheritance

    class Person{
    
        constructor(name, age){
            this.name = name;
            this.age = age;
        }
    
        doSomething(older){
            this.age += older;
        }
    
        static doSomething(person1, person2){
            return Math.abs(person1.age - person2.age);
        }
    }

Inheritance

    class Employee extends Person{
        constructor(name, age, job){
            super(name, age);
            this.job = job;
        }

        doSomething(){
           let something =  super.doSomething();
        }
    }

### instanceof
`let somebody = Person("Bob, 23);`
- `somebody instanceof Person;` true
- `soembody instanceOf Employee;` false
- 
### Prototypical Inheritance
    let p = {name: 'Bob', age : 23, sayHello: function(){
        console.log("I am ${this.name}" );
    }};
    let c = Object.create(p);

- c is a child of p. It has the name and properties of p.
- Prototype is by pointing to person to say what that person is.

`null -> Object.prototype -> person -> anotherPerson`

`Object.prototype` or `{}` is the uppermost prototype of all JavaScript objects.

`Object.getPrototypeOf(obj);` => gets the prototype of the object

---
### this Keyword
It points to current execution context.

    let introduce = function(){
      console.log(`I am hungry ${this.name}`);
    }
    
    let setting = function(){
      this.name = "Susan Doe";
    }
    
    let p ={
      name: "John Doe",
      introduce,
      setting,
    }
    
    p.introduce();
    p.setting();
    console.log(p.name);
---
### Built-In Functions Objects

| Function       | Description                                           |  
|----------------|-------------------------------------------------------|
| `Object.keys`    | keys of values                                        | 
| `Object.values`  | Uses default                                          |
| `Object.entries` | all key value pairs e.g. ["a", 1], ["b", 2], ["c", 3] |
|   `Object.assign` | assign the 2nd properties to the 1st |

### Create a Brand New Object Instead of Referencing

    let myObj = {a: 1, b : 2};
    let newObj = Object.assign({}, myObj);


### Built-In Functions Arrays

| Function      | Description                                                                                    |  
|---------------|------------------------------------------------------------------------------------------------|
| `arr.push`    | Add an element                                                                                 | 
| `arr.pop`     | Removes element                                                                                |
| `arr.splice`  | array.splice(startingIndex, removeHowMany, elementsToAdd);                                     |
| `arr.indexOf` | index at a specific element                                                                    |
| `arr.find`    | takes a function and returns 1st that fulfill condition                                        |
 | `arr.filter`  | takes a function and returns 1st that fulfill condition `arr.filter((item)=> item.val > 10)`   |
 | `arr.map`     | takes a function and returns 1st that fulfill condition   `arr.map((item)=> item.val * 2)`      |
 |`arr.reduce` | takes a function and returns a summation `arr.reduce((accum, curr)=> {return accum + curr},0)` |                             
---
### Arrow Function [ES6]
Use the function keyword inside classes, use arrow functions for most other cases
First instance works fine.
Second instance returns undefined.

    let obj = {name: 'Bob', sayHello: function(){
        console.log(`This is ${this.name}`);
    }}
    
    let obj = {name: 'Bob', sayHello: ()=>
        console.log(`This is ${this.name}`)
    }
---
### Default Arguments and Object in Arrows [ES6]

Example of default arguments

    let obj2 = (arg1="Bob", arg2="Knows", arg3="You") =>({
        arg1, arg2, arg3
    });
    
    console.log(obj2());

---
### Spread Operator [ES6]

It serves three functions:
- Combine objects and arrays
- Get function arguments as an array
- Pass array elements as arguments

Combine objects and arrays

    let personal = {name: 'Bob', age: 40};

    let profession = {job: 'clerk'};
    
    console.log({...personal, ...profession, hobbies: 'swimming'});
    
    let arr1 = [4, 5];
    
    let arr2 = [10, 11];
    
    console.log(...arr1, 6, 7, ...arr2);

 
Get function arguments as an array

    let arr1 = [4, 5];
    let arr2 = [10, 11];
    
    let test = (item1, item2, ...remainder) =>
      console.log(remainder);
    test(...arr1, 6, 7, ...arr2);

Pass array element as argument

    let arr = [1,2,3];

    let add = (x, y, z) =>  x + y + z;
    
    console.log(add(...arr));
---
 ## Object Destructuring [ES6]

Destructuring Object

    let person = {name: 'Bob', age: 40}
     let {name, age} = person;

Object with default value

      let person = {name: 'Bob'}
      let {name, age = 50} = person;

Object with new variable name 

        let person = {name: 'Bob'};
        let {name: personName, age = 50} = person;

Object with nested properties

        let person = {name: 'Bob', bodyMeasure: {
          height: 170, weight: 60
        }};
        let {
              name: personName, 
              age = 50, 
              bodyMeasure: {weight}
            } = person;
        
        console.log(personName);
        console.log(age);
        console.log(weight);

Arrays Destructuring

    let arr = [2,4,5,6]

    let [w, x] = arr
    
    console.log(w);
    console.log(x);
---
## JavaScript Import / Export [ES6]

Three types of exports:
- export default
- name export
- namespace export

| Type             | Before                | After (ES6)                                    |
|------------------|-----------------------|------------------------------------------------|
| export default   | `module.exports = {myFunc, myString};` | `export default {myFunc, myString};`           |
| import default  | `let myFunc = required('./someFile');` | `import {myString, myFunc} from './someFile';` |
| namespace export |                       | `import * as util from './utilities';`|
|name export |                       | `export let myString = "Hello"; export function myFunc(){}; import {myString, myFunc} from ./someFile';`|

`export default myFunc` is not the same as `module.exports = myFunc`.
It is more as such `modeul.exports.default = myFunc`.
Bear in mind when using mismatch of syntax. So, if you export default in one,
and use required in the other, required need to be: `let myFunc = required('./someFile').default;`

---
## Asychronous Javascript
Three forms of asynchronous Javascript:
- Callbacks
- Promises
- Async and Await


 