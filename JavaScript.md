<h2>General JavaScript Coding Tips</h2>

- Their are 6 types of values used in JS: number, string, Boolean, object, function and undefined.
- The typeOf operator can be used to identify a values type.
- Add an extra (); at the end “(function () {})();“ makes it a Self Executing(Imediately Invoking) Anonymous Function which would run imediately
- “(function ($){}(jQuery)” As above but passes the jQuery object as a parameter so that “$” refers to “jQuery”. In general widgets would be contained in a Immediate invoking function but initated by a global Controller. Often a single ";" is placed at the front of a anonymous function to stop syntax errors when JavaScript files are combined & minified.
- localStorage/sessionStorage – Clientside browser storage (localStorage is Persistant) limited to 5MB per domain IE8+
- When using optional parameters place into an options hash. function circle(x,y,radius,options) { options = options || {};}
- When JavaScript sees a string it immediately begins type coercing all value into strings. '1' + 2 +  3 ; // Equals '123',  3  + 2 + '1'; // Equals '51',  3  + 2 +  1 ; // Equals 6.
- element.getElementsByClassName() IE9+, element.getElementsByTagName & element.getElementsById full compatibility.
- Event Bubbling when a nested tag triggers the parent. The follow code can be used to prevent bubbling event.stopPropagation ? event.stopPropagation() : (event.cancelBubble=true) //event.cancelBubble used for IE<9
- Web Intents - a new framework for web-based inter-application communication and service discovery using JavaScript postMessage()
- navigator.getUserMedia() - Record Audio/Video (limited browser capatibility
- JavaScript Frameworks which add content to the DOM on page load eg. AngularJS, Backbone JS etc have problems with Search Engines(https://developers.google.com/webmasters/ajax-crawling/) they are therefore best utilized in CRUD apps (Create, Read, Update, Delete). With extra configuration pages can be recreted as HTML Snapshots & hosted on alternative URL's to index the content.
- Same Origin Policy is a security concept that stops browsers making cross domain XMLHttpRequests, For JSON you can avoid by using the datatype "JSONP" but also wrap the response in the requested serverside call back
- Console Debugging - Use console.time to track down bottlenecks & console.log to trace code but will break <IE10 when not using the Developer Tools. Use the below to allow for this:
```javascript
// Provide a mock object, so that calls to the console in <IE10 wouldn't result in an error
if(!window.console) {
  window.console = new function() {
    this.log = function(str) {};
    this.dir = function(str) {};
  };
}
```

- isNaN() checks if value is NaN which is achieved when Number() is unsuccessful in converting a value to a number
- Use % to determine if a number is divisible by another, it gives the remander value I.e:
```javascript
if(randomNum % 7 == 0)
// Do Something
```

- Using delete will destroy variables and properties, making them undefined when you try to access them. Though if you call delete on an item in an array, the array's .length is unaffected.
- JSON without " is evaluated as a object literal and JSON.Parse will not accept
- Place Google Analytics code at bottom even though Google recommends placing in the head, as pageviews will be tracked even if they leave the page before fully loaded also keeps the all the scripts together.
- The [] index will "dereference" a jQuery selector into a raw DOM object: $("#id")[0].style.color='#000000';
- When you change the value of a prototype property it also changes across all existing objects derived from it.
- Use Event Delegation instead of individual event listeners e.g. 

```javascript
//jQuery 1.4.3+ 
$("table").delegate("td", "click", function(){});
//jQuery 1.7+
$("table").on("click", "td", function() {});
//Vanilla JS
document.querySelector('#parent-list').addEventListener('click', function(e) {
        // e.target is the clicked element!
        if(e.target && e.target.tagName == 'LI') {}
});
```
- requestAnimationFrame() Limited Browser Compatibility(IE10+,Safari6+) - only triggers when the result will update the display i.e. Will not trigger on a hidden browser tab whereas SetInterval/SetTimeout will.
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

 - document.querySelector() & document.querySelectorAll() IE8+ Accepts any CSS selector, .querySelector() returns null if no matches are found, otherwise, it returns the first matching element. .querySelectorAll() returns a node list of all elements selected i.e. document.querySelectorAll("div.note, div.alert") returns a list of all div elements within the document with a class of either "note" or "alert".
 - Cross-origin resource sharing (CORS) IE10+(Partial Support for IE8/9) is a mechanism that allows JavaScript on a web page to make XMLHttpRequests to another domain which would otherwise be forbidden due to the Same Origin Policy.
- Automatic Type Conversion in JS means that varibles if different types can be compared I.e 

```javascript
false == 0 //true
"5" == 5 //true
!"" //true
null == undefined //true
```

- For cases where you do not want automatic type conversion to occur use '===' or '!==' I.e.

```javascript
"5" === 5 //false
false !== 0 //true
```

- Objects are set using the 'new' namespace
- Objects with the same properties are not equal unless they are assigned to each other see http://jsfiddle.net/sjmcpherso/YgEjv/
- The Arguments Object - is a system object resembling an array for accessing the variables past to an function. I.e

```javascript
testFunc(1,"go");
function testFunc(){
//argument.length = 2;
//argument[1] = "go";
}
```


<h3>JavaScript Shorthand</h3>

Variables
```javascript
//Longhand
var x;
var y;
var z = 3;
//Shorthand
var x, y, z=3;
```

If Statements
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

<h3>Array Object Methods</h3>
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
- array.splice(index,howmany,item1,.....,itemX) -	Adds/Removes elements from an array at a specific position i.e. array.splice(index,1) will remove 1 element at index. Distinct from "delete array[index]" which removes the element but doesnt adjust;
- array.toString() - Converts an array to a string, and returns the result, values are seperated by a comma
- array.unshift(item1,item2, ..., itemX) - IE9+	Adds new elements to the beginning of an array, and returns the new length

<h2>jQuery Specific Coding Tips</h2>
- Anonymous Functions “$(document).ready(function() {“ & “$(function(){“ are exactly the same where code is executed after DOM is loaded 
- To create a jQuery plugin use (function($){ $.fn.yourPluginName = function(){ /* Your code */ return this; }; })(jQuery);
- As of jQuery 1.7+ ".on()" depreciates .live(), .delegate() and .bind(). To remove events bound with .on() use .off()
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
- Check if selected objects exist if($("#element").length >0){} or if($("#element").is('*')) {}
- The [] index will "dereference" a jQuery selector into a raw DOM object: $("#id")[0].style.color='#000000'; I.e. $("#id")[0] is the same as getElementById("id");
- $("form").serialize() will return a string of all elements inside the form: "name=value&amp;name2=value2" etc.
- $("span", this) is the same as $(this).find('span')
- Pass raw DOM objects as arguments: $(document.getElementById("p1")).prepend(document.getElementById("p2"));
- Use .stop() to stop animations on the selected element. Useful to stop queued animations triggering well after the event.
- To determine if a selector exists use if($(element).length){}
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
<h2>JavaScript Performance</h2>
- Minifying JavaScript removes whitespace/linebreaks and shortends variables, reducing file size.
- &lt;script&gt;tags block parallel downloads, put them last so other resources can be downloaded first
- Defer Parsing of scripts that are not called at statup
- Async Loading via Lab.js or the 'async' attribute for the script tag (IE9 & below don’t support)
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

- Reference IDs rather than Classes (ID selection is native & increases performance)
- Web Worker i.e. var worker = new Worker('my_task.js'); runs in the background, independently of other scripts, without affecting the performance of the page.
- Where possible use CSS animations browsers optimise them for you and hardware accelerate them
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
- Stop Using Document Ready when loading scripts from bottom of the body tag
- .offset() used to get/set the x/y position of an element relative to the document. i.e. $(selector).offset().top;
- .position() same as above but relative to the parent.
- Cache elements when using selectors var elem = getElementByTagName('a');


<h2>Helpful JavaScript/jQuery scripts</h2>
- jquery.metadata.js takes attribute metadata from html attributes and converts into JSON.
- Respond.js – Adds browsers support to min-max css media queries for ie6-ie8. Can be added in with Modernizr
- selectivizr.js -  Adds support for CSS3 selectors (:first-child,:last-child,:nth-child) for ie6-ie8 can cause conflicts with respond.js must be placed before.
- Requirejs helps load script's in the right order, you can combine scripts via the RequireJS optimizer it also allows you to load scripts after the page has loaded (Just in time)
- jQuery-contextMenu.js For creating a custom Context menu (right-click menu)
- Equalize.js jQuery plugin for equalizing the height or width of sibling elements
- Underscore.js - Utilty functions uncluding map, select, javascript templating
- CoffeeScript - Programming language that transcompiles to JavaScript inspired by Ruby
- Adapt.js is a lightweight JavaScript file that determines which CSS file to load before the browser renders a page. If the browser tilts or resizes, Adapt.js simply checks its width, and serves only the CSS that is needed, when it is needed.
- Modernizr.js adds classes to the html element based on feature tests and includes HTML5 Shiv. Allows you to target parts of your CSS and JavaScript based on the features supported by a browser. Offers cross browser support for CSS3 TransitionEnd Event.
- hoverIntent replicates jQuery's shorthand hover method but will only call mouseover/mouseleave when mouse movement has slowed reducing excessive calls to these events.

