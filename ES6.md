# Introduction to the ES6 Challenges
ECMAScript is a standardized version of JavaScript with the goal of unifying the language's specifications and features. As all major browsers and JavaScript-runtimes follow this specification, the term ECMAScript is interchangeable with the term JavaScript.

Most of the challenges on freeCodeCamp use the ECMAScript 5 (ES5) specification of the language, finalized in 2009. But JavaScript is an evolving programming language. As features are added and revisions are made, new versions of the language are released for use by developers.

The most recent standardized version is called ECMAScript 6 (ES6), released in 2015. This new version of the language adds some powerful features that will be covered in this section of challenges, including:


* Arrow functions
* Classes
* Modules
* Promises
* Generators
* `let` and `const`


Note
Not all browsers support ES6 features. If you use ES6 in your own projects, you may need to use a program (transpiler) to convert your ES6 code into ES5 until browsers support ES6.

***

### ES6: Explore Differences Between the var and let Keywords
One of the biggest problems with declaring variables with the var keyword is that you can overwrite variable declarations without an error.

    var camper = 'James';
    var camper = 'David';
    console.log(camper);
    // logs 'David'
As you can see in the code above, the camper variable is originally declared as James and then overridden to be David.

In a small application, you might not run into this type of problem, but when your code becomes larger, you might accidentally overwrite a variable that you did not intend to overwrite.

Because this behavior does not throw an error, searching and fixing bugs becomes more difficult.

A new keyword called let was introduced in ES6 to solve this potential issue with the var keyword.

If you were to replace var with let in the variable declarations of the code above, the result would be an error.

    let camper = 'James';
    let camper = 'David'; // throws an error
This error can be seen in the console of your browser.

So unlike var, when using let, a variable with the same name can only be declared once.

Note the "use strict". This enables Strict Mode, which catches common coding mistakes and "unsafe" actions. For instance:

    "use strict";
    x = 3.14; // throws an error because x is not declared

Update the code so it only uses the let keyword.

    let catName;
    let quote;
    function catTalk() {
      "use strict";

      catName = "Oliver";
      quote = catName + " says Meow!";

    }
    catTalk();

***

### ES6: Compare Scopes of the var and let Keywords
When you declare a variable with the var keyword, it is declared globally, or locally if declared inside a function.

The let keyword behaves similarly, but with some extra features. When you declare a variable with the let keyword inside a block, statement, or expression, its scope is limited to that block, statement, or expression.

For example:

    var numArray = [];
    for (var i = 0; i < 3; i++) {
      numArray.push(i);
    }
    console.log(numArray);
    // returns [0, 1, 2]
    console.log(i);
    // returns 3
With the var keyword, i is declared globally. So when i++ is executed, it updates the global variable. This code is similar to the following:

    var numArray = [];
    var i;
    for (i = 0; i < 3; i++) {
      numArray.push(i);
    }
    console.log(numArray);
    // returns [0, 1, 2]
    console.log(i);
    // returns 3
This behavior will cause problems if you were to create a function and store it for later use inside a for loop that uses the i variable. This is because the stored function will always refer to the value of the updated global i variable.

    var printNumTwo;
    for (var i = 0; i < 3; i++) {
      if(i === 2){
        printNumTwo = function() {
          return i;
        };
      }
    }
    console.log(printNumTwo());
    // returns 3
As you can see, printNumTwo() prints 3 and not 2. This is because the value assigned to i was updated and the printNumTwo() returns the global i and not the value i had when the function was created in the for loop. The let keyword does not follow this behavior:

    'use strict';
    let printNumTwo;
    for (let i = 0; i < 3; i++) {
      if (i === 2) {
        printNumTwo = function() {
          return i;
        };
      }
    }
    console.log(printNumTwo());
    // returns 2
    console.log(i);
    // returns "i is not defined"
`i` is not defined because it was not declared in the global scope. It is only declared within the for loop statement. printNumTwo() returned the correct value because three different i variables with unique values (0, 1, and 2) were created by the let keyword within the loop statement.


Fix the code so that i declared in the if statement is a separate variable than i declared in the first line of the function. Be certain not to use the var keyword anywhere in your code.

This exercise is designed to illustrate the difference between how var and let keywords assign scope to the declared variable. When programming a function similar to the one used in this exercise, it is often better to use different variable names to avoid confusion.

    function checkScope() {
    "use strict";
      let i = "function scope";
      if (true) {
        let i = "block scope";
        console.log("Block scope i is: ", i);
      }
      console.log("Function scope i is: ", i);
      return i;
    }

***

### ES6: Declare a Read-Only Variable with the const Keyword
`let` is not the only new way to declare variables. In ES6, you can also declare variables using the `const` keyword.

`const` has all the awesome features that `let` has, with the added bonus that variables declared using `const` are read-only. They are a constant value, which means that once a variable is assigned with `const`, it cannot be reassigned.

    "use strict"
    const FAV_PET = "Cats";
    FAV_PET = "Dogs"; // returns error
As you can see, trying to reassign a variable declared with `const` will throw an error. You should always name variables you don't want to reassign using the `const` keyword. This helps when you accidentally attempt to reassign a variable that is meant to stay constant. A common practice when naming constants is to use all uppercase letters, with words separated by an underscore.


Change the code so that all variables are declared using `let` or `const`. Use `let` when you want the variable to change, and `const` when you want the variable to remain constant. Also, rename variables declared with `const` to conform to common practices, meaning constants should be in all caps.

    function printManyTimes(str) {
      "use strict";

      // change code below this line

      const SENTENCE = str + " is cool!";
      for(let i = 0; i < str.length; i+=2) {
        console.log(SENTENCE);
      }

      // change code above this line

    }
    printManyTimes("freeCodeCamp");


***

### ES6: Mutate an Array Declared with const
The `const` declaration has many use cases in modern JavaScript.

Some developers prefer to assign all their variables using `const` by default, unless they know they will need to reassign the value. Only in that case, they use `let`.

However, it is important to understand that objects (including arrays and functions) assigned to a variable using `const` are still mutable. Using the const declaration only prevents reassignment of the variable identifier.

    "use strict";
    const s = [5, 6, 7];
    s = [1, 2, 3]; // throws error, trying to assign a const
    s[2] = 45; // works just as it would with an array declared with var or let
    console.log(s); // returns [5, 6, 45]
As you can see, you can mutate the object `[5, 6, 7]` itself and the variable `s` will still point to the altered array `[5, 6, 45]`. Like all arrays, the array elements in `s` are mutable, but because `const` was used, you cannot use the variable identifier `s` to point to a different array using the assignment operator.


An array is declared as `const s = [5, 7, 2]`. Change the array to `[2, 5, 7]` using various element assignment.

    const s = [5, 7, 2];
    function editInPlace() {
      "use strict";
      // change code below this line
      s[0] = 2;
      s[1] = 5;
      s[2] = 7;
      // s = [2, 5, 7]; <- this is invalid

      // change code above this line
    }
    editInPlace();


***

### ES6: Prevent Object Mutation
As seen in the previous challenge, `const` declaration alone doesn't really protect your data from mutation. To ensure your data doesn't change, JavaScript provides a function `Object.freeze` to prevent data mutation.

Once the object is frozen, you can no longer add, update, or delete properties from it. Any attempt at changing the object will be rejected without an error.

    let obj = {
      name:"FreeCodeCamp",
      review:"Awesome"
    };
    Object.freeze(obj);
    obj.review = "bad"; //will be ignored. Mutation not allowed
    obj.newProp = "Test"; // will be ignored. Mutation not allowed
    console.log(obj); 
    // { name: "FreeCodeCamp", review:"Awesome"}

In this challenge you are going to use `Object.freeze` to prevent mathematical constants from changing. You need to freeze the `MATH_CONSTANTS` object so that no one is able alter the value of `PI`, add, or delete properties.

    function freezeObj() {
      "use strict";
      const MATH_CONSTANTS = {
        PI: 3.14
      };
      // change code below this line
      Object.freeze(MATH_CONSTANTS);

      // change code above this line
      try {
        MATH_CONSTANTS.PI = 99;
      } catch( ex ) {
        console.log(ex);
      }
      return MATH_CONSTANTS.PI;
    }
    const PI = freezeObj();


***

### ES6: Use Arrow Functions to Write Concise Anonymous Functions
In JavaScript, we often don't need to name our functions, especially when passing a function as an argument to another function. Instead, we create inline functions. We don't need to name these functions because we do not reuse them anywhere else.

To achieve this, we often use the following syntax:

    const myFunc = function() {
      const myVar = "value";
      return myVar;
    }
ES6 provides us with the syntactic sugar to not have to write anonymous functions this way. Instead, you can use arrow function syntax:

    const myFunc = () => {
      const myVar = "value";
      return myVar;
    }
When there is no function body, and only a return value, arrow function syntax allows you to omit the keyword return as well as the brackets surrounding the code. This helps simplify smaller functions into one-line statements:

    const myFunc = () => "value"
This code will still return value by default.


Rewrite the function assigned to the variable magic which returns a new Date() to use arrow function syntax. Also make sure nothing is defined using the keyword var.

    //var magic = function() {
    //  "use strict";
    //  return new Date();
    //};

    const magic = () => new Date();


***


### ES6: Write Arrow Functions with Parameters
Just like a normal function, you can pass arguments into arrow functions.

    // doubles input value and returns it
    const doubler = (item) => item * 2;
You can pass more than one argument into arrow functions as well.


Rewrite the myConcat function which appends contents of `arr2` to `arr1` so that the function uses arrow function syntax.

    //var myConcat = function(arr1, arr2) {
    //  "use strict";
    //  return arr1.concat(arr2);
    //};

    const myConcat = (arr1, arr2) => arr1.concat(arr2);
    // test your code
    console.log(myConcat([1, 2], [3, 4, 5]));


***

### ES6: Write Higher Order Arrow Functions
It's time we see how powerful arrow functions are when processing data.

Arrow functions work really well with higher order functions, such as `map()`, `filter()`, and `reduce()`, that take other functions as arguments for processing collections of data.

Read the following code:

    FBPosts.filter(function(post) {
      return post.thumbnail !== null && post.shares > 100 && post.likes > 500;
    })
We have written this with `filter()` to at least make it somewhat readable. Now compare it to the following code which uses arrow function syntax instead:

    FBPosts.filter((post) => post.thumbnail !== null && post.shares > 100 && post.likes > 500)
This code is more succinct and accomplishes the same task with fewer lines of code.


Use arrow function syntax to compute the square of only the positive integers (decimal numbers are not integers) in the array `realNumberArray` and store the new array in the variable `squaredIntegers`.

    const realNumberArray = [4, 5.6, -9.8, 3.14, 42, 6, 8.34, -2];
    const squareList = (arr) => {
      "use strict";
      // change code below this line
      const squaredIntegers = arr.filter( (num) => num > 0 && num % parseInt(num) === 0 ).map( (num) => Math.pow(num, 2) );
          // change code above this line
      return squaredIntegers;
    };
    // test your code
    const squaredIntegers = squareList(realNumberArray);
    console.log(squaredIntegers);


***

### ES6: Set Default Parameters for Your Functions
In order to help us create more flexible functions, ES6 introduces default parameters for functions.

Check out this code:

    function greeting(name = "Anonymous") {
      return "Hello " + name;
    }
    console.log(greeting("John")); // Hello John
    console.log(greeting()); // Hello Anonymous
The default parameter kicks in when the argument is not specified (it is undefined). As you can see in the example above, the parameter `name` will receive its default value `"Anonymous"` when you do not provide a value for the parameter. You can add default values for as many parameters as you want.


Modify the function increment by adding default parameters so that it will add 1 to number if value is not specified.

    const increment = (function() {
      "use strict";
      return function increment(number, value = 1) {
        return number + value;
      };
    })();
    console.log(increment(5, 2)); // returns 7
    console.log(increment(5)); // returns 6


***

### ES6: Use the Rest Operator with Function Parameters
In order to help us create more flexible functions, ES6 introduces the rest operator for function parameters. With the rest operator, you can create functions that take a variable number of arguments. These arguments are stored in an array that can be accessed later from inside the function.

Check out this code:

    function howMany(...args) {
      return "You have passed " + args.length + " arguments.";
    }
    console.log(howMany(0, 1, 2)); // You have passed 3 arguments
    console.log(howMany("string", null, [1, 2, 3], { })); // You have passed 4 arguments.
The rest operator eliminates the need to check the args array and allows us to apply `map()`, `filter()` and `reduce()` on the parameters array.


Modify the function sum so that it uses the rest operator and it works in the same way with any number of parameters.

    const sum = (function() {
      "use strict";
      return function sum(...args) {
        //const args = [ x, y, z ];
        return args.reduce((a, b) => a + b, 0);
      };
    })();
    console.log(sum(1, 2, 3)); // 6


***

### Use the Spread Operator to Evaluate Arrays In-Place
ES6 introduces the spread operator, which allows us to expand arrays and other expressions in places where multiple parameters or elements are expected.

The ES5 code below uses `apply()` to compute the maximum value in an array:

    var arr = [6, 89, 3, 45];
    var maximus = Math.max.apply(null, arr); // returns 89
We had to use `Math.max.apply(null, arr)` because `Math.max(arr)` returns `NaN`. `Math.max()` expects comma-separated arguments, but not an array.

The spread operator makes this syntax much better to read and maintain.

    const arr = [6, 89, 3, 45];
    const maximus = Math.max(...arr); // returns 89
`...arr` returns an unpacked array. In other words, it spreads the array.

However, the spread operator only works in-place, like in an argument to a function or in an array literal. The following code will not work:

    const spreaded = ...arr; // will throw a syntax error

Copy all contents of `arr1` into another array `arr2` using the spread operator.

    const arr1 = ['JAN', 'FEB', 'MAR', 'APR', 'MAY'];
    let arr2;
    (function() {
      "use strict";
      arr2 = [...arr1]; // change this line
    })();
    console.log(arr2);


***

### Use Destructuring Assignment to Assign Variables from Objects
We saw earlier how spread operator can effectively spread, or unpack, the contents of the array.

We can do something similar with objects as well. Destructuring assignment is special syntax for neatly assigning values taken directly from an object to variables.

Consider the following ES5 code:

    var voxel = {x: 3.6, y: 7.4, z: 6.54 };
    var x = voxel.x; // x = 3.6
    var y = voxel.y; // y = 7.4
    var z = voxel.z; // z = 6.54
Here's the same assignment statement with ES6 destructuring syntax:

    const { x, y, z } = voxel; // x = 3.6, y = 7.4, z = 6.54
If instead you want to store the values of voxel.x into a, voxel.y into b, and voxel.z into c, you have that freedom as well.

    const { x : a, y : b, z : c } = voxel // a = 3.6, b = 7.4, c = 6.54
You may read it as "get the field x and copy the value into a," and so on.


Use destructuring to obtain the average temperature for tomorrow from the input object `AVG_TEMPERATURES`, and assign value with key tomorrow to `tempOfTomorrow` in line.

    const AVG_TEMPERATURES = {
      today: 77.5,
      tomorrow: 79
    };

    function getTempOfTmrw(avgTemperatures) {
      "use strict";
      // change code below this line
      const {tomorrow : tempOfTomorrow } = avgTemperatures;
      // change code above this line
      return tempOfTomorrow;
    }

    console.log(getTempOfTmrw(AVG_TEMPERATURES)); // should be 79


***

### Use Destructuring Assignment to Assign Variables from Nested Objects
We can similarly destructure nested objects into variables.

Consider the following code:

    const a = {
      start: { x: 5, y: 6},
      end: { x: 6, y: -9 }
    };
    const { start : { x: startX, y: startY }} = a;
    console.log(startX, startY); // 5, 6
In the example above, the variable start is assigned the value of `a.start`, which is also an object.


Use destructuring assignment to obtain max of `forecast.tomorrow` and assign it to `maxOfTomorrow`.

    const LOCAL_FORECAST = {
      today: { min: 72, max: 83 },
      tomorrow: { min: 73.3, max: 84.6 }
    };

    function getMaxOfTmrw(forecast) {
      "use strict";
      // change code below this line
      const {tomorrow : {max : maxOfTomorrow}} = forecast; // change this line
      // change code above this line
      return maxOfTomorrow;
    }

    console.log(getMaxOfTmrw(LOCAL_FORECAST)); // should be 84.6


***

### Use Destructuring Assignment to Assign Variables from Arrays
ES6 makes destructuring arrays as easy as destructuring objects.

One key difference between the spread operator and array destructuring is that the spread operator unpacks all contents of an array into a comma-separated list. Consequently, you cannot pick or choose which elements you want to assign to variables.

Destructuring an array lets us do exactly that:

    const [a, b] = [1, 2, 3, 4, 5, 6];
    console.log(a, b); // 1, 2
The variable a is assigned the first value of the array, and b is assigned the second value of the array.

We can also access the value at any index in an array with destructuring by using commas to reach the desired index:

    const [a, b,,, c] = [1, 2, 3, 4, 5, 6];
    console.log(a, b, c); // 1, 2, 5

Use destructuring assignment to swap the values of a and b so that a receives the value stored in `b`, and `b` receives the value stored in `a`.

    let a = 8, b = 6;
    (() => {
      "use strict";
      // change code below this line
      [a, b] = [b, a]
      // change code above this line
    })();
    console.log(a); // should be 6
    console.log(b); // should be 8


***

### Use Destructuring Assignment with the Rest Operator to Reassign Array Elements
In some situations involving array destructuring, we might want to collect the rest of the elements into a separate array.

The result is similar to `Array.prototype.slice()`, as shown below:

    const [a, b, ...arr] = [1, 2, 3, 4, 5, 7];
    console.log(a, b); // 1, 2
    console.log(arr); // [3, 4, 5, 7]
Variables a and b take the first and second values from the array. After that, because of rest operator's presence, `arr` gets rest of the values in the form of an array.

The rest element only works correctly as the last variable in the list. As in, you cannot use the rest operator to catch a subarray that leaves out last element of the original array.


Use destructuring assignment with the rest operator to perform an effective `Array.prototype.slice()` so that `arr` is a sub-array of the original array source with the first two elements omitted.

    const source = [1,2,3,4,5,6,7,8,9,10];
    function removeFirstTwo(list) {
      "use strict";
      // change code below this line
      const [,,...arr] = list; // change this
      // change code above this line
      return arr;
    }
    const arr = removeFirstTwo(source);
    console.log(arr); // should be [3,4,5,6,7,8,9,10]
    console.log(source); // should be [1,2,3,4,5,6,7,8,9,10];


***

