<h2>Javascript Performance tips</h2>
<ul>
<li>Minify JS (Removes whitespace/linebreaks and shortends variables)</li>
<li>Combine JS (Reduces the amount of HTTP Requests)</li>
<li><code><script></code> tags block parallel downloads, put them last so other resources can be downloaded first</li>
<li>Defer Parsing of Javascript</li>
<li>Just in time Loading</li>
<li>Async Loading via Lab.js or  the async attribute for the script tag (IE9 & below don’t support)</li>
</ul>

<h2>Javascript Coding Tips</h2>
<ul>
<li>“$(document).ready(function() {“ vs “$(function(){“  Code is executed after DOM is loaded (Document Object Model, HTML. XML</li>
<li>Add an extra (); at the end “(function () {})();“ Self Executing(Imediately Invoking) anonymous function which would runs imediately</li>
<li>“(function ($){}(jQuery)” As above but passes the jQuery object as a parameter so that “$” refers to “jQuery”. In general widgets would be to be contained in a Immediate invoking function but Controller </li>
<li>localStorage/sessionStorage – Clientside browser storage (localStorage is Persistant) limited to 5MB per domain IE8+</li>
<li>Put all optional parameters into an options hash. function circle(x,y,radius,options) { options = options || {};}</li>
<li>firebugs console.time to track down bottlenecks & console.log to trace code</li>
<li>Use event delegation instead of individual event listeners</li>
<li>When javascript sees a string it immediately begins type coercing all value into strings. '1' + 2 +  3 ; // Equals '123',  3  + 2 + '1'; // Equals '51',  3  + 2 +  1 ; // Equals 6. </li>
</ul>

<h2>Helpful Javascript Coding Scripts</h2><ul>
<li>jquery.metadata.js takes attribute metadata from html attributes and converts into JSON.</li>
<li>respond.js – Adds browsers support to min-max css media queries for ie6-ie8.</li>
<li>selectivizr.js -  Adds support for CSS3 selectors (:first-child,:last-child,:nth-child) for ie6-ie8 can cause conflicts with respond.js must be placed before.</li>
<li>Javascript Frameworks manipulating DOM on page load have problems with Search Engines(https://developers.google.com/webmasters/ajax-crawling/) they are therefore best utilized in CRUD apps (Create, Read, Update, Delete).</li>
<li>Require.js helps load script in the right order, combine scripts via the RequireJS optimizer it also allows you to load scripts after the page has loaded (Just in time)</li>
</ul>

<h2>Database Tips</h2><ul>
<li>Relational Database – built on tables, fields & keys e.g MySQL, SQL Server</li>
<li>Document-oriented Database – A collection of independent documents. E.g CouchDB, MongoDB</li>
</ul>

<h2>Abbreviations/Terms:</h2><ul>
<li>IDE – Integrated Development Enviroment is a software application that provides computer programmers with a facility to edit, debug and/or compile source code</li>
<li>API – Application Programming Interface is a specification for combining software components.</li>
<li>SDK – Software Development Kit is a toolkit to allow softwore development on a specific framework or platform</li>
<li>CDN – Content Delivery Network is a large distributed system of servers hosting content with high availability and download speeds.</li>
<li>REST – REpresentational State Transfer is a Web service design model, conforming to REST constraits is considered RESTful</li>
<li>Progressive Enhancement – Using a feature that may not be supported by all browsers but does not break the page if it isn’t supported</li>
</ul>