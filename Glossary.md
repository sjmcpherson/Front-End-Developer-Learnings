Abbreviations/Terms:
------------------

- Abstraction - A process of structuring code to be more readable by making functions shorter and code reuseable. Object-Oriented Programming is an approach to Abstraction.
- API – Application Programming Interface is a specification for combining software components.
- AJAX an acronym for Asynchronous JavaScript and XML. Despite the name, the use of XML is not required as JSON is often used instead. With AJAX, web applications can send data, and retrieve data from, a server asynchronously (in the background therefore creating a new code thread) without interfering with the display and behavior of the existing page.
- Associative Array - Abstract data type composed of a collection of key/value pairs. Objects are Associative Arrays in JavaScript
- Asynchronous vs Synchronous, Asynchronouse permits other processing to continue while a transmission is being processed.
- Bower - A front-end package management system that runs on Node.js & npm
- Closure - A term used when you nest functions, as inner functions can refer to the variables present in their outer enclosing functions even after their parent functions have already executed. https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Closures, http://jsfiddle.net/sjmcpherso/ByJfv/ 
- CDN – Content Delivery Network is a large distributed system of servers hosting content with high availability and download speeds.
- CRUD - Create, Read, Update, Delete (Also BREAD - Browse, Read, Edit, Add, Delete) The major functions that are implemented in relational database applications
- Data Binding - Syncronises data between UI components which are bound to the data source
- Declarative Programming seeks to make you coding more descriptive by using techniques to show what is done rather than how is done. This is opposed to Imperative Programming.
- Dependency Injection(DI) is a software design pattern that deals with providing the dependencies that an object needs instead of having it construct them itself. AngularJS utilizes this pattern.
- Document-oriented Database – A collection of independent documents. E.g CouchDB, MongoDB
- DOM - Document Object Model
- DRY(Don't Repeat Yourself) is a principle of software development aimed at reducing repetition of information of all kinds, by making components reuseable.
- Emmet - a plugin for popular text editors which speed of HTML authoring using CSS like abreviations.
- Explicit Iteration vs Implicit Iteration - In jQuery:

```javascript
// Explicit iteration with the jQuery .each() method
$( "li" ).each(function() {
    $(this).addClass( "foo" );
});
// jQuery Implicit Iteration
    $( "li" ).addClass( "bar" );
```

- Expression - Something which evaluates to a value. Example: 1+2/x
- Encapsulation is a feature of OOP, that allows for separation of an objects implementation and its interface by defining its variables an methods as either public or private.
- Falsy - Term for a value which returns 'false' although not nessaarily of boolean type when using Equal/Not Equal operands. i.e. In JavaScript null,false,"",undefined and 0 are Falsy while all other values including Objects are Truthy, So '1 == true' would return true
- Functional Programming
- Graceful Degradation - Follows a top down approach to dealing with features and performance, building with latest technologies first then applying fallbacks for technologies that don't support the features used. 
- Grunt is a framework to build, run and test your project. It can process/minify/combine the likes of Less,Sass,JS,HAML,Markdown,CoffeeScript etc create a test enviroment and create a webserver to view your project on.
- Hash Table - 
- Hoisting - In JavaScript no matter where you declare a variable, its declaration is added to the top of its scope(function) this means JavaScript Scope is different to most other languages that use Block Level Scope inwhich new scope is created within any curly brakets('{}')
- IDE – Integrated Development Enviroment is a software application that provides computer programmers with a facility to edit, debug and/or compile source code.
- JSON - Stands for JavaScript Object Notation.
- Loose Coupling - Coupling measures the degree to which program modules rely on other modules. Loose coupling implies each component can operate or be tested independently of other components.
- Loosely Typed - Describes a programming language whereby it is not necessary to create a variable with a type as apposed to Strongly Typed e.g JavaScript.
- Markdown - A text to HTML conversion tool to simplify and speed up creating structurally valid XHTML text content for websites. http://daringfireball.net/projects/markdown/
 
```HTML
Header 1 Title
===========
- bullet point

Will be converted to:

<h1>Header 1 Title</h1>
<li>bullet point</li>
```


- Minification - Removes comments and white space to reduce the file size.
- MVC stands for Model View Controller which creates a structure of seperation in an application, the Model being the data, the View the presentation layer and the controller which acts as the glue between the Model & View manipulating Data and recording Events.
- MVVM stands for Model View ViewModel based on the MVC(Model View Controller) pattern, the difference being the ViewModel is more separated from the Data so that its commands can function without having to know where the data is coming from.
- MVW stands for Model View Whatever termed to avoid developers arguing over which category MV* Frameworks fall over.
- Obfuscation - Takes minifying JS a step further by shortening variable and function names. But can introduce bugs if not done properly.
- Parsing - Taking raw data and converting into a formal data structure.
- Primitive Data Type - A data type that can hold only single value i.e. no properties. In JS Primitive Data Types are Number, String, Boolean, null & undefined whereas Objects & Functions can have properties i.e. var a = {"a":1,"b":2}
- Progressive Enhancement – Uses a bottom up approach to development, aiming to meet a minium requirements then enhancing for more modern technologies.
- Prototypal Inheritance - In JavaScript Objects are inherited from other Objects using the 'new' operator, there is no distinguising between a object & the object it inherits from as opposed to a class based language.
- Relational Database – built on tables, fields & keys e.g MySQL, SQL Server.
- Race Condition - Are issues that arise when software depends on specific timing of threads to be functional i.e. When an AJAX request a seperate thread is created.
- REST – REpresentational State Transfer is a Web service design model, conforming to REST constraits is considered RESTful. REST is Resource based rather than Action based as opposed to SOAP. T
- Same Origin Policy - An important security concept used to stop Client-side programming languages accessing methods and properties across different hostnames.
- Sass - Preproccessor for CSS, which allow you to use Variables, Functions & Calcutions, their are 2 formats the standard .Sass format and the more widely used .Scss format.
- Semantic HTML - The use of HTML markup(tags & properties) to give meaning to the information displayed rather than just defining its presentation i.e. rather than &lt;i&gt;Yes&lt;i&gt; use "&lt;em&gt;Yes&lt;em&gt;"(emphasis) or "&lt;span class='emphasis'&gt;Yes&lt;span&gt;"
- SHA - Secure Hash Algorithm
- SOAP - Simple Object Access Protocol
- Software Development Methology - is a framework for structuring planning, controlling a software project. 
- SPA - Single Page Application or Single-page interface (SPI). The majority of HTML/CSS & JS is obtained in a single page with the goal of providing a more fluid experience akin to a desktop application.
- SDK – Software Development Kit is a toolkit to allow software development on a specific framework or platform.
- SSH - Secure Shell - is a network protocol for secure communication over an insecure network.
- Statement - A line of code which does something. Example: GOTO 100. An Expression is a Statement but a Statement is not necessarily an Expression.
- Strongly Typed - Describes a programming language that requires a variable be assigned a type as apposed to Loosely Typed and throws a type error when values of different types a evaluated.
- Surface Web - the World Wide Web that is indexable by conventional search engines as opposed to the Deep Web with is not reachable by conventional search engines.
- SVG - Scalable Vector Graphics - is a XML based vector graphics format with some support for interactivity and animations
- Two Way Data Binding - A feature of Silverlight & many MV* JS frameworks where changes by the user in the DOM are reflected in the JS model & changes to the model update the DOM seemlessly.
- URI - Uniform Resource Identifier
- User Experience(UX) - User Experience is a broader which is inclusive yet distinct from the User Interface as it encompasses the way a person feels about using a product, system or service.
- User Interface(UI) - The User Interface are the components which users interact with.
