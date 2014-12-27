##Abbreviations/Terms:
------------------
###A
 - <strong>Abstraction</strong> - A process of structuring code to be more readable by making functions shorter and code reuseable. Object-Oriented Programming is an approach to Abstraction.
 - <strong>API</strong> - Application Programming Interface is a specification for combining software components.
 - <strong>AJAX</strong> - an acronym for Asynchronous JavaScript and XML. Despite the name, the use of XML is not required as JSON is often used instead. With AJAX, web applications can send data, and retrieve data from, a server asynchronously (in the background therefore creating a new code thread) without interfering with the display and behavior of the existing page.
 - <strong>Associative Array</strong> - Abstract data type composed of a collection of key/value pairs. Objects are Associative Arrays in JavaScript
 - <strong>Asynchronous vs Synchronous</strong> - Asynchronouse permits other processing to continue while a transmission is being processed.
 - <strong>Atom</strong> - Building apone RSS, Atom is a XML language used for web feeds.

###B
 - <strong>Bower</strong> - A front-end package management system that runs on Node.js & npm

###C
 - <strong>CDN</strong> - Content Delivery Network is a large distributed system of servers hosting content with high availability and download speeds.
 - <strong>CGI</strong> - Common Gateway Interface is the standard method for server-side communication when transfering information between the web server & browser. 
 - <strong>Closure</strong> - A term used when you nest functions, as inner functions can refer to the variables present in their outer enclosing functions even after their parent functions have already executed. https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Closures, http://jsfiddle.net/sjmcpherso/ByJfv/ 
 - <strong>Concatenation</strong> - 
 - <strong>CRUD</strong> - Create, Read, Update, Delete (Also BREAD<strong>Browse, Read, Edit, Add, Delete) The major functions that are implemented in relational database applications

###D
 - <strong>Data Binding</strong> - Syncronises data between UI components which are bound to the data source
 - <strong>Declarative Programming</strong> - seeks to make you coding more descriptive by using techniques to show what is done rather than how is done. This is opposed to Imperative Programming.
 - <strong>Dependency Injection(DI)</strong> - is a software design pattern that deals with providing the dependencies that an object needs instead of having it construct them itself. AngularJS utilizes this pattern.
 - <strong>Dirty Checking</strong> - 
 - <strong>Document-oriented Database</strong> - A collection of independent documents. E.g CouchDB, MongoDB
 - <strong>DOM<strong>Document Object Model</strong> - 
 - <strong>DRY(Don't Repeat Yourself)</strong> - is a principle of software development aimed at reducing repetition of information of all kinds, by making components reuseable.

###E
 - <strong>Emmet</strong> - a plugin for popular text editors which speed of HTML authoring using CSS like abreviations.
 - <strong>Encapsulation</strong> - is a feature of OOP, that allows for separation of an objects implementation and its interface by defining its variables an methods as either public or private.
 - <strong>Epoch</strong> - The "epoch" then serves as a reference point from which time is measured. In most systems/languages this is 01 January 1970 00:00:00 UTC, the most notable exception is Apple's Cocoa(NSDate) which is from 2001
 - <strong>ESI (Edge Side Includes)</strong> - 
 - <strong>Explicit Iteration vs Implicit Iteration</strong> - In jQuery:
  
  ```javascript
  // Explicit iteration with the jQuery .each() method
  $( "li" ).each(function() {
  $(this).addClass( "foo" );
  });
  // jQuery Implicit Iteration
  $( "li" ).addClass( "bar" );
  ```
  - <strong>Expression</strong> - Something which evaluates to a value. Example: 1+2/x

###F
 - <strong>Falsy</strong> - Term for a value which returns 'false' although not nessaarily of boolean type when using Equal/Not Equal operands. i.e. In JavaScript null,false,"",undefined and 0 are Falsy while all other values including Objects are Truthy, So '1 == true' would return true
 - <strong>FastCGI</strong> - A system whereby CGI (Common Gateway Interface) programs stay in memory rather than being spawned as individual process when requested. This makes for much better efficiency. 
 - <strong>Functional Programming</strong> - 

###G
 - <strong>Graceful Degradation</strong> - Follows a top down approach to dealing with features and performance, building with latest technologies first then applying fallbacks for technologies that don't support the features used. 
 - <strong>Grunt</strong> - is a framework to build, run and test your project. It can process/minify/combine the likes of Less,Sass,JS,HAML,Markdown,CoffeeScript etc create a test enviroment and create a webserver to view your project on.

###H
 - <strong>Hash Table</strong> - 
 - <strong>Hoisting</strong> - In JavaScript no matter where you declare a variable, its declaration is added to the top of its scope(function) this means JavaScript Scope is different to most other languages that use Block Level Scope inwhich new scope is created within any curly brakets('{}')

###I
 - <strong>IDE</strong> - Integrated Development Enviroment is a software application that provides computer programmers with a facility to edit, debug and/or compile source code.
 - <strong>Immediately-Invoked Function Expression (IIFE)</strong> - 

###J
 - <strong>JSON</strong> - Stands for JavaScript Object Notation.

###L
 - <strong>Loose Coupling</strong> - Coupling measures the degree to which program modules rely on other modules. Loose coupling implies each component can operate or be tested independently of other components.
 - <strong>Loosely Typed</strong> - Describes a programming language whereby it is not necessary to create a variable with a type as apposed to Strongly Typed e.g JavaScript.

###M
 - <strong>Markdown</strong> - A text to HTML conversion tool to simplify and speed up creating structurally valid XHTML text content for websites. http://daringfireball.net/projects/markdown/
  
```HTML
  Header 1 Title
  ===========
  - bullet point  
Will be converted to:  
  <h1>Header 1 Title</h1>
  <li>bullet point</li>
```

 - <strong>Minification</strong> - Removes comments and white space to reduce the file size.
 - <strong>MVC</strong> - stands for Model View Controller which creates a structure of seperation in an application, the Model being the data, the View the presentation layer and the controller which acts as the glue between the Model & View manipulating Data and recording Events.
 - <strong>MVVM</strong> - stands for Model View ViewModel based on the MVC(Model View Controller) pattern, the difference being the ViewModel is more separated from the Data so that its commands can function without having to know where the data is coming from.
 - <strong>MVW</strong> - stands for Model View Whatever termed to avoid developers arguing over which category MV* Frameworks fall over.

###O
 - <strong>Obfuscation</strong> - Takes minifying JS a step further by shortening variable and function names. But can introduce bugs if not done properly.
 - <strong>OAuth</strong> - is a open standard for authorization to server resources for client applications. It provides a process for end users to authorize third-party access without needing to share their credentials. OAuth is commonly used as a way for users to log into third party web sites using their Google, Facebook or Twitter passwords, without worrying about their access credentials being compromised.

###P
 - <strong>Parsing</strong> - Taking raw data and converting into a formal data structure.
 - <strong>Primitive Data Type</strong> - A data type that can hold only single value i.e. no properties. In JS Primitive Data Types are Number, String, Boolean, null & undefined whereas Objects & Functions can have properties i.e. var a = {"a":1,"b":2}
 - <strong>Progressive Enhancement</strong> - Uses a bottom up approach to development, aiming to meet a minium requirements then enhancing for more modern technologies.
 - <strong>Prototypal Inheritance</strong> - In JavaScript Objects are inherited from other Objects using the 'new' operator, there is no distinguising between a object & the object it inherits from as opposed to a class based language.

###R
 - <strong>Race Condition</strong> - Are issues that arise when software depends on specific timing of threads to be functional i.e. When an AJAX request a seperate thread is created.
 - <strong>Relational Database</strong> - built on tables, fields & keys e.g MySQL, SQL Server.
 - <strong>REST (REpresentational State Transfer)</strong> - is a Web service design model, conforming to REST constraits is considered RESTful. REST is Resource based rather than Action based as opposed to SOAP. 
 - <strong>Rich Object Model</strong> - 

###S
 - <strong>Same Origin Policy</strong> - An important security concept used to stop Client-side programming languages accessing methods and properties across different hostnames.
 - <strong>Sass</strong> - Preproccessor for CSS, which allow you to use Variables, Functions & Calcutions, their are 2 formats the standard .Sass format and the more widely used .Scss format.
 - <strong>Semantic HTML</strong> - The use of HTML markup(tags & properties) to give meaning to the information displayed rather than just defining its presentation i.e. rather than &lt;i&gt;Yes&lt;i&gt; use "&lt;em&gt;Yes&lt;em&gt;"(emphasis) or "&lt;span class='emphasis'&gt;Yes&lt;span&gt;"
 - <strong>SHA (Secure Hash Algorithm)</strong> - 
 - <strong>Shadow DOM</strong> - 
 - <strong>Singleton</strong> - A programming design pattern which limits the number of instances of a particular object to just one.
 - <strong>SOAP (Simple Object Access Protocol)</strong> - 
 - <strong>Software Development Methology</strong> - is a ideology for structuring planning, controlling a software project. 
 - <strong>SPA Single Page Application or Single-page interface (SPI)</strong> - The majority of HTML/CSS & JS is obtained in a single page with the goal of providing a more fluid experience akin to a desktop application.
 - <strong>SDK</strong> - Software Development Kit is a toolkit to allow software development on a specific framework or platform.
 - <strong>SSL (Secure Sockets Layer)</strong> - a internet protocol for secure communication.
 - <strong>SSH (Secure Shell)</strong> - is a network protocol for secure communication over an insecure network.
 - <strong>Statement</strong> - A line of code which does something. Example: GOTO 100. An Expression is a Statement but a Statement is not necessarily an Expression.
 - <strong>Strongly Typed</strong> - Describes a programming language that requires a variable be assigned a type as apposed to Loosely Typed and throws a type error when values of different types a evaluated.
 - <strong>Surface Web</strong> - the World Wide Web that is indexable by conventional search engines as opposed to the Deep Web with is not reachable by conventional search engines.
 - <strong>SVG (Scalable Vector Graphics)</strong> - is a XML based vector graphics format with some support for interactivity and animations
 - <strong>Stylus</strong> - Another CSS preprocessor which brackets, colons, and semi-colons are all optional. Uses the .styl file extension

###T
 - <strong>Two Way Data Binding</strong> - A feature of Silverlight & many MV* JS frameworks where changes by the user in the DOM are reflected in the JS model & changes to the model update the DOM seemlessly.

###U
 - <strong>URI (Uniform Resource Identifier) </strong> - 
 - <strong>User Experience(UX)</strong> - User Experience is a broader which is inclusive yet distinct from the User Interface as it encompasses the way a person feels about using a product, system or service.
 - <strong>User Interface(UI)</strong> - The User Interface are the components which users interact with.

