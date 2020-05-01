# Introduction to the Basic Data Structure Challenges
Data can be stored and accessed in many different ways, both in Javascript and other languages. This section will teach you how to manipulate arrays, as well as access and copy the information within them. It will also teach you how to manipulate and access the data within Javascript objects, using both dot and bracket notation. When you're done with this section, you should understand the basic properties and differences between arrays and objects, as well as how to choose which to use for a given purpose.


***

### Basic Data Structures: Use an Array to Store a Collection of Data
The below is an example of the simplest implementation of an array data structure. This is known as a one-dimensional array, meaning it only has one level, or that it does not have any other arrays nested within it. Notice it contains booleans, strings, and numbers, among other valid JavaScript data types:

    let simpleArray = ['one', 2, 'three’, true, false, undefined, null];
    console.log(simpleArray.length);
    // logs 7
All array's have a length property, which as shown above, can be very easily accessed with the syntax Array.length.

A more complex implementation of an array can be seen below. This is known as a multi-dimensional array, or an array that contains other arrays. Notice that this array also contains JavaScript objects, which we will examine very closely in our next section, but for now, all you need to know is that arrays are also capable of storing complex objects.

    let complexArray = [
      [
        {
          one: 1,
          two: 2
        },
        {
          three: 3,
          four: 4
        }
      ],
      [
        {
          a: "a",
          b: "b"
        },
        {
          c: "c",
          d: “d”
        }
      ]
    ];

We have defined a variable called yourArray. Complete the statement by assigning an array of at least 5 elements in length to the yourArray variable. Your array should contain at least one string, one number, and one boolean.

        let yourArray = [ "Hello", 12, true, 22, { "a": 1, "b":2}, [1,2,3]]; // change this line


***

### Basic Data Structures: Access an Array's Contents Using Bracket Notation
The fundamental feature of any data structure is, of course, the ability to not only store data, but to be able to retrieve that data on command. So, now that we've learned how to create an array, let's begin to think about how we can access that array's information.

When we define a simple array as seen below, there are 3 items in it:

    let ourArray = ["a", "b", "c"];
In an array, each array item has an index. This index doubles as the position of that item in the array, and how you reference it. However, it is important to note, that JavaScript arrays are zero-indexed, meaning that the first element of an array is actually at the zeroth position, not the first.

In order to retrieve an element from an array we can enclose an index in brackets and append it to the end of an array, or more commonly, to a variable which references an array object. This is known as bracket notation.

For example, if we want to retrieve the `"a"` from `ourArray` and assign it to a variable, we can do so with the following code:

    let ourVariable = ourArray[0];
    // ourVariable equals "a"
In addition to accessing the value associated with an index, you can also set an index to a value using the same notation:

    ourArray[1] = "not b anymore";
    // ourArray now equals ["a", "not b anymore", "c"];
Using bracket notation, we have now reset the item at index 1 from `"b"`, to `"not b anymore"`.


In order to complete this challenge, set the 2nd position (index 1) of `myArray` to anything you want, besides `"b"`.

        let myArray = ["a", "b", "c", "d"];
        // change code below this line
        myArray[1] = "X"
        //change code above this line
        console.log(myArray);


***

### Basic Data Structures: Add Items to an Array with push() and unshift()
An array's length, like the data types it can contain, is not fixed. Arrays can be defined with a length of any number of elements, and elements can be added or removed over time; in other words, arrays are mutable. In this challenge, we will look at two methods with which we can programmatically modify an array: `Array.push()` and `Array.unshift()`.

Both methods take one or more elements as parameters and add those elements to the array the method is being called on; the `push()` method adds elements to the end of an array, and `unshift()` adds elements to the beginning. Consider the following:

    let twentyThree = 'XXIII';
    let romanNumerals = ['XXI', 'XXII'];

    romanNumerals.unshift('XIX', 'XX');
    // now equals ['XIX', 'XX', 'XXI', 'XXII']

    romanNumerals.push(twentyThree);
    // now equals ['XIX', 'XX', 'XXI', 'XXII', 'XXIII']
Notice that we can also pass variables, which allows us even greater flexibility in dynamically modifying our array's data.


We have defined a function, mixedNumbers, which we are passing an array as an argument. Modify the function by using `push()` and `unshift()` to add `'I', 2, 'three'` to the beginning of the array and `7, 'VIII', 9` to the end so that the returned array contains representations of the numbers 1-9 in order.

        function mixedNumbers(arr) {
        // change code below this line
            arr.push(7, 'VIII', 9);
            arr.unshift('I', 2, 'three');
        // change code above this line
        return arr;
        }

        // do not change code below this line
        console.log(mixedNumbers(['IV', 5, 'six']));


***

### Basic Data Structures: Remove Items from an Array with pop() and shift()
Both `push()` and `unshift()` have corresponding methods that are nearly functional opposites: `pop()` and `shift()`. As you may have guessed by now, instead of adding, `pop()` removes an element from the end of an array, while `shift()` removes an element from the beginning. The key difference between `pop()` and `shift()` and their cousins `push()` and `unshift()`, is that neither method takes parameters, and each only allows an array to be modified by a single element at a time.

Let's take a look:

    let greetings = ['whats up?', 'hello', 'see ya!'];

    greetings.pop();
    // now equals ['whats up?', 'hello']

    greetings.shift();
    // now equals ['hello']
We can also return the value of the removed element with either method like this:

    let popped = greetings.pop();
    // returns 'hello'
    // greetings now equals []

We have defined a function, popShift, which takes an array as an argument and returns a new array. Modify the function, using `pop()` and `shift()`, to remove the first and last elements of the argument array, and assign the removed elements to their corresponding variables, so that the returned array contains their values.

    function popShift(arr) {
      let popped = arr.pop(); // change this line
      let shifted = arr.shift(); // change this line
      return [shifted, popped];
    }

    // do not change code below this line
    console.log(popShift(['challenge', 'is', 'not', 'complete']));


***


### Basic Data Structures: Remove Items Using splice()
Ok, so we've learned how to remove elements from the beginning and end of arrays using `shift()` and `pop()`, but what if we want to remove an element from somewhere in the middle? Or remove more than one element at once? Well, that's where `splice()` comes in. `splice()` allows us to do just that: remove any number of consecutive elements from anywhere in an array.

`splice()` can take up to 3 parameters, but for now, we'll focus on just the first 2. The first two parameters of `splice()` are integers which represent indexes, or positions, of the array that `splice()` is being called upon. And remember, arrays are zero-indexed, so to indicate the first element of an array, we would use 0. `splice()`'s first parameter represents the index on the array from which to begin removing elements, while the second parameter indicates the number of elements to delete. For example:

    let array = ['today', 'was', 'not', 'so', 'great'];

    array.splice(2, 2);
    // remove 2 elements beginning with the 3rd element
    // array now equals ['today', 'was', 'great']
`splice()` not only modifies the array it's being called on, but it also returns a new array containing the value of the removed elements:

    let array = ['I', 'am', 'feeling', 'really', 'happy'];

    let newArray = array.splice(3, 2);
    // newArray equals ['really', 'happy']

We've defined a function, sumOfTen, which takes an array as an argument and returns the sum of that array's elements. Modify the function, using `splice()`, so that it returns a value of `10`.

    function sumOfTen(arr) {
      // change code below this line
      arr.splice(2,2);
      // change code above this line
      return arr.reduce((a, b) => a + b);
    }

    // do not change code below this line
    console.log(sumOfTen([2, 5, 1, 5, 2, 1]));


***

### Basic Data Structures: Add Items Using splice()
Remember in the last challenge we mentioned that `splice()` can take up to three parameters? Well, we can go one step further with `splice()` — in addition to removing elements, we can use that third parameter, which represents one or more elements, to add them as well. This can be incredibly useful for quickly switching out an element, or a set of elements, for another. For instance, let's say you're storing a color scheme for a set of DOM elements in an array, and want to dynamically change a color based on some action:

    function colorChange(arr, index, newColor) {
      arr.splice(index, 1, newColor);
      return arr;
    }

    let colorScheme = ['###878787', '###a08794', '###bb7e8c', '###c9b6be', '###d1becf'];

    colorScheme = colorChange(colorScheme, 2, '###332327');
    // we have removed '###bb7e8c' and added '###332327' in its place
    // colorScheme now equals ['###878787', '###a08794', '###332327', '###c9b6be', '###d1becf']
This function takes an array of hex values, an index at which to remove an element, and the new color to replace the removed element with. The return value is an array containing a newly modified color scheme! While this example is a bit oversimplified, we can see the value that utilizing `splice()` to its maximum potential can have.


We have defined a function, `htmlColorNames`, which takes an array of HTML colors as an argument. Modify the function using `splice()` to remove the first two elements of the array and add `'DarkSalmon'` and `'BlanchedAlmond'` in their respective places.

    function htmlColorNames(arr) {
      // change code below this line
      arr.splice(0, 2, 'DarkSalmon', 'BlanchedAlmond')
      // change code above this line
      return arr;
    } 
    
    // do not change code below this line
    console.log(htmlColorNames(['DarkGoldenRod', 'WhiteSmoke', 'LavenderBlush', 'PaleTurqoise', 'FireBrick']));


***

### Basic Data Structures: Copy Array Items Using slice()
The next method we will cover is `slice()`. `slice()`, rather than modifying an array, copies, or extracts, a given number of elements to a new array, leaving the array it is called upon untouched. `slice()` takes only 2 parameters — the first is the index at which to begin extraction, and the second is the index at which to stop extraction (extraction will occur up to, but not including the element at this index). Consider this:

    let weatherConditions = ['rain', 'snow', 'sleet', 'hail', 'clear'];

    let todaysWeather = weatherConditions.slice(1, 3);
    // todaysWeather equals ['snow', 'sleet'];
    // weatherConditions still equals ['rain', 'snow', 'sleet', 'hail', 'clear']
In effect, we have created a new array by extracting elements from an existing array.


We have defined a function, forecast, that takes an array as an argument. Modify the function using `slice()` to extract information from the argument array and return a new array that contains the elements `'warm'` and `'sunny'`.

    function forecast(arr) {
      // change code below this line
      let newarr =  arr.slice(2,4);
      return newarr;
    }

    // do not change code below this line
    console.log(forecast(['cold', 'rainy', 'warm', 'sunny', 'cool', 'thunderstorms']));


***

### Basic Data Structures: Copy an Array with the Spread Operator
While `slice()` allows us to be selective about what elements of an array to copy, among several other useful tasks, ES6's new _spread_ operator allows us to easily copy all of an array's elements, in order, with a simple and highly readable syntax. The spread syntax simply looks like this: `...`

In practice, we can use the spread operator to copy an array like so:

    let thisArray = [true, true, undefined, false, null];
    let thatArray = [...thisArray];
    // thatArray equals [true, true, undefined, false, null]
    // thisArray remains unchanged, and is identical to thatArray

We have defined a function, `copyMachine` which takes `arr` (an array) and `num` (a number) as arguments. The function is supposed to return a new array made up of `num` copies of `arr`. We have done most of the work for you, but it doesn't work quite right yet. Modify the function using spread syntax so that it works correctly (hint: another method we have already covered might come in handy here!).

    function copyMachine(arr, num) {
      let newArr = [];
      while (num >= 1) {
        // change code below this line
        newArr.push([...arr]);
        // change code above this line
        num--;
      }
      return newArr;
    }

    // change code here to test different cases:
    console.log(copyMachine([true, false, true], 2));


***

### Basic Data Structures: Combine Arrays with the Spread Operator
Another huge advantage of the spread operator, is the ability to combine arrays, or to insert all the elements of one array into another, at any index. With more traditional syntaxes, we can concatenate arrays, but this only allows us to combine arrays at the end of one, and at the start of another. Spread syntax makes the following operation extremely simple:

    let thisArray = ['sage', 'rosemary', 'parsley', 'thyme'];

    let thatArray = ['basil', 'cilantro', ...thisArray, 'coriander'];
    // thatArray now equals ['basil', 'cilantro', 'sage', 'rosemary', 'parsley', 'thyme', 'coriander']
Using spread syntax, we have just achieved an operation that would have been more complex and more verbose had we used traditional methods.


We have defined a function `spreadOut` that returns the variable sentence, modify the function using the spread operator so that it returns the array `['learning', 'to', 'code', 'is', 'fun']`.

    function spreadOut() {
      let fragment = ['to', 'code'];
      let sentence = ['learning', ...fragment, 'is', 'fun'];
      return sentence;
    }

    // do not change code below this line
    console.log(spreadOut());

***

### Basic Data Structures: Check For The Presence of an Element With indexOf()
Since arrays can be changed, or mutated, at any time, there's no guarantee about where a particular piece of data will be on a given array, or if that element even still exists. Luckily, JavaScript provides us with another built-in method, `indexOf()`, that allows us to quickly and easily check for the presence of an element on an array. `indexOf()` takes an element as a parameter, and when called, it returns the position, or index, of that element, or `-1` if the element does not exist on the array.

For example:

    let fruits = ['apples', 'pears', 'oranges', 'peaches', 'pears'];

    fruits.indexOf('dates') // returns -1
    fruits.indexOf('oranges') // returns 2
    fruits.indexOf('pears') // returns 1, the first index at which the element exists

`indexOf()` can be incredibly useful for quickly checking for the presence of an element on an array. We have defined a function, `quickCheck`, that takes an array and an element as arguments. Modify the function using `indexOf()` so that it returns true if the passed element exists on the array, and false if it does not.

    function quickCheck(arr, elem) {
      // change code below this line
      return arr.indexOf(elem) > -1 ? true : false;
      // change code above this line
    }

    // change code here to test different cases:
    console.log(quickCheck(['squash', 'onions', 'shallots'], 'mushrooms'));


***


### Basic Data Structures: Iterate Through All an Array's Items Using For Loops
Sometimes when working with arrays, it is very handy to be able to iterate through each item to find one or more elements that we might need, or to manipulate an array based on which data items meet a certain set of criteria. JavaScript offers several built in methods that each iterate over arrays in slightly different ways to achieve different results (such as `every()`, `forEach()`, `map()`, etc.), however the technique which is most flexible and offers us the greatest amount of control is a simple for loop.

Consider the following:

    function greaterThanTen(arr) {
      let newArr = [];
      for (let i = 0; i < arr.length; i++) {
        if (arr[i] > 10) {
          newArr.push(arr[i]);
        }
      }
      return newArr;
    }

    greaterThanTen([2, 12, 8, 14, 80, 0, 1]);
    // returns [12, 14, 80]
Using a for loop, this function iterates through and accesses each element of the array, and subjects it to a simple test that we have created. In this way, we have easily and programmatically determined which data items are greater than 10, and returned a new array containing those items.


We have defined a function, `filteredArray`, which takes `arr`, a nested array, and `elem` as arguments, and returns a new array. `elem` represents an element that may or may not be present on one or more of the arrays nested within `arr`. Modify the function, using a for loop, to return a filtered version of the passed array such that any array nested within `arr` containing elem has been removed.

    function filteredArray(arr, elem) {
      let newArr = [];
      // change code below this line
      outer:for (let i=0; i<arr.length; i++) {
        for (let j=0; j<arr[i].length;j++ ) {
          if (arr[i][j] === elem) { continue outer;}
        }
        newArr.push(arr[i]);
      }
      // change code above this line
      return newArr;
    }

    // change code here to test different cases:
    console.log(filteredArray([[3, 2, 3], [1, 6, 3], [3, 13, 26], [19, 3, 9]], 3));


***

### Basic Data Structures: Create complex multi-dimensional arrays
Awesome! You have just learned a ton about arrays! This has been a fairly high level overview, and there is plenty more to learn about working with arrays, much of which you will see in later sections. But before moving on to looking at Objects, lets take one more look, and see how arrays can become a bit more complex than what we have seen in previous challenges.

One of the most powerful features when thinking of arrays as data structures, is that arrays can contain, or even be completely made up of other arrays. We have seen arrays that contain arrays in previous challenges, but fairly simple ones. However, arrays can contain an infinite depth of arrays that can contain other arrays, each with their own arbitrary levels of depth, and so on. In this way, an array can very quickly become very complex data structure, known as a multi-dimensional, or nested array. Consider the following example:

    let nestedArray = [ // top, or first level - the outer most array
      ['deep'], // an array within an array, 2 levels of depth
      [
        ['deeper'], ['deeper'] // 2 arrays nested 3 levels deep
      ],
      [
        [
          ['deepest'], ['deepest'] // 2 arrays nested 4 levels deep
        ],
        [
          [
            ['deepest-est?'] // an array nested 5 levels deep
          ]
        ]
      ]
    ];
While this example may seem convoluted, this level of complexity is not unheard of, or even unusual, when dealing with large amounts of data.

However, we can still very easily access the deepest levels of an array this complex with bracket notation:

    console.log(nestedArray[2][1][0][0][0]);
    // logs: deepest-est?
And now that we know where that piece of data is, we can reset it if we need to:

    nestedArray[2][1][0][0][0] = 'deeper still';

    console.log(nestedArray[2][1][0][0][0]);
    // now logs: deeper still

We have defined a variable, `myNestedArray`, set equal to an array. Modify `myNestedArray`, using any combination of strings, numbers, and booleans for data elements, so that it has exactly five levels of depth (remember, the outer-most array is level 1). Somewhere on the third level, include the string `'deep'`, on the fourth level, include the string `'deeper'`, and on the fifth level, include the string `'deepest'`.

    let myNestedArray = [
      // change code below this line
      ['unshift', false, 1, 2, 3, 'complex', 'nested'],
      ['loop', 'shift', 6, 7, 1000, 'method'],
      ['concat', false, true, 'spread', 'array',["deep"]],
      ['mutate', 1327.98, 'splice', 'slice', 'push', [["deeper"]]],
      ['iterate', 1.3849, 7, '8.4876', 'arbitrary', 'depth', [[["deepest"]]] ]
      // change code above this line
    ];


***

### Basic Data Structures: Add Key-Value Pairs to JavaScript Objects
At their most basic, objects are just collections of key-value pairs, or in other words, pieces of data mapped to unique identifiers that we call _properties_ or _keys_. Let's take a look at a very simple example:

    let FCC_User = {
      username: 'awesome_coder',
      followers: 572,
      points: 1741,
      completedProjects: 15
    };
The above code defines an object called `FCC_User` that has four properties, each of which map to a specific value. If we wanted to know the number of followers `FCC_User` has, we can access that property by writing:

    let userData = FCC_User.followers;
    // userData equals 572
This is called dot notation. Alternatively, we can also access the property with brackets, like so:

    let userData = FCC_User['followers']
    // userData equals 572
Notice that with bracket notation, we enclosed followers in quotes. This is because the brackets actually allow us to pass a variable in to be evaluated as a property name (hint: keep this in mind for later!). Had we passed `followers` in without the quotes, the JavaScript engine would have attempted to evaluate it as a variable, and a `ReferenceError: followers is not defined` would have been thrown.


Using the same syntax, we can also add new key-value pairs to objects. We've created a `foods` object with three entries. Add three more entries: `bananas` with a value of `13`, `grapes` with a value of `35`, and `strawberries` with a value of `27`.

    let foods = {
      apples: 25,
      oranges: 32,
      plums: 28
    };

    // change code below this line
    foods.bananas = 13;
    foods.grapes = 35;
    foods.strawberries = 27;
    // change code above this line

    console.log(foods);


***

### Basic Data Structures: Modify an Object Nested Within an Object
Now let's take a look at a slightly more complex object. Object properties can be nested to an arbitrary depth, and their values can be any type of data supported by JavaScript, including arrays and even other objects. Consider the following:

    let nestedObject = {
      id: 28802695164,
      date: 'December 31, 2016',
      data: {
        totalUsers: 99,
        online: 80,
        onlineStatus: {
          active: 67,
          away: 13
        }
      }
    };
`nestedObject` has three unique keys: `id`, whose value is a `number`, `date` whose value is a `string`, and `data`, whose value is an `object` which has yet another object nested within it. While structures can quickly become complex, we can still use the same notations to access the information we need.


Here we've defined an object, `userActivity`, which includes another object nested within it. You can modify properties on this nested object in the same way you modified properties in the last challenge. Set the value of the `online` key to `45`.

    let userActivity = {
      id: 23894201352,
      date: 'January 1, 2017',
      data: {
        totalUsers: 51,
        online: 42
      }
    };

    // change code below this line
    userActivity.data.online = 45;
    // change code above this line

    console.log(userActivity);


***

### Basic Data Structures: Access Property Names with Bracket Notation
In the first object challenge we mentioned the use of bracket notation as a way to access property values using the evaluation of a variable. For instance, imagine that our foods object is being used in a program for a supermarket cash register. We have some function that sets the ### selectedFood and we want to check our foods object for the presence of that food. This might look like:

    let selectedFood = getCurrentFood(scannedItem);
    let inventory = foods[selectedFood];
This code will evaluate the value stored in the `selectedFood` variable and return the value of that key in the foods object, or undefined if it is not present. Bracket notation is very useful because sometimes object properties are not known before runtime or we need to access them in a more dynamic way.


We've defined a function, `checkInventory`, which receives a scanned item as an argument. Return the current value of the `scannedItem` key in the foods object. You can assume that only valid keys will be provided as an argument to `checkInventory`.

    let foods = {
      apples: 25,
      oranges: 32,
      plums: 28,
      bananas: 13,
      grapes: 35,
      strawberries: 27
    };
    // do not change code above this line

    function checkInventory(scannedItem) {
      // change code below this line
      return foods[scannedItem];
    }

    // change code below this line to test different cases:
    console.log(checkInventory("apples"));


***

### Basic Data Structures: Use the delete Keyword to Remove Object Properties
Now you know what objects are and their basic features and advantages. In short, they are key-value stores which provide a flexible, intuitive way to structure data, and, they provide very fast lookup time. Throughout the rest of these challenges, we will describe several common operations you can perform on objects so you can become comfortable applying these useful data structures in your programs.

In earlier challenges, we have both added to and modified an object's key-value pairs. Here we will see how we can remove a key-value pair from an object.

Let's revisit our `foods` object example one last time. If we wanted to remove the apples key, we can remove it by using the `delete` keyword like this:

    delete foods.apples;

Use the `delete` keyword to remove the `oranges`, `plums`, and `strawberries` keys from the `foods` object.

    let foods = {
      apples: 25,
      oranges: 32,
      plums: 28,
      bananas: 13,
      grapes: 35,
      strawberries: 27
    };

    // change code below this line
    delete foods.oranges;
    delete foods.plums;
    delete foods.strawberries;
    // change code above this line

    console.log(foods);


***

### Basic Data Structures: Check if an Object has a Property
Now we can add, modify, and remove keys from objects. But what if we just wanted to know if an object has a specific property? JavaScript provides us with two different ways to do this. One uses the `hasOwnProperty()` method and the other uses the `in` keyword. If we have an object users with a property of `Alan`, we could check for its presence in either of the following ways:

    users.hasOwnProperty('Alan');
    'Alan' in users;
    // both return true

We've created an object, `users`, with some users in it and a function `isEveryoneHere`, which we pass the users object to as an argument. Finish writing this function so that it returns `true` only if the users object contains all four names, `Alan`, `Jeff`, `Sarah`, and `Ryan`, as keys, and `false` otherwise.

    let users = {
      Alan: {
        age: 27,
        online: true
      },
      Jeff: {
        age: 32,
        online: true
      },
      Sarah: {
        age: 48,
        online: true
      },
      Ryan: {
        age: 19,
        online: true
      }
    };

    function isEveryoneHere(obj) {
      // change code below this line
      return (users.hasOwnProperty('Alan','Jeff','Sarah','Ryan')) ? true : false;
      // change code above this line
    }

    console.log(isEveryoneHere(users));


***

`Basic Data Structures: Iterate Through the Keys of an Object with a for...in Statement`
Sometimes you may need to iterate through all the keys within an object. This requires a specific syntax in JavaScript called a `for...in` statement. For our `users` object, this could look like:

    for (let user in users) {
      console.log(user);
    };

    // logs:
    Alan
    Jeff
    Sarah
    Ryan
In this statement, we defined a variable `user`, and as you can see, this variable was reset during each iteration to each of the object's keys as the statement looped through the object, resulting in each user's name being printed to the console.

NOTE:
Objects do not maintain an ordering to stored keys like arrays do; thus a keys position on an object, or the relative order in which it appears, is irrelevant when referencing or accessing that key.


We've defined a function, `countOnline`; use a `for...in` statement within this function to loop through the users in the `users` object and return the number of users whose online property is set to `true`.

    let users = {
      Alan: {
        age: 27,
        online: false
      },
      Jeff: {
        age: 32,
        online: true
      },
      Sarah: {
        age: 48,
        online: false
      },
      Ryan: {
        age: 19,
        online: true
      }
    };

    function countOnline(obj) {
      // change code below this line
      let counter = 0;
      for (let user in obj) {
        if (obj[user]["online"]) {counter++;} 
      }
      return counter;
      // change code above this line
    }

    console.log(countOnline(users));


***

### Basic Data Structures: Generate an Array of All Object Keys with Object.keys()
We can also generate an array which contains all the keys stored in an object using the `Object.keys()` method and passing in an object as the argument. This will return an array with strings representing each property in the object. Again, there will be no specific order to the entries in the array.


Finish writing the `getArrayOfUsers` function so that it returns an array containing all the properties in the object it receives as an argument.

    let users = {
      Alan: {
        age: 27,
        online: false
      },
      Jeff: {
        age: 32,
        online: true
      },
      Sarah: {
        age: 48,
        online: false
      },
      Ryan: {
        age: 19,
        online: true
      }
    };

    function getArrayOfUsers(obj) {
      // change code below this line
      return Object.keys(obj);
      // change code above this line
    }

    console.log(getArrayOfUsers(users));


***

### Basic Data Structures: Modify an Array Stored in an Object
Now you've seen all the basic operations for JavaScript objects. You can add, modify, and remove key-value pairs, check if keys exist, and iterate over all the keys in an object. As you continue learning JavaScript you will see even more versatile applications of objects. Additionally, the optional Advanced Data Structures lessons later in the curriculum also cover the ES6 Map and Set objects, both of which are similar to ordinary objects but provide some additional features. Now that you've learned the basics of arrays and objects, you're fully prepared to begin tackling more complex problems using JavaScript!


Take a look at the object we've provided in the code editor. The `user` object contains three keys. The data key contains five keys, one of which contains an array of `friends`. From this, you can see how flexible objects are as data structures. We've started writing a function `addFriend`. Finish writing it so that it takes a `user` object and adds the name of the `friend` argument to the array stored in `user.data.friends` and returns that array.

    let user = {
      name: 'Kenneth',
      age: 28,
      data: {
        username: 'kennethCodesAllDay',
        joinDate: 'March 26, 2016',
        organization: 'freeCodeCamp',
        friends: [
          'Sam',
          'Kira',
          'Tomo'
        ],
        location: {
          city: 'San Francisco',
          state: 'CA',
          country: 'USA'
        }
      }
    };

    function addFriend(userObj, friend) {
      // change code below this line  
      userObj.data.friends.push(friend);
      return userObj.data.friends;
      // change code above this line
    }

    console.log(addFriend(user, 'Pete'));


***

