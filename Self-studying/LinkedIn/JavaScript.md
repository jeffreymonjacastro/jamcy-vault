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

## String properties and methods

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

```

## Using objects for data modeling

```javascript

```

## Manipulating objects

```javascript

```

## 

![[Pasted image 20250124235236.png]]
![[Pasted image 20250124235847.png]]