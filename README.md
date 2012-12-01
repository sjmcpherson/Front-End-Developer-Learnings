Javascript Performance tips
•	Minify JS (Removes whitespace/linebreaks and shortends variables)
•	Combine JS (Reduces the amount of HTTP Requests)
•	<script> tags block parallel downloads, put them last so other resources can be downloaded first
•	Defer Parsing of Javascript
•	Just in time Loading
•	Async Loading via Lab.js or  the async attribute for the script tag (IE9 & below don’t support)


Javascript Coding Tips
•	“$(document).ready(function() {“ vs “$(function(){“  Code is executed after DOM is loaded (Document Object Model, HTML. XML
•	Add an extra (); at the end “(function () {})();“ Self Executing(Imediately Invoking) anonymous function which would runs imediately
•	“(function ($){}(jQuery)” As above but passes the jQuery object as a parameter so that “$” refers to “jQuery”. In general widgets would be to be contained in a Immediate invoking function but Controller 
•	localStorage/sessionStorage – Clientside browser storage (localStorage is Persistant) limited to 5MB per domain IE8+
•	Put all optional parameters into an options hash. function circle(x,y,radius,options) { options = options || {};}
•	Use firebugs console.time to track down bottlenecks & console.log to trace code
•	Use event delegation instead of individual event listeners
•	When javascript sees a string it immediately begins type coercing all value into strings. '1' + 2 +  3 ; // Equals '123',  3  + 2 + '1'; // Equals '51',  3  + 2 +  1 ; // Equals 6. 



Helpful Javascript Coding Scripts
•	jquery.metadata.js takes attribute metadata from html attributes and converts into JSON.
•	respond.js – Adds browsers support to min-max css media queries for ie6-ie8.
•	selectivizr.js -  Adds support for CSS3 selectors (:first-child,:last-child,:nth-child) for ie6-ie8 can cause conflicts with respond.js must be placed before.
•	Javascript Frameworks manipulating DOM on page load have problems with Search Engines(https://developers.google.com/webmasters/ajax-crawling/) they are therefore best utilized in CRUD apps (Create, Read, Update, Delete).
•	Require.js helps load script in the right order, combine scripts via the RequireJS optimizer it also allows you to load scripts after the page has loaded (Just in time)


Database Tips
•	Relational Database – built on tables, fields & keys e.g MySQL, SQL Server
•	Document-oriented Database – A collection of independent documents. E.g CouchDB, MongoDB


Abbreviations/Terms:
•	IDE – Integrated Development Enviroment is a software application that provides computer programmers with a facility to edit, debug and/or compile source code
•	API – Application Programming Interface is a specification for combining software components.
•	SDK – Software Development Kit is a toolkit to allow softwore development on a specific framework or platform
•	CDN – Content Delivery Network is a large distributed system of servers hosting content with high availability and download speeds.
•	REST – REpresentational State Transfer is a Web service design model, conforming to REST constraits is considered RESTful
•	Progressive Enhancement – Using a feature that may not be supported by all browsers but does not break the page if it isn’t supported
