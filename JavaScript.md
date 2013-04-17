<h2>General JavaScript Coding Tips</h2>

- Anonymous Functions “$(document).ready(function() {“ & “$(function(){“ are exactly the same where code is executed after DOM is loaded 
- Add an extra (); at the end “(function () {})();“ makes it a Self Executing(Imediately Invoking) Anonymous Function which would run imediately
- “(function ($){}(jQuery)” As above but passes the jQuery object as a parameter so that “$” refers to “jQuery”. In general widgets would be to be contained in a Immediate invoking function but initated by a global Controller.
- localStorage/sessionStorage – Clientside browser storage (localStorage is Persistant) limited to 5MB per domain IE8+
- When using optional parameters place into an options hash. function circle(x,y,radius,options) { options = options || {};}
- Use console.time to track down bottlenecks & console.log to trace code</li>
- When JavaScript sees a string it immediately begins type coercing all value into strings. '1' + 2 +  3 ; // Equals '123',  3  + 2 + '1'; // Equals '51',  3  + 2 +  1 ; // Equals 6.
- Event Bubbling when a nested tag triggers the parent. The follow code can be used to prevent bubbling event.stopPropagation ? event.stopPropagation() : (event.cancelBubble=true) //event.cancelBubble used for IE<9
- Web Intents - a new framework for web-based inter-application communication and service discovery using JavaScript postMessage()
- navigator.getUserMedia() - Record Audio/Video (limited browser capatibility
- JavaScript Frameworks manipulating DOM on page load have problems with Search Engines(https://developers.google.com/webmasters/ajax-crawling/) they are therefore best utilized in CRUD apps (Create, Read, Update, Delete).
- Same Origin Policy is a security concept that stops browsers making cross domain XMLHttpRequests, For JSON you can avoid by using the datatype "JSONP" but also wrap the response in the requested serverside call back
- Console Debugging will break IE when not using the Developer Tools.

```javascript
// This allows you to log things, if console
// is available, but takes no action, if not.
function log() {
  console && console.log(arguments);
}
```
- Using delete will destroy variables and properties, making them undefined when you try to access them. Though if you call delete on an item in an array, the array's .length is unaffected.
- Pass raw DOM objects as arguments: $(document.getElementById("p1")).prepend(document.getElementById("p2"));
- JSON without " is evaluated as a object literal and JSON.Parse will not accept
- Place Google Analytics code at bottom even though Google recommends placing in the head, as pageviews will be tracked even if they leave the page before fully loaded also keeps the all the scripts together.


<h2>jQuery Specific Coding Tips</h2>
- To create a jQuery plugin use (function($){ $.fn.yourPluginName = function(){ /* Your code */ return this; }; })(jQuery);
- As of jQuery 1.7+ ".on()" depreciates .live(), .delegate() and .bind(). To remove events bound with .on() use .off()
- Use event delegation instead of individual event listeners e.g. $("table").delegate("td", "click", function(){$(this).toggleClass("chosen");
});//jQuery 1.4.3+ $("table").on("click", "td", function() {$(this).toggleClass("chosen");});//jQuery 1.7+
- From >V1.6 .attr() returns the visable value and the new .prop() returns the underlying property i.e. &lt;input id="cb" type="checkbox" checked="checked"&gt; .attr(“checked”) “returns” checked whereas .prop(“checked”) returns “true” .prop() is the preferred method for returning properties from 1.6 onwards
- jQuery methods should chain:

```javascript
$.fn.enumerate = function() {
   return this; //Add to make the method chainable.
};
//Because of using "return this", it's chainable!
$("li").enumerate().css( "color", "red" );
```
- "$.grep" Finds the elements of an array which satisfy a filter function. The original array is not affected. arr = jQuery.grep(arr, function (a) { return a != 9; })
- Check if selected objects exist if($("#element").length >0){} or if($("#element").is('*')) {}
- The [] index will "dereference" a jQuery selector into a raw DOM object: $("#id")[0].style.color='#000000'; I.e. $("#id")[0] is the same as getElementById("id");


<h2>JavaScript Performance</h2>
- Minifying JavaScript removes whitespace/linebreaks and shortends variables, reducing file size.
- &lt;script&gt;tags block parallel downloads, put them last so other resources can be downloaded first
- Defer Parsing of scripts that are not called at statup
- Async Loading via Lab.js or the 'async' attribute for the script tag (IE9 & below don’t support)
- Avoid excess Style Recalculation which occurs when manipulating the DOM with JavaScript
- Reference IDs rather than Classes (ID selection is native & increases performance)
- Web Worker i.e. var worker = new Worker('my_task.js'); runs in the background, independently of other scripts, without affecting the performance of the page.
- Where possible use CSS animations browsers optimise them for you and hardware accelerate them
- Use requestAnimationFrame() instead of setInterval(). requestAnimationFrame() only triggers when the result will update the display i.e. Will not trigger on a hidden browser tab whereas SetInterval will.

<h2>Helpful JavaScript/jQuery scripts</h2>
- jquery.metadata.js takes attribute metadata from html attributes and converts into JSON.
- Respond.js – Adds browsers support to min-max css media queries for ie6-ie8. Can be added in with Modernizr
- selectivizr.js -  Adds support for CSS3 selectors (:first-child,:last-child,:nth-child) for ie6-ie8 can cause conflicts with respond.js must be placed before.
- Requirejs helps load script in the right order, combine scripts via the RequireJS optimizer it also allows you to load scripts after the page has loaded (Just in time)
- jQuery-contextMenu.js For creating a custom Context menu (right-click menu)
- Equalize.js jQuery plugin for equalizing the height or width of sibling elements
- Underscore.js - Utilty functions uncluding map, select, javascript templating
- CoffeeScript - Programming language that transcompiles to JavaScript inspired by Ruby
- Adapt.js is a lightweight JavaScript file that determines which CSS file to load before the browser renders a page. If the browser tilts or resizes, Adapt.js simply checks its width, and serves only the CSS that is needed, when it is needed.
- Modernizr.js adds classes to the html element based on feature tests and includes HTML5 Shiv. Allows you to target parts of your CSS and JavaScript based on the features supported by a browser. 
