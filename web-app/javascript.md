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

## JSON Data

#### Definition: Objects are unordered collections of related data or primitive or reference types.

```javascript
// JSON Objects
{
    "firstName": "dd",
    "role": "Instructor"
}

// JSON Arrays
{"TAs": [
    {"Name": "1", "Year": 2022},
    {"Name": "1", "Year": 2022},
    {"Name": "1", "Year": 2022}
    ]
}

// Use JSON
var text = JSON ARRAY;
obj = JSON.parse(text);
obj.TAs[0].Name, obj.TAs[1].Year

// Request JSON from server
Synchronous OR Asynchronous(Recommanded, produce a callback when data received)

// Callback Function
function greeting(name){ // Synchronous Example
    alert("Hello", name);
}
function processUserInput(callback){
    var name = prompt("Enter your name");
    callback(name);
}
processUserInput(greeting);

XMLHttpRequest() & fetch(): Promise-based method, new
Promise objects represents the eventual completion/failure of an 
async operation and its result value;

// XMLHttpRequest()
var url = "tas.json";
var req = new XMLHttpRequest();
req.open('GET', url, true); // true for async
req.responseType = 'json';

req.onload = function(){
    ...
}
req.send();

// fetch
fetch(url)
    .then(response=>response.json())
    .then(data=>{
        ...
    })
    .catch(error=>console.error(error));
    
// parse and stringify
var tas = parse(JSON); //JSON->JS
var tas = stringify(JS); //JS->JSON 
```

## Working with APIs

#### Definition: API facilitate the programming of complex functionality

Browser API: fullscreen, screen orientation, vibration....

Third-party API: Google Maps API, Twitter API....

_**JS interacts with APIs over JS obejcts**_

```html
<audio src="Haydn_Adagio.mp3" type="audio/mpeg">
</audio>
<button data-playing="false" role="switch" aria-checked="true">
    <span>Play | Pause</span>
</button>
```

```javascript
const audioContext = new AudioContext();
const audioElement = document.querySelector('audio');
const track = audioContext.createMediaElementSource(audioElement);
track.connect(audioContext.destination);

playButton.addEventListener('click', function() {
    if (audioContext.state === 'suspended') { 
        audioContext.resume();
    }
    if (this.dataset.playing === 'false') {        
        audioElement.play();this.dataset.playing = 'true';
        console.log("Playing...");    
    } else if (this.dataset.playing === 'true') {        
        audioElement.pause();
        this.dataset.playing = 'false';
        console.log("Stopped..."); 
    }
}, false);
audioElement.addEventListener('ended', () => {    
    playButton.dataset.playing = 'false';
}, false);
```

## Working with Component Library

**Bootstrap: npm install bootstrap**

Width breakpoints to reorganize the layout

* Container: basic element of layout

```html
<div class="container">
    ...
</div>

<div class="container-fluid">
    ...
</div>

<div class="container-{breakpoint}"> <!-- xs,sm,md,lg,xl -->
    ...
</div>
```

* Flex box: [https://flexbox.malven.co/](https://flexbox.malven.co)
* Grids

```html
<div class="row">
    <div class = "col-*-*"></div>
    <div class = "col-*-*"></div>
</div>

<!-- first * is grid class -->
```

![](<../.gitbook/assets/Screen Shot 2022-02-03 at 11.55.24 AM.png>)![](<../.gitbook/assets/Screen Shot 2022-02-03 at 11.56.23 AM.png>)

* Content

```html
<img src="..." class="img-fluid">

<table class="table">
    <theadclass="thead-dark">
        <tr>
            <th scope="col">...</th>      
            ...
            
<div class="table-responsive-sm">
    <tableclass="table">  
    ...
```

![](<../.gitbook/assets/Screen Shot 2022-02-03 at 12.03.56 PM.png>)![](<../.gitbook/assets/Screen Shot 2022-02-03 at 12.04.00 PM.png>)

{% embed url="https://getbootstrap.com/docs/4.3/getting-started/introduction" %}

{% embed url="https://www.tutorialrepublic.com/twitter-bootstrap-tutorial" %}

{% embed url="https://www.w3schools.com/bootstrap/default.asp" %}
