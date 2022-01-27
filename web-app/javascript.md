# JavaScript

## FrontEnd

* HTML: Basic Structures
* CSS: Style and format
* JavaScript: Hidden Layer-->Logic

```javascript
function myFunction(){
    document.getElementById("message").innerHTML = "Downloading...";
}
```

```html
<button onclick = "myFunction()">Download</button>
<p id="message"></p>
```

#### Ways to interact:

* Internal JS (loaded based on location in html, has delay sometimes)

```html
<script>
...
</script>
```

* Extrenal JS (defer and async attributes)

```html
<script src="script.js" defer></script> // defer: JS file load at same time
as HTML loading, No block
```

* Inline JS handler

```html
<button onclick="myFunction()">Download</button> // Deprecated, Unorganized
```

#### JS interpreted:

* JS engine: v8(Chrome), SpiderMonkey(Firefox)
* Node.js encompasses v\* within C++ environ to compile without browser (VScode Run with Node.js)
* Online Sandboxes (codepen.io, codesandbox.io)....
* LiveServer-->Local Server

## Syntax

* 7 standard data types: **numbers, string, boolean, null, undefined, symbol, object**
* Dynamically, loosely, typed languages; No need to specify, data type inferred, can change

```javascript
var userName = "Jack"; // Globally
let userName = "Jill" // Narrow scope: for loop
const interestRate = 4.25 // Final and Global, cannot change

var firstName = "Ru", lastName = "Wang", age = 26; // different data type same line
typeof firstName-->"string"

// Object: unorderd collections of data of PRIMITIVE/REFERENCE types->key: value statements
var TA = {
    firstName: "ALice",
    lastName: "Smith",
    age: 24
}
TA.lastName-->"Smith"
TA["lastName"]-->"Smith"

// Array: can contain elements of different types
var students = ["Andy", "David","Laura"];
students[3] = "Nathan";  // QUESTION HERE
students[4] = 4

// Function: Easy for debugging, recursion
function nameFunc(parameters){
    // Calculate
}

// Anonymous Function: Easy for scope, brevity
var first = function(array){return array[0]};
var first = array => return array[0]; // arrow function

// Function serve as methods with objects
var Report = {
    temp: 77,
    humidity: 64,
    celcius: function(){ // Anonymous funciton, no Name
        reuturn (this.temp-32)*5/9;
    }
}

// Conditionals
if...else
switch
Ternary operator

=== & !== (identical to/not identical to objects, value & type)
== & != (values, not type)

// Any value that is not false, undefined, null, 0, NaN, "" return true
var current = "Alice";
if(current){ // evaluate to true
    ...
}

// Ternary
(condition)? doSth: doSthElse

// for loop
for(initializer; exit-condition; final-expression){
    ...
}
```

## Interacting with User-facing elements

#### Document Object Model (DOM): Tree structure

Objects: HTML elements,

Property: Value that can get or set, like id of element

Method: An action, like adding or deleting and HTML element

#### Access HTML elements:

* getElementById(id).innerHTML (also using tag name, class name, CSS selector)
* getElementById(id).src = "HeadShot.png";
* getElementById(id).style.color = "red";
* querySelector(CSS selector)

#### DOM Events:

onclick, onload, onunload, onchange, onmouserover......

* Inline event handlers
* DOM on-event handler
* Event listener

```javascript
document.getElementById("convert").onclick = "convertTemp"; // No ()
function convertTemp(){
    ...
}

// Event Listeners
document.getElementById("convert").addEventListener("click", convertTemp); // No ()
function convertTemp(){
    ...
}

// Change multiple elements, all buttons have the same event in this case
document.body.addEventListener("click", event=>{
    if(event.target.nodeName=="BUTTON"){
        console.log("Clicked", event.target.textContent);
    }
});
```
