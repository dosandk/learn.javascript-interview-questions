# javascript-interview-questions

# Questions list

1. Find the sum of the elements of a two-dimensional 
array of the type `[[1,2,3], [4,5,6], [7,8,9]]`.

comment: Task on knowledge of array methods.

> complexity: ⭐  
tags: ["arrays"]  
 
<details>
  <summary>Answer</summary>

  ```js
  const arr = [[1,2,3],[4,5,6],[7,8,9]]; 
  const result = arr.flat().reduce((acc, cur) => acc + cur, 0); 
  ```
</details>

2. What does the console output?

comment: The task of knowledge of the working principle of "Prototype inheritance".
 
> complexity: ⭐⭐  
tags: ["prototype inheritance"]  

   ```js
   const obj1 = {}; 
   const obj2 = {}; 
   const number = 1;
    
   console.log(number.__proto__ === Number.prototype); 
   console.log(number.prototype === Number.prototype); 
   console.log(number.__proto__ === obj2.__proto__); 
   console.log(number.__proto__ === Number.__proto__); 
   console.log(obj1.prototype === Object.prototype); 
   console.log(obj1.__proto__ === obj2.__proto__); 
   ```
<details>
  <summary>Answer</summary>

  ```js
  console.log(number.__proto__ === Number.prototype); // true
  console.log(number.prototype === Number.prototype); // false
  console.log(number.__proto__ === obj2.__proto__); // false
  console.log(number.__proto__ === Number.__proto__); // false
  console.log(obj1.prototype === Object.prototype); // false
  console.log(obj1.__proto__ === obj2.__proto__); // true
  ```
</details>

3. What will the given console logs show?

comment: The task tests knowledge about type conversions.

> complexity: ⭐  
tags: ["types conversion"]  

  ```js
  console.log(1 + "2" + "2");  
  console.log(1 + +"2" + "2"); 
  console.log(1 + -"1" + "2"); 
  console.log(+"1" + "1" + "2"); 
  console.log( "A" - "B" + "2");
  сonsole.log( "A" - "B" + 2);
``` 

<details>
  <summary>Answer</summary>
  
   ```js
   console.log(1 + "2" + "2"); // 122
   console.log(1 + +"2" + "2"); // 32
   console.log(1 + -"1" + "2"); // 02
   console.log(+"1" + "1" + "2"); // 112
   console.log( "A" - "B" + "2"); // NaN2
   сonsole.log( "A" - "B" + 2); //Error
   ```
</details>

4. Define the `repeatify` method for the `String` object. 
The method accepts an integer that specifies how many times the string should be repeated. 
The function returns a string repeated the specified number of times.

comment: The question tests the developer's knowledge of inheritance in JavaScript and
the prototype property.

> complexity: ⭐⭐  
tags: ["prototype inheritance"]  

<details>
  <summary>Answer</summary>

  ```js
  function repeatString(val) {
    return this.repeat(val);
  }
  
  String.prototype.repeatify = repeatString;
  ```
</details>

5. The task tests the ability to work with `Date`. Write a function to 
add the specified `months` to the `Date`.

> complexity: ⭐  
tags: ["date"]  

<details>
  <summary>Answer</summary>

  ```js
  function addMonths(date, months) {
    return new Date(date.setMonth(date.getMonth() + months));
  }
  ```
</details>

6. The task tests knowledge of JavaScript logical operators. What will the given console 
output show?

> complexity: ⭐  
tags: ["logical operators"]  

```js
console.log(0 || 1);
console.log(1 || 2);
console.log(0 && 1);
console.log(1 && 2);
```

<details>
  <summary>Answer</summary>
  
   ```js
   console.log(0 || 1); // 1
   console.log(1 || 2); // 1
   console.log(0 && 1); // 0
   console.log(1 && 2); // 2
   ```
</details>

7. Tests knowledge of `Data types`. Write a function to return a `Boolean` 
value that determines whether the passed value is a primitive or not.

> complexity: ⭐  
tags: ["data types"]  

comment: bad realization
todo: fix it, use `isObject` realization

<details>
  <summary>Answer</summary>

  ```js
  function isPrimitive(val){
    const notPrimitiveTypes = ['object', 'function'];
  
    return !notPrimitiveTypes.includes(typeof val) || val === null; 
  }  
  ```
</details>

8. Testing knowledge about the "Event Loop".
In what order will the log results be displayed?

> complexity: ⭐⭐⭐  
tags: ["event loop"]  

```js
console.log(1); 

setTimeout(() => console.log(2)); 

Promise.resolve().then(() => console.log(3)); 
Promise.resolve().then(() => setTimeout(() => console.log(4)));
Promise.resolve().then(() => console.log(5)); 

setTimeout(() => console.log(6));

console.log(7); 
```

<details>
  <summary>Answer</summary>
  
   ```js
   console.log(1); // 1

   setTimeout(() => console.log(2)); // 5

   Promise.resolve().then(() => console.log(3)); // 3
   Promise.resolve().then(() => setTimeout(() => console.log(4))); // 7
   Promise.resolve().then(() => console.log(5)); // 4

   setTimeout(() => console.log(6)); // 6

   console.log(7); // 2
   ```
</details>

9. A task on the ability to use the reduce method for non-typical tasks.
Write the bifurcate function to divide the values of two given arrays into two groups.
If the element in the filter is `true`, the corresponding element in the collection 
belongs to the first group; otherwise, it belongs to the second group.

> complexity: ⭐⭐⭐  
tags: ["arrays", "reduce"]  

Example:
```js
console.log(bifurcate([1, 2, 3, 4], [true, true, false, true])); // output [[1, 2, 4], [3]]
```
<details>
  <summary>Answer</summary>

  ```js
  function bifurcate (arr, filter) {
    return arr.reduce(
      (acc, val, i) => (acc[filter[i] ? 0 : 1].push(val), acc),
      [[], []]
    );
  }
  ```
</details>

10. The task tests knowledge of how numbers are represented inside JavaScript.
What result will this code produce? Why exactly at the exit such a result was obtained?

> complexity: ⭐  
tags: ["numbers"]  

```js
console.log(0.1 + 0.2 === 0.3);
```

<details>
  <summary>Answer</summary>

  false because
  ```js
  0.1 + 0.2 === 0.30000000000000004
  ```
</details>

11. The task tests the ability to work with the properties of `Object`.
Write a function that accepts an `Object` and returns an array of the object's method names.

> complexity: ⭐  
tags: ["objects"]  

todo: replace key word function to arrow function

<details>
  <summary>Answer</summary>

  ```js
  function findAllMethods(obj) { 
    return Object.getOwnPropertyNames(obj).filter(function(property) { 
      return typeof obj[property] === "function"; 
    }); 
  } 
  ```
</details>

12. Tasks on the ability to process lines and on the ability to work with arrays.
Write a csv_to_array function to convert a string of comma-separated values (CSV)
to a two-dimensional array.

> complexity: ⭐  
tags: ["arrays"]  

todo: use only camelCase notation

Example:

```js
console.log(csv_to_array('a,b\nc,d'))); // output result [["a","b"],["c","d"]]
```

<details>
  <summary>Answer</summary>

  ```js
  function csvToArray(data, delimiter = ',') {
    return data.split('\n').map((v) => v.split(delimiter));
  }
  ```
</details>

13. Task tests knowledge of `String` methods. Write a function the reverses a string.

> complexity: ⭐  
tags: ["strings"]  

<details>
  <summary>Answer</summary>

  ```js
  const reverseString = (str) => str.split('').reverse().join('');
  ```
</details>

14. The task tests your knowledge of `closures` in Javascript. Write a function for 
multiplying two numbers that is called in this form `multiply(2)(3)`.

> complexity: ⭐  
tags: ["closure"]  

<details>
  <summary>Answer</summary>

  ```js
  const multiply = (first) => {
    return (second) => {
      return first * second;
    };
  }
  ```
</details>

15. Task tests knowledge about `Promise`. Write a function that will take a value and 
return a `Promise` containing that value.

> complexity: ⭐  
tags: ["promise"]  

<details>
  <summary>Answer</summary>

  ```js
  function wrapValueInPromise(value) {
    return new Promise((resolve, reject) => {
      resolve(value);
    });
  }
  ```
</details>

16. Task tests knowledge about `Set`. Write the `uniq` function that removes repeated 
elements from the array.

> complexity: ⭐  
tags: ["Set"]  

<details>
  <summary>Answer</summary>

  ```js
  const uniq = (arr) => [...new Set(arr)];
  ```
</details>

17. Task tests how person can work with `Array` and how person can use `recursion`.
Write a `deepFlatten` function that will place elements from the inner arrays into the 
top array.

> complexity: ⭐⭐  
tags: ["recursion", "arrays"]  

todo: need to add more clear solution without reduce

Example

```js
  deepFlatten([1, [2], [[3], [4, [5]]]]); // output result [1, 2, 3, 4, 5]
```

<details>
  <summary>Answer</summary>

  ```js
  function deepFlatten(arr) {
    return arr.reduce(
      (acc, el) => Array.isArray(el) ? [...acc, ...deepFlatten(el)] : [...acc, el],
    []);
  }
  ```
</details>

18. Task tests how person can work with 'Array'. Write a `sample(arr, n)` function 
that takes `n` random elements from an array.

> complexity: ⭐⭐  
tags: ["arrays"]  

todo: rethink solution

<details>
  <summary>Answer</summary>

  ```js
  function sample(arr, n) {
    const length = arr.length;
    const indices = [];

    while (indices.length < n) {
      const randomIndex = Math.floor(Math.random() * length);
                          
      if (indices.indexOf(randomIndex) === -1) {
        indices.push(randomIndex);
      }
    }

    return indices.map((i) => arr[i]);
  }
  ```
</details>
 
19. Task tests how person can work with `reduce` method. Write function `safeGet` 
that will get a value from an object by logical path "a.b.c".

> complexity: ⭐⭐  
tags: ["objects"]  

comment: better to use `for...of` loop

Example

```js
  safeGet({ a: { b: 5 } }, "a.b"); // output result 5
``` 

<details>
  <summary>Answer</summary>

  ```js
  function safeGet(obj, path) {
    const keys = path.split(".");
  
    return keys.reduce((acc, key) => {
      return (acc || {})[key] ? acc[key] : null;
    }, obj);
  }
  ```
</details>
  
20. Task tests how person can work with `recursion`. Write a function called `sumRange` 
using `recursion`. It will take a number and return the sum of all numbers from 1 up
to the number passed in.

> complexity: ⭐⭐  
tags: ["recursion"]  

todo: check, maybe this function better to call "factorial"?

<details>
  <summary>Answer</summary>

  ```js
  function sumRange(num){
    if(num === 1) return 1;

	  return num + sumRange(num - 1);
  }
  ```
</details>

21. Task tests how person can work with `String` type. Write a function that takes 
a string of braces, and determines if the order of the braces is valid.
It should return `true` if the string is valid, and `false` if it's invalid.

> complexity: ⭐⭐⭐  
tags: ["strings", "algorithms"]  

<details>
 <summary>Answer</summary>

  ```js
  function validBraces(braces) {
    const regex = /\(\)|\[\]|\{\}/;
	
    return regex.test(braces)
      ? validBraces(braces.replace(regex, ''))
      : '' === braces;
  }
  ```
</details>
	
22. Task tests how person can work with `String` type. An isogram is a word that has no 
repeating letters, consecutive or non-consecutive. Implement a function that determines
whether a string that contains only letters is an isogram. Assume the empty string 
is an isogram. Ignore letter case.

> complexity: ⭐  
tags: ["strings"]  

<details>
 <summary>Answer</summary>

  ```js
  function isIsogram(str) {
    return (
      new Set(str.toLowerCase()).size === str.length
    );
  }
  ```
</details>
	
23. Task tests how person can work with `Array`. Implement the function `uniqueInOrder`
which takes as argument a sequence and returns a list of items without any elements 
with the same value next to each other and preserving the original order of elements. 

> complexity: ⭐⭐  
tags: ["arrays"]  

Examples

```js
uniqueInOrder('AAAABBBCCDAABBB'); // output result ['A', 'B', 'C', 'D', 'A', 'B']
uniqueInOrder('ABBCcAD'); // output result ['A', 'B', 'C', 'c', 'A', 'D']
uniqueInOrder([1,2,2,3,3]); // output result [1,2,3]
```

<details>
 <summary>Answer</summary>

  ```js
  function uniqueInOrder(iterable) {
    return [...iterable].filter((a, i) => a !== iterable[i - 1]);
  };
  ```
</details>
	
24. Task tests how person can work with `Array`. Create a function that returns the 
sum of the two lowest positive numbers given an array of minimum `4` positive integers.
No floats or non-positive integers will be passed.

> complexity: ⭐  
tags: ["arrays"]  

<details>
  <summary>Answer</summary>

  ```js
  function sumTwoSmallestNumbers(numbers) {  
    const [ a, b ] = numbers.sort((a, b) => a - b);

    return a + b;
  }
  ```
</details>

25. Task tests knowledge about working with `primitive data types`. Implement a function 
that adds two numbers together and returns their sum in binary. The conversion can 
be done before, or after the addition. The binary number returned should be a string.

> complexity: ⭐  
tags: ["types conversion", "strings", "numbers"]  

```js
addBinary(5, 9); // return "1110" (5 + 9 = 14 in decimal or 1110 in binary)
```
  
<details>
  <summary>Answer</summary>

  ```js
  function addBinary(a,b){
    return (a+b).toString(2);
  }
  ```
</details>

	
26. Task tests knowledge about `context of function`. Can we change this with 
additional binding? What will this code output?

> complexity: ⭐  
tags: ["context"]  

todo: remove alerts

```js
function f() {
  alert(this.name);
}

f = f.bind( {name: "Alex"} ).bind( {name: "Bob" } );

f();
```
<details>
  <summary>Answer</summary>

```js
function f() {
  alert(this.name);
}

f = f.bind( {name: "Alex"} ).bind( {name: "Bob" } );

f(); // result "Alex"
```
</details>

27. Task tests knowledge about `context of function`. Can we change this with 
additional binding? What will this code output?

> complexity: ⭐  
tags: ["context"]  

```js
function sayHi() {
  alert( this.name );
}
sayHi.test = 5;

let bound = sayHi.bind({
  name: "Alex"
});

alert( bound.test );
```
<details>
  <summary>Answer</summary>

```js
function sayHi() {
  alert( this.name );
}
sayHi.test = 5;

let bound = sayHi.bind({
  name: "Alex"
});

alert( bound.test ); // result undefiend
```
</details>

28. Task tests knowledge about `decorators`. The result of the `debounce(f, ms)` 
decorator must be a wrapper that passes the call to f at most once every `ms` milliseconds.
In other words, when we call debounce, it ensures that all other calls are ignored for 
`ms`. Write `debounce`.

comment: better to use it for online.editor

<details>
  <summary>Answer</summary>

  ```js	
  function debounce(f, ms) {

    let isCooldown = false;

    return function() {
      if (isCooldown) return;

      f.apply(this, arguments);

      isCooldown = true;

      setTimeout(() => isCooldown = false, ms);
   };
  }
  ```
</details>

29. Task tests knowledge about `Class inheritance`. In the code below, the `Rabbit` 
class inherits from `Animal`. Unfortunately, an object of the `Rabbit` class is not created.
What's wrong? Correct the mistake.

comment: please use english for all code examples!
wrong error message!

```js
class Animal {
  constructor(name) {
    this.name = name;
  }
}

class Rabbit extends Animal {
  constructor(name) {
    this.name = name;
    this.created = Date.now();
  }
}

let rabbit = new Rabbit("White rabbit");
alert(rabbit.name);
```

<details>
  <summary>Answer</summary>

```js
class Animal {
  constructor(name) {
    this.name = name;
  }
}

class Rabbit extends Animal {
  constructor(name) {
    super(name);
    this.created = Date.now();
  }
}

let rabbit = new Rabbit("White rabbit");
alert(rabbit.name);
```
</details>

30. What are the different data types present in javascript?

31. Implement counter via closure

> complexity: ⭐  
tags: ["closure"]  

```js
const makeCounter = () => {
  let count = 0;
  
  return () => {
    count += 1;
    
    return count;
  }
};

const counter = makeCounter();

counter();
```

32. Explain passed by value and passed by reference.

> complexity: ⭐  
tags: ["object", "primitive values"]  

33. Give an example of context loss

> complexity: ⭐  
tags: ["context"]  

<details>
  <summary>Answer</summary>

  ```js
  const obj = {
    color: 'green',
    getColor() {
      return this.color;
    }
  };

  const getColor = obj.getColor;

  getColor(); // ?
  ```
</details>


34. In which situation we should use `Map` collection instead
  object?

> complexity: ⭐⭐  
tags: ["Map"]  


<details>
  <summary>Answer</summary>

  When to use Map?

  Maps are similar to Objects in that they hold key/value pairs,
  but Maps have several advantages over objects:

  - **Size** Maps have a size property, whereas Objects do not have a built-in way
    to retrieve their size.
  - **Iteration** - Maps are directly iterable, whereas Objects are not.
  - **Flexibility** - Maps can have any data type (primitive or Object) as the key
    to a value, while Objects can only have strings.
  -  **Ordered** - Maps retain their insertion order, whereas objects do not have
     a guaranteed order.

</details>

35. In which situations do you use `Set` collection?

> complexity: ⭐⭐  
tags: ["Set"]  

36. Please tell details about `WeakSet` and `WeakMap` practical use cases

> complexity: ⭐⭐  
tags: ["WeakSet", "WeakMap"]  

37. Describe advantages of `hasOwn` method usage in comparison with
  `hasOwnPropery`

> complexity: ⭐⭐  
tags: ["hasOwn", "hasOwnProperty", "prototype inheritance"]  


38. How in JavaScript create object without prototype?
  Why we need such kind of object?

```js
const dictionary = Object.create(null);

dictionary.__proto__ = "some value";

console.log(dictionary.__proto__); // "some value"
console.log(dictionary.hasOwnProperty("toString")); // TypeError: dictionary.hasOwnProperty is not a function

Object.hasOwn(dictionary); // false
```

> complexity: ⭐⭐  
tags: ["prototype inheritance"]  


39. Implement `isObject` function. It should return `true` only for objects and
  `false` for all primitives and other values inherited from object, such us array,
  function, etc.

40. How to correct compare strings in JavaScript?
  How to correct compare diacritical marks?

> complexity: ⭐  
tags: ["strings"]  


41. Can we use `Array.from` to copy array? What is the difference in comparison
  with "spread syntax"

42. Please tell in which order and why logs will appear?

> complexity: ⭐⭐  
tags: ["promise", "event loop"]  

```js
  setTimeout(function a () {
  console.error(4);
}, 0);

new Promise(function b (resolve) {
  console.error(1);

  setTimeout(function c () {
    console.error(2);
    resolve();
  }, 0);
})
  .then(function d () {
    console.error(3);
  });

console.error(0);

// 1. Добавили ф-ю "a" как Macro-задачу в очередь: `console.error(4)`  
// 2. Выполняем синхронный код ф-ии "b" внутри `new Promise`: `console.error(1)`  
// 3. Добавили ф-ю "c" как Macro-задачу в очередь: `console.error(2); resolve();`  
// 4. Добавили ф-ю "d" как Micro-задачу из then в очередь: `console.log(3)` (выполнится после `console.error(2); resolve();`)  
// 5. Выполняем синхронный код: `console.error(0)`  

// Порядок: 1 --> 0 --> 4 --> 2 --> 3
```

If we change order?

```js
  new Promise((resolve) => {  
    console.error(1);  
  
    setTimeout(() => {  
      console.error(2);  
      resolve();  
    }, 0);  
  })  
  .then(() => {  
    console.error(3);  
  });  
  
  setTimeout(() => {  
    console.error(4);  
  }, 0);  
  
  console.error(0);  
  
// 1. Выполняем синхронный код внутри `new Promise`: `console.error(1)`  
// 2. Добавили Macro-задачу в очередь: `console.error(2); resolve();`  
// 3. Добавили Micro-задачу из then в очередь: `console.log(3)` (выполнится после `console.error(2); resolve();`)  
// 4. Добавили Macro-задачу в очередь: `console.error(4)`  
// 5. Выполняем синхронный код: `console.error(0)`  
  
// Порядок: 1 --> 0 --> 2 --> 3 --> 4
```

43. In which order we will see console output?

> complexity: ⭐⭐⭐  
tags: ["event listeners", "event loop"]

```js
document.addEventListener('click', () => {
  console.log('a1')
  Promise.resolve('a2').then(console.log)
});

document.addEventListener('click', () => {
  console.log('b1')
  Promise.resolve('b2').then(console.log)
});

document.body.click(); // a1 b1 a2 b2
```

What happened if we trigger click event in the next way?

```js
const event = new MouseEvent("click");
btn.dispatchEvent(event);
```

44. How to handle asynchronous errors in JavaScript?
  Will this error be caught?

> complexity: ⭐⭐  
tags: ["error handling", "async code"]  

```js
try {
  setTimeout(() => {
    throw new Error('some error');
  }, 0);
} catch (error) {
  console.error('Something went wrong: ', error.message);
}
```

45. Can we catch error in this way?

> complexity: ⭐⭐  
tags: ["error handling", "async code"]  

```js
try {  
  fetch('https://jsonplaceholder.typicode.com/todos/1')  
    .then(response => response.json())  
    .then(json => {  
      console.log(json);  
    })  
} catch (error) {  
  console.error(`Fetch error: `, error);  
}
```

46. How to iterate over object properties? Describe downsides of `for...in`
  loop.

> complexity: ⭐⭐  
tags: ["objects"]  

47. What is the difference between `Object.assign` and "spread syntax"
  according to object coping process.

```js
function makeObj1(other) {
  return Object.assign({
    set foo(x) {
      console.log(`set called with: [${x}]`);
      this._foo = x;
    },
    get foo() {
      console.log("get called");
      return this._foo;
    }
  }, 
   other); // merge via Object.assign
}

function makeObj2(other) {
  return {
    set foo(x) {
      console.log("set called with:", x)
      this._foo = x;
    },
    get foo() {
      console.log("get called")
      return this._foo;
    },
    ...other //merge via spread
  }
}

console.log("--- obj1 ---")
//getter and setter preserved
const obj1 = makeObj1({foo: "bar"});
console.log(`obj1.foo: [${obj1.foo}]`);


console.log("--- obj2 ---")
//getter and setter are wiped out
const obj2 = makeObj2({foo: "baz"});
console.log(`obj2.foo: [${obj2.foo}]`);
```

48. It's possible to call static method via `this.constructor.<method name>`?
  What will be logged in this case to console?

> complexity: ⭐⭐  
tags: ["classes", "static methods", "prototype inheritance"]  

```js
class NotificationMessage {
  static getName() {
    return "My name is NotificationMessage";
  }

  lognameA() {
    console.log(NotificationMessage.getName());
  }

  lognameB() {
    console.log(this.constructor.getName());
  }
}

class ErrorNotification extends NotificationMessage {
  static getName() {
    return "My name is ErrorNotification";
  }
}

const errorNotification = new ErrorNotification();

errorNotification.lognameA(); // My name is NotificationMessage
errorNotification.lognameB(); // My name is ErrorNotification
```

49. Does this code example log "hi" to console?

> complexity: ⭐  
tags: ["arrays""]  

```js
if ([0]) {
  console.log('hi')
}
```

50. Please comment result of next comparisons:

```js
const arr = [
  { name: "John" },
  { name: "Peter" }
];

const copy = [...arr];

console.log(arr === copy); // ?
console.log(arr[0] === copy[0]); // ?
```

51. What is the difference between `==` and `===` operators?

```js
console.log(1 == true);
console.log(1 === true);

console.log(0 == false);
console.log(0 === false);
```

52. Please implement `isNaN` function which returns "true" only for `NaN`
  value

> complexity: ⭐
tags: ["primitives", "NaN"]  

```js
const isNaN = value => {
  return !(value === value);
}
```

53. How does "this" keyword work?

54. What is the difference between function declared via key word `function`
  and arrow function?

55. How to get all function arguments?
56. What is the length of current array?

```js
const arr1 = new Array(1, 2);
const arr2 = new Array(10);

console.log(arr1.length); // 2
console.log(arr2.length); // 10
```

57. How to copy object in JavaScript?

58. Why counter doesn't change? 

```js
function preloadImages(sources, callback) {
  let counter = 0;

  for (const source of sources) {
    const img = document.createElement('img');
    
    img.src = source;
    img.onload = img.onerror = () => {
      counter++;
    }
  }

  if (counter === sources.length) {
    callback();
  }
}

preloadImages(["link1", "link2", "link3"], () => {
  console.log("finished");
});
```

But why counter works in this example?

```js
function preloadImages(sources, callback) {
  let counter = 0;

  function onLoad() {
    counter++;
    
    if (counter === sources.length) {
      callback();
    }
  }

  for(const source of sources) {
    const img = document.createElement('img');
    
    img.src = source;
    img.onload = img.onerror = onLoad;
  }
}
```


