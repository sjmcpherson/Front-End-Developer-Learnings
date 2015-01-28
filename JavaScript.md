<h2>General JavaScript Coding Tips</h2>

<h3>What is JavaScript</h3>
- JavaScript commonly abbreviated to JS is a scripted language rather than a compiled language like C#, C++, Java etc. This means it is executed line by line by its host environment(commonly the web browser) at run time. 
- Initially called LiveScript, JS is built from ECMAScript standards and its current version is v5 although modern web browser have started implementing many ECMAScript v6 features.

<h3>JavaScript Data Types</h3>
- There are 7 identifiable data types in JavaScript: number, string, boolean, object, function, undefined and null. They can be determined by using the 'typeof' operator. i.e. var theType = typeof ""; The variable 'theType' would equal 'string'. Although a bug exists when using typeof with 'null' values as it will return 'object'.

#####Dynamic Typed
- JavaScript is a Dynamically Typed language, As it is not compiled their is no Static Type Checking and variables are not initialised with a type at Runtime. JS therefore must deal with Type errors differently to Static Type languages like C#, C++, Java etc.

#####Primative Values
- The Data types number, boolean, null and undefined are Primative values meaning they do not have methods associated with them. Whereas objects and functions do. String's when not using the 'new' keyword are classed as Primitives although they are automatically converted to an object when using the String objects methods.

<h4>Variable Scope</h4>
#####Implied Global Variables
JavaScript has Implied Global Variables which means if a variable is initialized without using the 'var' keyword it will be deemed a Global Variable. For good practise always initialize with the 'var' keyword.

```javascript
  //Longhand
  var x;
  var y;
  var z = 3;
  //Shorthand
  var x, y, z=3;
```
#####Function Level Scoping
- JavaScript uses Function scoping rather than Block-level scoping i.e. if you declare a variable inside a "for" loop or "if" statement it will be accesseble outside that block but not outside its function. 

#####Variable Hoisting
- No matter where you declare a variable and what you set it to, the declaration will moved to the top of its scope(i.e its function) and assigned 'undefined'. This is called Variable Hoisting, so its good practise to always declare your variables at the top of the scope. See http://jsfiddle.net/sjmcpherso/qHBUY/

<h4>Boolean</h4>
- Only 2 Boolean values exist: true & false, although values of other types are also deemed either Truthy or Falsey.
- "Falsey" values are false, null ,"" ,0 , undefined ,NaN. All other values including objects are "Truthy"
- Truthy & Falsy values can be converted into real Booleans by using double negation '!!' i.e '!!0' Will equal false 

<h4>Numbers</h4>
- Only 1 number type (i.e no integer) which is represented as a 64bit floating point also known as Double.
- Has problems mapping to common arithmetic I.e var cur = 0.1 + 0.2; Will equal 0.3000000000004 so use parseFloat(0.1 + 0.2).toFixed(2) for currency calculations.
- isNaN() checks if value is NaN(Not a Number) which is achieved when JS is unsuccessful in converting a value to a number I.e when using the function Number(value) to convert a string to a number.
- parseInt can also be used to parse a string into a number but in the form of an integer i.e. parseInt('20px') = 20 because of type coersion.
- Modulus(division remainder) Use % to determine if a number is divisible by another, it gives the remander value i.e:

```javascript
if(randomNum % 7 == 0)
// Do Something
```

<h4>Strings</h4>
- A string can contain an unlimited amount of characters and has methods attached to it.
- Strings can concatenated with + "Hello " + "world!"; // = "Hello world!" Although issues with Type Coersion can occur
- string.concat - To avoid Type Coersion concat with string1.concat(string1)
- string.charAt
- string.slice
- string.split
- string.indexOf
- string.lastIndexOf
- string.substring
- string.replace
- string.toLowerCase
- string.toUpperCase

<h4>Objects</h4>
- Objects are an unordered list of name/value pairs. Names are strings and values can be any type including other objects
- Objects are initialized using the 'new' namespace i.e 'var obj = new Object()' or using Literal notation i.e. 'var obj = {}';
- For code consistancy use capitals for the name of a constructor of an Object but use lower case for Instance names. i.e. var car = new Car();
- In JavaScript, all objects are passed by reference. When you make a change to a reference to an object, you change the actual object. Primitive types are passed by value. see http://jsfiddle.net/sjmcpherso/YgEjv/
- When you change the value of a prototype property it also changes across all existing objects derived from it. This is called Prototypal Inheritance.
- Using delete will destroy variables and properties, making them undefined when you try to access them. Though if you call delete on an item in an array, the array's .length is unaffected.
- hasOwnProperty - This is used to determine whether a property is part of the prototype chain or not. This is useful in checking if a native prototype is supported and for use in a 'for in' loop to avoid errors from extending the native prototype
 
```javascript
// Poisoning Object.prototype
Object.prototype.bar = 1;
var foo = {goo: undefined};

foo.bar; // 1
'bar' in foo; // true

foo.hasOwnProperty('bar'); // false
foo.hasOwnProperty('goo'); // true
```

<h4>Undefined</h4>
- Undefined is the value of a variable which has been initialized but not assigned a type or a value. i.e. var a; 'typeof a' will equal undefined.
- A value can also be set to undefinend i.e. a = undefined; 
- Undefined is a 'Falsy' value

<h4>Null</h4>
- Null is a primative value that can be used by developers to set an object to no value.
```javascript
alert(typeof null); //alerts object (A bug in ECMAScript it should alert '"null') 
var a = null;
alert(a); //alerts null
alert(typeof a); //alerts object
```

<h4>Functions</h4>
- 'function a(){}' is essentially shorthand for 'var a = function a(){}'; though will cause different results based on the differences between Function & Variable Hoisting.  See http://jsfiddle.net/sjmcpherso/qHBUY/
- The Arguments Object - is a system object resembling an array for accessing the variables past to an function. It has the length property but no Array methods i.e

```javascript
testFunc(1,"go");
function testFunc(){
//argument.length = 2;
//argument[1] = "go";
}
```

- Add an extra (); at the end “(function () {})();“ makes it a Self Executing(Imediately Invoking) Anonymous Function which would run imediately
- When using optional parameters place into an options hash. function circle(x,y,radius,options) { options = options || {};}
- Functions inherit the object prototype therefore methods and properties can be assigned to them.
- JavaScript Scope, Function-Level & Hoisting: http://coding.smashingmagazine.com/2009/08/01/what-you-need-to-know-about-javascript-scope/, http://www.adequatelygood.com/JavaScript-Scoping-and-Hoisting.html
- Initializing a variable in a Function will mean that it is only available to operations inside this function. Functions are the only place where a new scope is created.
- Inner(or Nested) functions can refer to the variables present in their outer enclosing functions even after their parent functions have already executed. This is called Closure. See https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Closures, http://jsfiddle.net/sjmcpherso/ByJfv/ 
- function.call vs function.apply - .apply and .call do the same thing, but .apply uses an array containing arguments for the target method as the second parameter.

<h3>Type Coercion</h3>
- Due to JS being a loosely typed programming language, JS uses type coersion to evaluate equations made up of different value types rather than throwing an error like a Strongly-Typed language would.
- When JavaScript is adding values it immediately begins type coercing all value into strings that proceed a string i.e. '1' + 2 +  3 ; // Equals '123',  3  + 2 + '1'; // Equals '51',  3  + 2 +  1 ; // Equals 6.
- When using other operators(-,*,/,%,<,>) JavaScript type coerces values in to numbers i.e. true - '1'; //Equals 0, 'true' * 1 //Equals NaN
- Automatic Type Conversion in JS means that varibles if different types can be compared i.e

```javascript
false == 0 //true
"5" == 5 //true
!"" //true
null == undefined //true
```

- For cases where you do not want automatic type conversion to occur use '===' or '!==' i.e

```javascript
"5" === 5 //false
false !== 0 //true
```

<h3>Operators</h3>
- Type Coercion can affect comparison of values with Equal & Non-equal operators so its recommended to use '===' and '!==' for strict comparison. See http://jsfiddle.net/sjmcpherso/S6W22/
- '&&' Can be used to avoid null references, if the first operand is Truthy then the result is the second operand else result is the first. 
- '||' As above but if the first operand is Truthy then the result is the first operand i.e. var inputVal = input || ""; Think of the second operated as of setting a default value.

```javascript
  var inputVal = input && "";
  //Is the same as
  var inputVal;
  if(input == true)
    inputVal = "";
  else
    inputVal = input
  
  //Where as
  var inputVal = input || "";
  //Is the same as
  if(input == true)
    inputVal = input;
  else
    inputVal = "";
```

- If Statements can be written in a number of ways e.g:

```javascript
//Longhand
var big;
if (x > 10) {
    big = true;
}
else {
    big = false;
}
//Shorthand
var big = (x > 10) ? true : false;
//Also Will Work
var big = (x > 10);
```

<h3>Iteration VS Enumeration </h3>
- iteration - the for statement 
- enumeration - the for in statement enumeration order is not guaranteed 
- enumeration order is not guaranteed see the follow example:
```javascript
var obj:Object = {};
obj.name = "Manish Jethani";
obj.city = "Copenhagen";
obj.os = "Mac OS X 10.4";
for (var p:* in obj)
    trace(p + ": " + obj[p]);
//The above can print name, city, and os inA ANY order. 
```

    
<h3>System Objects</h3>
<h4>The Math Object</h4>
- Math object used for more complex math functions
- The Math Object has a number of constants: Math.E, Math.PI etc and a number methods the most useful below:
- Math.floor(x) - Round a number downward to its nearest integer. Best used to take the integer part of a number.
- Math.ceil(x) - As above but rounds Upward to the nearest integer.
- Math.random - Returns a random number between 0 and 1. Math.floor((Math.random()*100)+1) returns a number between 1 & 100.
- Math.max(x,y,z,...,n) - Returns the highest value, use Math.max.apply(null, array) to get the highest value of a numeric array.
- Math.min(x,y,z,...,n) - As above but returns the lowest value
- The other Math methods are Math.abs(x), Math.acos(x), Math.asin(x), Math.atan(x), Math.atan2(y,x), Math.cos(x), Math.exp(x), Math.log(x), Math.pow(x,y), Math.sin(x), Math.sqrt(x), Math.tan(x)

<h4>The Array Object</h4>
- Arrays can be initialized via 'var arr = []' or 'var arr = new Array()' and are objects with extra properties i.e. length, sort and the methods below
- Array length is the value 1 higher than the array's subscript.
- Use 'value instanceof Array' or 'value.contructor === Array' to determine if Array
- array1.concat(array2,array3,...,arrayX) - Joins two or more arrays, and returns a copy of the joined arrays
- array.indexOf(item,start) - IE9+ Search the array for an element and returns its position
- array.join(separator) -	Joins all elements of an array into a string
- array.lastIndexOf(item,start) - IE9+ Search the array for an element, starting at the end, and returns its position
- array.pop() -	Removes the last element of an array, and returns that element
- array.push(item1, item2, ..., itemX) - Adds new elements to the end of an array, and returns the new length
- array.reverse() -	Reverses the order of the elements in an array
- array.shift() -	Removes the first element of an array, and returns that element
- array.slice(start, end) -	Selects a part of an array, and returns the new array
- array.sort(sortfunction) - Sorts the elements of an array
- array.splice(index,howmany,item1,.....,itemX) -	Adds/Removes elements from an array at a specific position i.e. array.splice(index,1) will remove 1 element at index. Distinct from "delete array[index]" which just sets the deleted index to undefined and therefore does not alter the length 
- array.toString() - Converts an array to a string, and returns the result, values are seperated by a comma
- array.unshift(item1,item2, ..., itemX) - IE9+	Adds new elements to the beginning of an array, and returns the new length
- array.map(callback, object) - creates an array of the results of a provided function on each item in the array.
- array.reduce()
- Avoid using the 'for-in' loop to iterate through an array, as properties and extending Array.prototype will also be iterated. i.e
- The correct way to clear an Array is arr.length = 0 not arr = [] as often used


```javascript
	Array.prototype.foo = "foo!";
	var array = ['a', 'b', 'c'];
	array.total = "10";
	
	for (var i in array) {
	  alert(array[i]);
	}
	//The above code will alert, "a", "b", "c","foo!" and 10.
```
 
<h4>The Document Object</h4>
- Where the DOM is accessed
- A full list of the Document Objects Methods & Properties https://developer.mozilla.org/en-US/docs/Web/API/document

<h4>The Window Object</h4>
- The window object represents the browser window and creates another window object for each frame/iframe. It holds a number of important properties and objects i.e. The document object, the history object and the location object.
- window.innerWidth/innerHeight - Read-only property which represents the viewport dimensions of the browser window. Helpful when debugging responsive screen sizes. IE9+ only

<h4>The Image Object</h4>
- img.complete - Read-only boolean property to determine if image is loaded.
- img.naturalWidth/naturalHeight - Read-only property which represents the original(unmanipulated by CSS/JS) size of the image. Only available after image load. IE9+

<h4>The XMLHttpRequest(XHR) Object</h4>
- XMLHttpRequest object (IE7+) Object can use 'ActiveXObject("Microsoft.XMLHTTP")' for IE6 IE5.
- GET vs POST - GET is simpler and faster than POST and therefore used in AJAX enviroments. POST offers a more secure option.
- .open(method,url,asyc,user,password) - Intializes the request. 'method' specifies the type of request("GET", "POST", "PUT" or "DELETE"), 'url' the URL(Location of file on server). Optional parameters 'asyc'(default: true) if the request should be handled asynchronously or not and user & password strings for authentication purposes.
- .send(string) - Sends the request, the string value is only used in POST requests.
- .onreadystatechange - Property that stores a function which is called each time the readyState property changes.
- .readyState - Property for the status of the XMLHTTPRequest - 0:request not initialized,1:server connection,2:request received,3:processing request, 4:request complete.
- .status - Property for that result of the XMLHttpRequest - 200: 'OK', 404: 'Page not found'
- .responseText/.responseXML - Property to get the response from server.
- Modern browsers support cross-site requests by implementing the web applications working group's Access Control for Cross-Site Requests standard.  As long as the server is configured to allow requests from your web application's origin, XMLHttpRequest will work.  Otherwise, an INVALID_ACCESS_ERR exception is thrown.

<h4>The Date Object</h4>
- <code>var currentDateTime = Date()</code> sets the current milliseconds since Epoch(1/1/1970 00:00:00) which then needs to put through a date formatter to convert to a human readable date. 
- Their are 4 ways of initiating a date value with the new Date() constructor.

```javascript
var currentDate = new Date(); //Current Date Time
var epoch = new Date(0); //Milliseconds since Epoch i.e. new Date(86400000) + 1 day
var date = new Date("January 13, 2015 12:30:00"); //Datestring
var date = new Date(2015, 0, 13, 12, 30, 0, 0); //year, month, day, hour, minute, second, and millisecond, in that order. NOTE the month reference is from 0 so in most cases you will need to decrease month variable by 1
```

<h3>Timers & Timeouts</h3>
- setTimeout(function, delay in milliseconds);

<h3>JavaScript Selectors</h3>
- element.getElementById(id) - (full support)
- element.getElementsByName(name) - returns a NodeList(not an array see ) matching the name attribute although in IE & Opera will also return elements that have an id attribute with the specified value. Although a NodeList doesnt not have the methods. (full support) 
- element.getElementsByTagName(tag) - returns a NodeList matching the tag name.  (full support)
- element.querySelector(CSS selectors) - 'CSS selectors' is a string of one or more CSS selectors. Returns null if no matches are found; otherwise, it returns the first matching element. Pseudo selectors are NOT supported. IE8+
- element.querySelectorAll(CSS selectors) - returns a NodeList(not an array) of all elements selected. Pseudo selectors are supported. i.e. var el = document.body.querySelector("style[type='text/css]'], style:not([type])"); (IE8+ for CSS2 selectors, IE9+ for CSS3 selectors)
- element.getElementsByClassName(class) - IE9+ i.e. document.getElementsByClassName('red test') = Get all elements that have both the 'red' and 'test' classes.
- You can also chain selectors i.e. document.getElementById('main').getElementsByClassName('test') although its better practise to cache elements for reuse i.e. var d = document;var main = d.getElementById('main');var testList = main.getElementsByClassName('test');
- elementNodeReference.childNodes - gets a NodeList of direct children. (full support)
- element.nextSibling - gets the next element in the parent elements child node list. (full support)
- element.parentElement - gets the parent element. (full support)

<h4>The NodeList Object</h4>
- What is a NodeList Object - it is a collection of Nodes obtained via element.childNodes, element.querySelectorAll etc but is NOT an Array as it does not have all the properties and methods associated with Array.prototype, it does have the property length which allows you to iterate over it with a standard For-Loop.
- Converting a NodeList to an Array - var nodesArray = Array.prototype.slice.call(document.querySelectorAll("div"));

<h3>JSON</h3>
- JSON without " is evaluated as a object literal and JSON.Parse will not accept
- JSONP stands for JSON with padding. The padding is a callback function that is used to wrap the data returned from the server. The reason for its existence is to get around browser's same-origin restriction against cross domain requests.

<h3>JavaScript Events</h3>
- Use Event Delegation instead of individual event listeners (read more http://davidwalsh.name/event-delegate) e.g. 

```javascript
//jQuery 1.4.3+ 
$("table").delegate("td", "click", function(){});
//jQuery 1.7+
$("table").on("click", "td", function() {});
//Vanilla JS
document.querySelectorAll('table').addEventListener('click', function(e) {
        // e.target is the clicked element!
        if(e.target && e.target.tagName == 'td') {}
});
```

- return false - Adding this to your event handler will prevent the default event from occuring, NOTE if used in a jQuery event handler it will also prevent the event from bubbling up, effectively simulating jQuery funcitions e.preventDefault() & e.stopPropagation().
- Event Bubbling when a nested element triggers the parents event handler. The follow code can be used to prevent bubbling event.stopPropagation ? event.stopPropagation() : (event.cancelBubble=true) //event.cancelBubble used for IE<9
- addEventListener(event,function,useCapture) IE9+ allows you to have multiple events call throughout code without them being overwritten like 'element.onclick = function(){}' would deprecietes attachEvent(event,function);
- attachEvent(event,function) depreciated version of AddEventListener used in <IE9, note the value of "this" will be a reference to the window object instead of the element on which it was fired.
- Use something like the below as a cross browser AddEventListener override

```javascript
function AddEvent(html_element, event_name, event_function) 
{       
   if(html_element.attachEvent) //Internet Explorer
      html_element.attachEvent("on" + event_name, function() {event_function.call(html_element);}); 
   else if(html_element.addEventListener) //Firefox & company
      html_element.addEventListener(event_name, event_function, false); //don't need the 'call' trick because in FF everything already works in the right way          
} 
```

<h3>Prototypal Inheritance</h3>
- Distinct from Class Inheritance, where an object inherits properties from an object assigned to it.
- Extending native prototypes - To use newer features added to JS you will often need to back port native prototypes for older browsers this breaks this breaks encapsulation e.g Array.ForEach

<h3>Constructors</h3>
- The 'new' keyword signify's the use of a constructor
- 'instanceof' can be used to determine if the variable is an instance of a constructor i.e. var a = new Person(); if(a instanceof Person){//Will run}

<h3>Debugging</h3>
- console.log() - Used to output values to the console window.
- console.table() - (Firefox, Chrome Only) Is used to output tabular data to the console window e.g JSON & Array Objects, to display only certain fields you can use "console.table(languages, ["name", "paradigm"]);" 
- console.count(label) - Outputs the number times the line of code has been invoked with an optional string as a label
- console.assert(expression, message) - Will display the message if the expression in the first argument is false
- console.time(message)/console.timeEnd(message) - Time the performance of code between .time() & .timeEnd() statements
- NOTE: use of the Console object will break <IE10 but NOT while the IE Developer Tools window is open.

<h3>Design Patterns</h3>
- Module pattern is a way of organizing and encapsulating code via a closure. It allows you to create public/private functions and vars inside an object (the module). It lessens the likelihood of naming conflicts and unintended interactions with other functions/vars on the page. Modules should work independently and be easily extensible. Using modules enables to write widgets and plugins that interact with each other.

```javascript
//Addy Osmani's example from his book Essential JavaScript Design Datterns http://addyosmani.com/resources/essentialjsdesignpatterns/book/#modulepatternjavascript
var myModulePattern = (function () {
  var myPrivateVar, myPrivateMethod;
  myPrivateVar = 0; // A private counter variable
  myPrivateMethod = function( foo ) {console.log( foo );};  // A private function which logs any arguments
  return {
    myPublicVar: "foo",  // A public variable
    myPublicFunction: function( bar ) {// A public function utilizing privates
      myPrivateVar++;  // Increment our private counter
        myPrivateMethod( bar ); // Call our private method using bar
    }
  };
})(); 
```
- Singleton - a pattern for a class which initializes a single object over the lifetime of a program.

```javascript
//Addy Osmani's example which expands on the Module Pattern
var mySingleton = (function () {
  var instance; // Instance stores a reference to the Singleton
  function init() {    // Private methods and variables
    var privateVariable = "Im also private";
    function privateMethod(){console.log( "I am private" );}
    return {      // Public methods and variables
      publicMethod: function () {console.log( "The public can see me!" );},
      publicProperty: "I am also public"
    };
  };
  return {
    // Get the Singleton instance if one exists or create one if it doesn't
    getInstance: function () {
      if ( !instance ){instance = init();}
      return instance;
    }
   };
})();
```


<h3>RequestAnimationFrame</h3>
 - CSS should be used for simple transitions & animations i.e. button rollovers, dropdown menus etc
 - Using RequestAnimationFrame over other techniques the browser optimizes it with hardware acceleration to make them smoother.
 - Animations in inactive tabs will stop, utilizing CPU elsewhere
 - It helps with battery life


<h3>JavaScript Promises</h3>
```javascript
function simplePromise() {
  return {
    then: function(callback) {
      var value = 42;
      callback(value);
    }
  };
}

simplePromise().then(function(result) {
    log("got a result", result);
});
```
- Promise Libraries: Q, when, WinJS, RSVP.js
- JavaScript Promise API (Chrome, Firefox, Opera Only)

<h3>Other JavaScript APIs</h3>
- navigator.getUserMedia() - For capturing Audio/Video client side (limited browser capatibility)
- localStorage/sessionStorage – Clientside browser storage (localStorage is Persistant) limited to 5MB per domain IE8+
- Full Screen API with requestFullScreen
- animationstart, animationiteration, animationend allow JavaScript control over CSS3 Animations. IE10+ & prefixes required for most browsers through:
```javascript
var pfx = ["webkit", "moz", "MS", "o", ""];
function PrefixedEvent(element, type, callback) {
	for (var p = 0; p < pfx.length; p++) {
		if (!pfx[p]) type = type.toLowerCase();
		element.addEventListener(pfx[p]+type, callback, false);
	}
}
PrefixedEvent(anim, "AnimationStart", AnimationListener);
```
- Web Workers - An API for defining background scripts to run concurrently from the main thread handling user interactions. IE10+ See http://www.html5rocks.com/en/tutorials/workers/basics/
- WebSockets - Allows the browser to open 2 way communication with the server this allows real time communication rather than relying on polling. (More Info  https://developer.mozilla.org/en-US/docs/WebSockets/Writing_WebSocket_client_applications)
- Server Side Events(SSEs) - 
- Page Visibility - Using document.hidden and/or document.visibilityState you can determine whether the page is in the active tab of the browser and whether the browser window is minified or not

```javascript
function handleVisibilityChange() {
  if (document.hidden)
    pauseSimulation();
  else
    startSimulation();
}

document.addEventListener("visibilitychange", handleVisibilityChange, false);
```

- Web Notifications - Allows you to send notifications to the user outside of the browser window. The user must allow permission for your application to use them. The look is largely based on the browser and compatibility is limited
- Application Cache - Allows pages and resources to be cached for offline usage
- Network Information - Can be used to determine what internet connection is being used I.e wifi, cellular etc
- Vibration - Trigger vibration in mobile devices
- Battery - Detect if the battery is low on the device
- classList - A performance optimized API to manipulate classes on elements. div.classList.add("class"); IE10+ 


<h3>JavaScript Frameworks</h3>
- JavaScript Frameworks which add content to the DOM on page load eg. AngularJS, Backbone JS etc have problems with Search Engines(https://developers.google.com/webmasters/ajax-crawling/) they are therefore best utilized in CRUD apps (Create, Read, Update, Delete). With extra configuration pages can be recreted as HTML Snapshots & hosted on alternative URL's to index the content.


<h2>ECMAScript 6</h2>
- This the next version of the JS standard, code-named "Harmony" or "ES.next. Very limited support for most. Browser Support list found at http://kangax.github.io/es5-compat-table/es6/
- Const - Varible declaration for Constants acts in the same way as "var" but is Read-Only. IE11+, Safari 6+
- Let - Block-level variable declaration acts in the same way as "var" but scope is at the block-level rather than the whole function. i.e. block-level includes for loops, if/cases statement etc
- Default Parameter Values - Will allow you to set default values for parameters that are undefined. i.e.
```javascript
function Point(x = 0, y = 0) {
   this.x = x;
   this.y = y;
}

var p = new Point(); // => { 0, 0 }
```
- The Spread Operator - Allows parameters to be summarised in places where multiple arguments or elements are expected
```javascript
function add(...values) {}
add(2, 5, 3);

var a = [0, 1, 2];
var b = [3, 4, 5];

a.push(...b); // => [0, 1, 2, 3, 4, 5]
```

- Classes - A clean simple declarative syntax for defining object prototypes and inheritance chains.
- Generators - A type of function that can be stopped during execution to allow other code to run and then resumed once or many times.


<h2>jQuery Specific Coding Tips</h2>
- The jQuery '$' is just a function that returns jQuery's 'init' function
- $.fn is just shorthand for the jQuery Prototype object i.e. jQuery.fn = jQuery.prototype
- Get the version of jQuery used on a webpage via $.fn.jquery
- Anonymous Functions “$(document).ready(function() {“ & “$(function(){“ are exactly the same where code is executed after DOM is loaded 
- “(function ($){}(jQuery)” Passes the jQuery object as a parameter so that “$” refers to “jQuery”. In general widgets would be contained in a Immediate invoking function but initated by a global Controller. Often a single ";" is placed at the front of a anonymous function to stop syntax errors when JavaScript files are combined & minified.
- Of course if your following best practises and adding your javascript files before the closing body tag you don't need $(document).ready as the DOM will have already loaded.
- To create a jQuery plugin use (function($){ $.fn.yourPluginName = function(){ /* Your code */ return this; }; })(jQuery);
- As of jQuery 1.7+ ".on()" depreciates .live(), .delegate() and .bind(). To remove events bound with .oconsn() use .off()
- From >V1.6 .attr() returns the visable value and the new .prop() returns the underlying property i.e. &lt;input id="cb" type="checkbox" checked="checked"&gt; .attr(“checked”) “returns” checked whereas .prop(“checked”) returns “true” .prop() is the preferred method for returning properties from 1.6 onwards
- jQuery methods should chain:

```javascript
$.fn.enumerate = function() {
        return this; //Add to make the method chainable.
};
//Because of using "return this", it's chainable!
$("li").enumerate().css( "color", "red" );
```

- "$.grep" Finds the elements of an array which satisfy a filter function. The original array is not affected. arr = jQuery.grep(arr, function (a) { return a != 9; }) Useful as JS .filter(callback[, thisObject]) method is only IE9+
- Check if selected objects exist if($("#element").length){} as '0' is Falsy or if($("#element").is('*')) {}
- The [] index will "dereference" a jQuery selector into a raw DOM object: $("#id")[0].style.color='#000000'; i.e. $("#id")[0] is the same as getElementById("id");
- $("form").serialize() will return a string of all elements inside the form: "name=value&amp;name2=value2" etc.
- $("span", this) is the same as $(this).find('span')
- Pass raw DOM objects as arguments: $(document.getElementById("p1")).prepend(document.getElementById("p2"));
- Use .stop() to stop animations on the selected element. Useful to stop queued animations triggering well after the event.
- .hover() is shorthand for mouseenter mouseleave events:

```javascript
$("td").hover(
  function () {
    $(this).addClass("hover");
  },
  function () {
    $(this).removeClass("hover");
  }
);
```
- $('body').disableSelection(); (jquery-ui.js) prevents selection of text.
-  $("a[href='" + document.location.pathname + "']").addClass("current"); Use the filename to highlight the current page on a nav
- In firebug you can load the latest version of jQuery via the Command Line using "include('jquery')". Otherwise you can add to the Console something like this:

```javascript
var jq = document.createElement('script');
jq.src = "https://ajax.googleapis.com/ajax/libs/jquery/1/jquery.min.js";
document.getElementsByTagName('head')[0].appendChild(jq);
// ... give time for script to load, then type.
jQuery.noConflict();
```

<h2>JavaScript Performance</h2>
- Avoid using jQuery when unnessary. jQuery is a broad library offering new & additional functionality covering selectors, animations, events & Ajax, including polyfills across lecacy browsers that may not be need. This quite often adds alot of bloat to your JS download. Also runtime performance can be affected as extra methods & properties are often added to native JS.
- Minifying JavaScript removes whitespace/linebreaks and shortends variables, reducing file size.
- 'script' tags block parallel downloads, put them last so other resources can be downloaded first
- Defer Parsing of scripts that are not called at startup.
- Async Loading via Lab.js or the 'async' attribute for the script tag (IE9 & below don’t support).
- Avoid excess DOM manipulation. Don't append on every iteration as below:

```javascript
var list = document.querySelector('ul');
ajaxResult.items.forEach(function(item) {
        var li = document.createElement('li');
        li.innerHTML = item.text;
        list.apppendChild(li);
});
```

Instead place the LI into a fragment and add to the DOM in one go.

```javascript
var frag = document.createDocumentFragment();
ajaxResult.items.forEach(function(item) {
        var li = document.createElement('li');
        li.innerHTML = item.text;
        frag.appendChild(li);
});
document.querySelector('ul').appendChild(frag);
```

- Cache AJAX results to reduce unnessary requests. Use flags to determine whether to request new data and/or periodical clearing of the cache if data is updated externally. i.e. 
- Where possible use CSS animations, browsers take advantage of hardware acceleration.
- Debounce when using scroll & resize events, use setTimeout/setInterval to limit excessive triggering of event, this is called Debouncing.
- Avoid using an anonymous function body to process your event code as in the first case below, as this code would be duplicated multiple times due to the for loop, use the 2nd case.

```javascript
for(i=0 ; i<arrElements.length ; i++){
  arrElements[i].addEventListener("click", function(e){var field = i;}, false);
}
 
for(i=0 ; i<arrElements.length ; i++){
  arrElements[i].addEventListener("click", function(e){clickEvent(i)}, false);
}
```
- .offset() used to get/set the x/y position of an element relative to the document. i.e. $(selector).offset().top;
- .position() same as above but relative to the parent.
- Cache elements when using selectors var elem = getElementByTagName('a');
- Avoid using the eval() function as well as potential security implications it causes code executed by the eval function to run at least twice as slow. There maybe times when it is necessary i.e. when executing code inside JSON.
- For loops can create bottlenecks simple optimizations like caching object lookups can help ie.

```javascript
//Bad
var total;
for (var i = 0; i < values.length; i++){
    myFramework.utils.addText(value[i]); 
    total += value[i];
}
//Optimized    
var total, amount, utilsMyFramework = myFramework.utils; //Declare reused variables outside of for loop, cache object look
for (var i = 0, l = values.length; i < l; i++){//Cache array length propery, being recalculated on each cycle
    amount = value[i]; //Cache resused variable
    utilsMyFramework.addText(amount); //Cache object lookup     
    total += value[i];
}    
```

<h2>Helpful JavaScript/jQuery Libraries & Scripts</h2>
- jquery.metadata.js takes attribute metadata from html attributes and converts into JSON.
- jQuery-contextMenu.js For creating a custom Context menu (right-click menu)
- JSX a statically typed, object oriented programming language that compiles to JS, which offers performance and error checking improvements.
- Equalize.js jQuery plugin for equalizing the height or width of sibling elements
- ajax-cache.js - Provides a AJAX response caching object so as to limit unnessary requests. https://code.google.com/p/ajax-cache/
- Underscore.js - Utilty functions uncluding map, select, javascript templating
- CoffeeScript - Programming language that transcompiles to JavaScript inspired by Ruby
- Adapt.js is a lightweight JavaScript file that determines which CSS file to load before the browser renders a page. If the browser tilts or resizes, Adapt.js simply checks its width, and serves only the CSS that is needed, when it is needed.
- htm5shiv.js/html5shim.js - Allows the styling of HTML5 Elements such as Section, Article, Header in <IE9.
- Reactjs a JS library developed by Facebook which alters Virtual DOM in the form of components to make changes to the View. This improves performance over changes to the Actual DOM. 
- Requirejs helps load script's in the right order, you can combine scripts via the RequireJS optimizer it also allows you to load scripts after the page has loaded (Just in time)
- Respond.js – Adds browsers support to min-max css media queries for ie6-ie8. Can be added in with Modernizr
- selectivizr.js -  Adds support for CSS3 selectors (:first-child,:last-child,:nth-child) for ie6-ie8 can cause conflicts with respond.js must be placed before.
- Modernizr.js - Adds classes to the html element based on feature tests and includes HTML5 Shiv. Allows you to target parts of your CSS and JavaScript based on the features supported by a browser. Offers cross browser support for CSS3 TransitionEnd Event.
- hoverIntent replicates jQuery's shorthand hover method but will only call mouseover/mouseleave when mouse movement has slowed reducing excessive calls to these events.
- Handlebars.js - Lightweight, library to build semantic templates i.e.
- Bower - A command line package manager to automate searching and downloading front-end development tools.

```HTML
<div class="entry">
  <h1>{{title}}</h1>
  <div class="body">
    {{body}}
  </div>
</div>
```

<h2>Node & NPM</h2>

<h3>Dependency Management</h3>
- Create a package.json in your projects route directory with "npm init" to document your dependencies

```javascript
   npm install %package% --save
   npm install %package% --save-dev
```



<h2>Source Control</h2>
- echo "" > .hgignore

