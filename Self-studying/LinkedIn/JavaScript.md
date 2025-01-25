#### Resources
+ [Eloquent JavaScript](https://eloquentjavascript.net)
+ [Exploring JS](https://exploringjs.com)
+ [You Dont know JS](https://github.com/getify/You-Dont-Know-JS)
+ [Oreilly](https://shop.oreilly.com/product/9780596517748.do)
+ [JS the good parts notes](https://github.com/dwyl/Javascript-the-Good-Parts-notes)
+ [Mozilla](https://developer.mozilla.org)
+ [Can I use](https://caniuse.com)
+ [Quirks Mode](https://quirksmode.org)

# Variables and Types
## Declaring and assigning variables

```javascript
var x = 32;
x;

var whereAmI = "Santa Barbara, CA";
whereAmI;

x = 45;
x;
whereAmI = 75;
whereAmI;

var monster1 = "Grover", monster2 = 'Cookie Monster', monster3 = 'Animal';
monster1;
monster2;
monster3;
```

## Strings

```javascript
"This is a string";
"12";
12;

'This is also a string';
'This is a string"; // mismatched quotes - this will not execute

'<a href="">';
'<a href="http://www.example.com">';

"This is Joe's favorite string";
"This is Joe's \"favorite\" string";
"This is Joe's "favorite" string"; // this line will not work

"This is \
Joe's Favorite \
String EVER";
```

### String properties and methods

```javascript
var myString = "This is my string. Leave it alone";
myString;
myString.length;
myString.toUpperCase();

"This is my string".length;

let declaration = `This I say to you: "good morning". Huzzah!`;
declaration;

declaration = `This I say to you: "${myString}". Huzzah!`;
declaration;
```

## Numbers

```javascript
12
12.0
12.82358972893527582
-12
Infinity
-Infinity
NaN

var myNumber = 33;

Math;
Math.round(12.4984012840918);
Math.round(12.92309820948209384);

Math.random();
Math.random();
Math.random();
Math.random();
```

## Booleans for what is true

```javascript
true;
false;

True;
FALSE;
tRuE;
true;
false;

buttonHasBeenClicked = false;

var myLocation = "Santa Barbara", myOtherLocation = "Los Angeles";

myLocation === myOtherLocation;

myOtherLocation = "Santa Barbara";

myLocation === myOtherLocation;
```

## Variable mutability

```javascript
const dozen = 12, halfDozen = 6, bakersDozen = 13;

dozen = 13;

var cookieCount = 5;
let cookieCount = 5;
```

# Objects, Arrays and More

## Objects

```javascript
12;
("strings");
true;

// prettier-ignore
{}
var emptyObject = {};
emptyObject;

var notEmptyObject = {
  label: "value",
  label2: "value2",
};
notEmptyObject;
```

### Using objects for data modeling

```javascript
let bird = {
  genus: "corvus",
  species: "corvax",
  commonName: "raven",
  callType: "squawky",
  quote: "Nevermore",
  maxOffspring: 5,
  noisy: true,
  deadly: false,
};

let bear = {
  genus: "ursus",
  species: "arctos",
  commonName: "brown bear",
  callType: "roar",
  quote: "",
  maxOffspring: 3,
  noisy: true,
  deadly: true,
};

const bookOfKnowledge = {
  "lunch time": "12:30 PM",
  "the ultimate answer": 42,
  bestSong: "Lonnie's Lament",
  earth: "Mostly harmless.",
};
```

### Manipulating objects

```javascript
var bird = {
	genus : 'corvus',
	species : 'corvax',
	commonName: 'raven',
	callType : 'squawky',
	quote : 'Nevermore',
	maxOffspring : 5,
	noisy : true,
	deadly : false
};

bird.quote;

bird."quote"; // this does not work

bird["quote"];

bird.color = "black";

bird;

bird["where it lives"] = "in a tree";
bird.whereItLives = "in a tree";
bird.whereItLives;
bird['whereItLives'];

delete bird.color;
bird;
```

### Jargon: References

```javascript
var animal = {
  genus: "corvus",
  species: "corvax",
  commonName: "raven",
  callType: "squawky",
  quote: "Nevermore",
  maxOffspring: 5,
  noisy: true,
  deadly: false,
};
animal;

var animal2 = animal;
animal2;

animal2.genus = "ursus";
animal2;
animal;

animal2 = {
  genus: "corvus",
  species: "corvax",
  commonName: "raven",
  callType: "squawky", // there is a deliberate bug here in the course, removed for your convenience :)
  quote: "Nevermore",
  maxOffspring: 5,
  noisy: true,
  deadly: false,
};

// bonus: make a copy of an object safely
animal2 = Object.assign({}, animal);
animal2 = { ...animal };
animal2 = JSON.parse(JSON.stringify(animal));

animal2.genus = "ursus";
animal2;
animal;
```

## Arrays

```javascript
var myArray = [];
myArray;

var daysOfTheWeek = ["Sunday", "Monday", "Tuesday", "Wednesday"];
daysOfTheWeek;

var myList = [0, 1, 2, "string1", "string2", "string3", true, false];
myList;

var counties = ["Belknap", "Strafford", "Carroll", "Rockingham"];
counties;

var listOfStuff = [{ name: "value" }, [1, 2, 3], true, "nifty"];
listOfStuff;
listOfStuff.length;
```

### Manipulating Arrays

```javascript
var counties = ["Belknap", "Strafford", "Carroll", "Rockingham"];

counties[0];
counties[2];

counties[2] = "Cheshire";
counties;

counties[4] = "Carroll";
counties;

counties[counties.length] = "Merrimack";
counties;

counties.push("Coos");
counties;

counties.pop();

delete counties[2];
counties;

counties.splice(2, 1);
counties;
counties.length;
```

## Readability 
### Whitespace

```javascript
var year=2012,month='October',day=31,holiday='Halloween';

var year   = 2012,       month    =    'October', day =          31,          holiday='Halloween';

var year = 2012,
	month = 'October',
	day = 31,
	holiday = 'Halloween';
	
var year  = 2012,
	month   = 'October',
	day     = 31,
	holiday = 'Halloween';

var tinyAlmanac={'year':2012,'month':'October','day':31,'holiday':'Halloween'};

var tinyAlmanac = {
	'year' : 2012,
	'month' : 'October',
	'day' : 31,
	'holiday' : 'Halloween'
};

var longString = "Four score \
and seven years ago \
our fathers brought forth \
on this continent \
a new nation";
```

### Comments

```javascript
// another after the slashes does not execute
var year = 2012,
  month = "October", // this is the month
  // day = 31,
  holiday = "Halloween";

/*
You can write comments
across multiple lines
finally ending with:
*/

var tinyAlmanac = {
  year: 2012,
  month: "October",
  day: 31,
  holiday: "Halloween"
};

// watch out for block comments here
var myRegExp = /[0-9].*/;
```

## Regular expressions

```javascript
var string1 = "This is the longest string ever.";
var string2 = "This is the shortest string ever.";
var string3 = "Is this the thing called Mount Everest?";
var string4 = "This is the Sherman on the Mount.";

var regex = /this/;

regex.test(string1);
regex.test(string2);
regex.test(string3);
regex.test(string4);

regex = /this/i;

regex = /^this/i;

regex = /this$/i;

regex = /ever.$/i;

regex = /ever\.$/i;

```

# Operators

## Simple Comparisons

```javascript
var one = 1,
  two = 2;

one === one; // true
one !== one; // false
one !== two; // true
one === two; // false

one == one; // true
one == "1"; // true (?!)
one != "1"; // false (?!)
one === "1"; // false

one < two; // true

one > two; // false

one <= two; // true

one <= one; // true

one >= two; // false

10 >= two; // true

```

## Arirhmetic operators

```javascript
2 + 5;
4 - 3;
5 - 9;
3 * 5;
36 / 6;
36 / 5;

20 % 2;
19 % 2;

// twenty an even number?
20 % 2 === 0; // true

const perPage = 20;
const totalResults = 254;
totalResults % perPage;

var counter = 0;
counter = counter + 1;

counter += 1;
counter++;

counter += 5;
counter += -4;

counter -= 1;
counter--;
counter;

counter *= 2;

"cat" + "dog";
"cat " + "dog";
"cat" + " and " + "dog";

"1" + "2";
```

## Logical operators

```javascript
// &&
// ||

let animal1 = "monkey", animal2 = "bear", animal3 = "tiger";

// Pretend there's code that might change the values of the animal variables here, then…

animal1 === "monkey" && animal2 === "bear"; // true
animal1 === "ape" && animal2 === "bear"; // false
animal1 === "ape" && animal2 === "bear" && animal3 === "tiger"; // false
animal1 === "monkey" && animal2 === "bear" && animal3 === "tiger"; // true

animal1 === "monkey" || animal2 === "bear"; // true
animal1 === "ape" || animal2 === "bear"; // true
animal1 === "ape" || animal2 === "ostrich"; // false

animal1 === "monkey" || animal2 === "monkey" && animal3 === "tiger";
(animal1 === "monkey" || animal2 === "monkey") && animal3 === "tiger";

!true; // false
!false; // true

animal1 === "monkey" && animal2 === "zebra"; // false
!(animal1 === "monkey" && animal2 === "zebra"); // true
animal1 !== "monkey" && animal2 !== "zebra"; // false
animal1 !== "monkey" || animal2 !== "zebra"; // true
```

# Control Structures

## Conditionals: If

```javascript
// Execute these in a browser
var answer = window.confirm("Click OK, get true.  Click cancel, get false.");

if (answer === true) {
  console.log("You said true!");
}

if (answer === true) {
  console.log("You said true!");
} else {
  console.log("You said something else");
}

var answer = window.prompt("Type YES, NO, or MAYBE.  Then click OK.");
if (answer === "YES") {
  console.log("You said YES!");
} else if (answer === "MAYBE") {
  console.log("You said maybe. I don't know what to make of that."); // note the double primes
} else if (answer === "NO") {
  console.log("You said no. :(");
} else {
  console.log("You rebel, you!");
}

var answer = window.prompt("Type YES, NO, or MAYBE.  Then click OK.");
if (answer === "YES" || answer === "NO") {
  // Do some common actions for YES and NO

  if (answer === "YES") {
    console.log("You said YES!");
    // do some other things
  } else {
    console.log("You said no. :(");
    // do some things only for NO
  }
} else if (answer === "MAYBE") {
  console.log("You said maybe.  I don't know what to make of that.");
} else {
  console.log("You rebel, you!");
}
```

### Terse ifs: One-liners

```javascript
var cherub = "Cupid";
// cherub = 'Norman';

if (cherub === "Cupid") console.log("Ouch, an arrow!  Ooo, I'm in love!");

if (cherub === "Cupid") console.log("Ouch, an arrow!  Ooo, I'm in love!");
else console.log("I feel nothing!");

let errorMsg = '';

if (errorMsg) {
  console.error('There was an error', errorMsg);
}

if (!errorMsg) {
  console.log('Yay! No errors!');
}

let errors = [];

// if (errors) { // Nope - empty arrays are truthy

if (errors.length) {
  console.error("Please fix these errors", errors);
}
```

### Terse ifs: Terenaries

```javascript
var animal = "cat";
// animal = 'dog';

animal === "cat"
  ? console.log("You will be a cat herder.")
  : console.log("You will be a dog catcher.");

var job = animal === "cat" ? "cat herder" : "dog catcher";

// prettier-ignore
var job = (animal === "cat") ? "cat herder" : "dog catcher";
```
## Conditionals: Switch

```javascript
var answer = window.prompt("Type YES, NO, or MAYBE.  Then click OK.");

if (answer === "YES") {
  console.log("You said YES!");
} else if (answer === "MAYBE") {
  console.log("You said maybe. I don't know what to make of that.");
} else if (answer === "NO") {
  console.log("You said no. :(");
} else {
  console.log("You rebel, you!");
}

switch (answer) {
  case "YES":
    console.log("You said YES!");
    break;
  case "MAYBE":
    console.log("You said maybe. I don't know what to make of that.");
    break;
  case "NO":
    console.log("You said no. :(");
    break;
  default:
    console.log("You rebel, you!");
    break;
}

```

## Type Checking

```javascript
var thing = 12;
thing = "twelve";
typeof thing;

thing = 12;
typeof thing;

thing = false;
typeof thing;

thing = {};
typeof thing;

thing = [];
typeof thing;
typeof thing === "object" && thing.hasOwnProperty("length"); // true

thing = {};
typeof thing === "object" && thing.hasOwnProperty("length"); // false

NaN;
typeof NaN;
Number.isNaN();

typeof null;
thing === null;
thing = null;
thing === null;

let somethingLater;
typeof somethingLater;
typeof nothingSilly;
```

# Loops

## For loops

### Sequential

```javascript
for (let i = 0; i < 10; i += 1) {
  console.log(i);
}

// very common use case: looping over an array.
var pageNames = [
  "Home",
  "About Us",
  "Contact Us",
  "JavaScript Playground",
  "News",
  "Blog"
];
for (i = 0; i < pageNames.length; i += 1) {
  if (document.title === pageNames[i]) {
    console.log("We ARE here: " + pageNames[i]);
  } else {
    console.log("We are not here: " + pageNames[i]);
  }
}

// don't repeat yourself:
var pageNames = [
  "Home",
  "About Us",
  "Contact Us",
  "JavaScript Playground",
  "News",
  "Blog"
];
for (i = 0; i < pageNames.length; i += 1) {
  var currentPageTitle = pageNames[i];

  if (document.title === currentPageTitle) {
    console.log("We ARE here: " + currentPageTitle);
  } else {
    console.log("We are not here: " + currentPageTitle);
  }
}
```

### Enumerative

```javascript
// iterate over an array
var pageNames = [
  "Home",
  "About Us",
  "Contact Us",
  "JavaScript Playground",
  "News",
  "Blog",
];

for (let i = 0; i < pageNames.length; i += 1) {
  console.log(i, pageNames[i]);
}

for (var p in pageNames) {
  console.log(p, pageNames[p]);
}

for (var v of pageNames) {
  console.log(v);
}

// iterate over an object
var pages = {
  first: "Home",
  second: "About Us",
  third: "Contact Us",
  fourth: "JavaScript Playground",
  fifth: "Blog",
};
for (var p in pages) {
  if (pages.hasOwnProperty(p)) {
    console.log(p, pages[p]);
  }
}
```

## While loops

```javascript
// for loop
for (let i = 0; i < 10; i += 1) {
  console.log(i);
}

// same thing as a while loop
let i = 0;
while (i < 10) {
  console.log(i + "... This will go until we hit 10");
  i += 1;
}

var myList = [true, true, true, false, true, true];

var myItem = null;

while (myItem !== false) {
  console.log(
    "myList has " +
      myList.length +
      " items now. This loop will keep going until we pop a false."
  );
  myItem = myList.pop();
}

var counter = 1;
while (true) {
  console.log(counter);
  counter++;
  break; // comment out this break statement to make this loop go forever and potentially lock up your web browser
}

var myList = [true, true, true, false, true, true];

var myItem = false;
do {
  console.log(
    "myList has " +
      myList.length +
      " items now. This loop will go until we pop a false."
  );
  myItem = myList.pop();
} while (myItem !== false);
```

## Set and Maps

![[Pasted image 20250124235236.png]]
![[Pasted image 20250124235847.png]]

```javascript
// This array has two copies of its first item
let myList = [1, 1, 2, 3, 5, 8, 13, "fibonacci"];

// The same thing using the Set API
let mySet = new Set();
mySet.add(1);
mySet.add(1); // this won't change mySet, since 1 is already in there
mySet.add(2);
mySet.add(3);
// ... this gets tedious

// An array can be turned into a set
// If you want to quickly remove all duplicates from an array, this is a good tool!
let mySet2 = new Set(myList);

mySet2.has(3); // true
mySet2.has(12); // false

// For...of loop iteration works
for (let item of mySet2) {
  console.log('mySet contains', item);
}

// This object is a bird
var bird = {
  genus: "corvus",
  species: "corvax",
  commonName: "raven",
};

// Here is a map using the same structure
var birdMap = new Map();
birdMap.set("genus", "corvus");
birdMap.set("species", "corvax");
birdMap.set("commonName", "raven");

birdMap.get("genus"); // 'corvus'

birdMap.has("genus"); // true
birdMap.has("corvus"); // false (keys only)

// for...of loops work on Maps, with key and value returned
for (let value of birdMap) {
  console.log(value);
}

birdMap.entries();

Object.entries(bird);

birdMap2 = new Map(Object.entries(bird));
```

# Functions

## Basic functions

```javascript
console.log('Arf');
console.log('Woof');
console.log('Meow');
console.log('Moooooooooooo');

function speak() {
	console.log('Arf');
	console.log('Woof');
	console.log('Meow');
	console.log('Moooooooooooo');
}

speak();

// Function expression assigned to a variable
const speak = function() {
	console.log('Arf');
	console.log('Woof');
	console.log('Meow');
	console.log('Moooooooooooo');
}
```

## Arguments and parameters

```javascript
fuddify("Be very quiet, I'm hunting rabbits.");
fuddify("You screwy rabbit.");
fuddify("Rabbit tracks!");

function fuddify(speech) {
  // if it's not a string, return an error message
  if (typeof speech !== "string") {
    console.error("Nice twy, wabbit!");
    return;
  }

  // otherwise, make it sound like Elmer Fudd
  speech = speech.replace(/r/g, "w");
  speech = speech.replace(/R/g, "W");

  return speech;
}

var utterance = fuddify("You screwy rabbit");
utterance;

function isEven(num) {
  if (num % 2 === 0) {
    return true;
  } else {
    return false;
  }
}

isEven(12);
12 % 2;

function isEven(num) {
  return num % 2 === 0;
}
```

```javascript
function speakSomething(what = "Default speech", howMany = 10) {
  for (var i = 0; i < howMany; i += 1) {
    console.log(what + " (" + i + ")");
  }
}

speakSomething("Good morning", 5);
speakSomething("Good morning");
speakSomething();

function addingMachine() {
  // initialize the total we'll be returning
  var total = 0;

  for (var i = 0; i < arguments.length; i += 1) {
    // grab the next number
    var number = arguments[i];

    // check if the argument is a number.
    // if so, add it to the running total
    if (typeof number === "number") {
      total += number;
    }
  }

  // done - return the total
  return total;
}

addingMachine(1, 2, 3);
addingMachine(1, 2, 3, 4, 5, 6, 7, 8, 9, 1204910249014);
```
## Objects, references, and functions

```javascript
var calvin = {
  name: "Calvin",
  bestFriend: "Hobbes",
  form: "human boy",
};

// you can also pass an object to a function
// because objects are using a copy of a reference, the argument will be modified
function transmogrifier(calvin) {
  if (typeof calvin !== "object") {
    console.error("Calvin is not an object.");
    return;
  }

  // generate a random number between 1 and 5
  var randomNumber = Math.floor(Math.random() * 5) + 1;

  switch (randomNumber) {
    case 1:
      calvin.form = "tyrannosaurus";
      break;
    case 2:
      calvin.form = "grey wolf";
      break;
    case 3:
      calvin.form = "bengal tiger";
      break;
    case 4:
      calvin.form = "grizzly bear";
      break;
    case 5:
      calvin.form = "canary";
      break;
    default:
      // he stays human
      calvin.form = "human boy";
      break;
  }
}

// this version of the transmogifier does return a copy, leaving the original alone
function transmogrifyCopy(calvin) {
  if (typeof calvin !== "object") {
    console.error("Calvin is not an object.");
    return;
  }

  // generate a random number between 1 and 5
  var randomNumber = Math.floor(Math.random() * 5) + 1;

  var newForm = calvin.form; // by default, do not change

  switch (randomNumber) {
    case 1:
      newForm = "tyrannosaurus";
      break;
    case 2:
      newForm = "grey wolf";
      break;
    case 3:
      newForm = "bengal tiger";
      break;
    case 4:
      newForm = "grizzly bear";
      break;
    case 5:
      newForm = "canary";
      break;
    default:
      // he stays human
      newForm = "human boy";
      break;
  }

  // return a new object that's just like calvin,
  // but transmogrified!
  return {
    name: calvin.name,
    bestFriend: calvin.bestFriend,
    form: newForm,
  };
}
```

## Functions are objects

```javascript
function speakSomething(what = 'Speaking!') {
  for (var i = 0; i < 10; i += 1) {
    console.log(what);
  }
}

var speakSomething = function(what = 'Speaking!') {
  for (var i = 0; i < 10; i += 1) {
    console.log(what);
  }
};

setTimeout(speakSomething, 5000);

var obj = {
  sayHello: function() {
    console.log("Hello");
  }
};

obj.sayHello();
```

## Functions and scope

```javascript
// Shim allowing this code to work in a browser as well as node
if (!global && typeof window !== 'undefined') {
  var global = window;
}

var myNum = 32;
var myResult = "Success!";

function randomizer(limit) {
  var randomNumber = Math.floor(Math.random() * limit);

  var myNum = randomNumber;

  console.log("Local myNum is", myNum);
  console.log("Global myNum is", global.myNum);

  console.log("Our result is", myResult);

  return myNum;
}

randomizer(10);

function doubleIt(num) {
  var myNum = num * 2;

  return myNum;
}

if (1 === 1) {
  const oneIsOne = 'Yes indeed.';
  console.log('One is one, right?', oneIsOne);
}

console.log('One is still one, right?', oneIsOne); // ReferenceError
```

## Arrow functions

```javascript
// Before:
const speak = function () {
  console.log("Arf");
  console.log("Woof");
  console.log("Meow");
  console.log("Moooooooooooo");
};

// After:
const speak = () => {
  console.log("Arf");
  console.log("Woof");
  console.log("Meow");
  console.log("Moooooooooooo");
};

// Before:
function isEven(num) {
  return num % 2 === 0;
}

// After:
let isEven = (num) => {
  return num % 2 === 0;
};

// or:
isEven = (num) => num % 2 === 0;

// And most succinctly:
// prettier-ignore
isEven = num => num % 2 === 0;
```

## Three little dots

```javascript
// function addingMachine(...terms)

function addingMachine(...terms) {
  // initialize the total we'll be returning
  var total = 0;

  // this used to be `arguments` instead of `terms`
  for (var i = 0; i < terms.length; i += 1) {
    // grab the next number
    var number = terms[i];

    // check if the argument is a number.
    // if so, add it to the running total
    if (typeof number === "number") {
      total += number;
    }
  }

  // done - return the total
  return total;
}

function bake(temp = 350, time = 35, ...flavors) {
  console.log(`Let's bake this cake at ${temp} degrees,`);
  console.log(`for ${time} minutes\n`);
  
  if (flavors.length > 0) {
    console.log("And let's not forget these flavors", flavors);
  }
  
  console.log("Arguments contains everything", arguments);
}

bake(425, 30, 'chocolate', 'lemon', 'black forest');
bake(300, 30, 'vanilla');
bake();
```

## Callback functions and looping

```javascript
function doubleIt(number) {
  return (number *= 2);
}

var myNumbers = [1, 2, 3, 4, 5];

var myDoubles = myNumbers.map(doubleIt);

myNumbers.forEach(function (number) {
  console.log("My array contains", number);
});

myNumbers.forEach((number) => {
  console.log("My array contains", number);
});

// this is a browser-based example
const myTextField = document.getElementById("myTextField");
myTextField.addEventListener("keyup", () => {
  console.log("Someone is typing!");
});
```

# Advanced topics

## Asynchronous code

```javascript
/**
 * Callbacks
 */

// With one, it's simple enough
jQuery.get("https://httpbin.org/get?data=1", function(response) {
  // Now I have some data
});

// Callbacks get nested ad infinitum
jQuery.get("https://httpbin.org/get", function(response) {
  // Now I have some data

  jQuery.get("https://httpbin.org/get", function(response) {
    // Now I have some more data

    jQuery.get("https://httpbin.org/get", function(response) {
      // Now I have even more data!
    });
  });
});

/**
 * Promises
 */

// One Promise
axios.get("https://httpbin.org/get").then(function(response) {
  // now I have some data
});

// Multiple promises in sequence, no nesting
axios
  .get("https://httpbin.org/get")
  .then(function(response) {
    // now I have some data

    return axios.get("https://httpbin.org/get");
  })
  .then(function(response) {
    // now I have some data

    return axios.get("https://httpbin.org/get");
  });

/**
 * Async / Await
 */

// One request
async function getOneThing() {
  var response = await axios.get("https://httpbin.org/get");

  // now I have some data
}

// Multiple requests
async function getLotsOfThings() {
  var response1 = await axios.get("https://httpbin.org/get");
  var response2 = await axios.get("https://httpbin.org/get");
  var response3 = await axios.get("https://httpbin.org/get");

  // Now I have lots of data
}
```

## Object-oriented 

![[Pasted image 20250125145145.png]]

```javascript
/**
 * Classes
 */

let Cake = {};

Cake.prototype.bake = function(temp, minutes) {
  // Bake a cake at a particular temperature
  // for a number of minutes
}

class CakeClass {
  bake(temp, minutes) {

  }
}
```

## Strong vs. loosely typed


## Modern JavaScript
Webpack
Rollup
Vite
Axios
Yarn
Npm
Babel
TypeScript

## Responsible JavaScript
