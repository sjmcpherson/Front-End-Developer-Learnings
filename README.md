<h2>HTML Coding & Performance tips</h2>

 - Reduce unecessary html tags to improve performance
 - Use image sprites to reduce round trips to server
 - Serve all referenced files css, js, images on dispersed servers.
 - Putting stylesheets in the &lt;head&gt; allows the page to render progressively.
 - HTML5 Doctype &lt;!DOCTYPE html&gt;
 - Doctype must be first on page or IE will revert to Quirks Mode (Dreamweaver Templates can mess with this)
 - HTML5 Inputs with graceful degredation: type=search, email, url, number, and tel
 - Use input[placeholder] with IE&lt;10 polyfill fallback jquery-placeholder.js
 - &lt;meter value="2" min="0" max="10"&gt;2 out of 10&lt;/meter&gt; tag defines a measurement within a known range, or a fractional value.
 - The "download" attribute forces browser to invoke download dialog &lt;a href="logo.png" download="Logo.png"&gt;download me&lt;/a&gt;
 - &lt;datalist&gt; Databinding Autocomplete example
 
```HTML
<input list="browsers">
<datalist id="browsers">
  <option value="Chrome">
  <option value="Firefox">
  <option value="Safari">
</datalist>
```

 - &lt;figure&gt; used to markup illustrations, graphs and images used with &lt;figurecaption&gt;
 - &lt;video autoplay controls&gt;&lt;/video&gt;
 - Progressive vs Baseline JPEGs -  A Progressive jpeg is a series of scans of increasing quality, a Baseline jpeg is a single full resolution scan, Progressive JPEGs load faster on IE9, Chrome & Firefox but use more CPU. http://calendar.perfplanet.com/2012/progressive-jpegs-a-new-best-practice/



<h2>CSS Coding & Performance Tips</h2>

 - Limit CSS Box-shadows, Gradients
 - Minify CSS (Removes whitespace/linebreaks reducing file size)
 - Combine CSS (Reduce the amount of HTTP Requests)
 - :after{content:”more”;} & :before{} IE8+ Allows you to add content before/after an element
 - *{} targets every element (Not recommend adds performance issues)
 - ul > li{} IE7+ targets direct children
 - ul ~ p{} IE7+ targets p tags after ul tag
 - Avoid using IDs in CSS
 - h1 + p{} IE7+ targets adjacent p tags directly after h1 tags
 - a[data-info~="image"]{} IE7+ selects all elements that have a data-info of “image” including multiple values such as  data-info="external image"
 - :first-child{} IE7+ targets the first child element
 - :last-child{} IE9+ targets the last child element
 - li:nth-child(3) IE9+
 - background-image: image-set(url("test.png") 1x, url("test-2x.png") 2x); Safari 6+ and Chrome 21+ ONLY
 - background-clip, background-origin and background-size IE9+
 - HasLayout - The single most important thing you need to know about fixing bugs in <IE8, Giving an element "Layout" will fix 99% of IE rendering bugs, as if by magic. The other 1% will most likely be related to position: relative; or floats. Use "zoom: 1" as a trigger for whatever IE versions need it. Eg .ie6 #myElement, .ie7 #myElement { zoom: 1 }
 - X:first-letter/:first-line apply to block level elements compatible with all browser versions
 - Avoid unnecessary tag identifiers for performance i.e. ul#navigation,ul.menu{} replace #navigation,.menu{}
 - Avoid using ancestors html div tr td{} Most modern browsers work from the right & work them way up
 - Chaining can mean loss of performance so when you do chain use the least used first i.e. use #foo.bar instead of .bar#foo
 - Multi-column Wrapping Text layouts with -column-count: 3; IE10+
 - -flex: The new Flexible Box layout Module for fluid layouts - http://html5-demos.appspot.com/static/css/flexbox/index.html IE10+ includes -order: for ordering structure elements -justify-content: for aligning structure elements and -webkit-flex-direction: for positioning
 - -calc: Dynamic css calculations div {width: +calc(100% - 4em);}
 - Versions of Chrome & Safari change the anti-alias of text during CSS animations fix with body{-webkit-backface-visibility: hidden;} or on the problematic area (causes WebKit to use hardware acceleration for the animations)


<h2>Javascript/jQuery Coding & Performance Tips</h2>
- Minify JS (Removes whitespace/linebreaks and shortends variables)
- Combine JS (Reduces the amount of HTTP Requests)
- &lt;script&gt;tags block parallel downloads, put them last so other resources can be downloaded first
- Defer Parsing of scripts that are not called at statup.h
- Async Loading via Lab.js or the async attribute for the script tag (IE9 & below don’t support)
- Avoid excess Style Recalculation which occurs when manipulating the DOM with javascript
- “$(document).ready(function() {“ vs “$(function(){“  Code is executed after DOM is loaded
- Add an extra (); at the end “(function () {})();“ makes it a Self Executing(Imediately Invoking) anonymous function which would run imediately
- “(function ($){}(jQuery)” As above but passes the jQuery object as a parameter so that “$” refers to “jQuery”. In general widgets would be to be contained in a Immediate invoking function but initated by a global Controller.
- localStorage/sessionStorage – Clientside browser storage (localStorage is Persistant) limited to 5MB per domain IE8+
- When using optional parameters place into an options hash. function circle(x,y,radius,options) { options = options || {};}
- Use console.time to track down bottlenecks & console.log to trace code</li>
- As of jQuery 1.7+ ".on()" depreciates .live(), .delegate() and .bind(). To remove events bound with .on() use .off()
- Use event delegation instead of individual event listeners e.g. $("table").delegate("td", "click", function(){$(this).toggleClass("chosen");
});//jQuery 1.4.3+ $("table").on("click", "td", function() {$(this).toggleClass("chosen");});//jQuery 1.7+
- When javascript sees a string it immediately begins type coercing all value into strings. '1' + 2 +  3 ; // Equals '123',  3  + 2 + '1'; // Equals '51',  3  + 2 +  1 ; // Equals 6.
- Reference Ids rather than classes (Id selection is native increases performance}
- From >V1.6 .attr() returns the visable value and the new .prop() returns the underlying property i.e. &lt;input id="cb" type="checkbox" checked="checked"&gt; .attr(“checked”) “returns” checked whereas .prop(“checked”) returns “true” .prop() is the preferred method for returning properties from 1.6 onwards
- Event Bubbling when a nested tag triggers the parent. The follow code can be used to prevent bubbling event.stopPropagation ? event.stopPropagation() : (event.cancelBubble=true) //event.cancelBubble used for IE<9
- "$.grep" Finds the elements of an array which satisfy a filter function. The original array is not affected. arr = jQuery.grep(arr, function (a) { return a != 9; })
- Web Worker i.e. var worker = new Worker('my_task.js'); runs in the background, independently of other scripts, without affecting the performance of the page.
- Web Intents - a new framework for web-based inter-application communication and service discovery using Javascript postMessage()
- navigator.getUserMedia() - Record Audio/Video (limited browser capatibility
- Javascript Frameworks manipulating DOM on page load have problems with Search Engines(https://developers.google.com/webmasters/ajax-crawling/) they are therefore best utilized in CRUD apps (Create, Read, Update, Delete).
- Same Origin Policy is a security concept that stops browsers making cross domain XMLHttpRequests, For JSON you can avoid by using the datatype "JSONP" but also wrap the response in the requested serverside call back
- Jquery methods should chain:

```javascript
$.fn.enumerate = function() {
   return this; //Add to make the method chainable.
};
//Because of using "return this", it's chainable!
$("li").enumerate().css( "color", "red" );
```

- Console Debugging will break IE when not using the Developer Tools.

```javascript
// This allows you to log things, if console
// is available, but takes no action, if not.
function log() {
  console && console.log(arguments);
}
```

- Using delete will destroy variables and properties, making them undefined when you try to access them. Though if you call delete on an item in an array, the array's .length is unaffected.





<h2>Helpful Javascript/jQuery Scripts</h2><ul>
<li>jquery.metadata.js takes attribute metadata from html attributes and converts into JSON.</li>
<li>Respond.js – Adds browsers support to min-max css media queries for ie6-ie8. Can be added in with Modernizr</li>
<li>selectivizr.js -  Adds support for CSS3 selectors (:first-child,:last-child,:nth-child) for ie6-ie8 can cause conflicts with respond.js must be placed before.</li>
<li>Requirejs helps load script in the right order, combine scripts via the RequireJS optimizer it also allows you to load scripts after the page has loaded (Just in time)</li>
<li>jQuery-contextMenu.js For creating a custom Context menu (right-click menu)</li>
<li>Equalize.js jQuery plugin for equalizing the height or width of sibling elements</li>
<li>Underscore.js - Utilty functions uncluding map, select, javascript templating</li>
<li>CoffeeScript - Programming language that transcompiles to JavaScript inspired by Ruby</li>
</ul>

<h2>Abbreviations/Terms:</h2>

- UI - User Interface are the components by which users interact with</li>
- UX - User Experience is a broader term which is distinct from UI as it encompasses the way a person feels about using a product, system or service</li>
- IDE – Integrated Development Enviroment is a software application that provides computer programmers with a facility to edit, debug and/or compile source code</li>
- Relational Database – built on tables, fields & keys e.g MySQL, SQL Server
- Document-oriented Database – A collection of independent documents. E.g CouchDB, MongoDB
- API – Application Programming Interface is a specification for combining software components.</li>
- SDK – Software Development Kit is a toolkit to allow software development on a specific framework or platform</li>
- CDN – Content Delivery Network is a large distributed system of servers hosting content with high availability and download speeds.</li>
- REST – REpresentational State Transfer is a Web service design model, conforming to REST constraits is considered RESTful</li>
- Progressive Enhancement – Using a feature that may not be supported by all browsers but does not break the page if it isn’t supported</li>
- Data Binding - Syncronises data between UI components which are bound to the data source</li>
- CRUD - Create, Read, Update, Delete (Also BREAD - Browse, Read, Edit, Add, Delete) The major functions that are implemented in relational database applications</li>
- Loose Coupling - Coupling measures the degree to which program modules rely on other modules. Loose coupling implies each component can operate or be tested independently of other components.</li>
- Explicit iteration vs Implicit Iteration - In jQuery:

```javascript
// Explicit iteration with the jQuery .each() method
$( "li" ).each(function() {
  $(this).addClass( "foo" );
});
// jQuery Implicit Iteration
$( "li" ).addClass( "bar" );
```

