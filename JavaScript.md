<h1>General JavaScript Coding Tips</h2>

<h2>What is JavaScript</h2>
- JavaScript commonly abbreviated to just JS was initially called LiveScript, JS is built from ECMAScript standards and its current version is v5 although modern web browser have started implementing many ECMAScript v6 features.


<h2>JavaScript Execution</h2>
- JS is a scripted language rather than a compiled language like C#, C++, Java etc. This means it is executed line by line by its host environment(commonly the web browser) at run time. 

<h2>JavaScript Data Types</h2>
- There are 7 identifiable data types in JavaScript: number, string, boolean, object, function, undefined and null. They can be determined by using the 'typeof' operator. Although a bug exists when using typeof with 'null' values as it will return 'object'.

```javascript
	var theType = typeof false //'theType' would equal 'boolean'.
	var theType = typeof ""; //'theType' would equal 'string'.
	var theType = typeof null; //'theType' would equal 'undefined' (which is a bug).
```

<h3>The Data Types</h3>
<h4>Boolean</h4>
- Only 2 Boolean values exist: true & false, although values of other types are also deemed either Truthy or Falsey.
- "Falsey" values are false, null ,"" ,0 , undefined ,NaN. All other values including objects are "Truthy"
- Truthy & Falsy variables can be toggled by equating a single negation of itself i.e true = !true //Will equal false
- Truthy & Falsy values can be converted into real Booleans by using double negation '!!' i.e '!!0' Will equal false !!{} will equal true. This can be helpful when comparing truthy/falsy value as strict equality can be used i.e.

```javascript
var a = {}
a == true //false, using Loose Equaition can cause inconsistant results, because of Type Coercion
a === true //false, using Strict Equation values must be the same Type
!!a === true //true, correct check for truthy value
```



<h4>Numbers</h4>
- Only 1 number type (i.e no integer) which is represented as a 64bit floating point also known as Double.
- Has problems mapping to common arithmetic I.e var cur = 0.1 + 0.2; Will equal 0.3000000000004 so use parseFloat(0.1 + 0.2).toFixed(2) for currency calculations.
- isNaN() checks if value is NaN(Not a Number) which is achieved when JS is unsuccessful in converting a value to a number. 
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

- Add an extra (); at the end “(function () {})();“ or “(function () {}());“ makes it a Self Executing(Immediately Invoking) Anonymous Function which would run imediately
- When using optional parameters place into an options hash. function circle(x,y,radius,options) { options = options || {};} //if options parameter is undefined set options to an empt object
- Functions inherit the object prototype therefore methods and properties can be assigned to them.
- JavaScript Scope, Function-Level & Hoisting: http://coding.smashingmagazine.com/2009/08/01/what-you-need-to-know-about-javascript-scope/, http://www.adequatelygood.com/JavaScript-Scoping-and-Hoisting.html
- Initializing a variable in a Function will mean that it is only available to operations inside this function. Functions are the only place where a new scope is created.
- Inner(or Nested) functions can refer to the variables present in their outer enclosing functions even after their parent functions have already executed. This is called Closure. See https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Closures, http://jsfiddle.net/sjmcpherso/ByJfv/ 
- function.call vs function.apply - .apply and .call do the same thing, but .apply uses an array containing arguments for the target method as the second parameter.


####Primative Values
- The Data types number, boolean, null and undefined are Primative values meaning they do not have methods associated with them. Whereas objects and functions do. String's when not using the 'new' keyword are classed as Primitives although they are automatically converted to an object when using String object methods.

###Variables
#####Dynamic Typed
- JavaScript is a Dynamically Typed language, as it is not compiled, there is no Static Type Checking and variables are not initialised with a type at Runtime. JS therefore must deal with Type errors differently to Static Type languages like C#, C++, Java etc. i.e. see Type Coercion

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
- JavaScript uses Function scoping rather than Block-level scoping i.e. if you declare a variable inside a "for" loop or "if" statement it will be accessable outside that block but not outside its function.

#####Variable Hoisting
- No matter where you declare a variable and what you set it to, the declaration will moved to the top of its scope(i.e its function) and assigned 'undefined'. This is called Variable Hoisting, so its good practise to always declare your variables at the top of the scope. See http://jsfiddle.net/sjmcpherso/qHBUY/

<h4>Type Coercion</h4>
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

<h3>Loops</h3>

<h4>For Loop</h4>
```javascript
for (var i=startvalue; i<=endvalue; incrementfactor){ 
  //Your code here
}
```

<h4>While Loop</h4>
```javascript
while(i<=endvalue){ 
//Your code here
}
```
- Note: forgetting to increase the variable in the condition will mean the loop will never end and crash the browser.

<h4>Do While Loop</h4>
```javascript
do{ 
//Your code here
} while (i < endvalue);
```
- Note: forgetting to increase the variable in the condition will mean the loop will never end and crash the browser.


<h4>For Each...in Loop (Depreciated)</h4>
- Not to be confused with 'array.forEach() or map.forEach()' which cannot use 'break' or 'continue' functions.
```javascript
for each (variable in object) {
  statement
}
```

<h4>For In Loop (ES6)</h4>
- Iterates an object, in arbitrary order, outputing property <strong>name</strong>
```javascript
	for (property in object) {...
	}
```
- Note: for...in should not be used to iterate over an Array where the index order is important.
- If you only want to consider properties attached to the object/array itself, and not its prototypes, use getOwnPropertyNames() or perform a hasOwnProperty() i.e:
```javascript
	for (var key in obj) {
	  if (obj.hasOwnProperty(key)) {/iterate all the properties in an object & ignores properties attached via its prototype
	    console.log(key + " -> " + obj[key]); 
	  }
	}
```


<h4>For Of Loop (ES6)</h4>
- Iterates objects (including Array, Map, Set, arguments), outputing property <strong>value</strong>
```javascript
	for (value of object) {...
	}
```

break and continue.

 - <strong>Array ForEach</strong>
```javascript
arr.forEach(callback[, thisArg])

[2, 5, , 9].forEach(function(element, index, array) {});
```


<h4>Iteration VS Enumeration </h4>
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

<h3>URI & Parameters</h3>
 - <strong>encodeURIComponent(string)</strong>

<h3>Strict mode vs Non-strict mode</h3>
- To set Strict Mode "use strict" at the beginning of a script or for mixed mode it can be added at the function level.
- Support is for IE9+
- Strict mode helps development by causing potentially problematic syntax to error.
- Note: Becareful with concatenation of scripts. If a script level Strict mode file is concatenated with a Non-strict mode file both will be forced into Strict mode. 

<h4>Not Allowed in Strict Mode</h4>
- Undeclared variables - i.e. "use strict"; x = 3; // Will error "ReferenceError: x is not defined"
- Deleting a variable or function - i.e. "use strict"; delete arg; //Will error "Delete of an unqualified identifier in strict mode."
- Defining a property twice - i.e "use strict"; var x = {p1:10, p1:20}; //Will error Duplicate data property in object literal not allowed in strict mode
- Duplicate parameters - i.e. "use strict";function x(p1, p1) {};
- Writing to read-only or get-only property
- Some specified variables names using reserved words. e.g arguments, eval
- In standard function calls, the 'this' value was the global object. In strict mode, it is now undefined.
- Most usage of eval 

<h2>System Objects</h2>
<h3>The Math Object</h3>
- Math object used for more complex math functions
- The Math Object has a number of constants: Math.E, Math.PI etc and a number methods the most useful below:
- Math.floor(x) - Round a number downward to its nearest integer. Best used to take the integer part of a number.
- Math.ceil(x) - As above but rounds Upward to the nearest integer.
- Math.random - Returns a random number between 0 and 1. Math.floor((Math.random()*100)+1) returns a number between 1 & 100.
- Math.max(x,y,z,...,n) - Returns the highest value, use Math.max.apply(null, array) to get the highest value of a numeric array.
- Math.min(x,y,z,...,n) - As above but returns the lowest value
- The other Math methods are Math.abs(x), Math.acos(x), Math.asin(x), Math.atan(x), Math.atan2(y,x), Math.cos(x), Math.exp(x), Math.log(x), Math.pow(x,y), Math.sin(x), Math.sqrt(x), Math.tan(x)

<h3>The Array Object</h3>
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
 

<h3>The Window Object</h3>
- <strong>The window object</strong> represents the browser window and creates another window object for each frame/iframe. It holds a number of important properties and objects i.e. The document object, history object, navigator object and location object.
- <strong>window.innerWidth/innerHeight</strong> - Read-only property which represents the viewport dimensions of the browser window. Helpful when debugging responsive screen sizes. IE9+ only
- <strong>window.length</strong> will give you the number of iframe elmements in the current window.
- <strong>window.postMessage()</strong> - A method to allow cross-domain communication between 'frame'/'iframe' tags (IE8+) & browser Windows/Tabs (IE10+)

<h3>The Document Object</h3>
- Where the DOM is accessed
- A full list of the Document Objects Methods & Properties https://developer.mozilla.org/en-US/docs/Web/API/document

<h3>The History Object</h3>
- Contains a list of URLs visited that cannot be read, only navigated to
- window.history.forward() & window.history.back() are used to navigate to the next & previous entries
- window.history.go() is used to navigate back or forward a number of entries in the history i.e. window.history.go(-4);

<h3>The Image Object</h3>
- img.complete - Read-only boolean property to determine if image is loaded.
- img.naturalWidth/naturalHeight - Read-only property which represents the original(unmanipulated by CSS/JS) size of the image. Only available after image load. IE9+
- img.onerror

<h3>The XMLHttpRequest(XHR) Object</h3>
- XMLHttpRequest object (IE7+) Object can use 'ActiveXObject("Microsoft.XMLHTTP")' for IE6 IE5.
- GET vs POST - GET is simpler and faster than POST and therefore used in AJAX enviroments. POST offers a more secure option.
- .open(method,url,asyc,user,password) - Intializes the request. 'method' specifies the type of request("GET", "POST", "PUT" or "DELETE"), 'url' the URL(Location of file on server). Optional parameters 'asyc'(default: true) if the request should be handled asynchronously or not and user & password strings for authentication purposes.
- .send(string) - Sends the request, the string value is only used in POST requests.
- .onreadystatechange - Property that stores a function which is called each time the readyState property changes.
- .readyState - Property for the status of the XMLHTTPRequest - 0:request not initialized,1:server connection,2:request received,3:processing request, 4:request complete.
- .status - Property for that result of the XMLHttpRequest - 200: 'OK', 404: 'Page not found'
- .responseText/.responseXML - Property to get the response from server.
- Modern browsers support cross-site requests by implementing the web applications working group's Access Control for Cross-Site Requests standard.  As long as the server is configured to allow requests from your web application's origin, XMLHttpRequest will work.  Otherwise, an INVALID_ACCESS_ERR exception is thrown.

<h3>The Date Object</h3>
- <code>var currentDateTime = new Date()</code> sets a date object equavalent to the current milliseconds since Epoch(1/1/1970 00:00:00). 
- new Date().getTime() is the equavalent to Date.now(), although Date.now() is IE9+.
- Their are 4 ways of initiating a date value with the new Date() constructor.

```javascript
var currentDate = new Date(); //Current Date Time
var epoch = new Date(0); //Milliseconds since Epoch i.e. new Date(86400000) + 1 day
var date = new Date("January 13, 2015 12:30:00"); //Datestring
var date = new Date(2015, 0, 13, 12, 30, 0, 0); //year, month, day, hour, minute, second, and millisecond, in that order. NOTE the month reference is from 0 so in most cases you will need to decrease month variable by 1
```

<h2>Timers & Timeouts</h2>
- setTimeout(function, delay in milliseconds);

<h2>Threading in JavaScript</h2>
- JavaScript is regarded as single-threaded in that it can only ever execute one piece of code (thread) at a time. This means that when an asynchronous event occurs (like a mouse click, a timer firing, or an XMLHttpRequest completing) it gets queued up to be executed later if code is currently being run. This single thread is shared with JS execution and browser rendering, as JS can alter how the browser renders we do not want Race conditions to occur. 
- Web Workers a new API (IE10+) look to add multi-threading by defining background scripts that can run concurrently from the main thread.

<h2>JavaScript Selectors</h2>
- <strong>element.getElementById(id)</strong> - (full support)
- <strong>element.getElementsByName(name)</strong> - returns a NodeList(not an array) matching the name attribute although in IE & Opera will also return elements that have an id attribute with the specified value. Although a NodeList doesnt not have the methods. (full support) 
- <strong>element.getElementsByTagName(tag)</strong> - returns a NodeList matching the tag name.  (full support)
- <strong>element.querySelector(CSS selectors)</strong> - 'CSS selectors' is a string of one or more CSS selectors. Returns null if no matches are found; otherwise, it returns the first matching element. Pseudo selectors are NOT supported. IE8+
- <strong>element.querySelectorAll(CSS selectors)</strong> - returns a NodeList(not an array) of all elements selected. Pseudo selectors are supported. i.e. var el = document.body.querySelector("style[type='text/css]'], style:not([type])"); (IE8+ for CSS2 selectors, IE9+ for CSS3 selectors)
- <strong>element.getElementsByClassName(class)</strong> - returns a HTMLCollection of elements with a matching class or classes i.e. document.getElementsByClassName('red test') //Returns all elements that have both the 'red' and 'test' classes. IE9+
- <strong>Chaining Selectors</strong> - Just like with jQuery you can chain selectors i.e. document.getElementById('main').getElementsByClassName('test') although its better practise to cache elements for reuse i.e. var d = document;var main = d.getElementById('main');var testList = main.getElementsByClassName('test');
- <strong>element.children</strong> - gets a HTMLCollection of direct children. (IE9+) IE 6-8 support it, but include comment nodes.
- <strong>element.childNodes</strong> - returns a NodeList of direct children. Note: Includes text nodes. (full support)
- <strong>element.nextElementSibling/element.previousElementSibling</strong> - gets the next/previous element in the parent elements child HTMLColl. (IE10+)
- <strong>node.nextSibling/node.previousSibling</strong> - returns the next/previous node in the parent elements child node list. Note: Includes text nodes. (full support) 
- <strong>element.firstElementChild/element.lastElementChild</strong> - returns the first/last child of the element  (IE9+)
- - <strong>node.firstChild/node.lastChild</strong> - returns the first/last child node of the element. Includes text nodes. (full support) 
- <strong>element.parentElement</strong> - returns the parent element. (full support)
- <strong>ClassList API</strong> - Allows access to an elements classes and contains 4 simple methods to help manipulate them and the 'length' property. Methods are: add, remove, toggle & contains. IE10+

```JavaScript
div.classList.add("class","anotherclass");
div.classList.remove(class);
div.classList.toggle(class);// if visible is set remove it, otherwise add it
div.classList.contains("foo"); //Returns true or false
```

<h3>Incrementation</h3>

- Pre-Incrementation (++x) - Increments then returns the incremented value.
- Post-Incrementation (x++) - Returns the value, then increaments.

```JavaScript
var x = 1;
var y = x++; //returns x, then increments it. y = 1, x = 2
var z = ++x; //increments x, then returns it. z = 3, x = 3
var z = x =+ 1; //equivalent to ++x;
```

<h3>The NodeList Object</h3>
- A NodeList Object it is a read-only collection of ordered Nodes obtained via element.childNodes, element.querySelectorAll etc but is NOT an Array as it does not have all the properties and methods associated with Array.prototype, it does have the property length which allows you to iterate over it with a standard For-Loop.

<h4>Iterating over a NodeList Object</h4>
```JavaScript
var myNodeList = document.querySelectorAll( 'input[type=checkbox]' );
for (var i = 0; i < myNodeList.length; ++i) {
  var item = myNodeList[i];  // Calling myNodeList.item(i) isn't necessary in JavaScript
}
```

<h4>Converting a NodeList to an Array</h4>
- Sometimes you will need to convert to an Array to use Array methods;

```JavaScript
var NodeList = document.querySelectorAll('div'); // returns a NodeList
var ArrayVar = Array.prototype.slice.call(NodeList); // converts NodeList to Array
```


<h3>Manipulating the DOM</h3>
- DOM manipulations can affect performance so its important to limit the amount of changes to the DOM i.e. in the case of creating multiple Nodes in a Loop

```javascript
for(i=0;i<100;i++){
	var div = document.createElement('div');
	document.body.appendChild(div); //Bad DOM is Changed 100 times
}
```
```javascript
var container = document.createElement('div');
for(i=0;i<100;i++){
	var div = document.createElement('div');
	container.appendChild(div); 
}
document.body.appendChild(container); //Better DOM is changed only once
```

- <strong>document.createDocumentFragment()</strong> - DocumentFragment acts like a pseudo-DOM node, this maybe preferable to creating a container with an actual DOM node with document.createElement i.e.

```javascript
var ul = document.getElementsByTagName('ul');
var frag = document.createDocumentFragment();
for(i=0;i<100;i++){
	var li = document.createElement('li');
	frag.appendChild(li); 
}
ul[0].appendChild(frag);
```

<h2>JSON</h2>
- JSON without " is evaluated as a object literal and JSON.Parse will not accept
- JSONP stands for JSON with padding. The padding is a callback function that is used to wrap the data returned from the server. The reason for its existence is to get around browser's same-origin restriction against cross domain requests.

<h2>JavaScript Events</h2>
- <strong>addEventListener(event,function,useCapture)</strong> - IE9+ allows you to have multiple events call throughout code without them being overwritten like 'element.onclick = function(){}'
- <strong>attachEvent(event,function)</strong> - Is a depreciated version of AddEventListener used in <IE9, note the value of "this" will be a reference to the window object instead of the element on which it was fired.
- <strong>Crossbrowser addEventListener</strong> - Use something like the below as a cross browser AddEventListener override

```javascript
function AddEvent(html_element, event_name, event_function) 
{       
   if(html_element.attachEvent) //Internet Explorer
      html_element.attachEvent("on" + event_name, function() {event_function.call(html_element);}); 
   else if(html_element.addEventListener) //Firefox & company
      html_element.addEventListener(event_name, event_function, false); //don't need the 'call' trick because in FF everything already works in the right way          
} 
```

<h3>Event Delegation</h3>
- <strong>Event Delegation</strong> - An method that instead of using multiple individual event listeners, places a single event listener on a parent (read more http://davidwalsh.name/event-delegate) e.g. 

```javascript
//jQuery 1.4.3+  
$("nav").delegate("a", "click", function(){});
//jQuery 1.7+
$("nav").on("click", "a", function() {});
//Vanilla JS
document.querySelectorAll('nav').addEventListener('click', function(e) {
        // e.target is the clicked element!
        if(e.target && e.target.tagName == 'a') {}
});
```

<h3>Event Bubbling & Default Event Canceling</h3>
- <strong>Event Bubbling</strong> - is when a nested element triggers the parents event handler. The following code can be used to prevent bubbling.
- <strong>return false</strong> - Adding this to your event handler will prevent the default event from occuring, NOTE if used in a jQuery event handler it will also prevent the event from bubbling up, effectively simulating functions event.preventDefault() & event.stopPropagation().
- <strong>event.preventDefault()</strong> - Cancels the default event(if cancelable) codepen.io/sjmcpherso/pen/gboxaa
-  <strong>event.stopPropagation()</strong> - event.stopPropagation ? event.stopPropagation() : (event.cancelBubble=true) //event.cancelBubble used for IE<9


<h3>Scroll Event</h3>
- Can be used on any scrolling element with element.onscroll = function (event) {} but is general used on the Window object i.e. window.onscroll = function (event) {}
- Unbind the scroll event by setting to null i.e. window.onscroll = null; 
- Can also be used with addEventListener i.e. element.addEventListener("scroll", myFunction); although addEventListener is only IE9+
- Performance heavy as trigged everytime you scroll one pixel (or one scroll unit, whatever that is on your OS)
- window.onscroll event - Detects scrolling

<h3>DOM/Page Load Events</h3>
- <strong>Window Load/Onload Event</strong> - Triggers when all content is loaded including images/js/iframes etc

```javascript
window.onload = function(){}
//Or
window.addEventListener('load', function(){})//IE9+
```

- <strong>DOMContentLoaded Event</strong> - Triggers when the HTML Document has been loaded & parsed, without waiting for CSS/images/JS/iframes etc to finish loading. jQUery's 'ready' function defaults to this event.

```javascript
document.addEventListener("DOMContentLoaded", function(){})//IE9+
```

<h3>Asyncronous Script Loading</h3>
- <strong>Window Load/Onload Event</strong>

<h2>Prototypal Inheritance</h2>
- Distinct from Class Inheritance, where an object inherits properties from an object assigned to it.
- Extending native prototypes - To use newer features added to JS you will often need to back port native prototypes for older browsers this breaks this breaks encapsulation e.g Array.ForEach


<h2>Design Patterns</h2>

<h3>Singleton</h3>

- A pattern for a class which initializes a single object over the lifetime of a program.

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

<h3>the Constructor Pattern</h3>
- Object constructors are used to create specific types of objects
- The 'new' keyword signify's the use of a constructor instance
- For conventions name Constructors with Initial Caps i.e. var person = new Person();
- 'this' keyword can be used to refer to the object created
- 'instanceof' can be used to determine if the variable is an instance of a constructor i.e. var a = new Person(); if(a instanceof Person){//Will run}

```javascript
function Beverage(name,temperature){
	this.name = name;
	this.temperature = temperature; //A beverage can be hot or cold.
}
Beverage.prototype.drink = function(){
	console.log("I'm drinking " + this.name);
}
function Coffee(type){
	this.type = type;//A coffee can be Dark or Mild
        Beverage.call(this, "coffee", "hot"); //Coffee class inherits the properties from Beverage
}
Coffee.prototype = Object.create(Beverage.prototype); //Coffee class inherits prototype chain from Beverage

var darkRoastCoffee = new Coffee("dark");//Create a instance of the inherited Coffee class
darkRoastCoffee.drink();//Call Drink function will produce "I am drinking coffee"
```

<h3>The Module Pattern</h3>

- Module pattern is a way of organizing and encapsulating code via a closure. It allows you to create public/private functions and vars inside an object (the module). It lessens the likelihood of naming conflicts and unintended interactions with other functions/vars on the page. Modules should work independently and be easily extensible. Using modules enables to write widgets and plugins that interact with each other.

```javascript
var testModule = (function () {
   var counter = 0;
  return {
    incrementCounter: function () {
      return counter++;
    },
    resetCounter: function () {
      console.log( "counter value prior to reset: " + counter );
      counter = 0;
    }
  };
})();
testModule.incrementCounter();
```


<h2>Debugging & Error Checking</h2>

<h3>Syntax vs Runtime Errors</h3>
- Syntax errors are picked up by the browser when the script is parsed, if an error is found by the parser none of the script is executed.
- Runtime errors are found by the browser at execution time but only code after the error will not be executed.

<h3>The Console</h3>
- console.log() - Used to output values to the console window.
- console.table() - (Firefox, Chrome Only) Is used to output tabular data to the console window e.g JSON & Array Objects, to display only certain fields you can use "console.table(languages, ["name", "paradigm"]);" 
- console.count(label) - Outputs the number times the line of code has been invoked with an optional string as a label
- console.assert(expression, message) - Will display the message if the expression in the first argument is false
- console.time(message)/console.timeEnd(message) - Time the performance of code between .time() & .timeEnd() statements. i.e.

```javascript 
console.time("test");
for(var i=0;i<100000;i++){
	var j = Math.random()*1;
}
console.timeEnd("test"); //Will output "test: 8.75ms"
```

- NOTE: use of the Console object will break <IE9 but NOT while the IE Developer Tools window is open.

<h3>Try Catch Statement</h3>
- Use to surround a block of statements to handle when an exception occurs
- The 'try' block encompases where to track for exceptions
- The 'catch' block is where the response to the exception is handled
- The 'finally' block will be executed after the 'try' or 'catch' (in the case of an exception in the 'try') block.

```javascript 
try {
  try {
    throw new Error("oops");
  }
  catch (ex) {
    console.error("inner", ex.message);
  }
  finally {
    console.log("finally");
  }
}
catch (ex) {
  console.error("outer", ex.message);
}
```

<h4>Throw Statement</h4>
- The throw statement can be used to simulate an exception and therefore be used to test Try/Catch statements 

```javascript 
throw new Error("oops");
```


<h2>Synchronous vs Asynchronous Script Loading</h2>
- By default scripts are downloaded & executed synchronously

<h2>Animating</h2>
<h3>RequestAnimationFrame</h3>
 - CSS should be used for simple transitions & animations i.e. button rollovers, dropdown menus etc
 - Using RequestAnimationFrame over other techniques the browser optimizes it with hardware acceleration to make them smoother.
 - Animations in inactive tabs will stop, utilizing CPU elsewhere
 - It helps with battery life


<h2>JavaScript Promises</h2>
- A Promise is a way to manage asynchronous operations
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
- JavaScript ES6 Promise API (Latest browsers Only, IE12+ but Polyfils available) 



<h2>Client-side Data Storage</h2>

- <strong>localStorage/sessionStorage</strong> - A single persistent object, storage limit at least 5MB per origin (domain/protocol). localStorge persists when browser closed, sessionStorage clears when window closed. IE8+. Note: All variables are converted to strings i.e. so the output of localStorage.setItem("bool", true); &  localStorage.setItem("num", 1); would be "true" & "1" respectively

```javascript
localStorage.setItem("username", "John");// Save data to the current local store also use localStorage.username = "John";
alert( "username = " + localStorage.getItem("username"));// Access some stored data
```

- <strong>Indexed Database (IndexedDB)</strong> -  A collection of object stores, with an asynchronous API. Indexes on stores can be created to improve search speed.


<h2>Other JavaScript APIs</h2>
- navigator.getUserMedia() - For capturing Audio/Video client side (limited browser capatibility)
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
- Page Visibility - Using document.hidden and/or document.visibilityState you can determine whether the page is in the active tab of the browser and whether the browser window is minified or not. IE10+

```javascript
function handleVisibilityChange() {
  if (document.hidden)
    pauseSimulation();
  else
    startSimulation();
}

document.addEventListener("visibilitychange", handleVisibilityChange, false);
```

- Web Notifications - Allows you to send notifications to the user outside of the browser window. The user must allow permission for your application to use them. The look is largely based on the browser and compatibility is limited.
```javascript
if(window.Notification && Notification.permission !== "denied") {
	Notification.requestPermission(function(status) {  // status is "granted", if accepted by user
		var n = new Notification('Title', { body: 'I am the body text!' }); 
	});
}
```
- Application Cache - Allows pages and resources to be cached for offline usage
- Network Information - Can be used to determine what internet connection is being used I.e wifi, cellular etc
- Vibration - Trigger vibration in mobile devices
- Battery - Detect if the battery is low on the device

<h2>ECMAScript 6 (ES2015)</h2>
- This the next version of the JS standard, code-named "Harmony" or "ES.next", abreviated to ES6 and more recently called ES2015. Limited support for most. Browser Support list found at http://kangax.github.io/es5-compat-table/es6/
- Can be compiled to EcmaScript 5 via Google Traceur or BabelJS.




<h3>ES6 Variables</h3>
- <strong>Let</strong> - Block-level variable declaration acts in the same way as "var" but scope is at the block-level, rather than the whole function. i.e. block-level includes for loops, if/cases statement etc. 'let' unlike 'var' variables are not hoisted to thte top of the block. IE11+ 

```javascript
var l = 5;
var v = 10;
if (l === 5) {
  console.log(l + v); // 5 + 1
  let v = 4; // The scope is inside the if-block and not hoisted to the top of the block
  var b = 1; // The scope is inside the function
  console.log(l + v); // 4 + 1
} 
console.log(l + v); // 5 + 1
```

- <strong>Const</strong> - Varible declaration for Constants acts in the same way as "let" but is Read-Only. IE11+, Safari 6+. Note that when defining an object with 'const' the properties of the object still remain mutable i.e

```javascript
const obj = {
  foo: "123";
}
obj = {}; //Won't change anything;
obj.foo = "abc"; //Changes obj.foo
```

- <strong>Default Parameter Values</strong> - Will allow you to set default values for parameters that are undefined. i.e.
```javascript
function Point(x = 0, y = 0) {
   this.x = x;
   this.y = y;
}
var p = new Point(); // => { 0, 0 }
```
- <strong>The Spread Operator</strong> - Allows parameters to be summarised in places where multiple arguments or elements are expected
```javascript
function add(...values) {}
add(2, 5, 3);
var a = [0, 1, 2];
var b = [3, 4, 5];

a.push(...b); // => [0, 1, 2, 3, 4, 5]
```

- <strong>Template Strings</strong> - 


<h4>TDZ (Temporal Dead Zone)</h4>
- Let/Const take a different technique to dealing with Hoisting to variables declared with var, rather than being set to undefined a variable initialized with 'let' or 'const' will give a "ReferenceError" when accessed before being declared. Take the following example:

```javascript
let l = 'let'; //Confirms hoisting still occurs with Let
(function() {
    console.log(v); //Undefined
    console.log(l); //Reference Error 
    let v = 'var';
    let l = 'let';
}());
```

<h4>Destructuring</h4>
- Assignment of variables from arrays or objects using syntax that mirrors their construction.

<h5>Array Destructuring</h5>

```javascript
var array = [1, 2]
var [first, second] = array // first equals 1, second equals 2

var a = 1, b = 2
[a, b] = [b, a] //Switches values

//return multiple values
function f(){
	return [1,2]
}
[a, b] = f(); //a equals 1, b equals 2

```

<h5>Object Destructuring</h5>

```javascript
var foo = {bar:1, baz:2};
var {baz} = foo; //baz equals 2 

var a = 1;
var foo = {a} //Shorthand for var foo = {};foo.a = a;

// Assign new variable names
var {p: foo, q: bar} = o; //Shorthand for var foo = o.p, bar = o.q;

//Object destructoring for parameters, with new variable assignement and default values;
function f({weight:w, height:h, max=25, min=10}){
	if(max<25 && min>10)
		var answer = w * h;
}
f({weight, height, min})

```

<h4>Template Strings</h4>

- Template strings are string literals allowing embedded expressions. You can use multi-line strings and string interpolation features with them.

```javascript
var name = "doug";
var ageInMonths = 24;

var string  = `${name} is
${ageInMonths / 12} years old`;
```



<h3>ES6 Functions</h3>

<h4>Arrow Functions</h4>
- <strong>Arrows</strong> - Using the following '=>' characters to provide a shortend version of a standard function that returns an expression i.e. result = arguments => expression. Arrow functions can be used instead of a standard function syntax except it cannot be used for a constructor(with 'new') and when using 'this' with Arrow functions it effectively has lexical scope and is readonly. Simple example of Arrow Function:  

```javascript
var result = (par1,par2) => par1*par2;
//is the equavalent to
var result = function(par1,par2){
  return par1*par2;
}
```

<h4>ES6 Classes</h4>

- A clean simple declarative syntax for defining object prototypes and inheritance chains. The bodies of class declarations and class expressions are executed in strict mode. Class declarations are not hoisted.

```javascript
    class Foo {
        constructor() {
        }
    }
    let foo = new Foo();    
```

- <strong>Constructor Method</strong> - For creating and initializing an object created within a class, can only be a single contructor in a class.

```javascript
    class Foo {
        constructor(prop) {
            this.prop = prop;
        }
    }
    let foo = new Foo(123);    
```

- <strong>Static Methods<strong> - Static methods have no access to the fields, properties, and methods defined on an instance of the class using 'this'. However, static methods are often useful and can play the roles of factory methods, conversion methods, or general class helper methods.

```javascript
    class Foo {
        constructor(prop) {
            this.prop = prop;
        }
        static staticMethod() {
            return 'classy';
        }
    }
    let foo = new Foo(123);
```

- <strong>Sub classing with extends</strong>


<h4>Generators</h4>
- <strong>Generators</strong> - A type of function that can be stopped during execution to allow other code to run and then resumed once or many times.
- <strong>For In/Of Loop</strong>
```javascript
let arr = [3, 5, 7];
arr.foo = "hello";
for (let i in arr) { //for in iterates over property names
   console.log(i); //logs "0", "1", "2", "foo"
}
for (let i of arr) { //for of iterates over property values
   console.log(i); //logs "3", "5", "7"
}
```


<h3>ES6 Modules</h3>

- Modules are 


<h4>ES6 APIs</h4>
- <strong>Fetch API</strong> - Provides a interface for network responses & redirects and as an improvement to XMLHttpRequest

<h2>ECMAScript 7</h2>
- Object.Observe - Chrome only


<h2>jQuery</h2>

<h3>The $ sign</h3>
- The jQuery '$' is just a function that returns jQuery's 'init' function
- $.fn is just shorthand for the jQuery Prototype object i.e. jQuery.fn = jQuery.prototype

<h3>jQuery.noConflict()</h3>
- jQuery.noConflict() - Removes the jQuery object from the variable '$' so that other libraries that may conflict can use it.

<h3>Getting/Setting the Version</h3>
- Get the version of jQuery used on a webpage via $.fn.jquery
- In firebug you can load the latest version of jQuery via the Command Line using "include('jquery')". Otherwise you can add to the Console something like this:

```javascript
var jq = document.createElement('script');
jq.src = "https://ajax.googleapis.com/ajax/libs/jquery/1/jquery.min.js";
document.getElementsByTagName('head')[0].appendChild(jq);
// ... give time for script to load, then type.
jQuery.noConflict();
```

<h3>Document Ready</h3>
- Runs code in a after a "DOMContentLoaded" event is trigged and falls back to a window.onload event if unsuppported. 
- Anonymous Functions “$(document).ready(function() {“ & “$(function(){“ are exactly the same where code is executed after DOM is loaded 
- “(function ($){}(jQuery)” Passes the jQuery object as a parameter so that “$” refers to “jQuery”. In general widgets would be contained in a Immediate invoking function but initated by a global Controller. Often a single ";" is placed at the front of a anonymous function to stop syntax errors when JavaScript files are combined & minified.
- Of course if your following best practises and adding your javascript files before the closing body tag you don't need $(document).ready as the DOM will have already loaded.

<h3>Chaining</h3>
- Custom jQuery methods can be set to chain with:

```javascript
$.fn.enumerate = function() {
        return this; //Add to make the method chainable.
};
//Because of using "return this", it's chainable!
$("li").enumerate().css( "color", "red" );
```
<h3>jQuery Events</h3>
- As of jQuery 1.7+ ".on()" depreciates .live(), .delegate() and .bind(). To remove events bound with .oconsn() use .off()

<h3>jQuery Plugin</h3>
- To create a jQuery plugin use (function($){ $.fn.yourPluginName = function(){ /* Your code */ return this; }; })(jQuery);

<h3>Helpful jQuery Snippets/Methods</h3>
- $("span", this) is the same as $(this).find('span')
- Check if selected objects exist if($("#element").length){} as '0' is Falsy or if($("#element").is('*')) {}
- Use .stop() to stop animations on the selected element. Useful to stop queued animations triggering well after the event.
- .hover() is shorthand for mouseenter mouseleave events:

```javascript
$("td").hover(
  function () {
    $(this).addClass("hover");
  }, function () {
    $(this).removeClass("hover");
  }
);
```
- From >V1.6 .attr() returns the visable value and the new .prop() returns the underlying property i.e. &lt;input id="cb" type="checkbox" checked="checked"&gt; .attr(“checked”) “returns” checked whereas .prop(“checked”) returns “true” .prop() is the preferred method for returning properties from 1.6 onwards
- "$.grep" Finds the elements of an array which satisfy a filter function. The original array is not affected. arr = jQuery.grep(arr, function (a) { return a != 9; }) Useful as JS .filter(callback[, thisObject]) method is only IE9+
- The [] index will "dereference" a jQuery selector into a raw DOM object: $("#id")[0].style.color='#000000'; i.e. $("#id")[0] is the same as getElementById("id");
- Pass raw DOM objects as arguments: $(document.getElementById("p1")).prepend(document.getElementById("p2"));
- $("form").serialize() will return a string of all elements inside the form: "name=value&amp;name2=value2" etc.
- $('body').disableSelection(); (jquery-ui.js) prevents selection of text.
-  $("a[href='" + document.location.pathname + "']").addClass("current"); Use the filename to highlight the current page on a nav


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



<h2>JavaScript Frameworks, Library's, Languages and Scripts</h2>

<h3>JavaScript Frameworks</h3>
- JavaScript Frameworks which add content to the DOM on page load eg. AngularJS, Backbone JS etc have problems with Search Engines(https://developers.google.com/webmasters/ajax-crawling/) they are therefore best utilized in CRUD apps (Create, Read, Update, Delete). With extra configuration pages can be recreted as HTML Snapshots & hosted on alternative URL's to index the content.
- AngularJS
- Backbone
- EmberJS
- Ext JS

<h3>JS Compilers/Languages</h3>
- asm.js
- CoffeeScript - Programming language that transcompiles to JavaScript inspired by Ruby
- JSX a statically typed, object oriented programming language that compiles to JS, which offers performance and error checking improvements.
- TypeScript - A strict sperset of JS which adds EcmaScript 6, optional static typing and class-based support amongst other things to the language. Backed by Microsoft
- AtScript - Backed by Google but likely to merge under TypeScript

<h3>Library</h3>
- Reactjs a JS library developed by Facebook which alters Virtual DOM in the form of components to make changes to the View. This improves performance over changes to the Actual DOM. 
- Handlebars.js - Lightweight, library to build semantic templates i.e.
- Modernizr.js - Adds classes to the html element based on feature tests and includes HTML5 Shiv. Allows you to target parts of your CSS and JavaScript based on the features supported by a browser. Offers cross browser support for CSS3 TransitionEnd Event.
- Underscore.js - Utilty functions uncluding map, select, javascript templating

<h3>Scripts</h3>
- ajax-cache.js - Provides a AJAX response caching object so as to limit unnessary requests. https://code.google.com/p/ajax-cache/
- Equalize.js jQuery plugin for equalizing the height or width of sibling elements
- jquery.metadata.js takes attribute metadata from html attributes and converts into JSON.
- jQuery-contextMenu.js For creating a custom Context menu (right-click menu)
- Adapt.js is a lightweight JavaScript file that determines which CSS file to load before the browser renders a page. If the browser tilts or resizes, Adapt.js simply checks its width, and serves only the CSS that is needed, when it is needed.
- htm5shiv.js/html5shim.js - Allows the styling of HTML5 Elements such as Section, Article, Header in <IE9.
- Requirejs helps load script's in the right order, you can combine scripts via the RequireJS optimizer it also allows you to load scripts after the page has loaded (Just in time)
- Respond.js – Adds browsers support to min-max css media queries for ie6-ie8. Can be added in with Modernizr. Note: CSS must be loaded before and be from a local directory i.e. not from a CDN or subdomain.
- selectivizr.js -  Adds support for CSS3 selectors (:first-child,:last-child,:nth-child) for ie6-ie8 can cause conflicts with respond.js must be placed before.
- hoverIntent replicates jQuery's shorthand hover method but will only call mouseover/mouseleave when mouse movement has slowed reducing excessive calls to these events.
- Bower - A command line package manager to automate searching and downloading front-end development tools.

<h2>Node & NPM</h2>

<h3>Dependency Management</h3>
- Create a package.json in your projects route directory with "npm init" to document your dependencies

```javascript
   npm install %package% --save
   npm install %package% --save-dev
```



<h2>Source Control</h2>
- echo "" > .hgignore

