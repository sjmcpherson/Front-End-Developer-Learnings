##Abbreviations/Terms:
------------------
<dl>
  <dt>
    Abstraction
  </dt>
  <dd>
    A process of structuring code to be more readable by making functions shorter and code reuseable. Object-Oriented Programming is an approach to Abstraction.
  </dd>
  <dt>
    API
  </dt>
  <dd>
    Application Programming Interface is a specification for combining software components.
  </dd>
  <dt>
    AJAX
  </dt>
  <dd>
    an acronym for Asynchronous JavaScript and XML. Despite the name, the use of XML is not required as JSON is often used instead. With AJAX, web applications can send data, and retrieve data from, a server asynchronously (in the background therefore creating a new code thread) without interfering with the display and behavior of the existing page.
  </dd>
  <dt>
    Associative Array
  </dt>
  <dd>
    Abstract data type composed of a collection of key/value pairs. Objects are Associative Arrays in JavaScript
  </dd>
  <dt>
    Asynchronous vs Synchronous
  </dt>
  <dd>
    Asynchronouse permits other processing to continue while a transmission is being processed.
  </dd>
  <dt>
    Atom
  </dt>
  <dd>
    Building apone RSS, Atom is a XML language used for web feeds.
  </dd>
  <dt>
    Bower
  </dt>
  <dd>
    A front-end package management system that runs on Node.js & npm
  </dd>
  <dt>
    CDN
  </dt>
  <dd>
    Content Delivery Network is a large distributed system of servers hosting content with high availability and download speeds.
  </dd>
  <dt>
    CGI
  </dt>
  <dd>
    Common Gateway Interface is the standard method for server-side communication when transfering information between the web server & browser. 
  </dd>
  <dt>
    Closure
  </dt>
  <dd>
    A term used when you nest functions, as inner functions can refer to the variables present in their outer enclosing functions even after their parent functions have already executed. https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Closures, http://jsfiddle.net/sjmcpherso/ByJfv/ 
  </dd>
  <dt>
    Concatenation
  </dt>
  
  <dt>
    CRUD
  </dt>
  <dd>
    Create, Read, Update, Delete (Also BREAD - Browse, Read, Edit, Add, Delete) The major functions that are implemented in relational database applications
  </dd>
  <dt>
    Data Binding
  </dt>
  <dd>
    Syncronises data between UI components which are bound to the data source
  </dd>
  <dt>
    Declarative Programming
  </dt>
  <dd>
    seeks to make you coding more descriptive by using techniques to show what is done rather than how is done. This is opposed to Imperative Programming.
  </dd>
  <dt>
    Dependency Injection(DI)
  </dt>
  <dd>
    is a software design pattern that deals with providing the dependencies that an object needs instead of having it construct them itself. AngularJS utilizes this pattern.
  </dd>
  <dt>
    Dirty Checking
  </dt>
  
  <dt>
    Document-oriented Database
  </dt>
  <dd>
    A collection of independent documents. E.g CouchDB, MongoDB
  </dd>
  <dt>
    DOM - Document Object Model
  </dt>
  <dt>
    DRY(Don't Repeat Yourself)
  </dt>
  <dd>
    is a principle of software development aimed at reducing repetition of information of all kinds, by making components reuseable.
  </dd>
  <dt>
    Emmet
  </dt>
  <dd>
    a plugin for popular text editors which speed of HTML authoring using CSS like abreviations.
  </dd>
  <dt>
    Explicit Iteration vs Implicit Iteration
  </dt>
  <dd>
    In jQuery:
  </dd>
  
  ```javascript
  // Explicit iteration with the jQuery .each() method
  $( "li" ).each(function() {
  $(this).addClass( "foo" );
  });
  // jQuery Implicit Iteration
  $( "li" ).addClass( "bar" );
  ```
  
  <dt>
    Expression
  </dt>
  <dd>
    Something which evaluates to a value. Example: 1+2/x
  </dd>
  <dt>
    Encapsulation
  </dt>
  <dd>
    is a feature of OOP, that allows for separation of an objects implementation and its interface by defining its variables an methods as either public or private.
  </dd>
  <dt>
    Epoch
  </dt>
  <dd>
    The "epoch" then serves as a reference point from which time is measured. In most systems/languages this is 01 January 1970 00:00:00 UTC, the most notable exception is Apple's Cocoa(NSDate) which is from 2001
  </dd>
  <dt>
    Falsy
  </dt>
  <dd>
    Term for a value which returns 'false' although not nessaarily of boolean type when using Equal/Not Equal operands. i.e. In JavaScript null,false,"",undefined and 0 are Falsy while all other values including Objects are Truthy, So '1 == true' would return true
  </dd>
  <dt>
    ESI
  </dt>
  <dd>
    Edge Side Includes
  </dd>
  <dt>
    FastCGI
  </dt>
  <dd>
    A system whereby CGI (Common Gateway Interface) programs stay in memory rather than being spawned as individual process when requested. This makes for much better efficiency. 
  </dd>
  <dt>
    Functional Programming
  </dt>
  <dt>
    Graceful Degradation
  </dt>
  <dd>
    Follows a top down approach to dealing with features and performance, building with latest technologies first then applying fallbacks for technologies that don't support the features used. 
  </dd>
  <dt>
    Grunt
  </dt>
  <dd>
    is a framework to build, run and test your project. It can process/minify/combine the likes of Less,Sass,JS,HAML,Markdown,CoffeeScript etc create a test enviroment and create a webserver to view your project on.
  </dd>
  <dt>
    Hash Table
  </dt>
  <dt>
    Hoisting
  </dt>
  <dd>
    In JavaScript no matter where you declare a variable, its declaration is added to the top of its scope(function) this means JavaScript Scope is different to most other languages that use Block Level Scope inwhich new scope is created within any curly brakets('{}')
  </dd>
  <dt>
    IDE
  </dt>
  <dd>
    Integrated Development Enviroment is a software application that provides computer programmers with a facility to edit, debug and/or compile source code.
  </dd>
  <dt>
    Immediately-Invoked Function Expression (IIFE)
  </dt>
  <dt>
    JSON 
  </dt>
  <dd>
    Stands for JavaScript Object Notation.
  </dd>
  <dt>
    Loose Coupling
  </dt>
  <dd>
    Coupling measures the degree to which program modules rely on other modules. Loose coupling implies each component can operate or be tested independently of other components.
  </dd>
  <dt>
    Loosely Typed
  </dt>
  <dd>
    Describes a programming language whereby it is not necessary to create a variable with a type as apposed to Strongly Typed e.g JavaScript.
  </dd>
  <dt>
    Markdown
  </dt>
  <dd>
    A text to HTML conversion tool to simplify and speed up creating structurally valid XHTML text content for websites. http://daringfireball.net/projects/markdown/

  ```HTML
  Header 1 Title
  ===========
  - bullet point
  
  Will be converted to:
  <h1>Header 1 Title</h1>
  <li>bullet point</li>
  ```
  
  </dd>
  <dt>
    Minification
  </dt>
  <dd>
    Removes comments and white space to reduce the file size.
  </dd>
  <dt>
    MVC
  </dt>
  <dd>
    stands for Model View Controller which creates a structure of seperation in an application, the Model being the data, the View the presentation layer and the controller which acts as the glue between the Model & View manipulating Data and recording Events.
  </dd>
  <dt>
    MVVM
  </dt>
  <dd>
    stands for Model View ViewModel based on the MVC(Model View Controller) pattern, the difference being the ViewModel is more separated from the Data so that its commands can function without having to know where the data is coming from.
  </dd>
  <dt>
    MVW
  </dt>
  <dd>
    stands for Model View Whatever termed to avoid developers arguing over which category MV* Frameworks fall over.
  </dd>
  <dt>
    Obfuscation
  </dt>
  <dd>
    Takes minifying JS a step further by shortening variable and function names. But can introduce bugs if not done properly.
  </dd>
  <dt>
    OAuth
  </dt>
  <dd>
    is a open standard for authorization to server resources for client applications. It provides a process for end users to authorize third-party access without needing to share their credentials. OAuth is commonly used as a way for users to log into third party web sites using their Google, Facebook or Twitter passwords, without worrying about their access credentials being compromised.
  </dd>
  <dt>
    Parsing
  </dt>
  <dd>
    Taking raw data and converting into a formal data structure.
  </dd>
  <dt>
    Primitive Data Type
  </dt>
  <dd>
    A data type that can hold only single value i.e. no properties. In JS Primitive Data Types are Number, String, Boolean, null & undefined whereas Objects & Functions can have properties i.e. var a = {"a":1,"b":2}
  </dd>
  <dt>
    Progressive Enhancement
  </dt>
  <dd>
    Uses a bottom up approach to development, aiming to meet a minium requirements then enhancing for more modern technologies.
  </dd>
  <dt>
    Prototypal Inheritance
  </dt>
  <dd>
    In JavaScript Objects are inherited from other Objects using the 'new' operator, there is no distinguising between a object & the object it inherits from as opposed to a class based language.
  </dd>
  
  <dt>
    Relational Database
  </dt>
  <dd>
    built on tables, fields & keys e.g MySQL, SQL Server.
  </dd>
  <dt>
    Race Condition
  </dt>
  <dd>
    Are issues that arise when software depends on specific timing of threads to be functional i.e. When an AJAX request a seperate thread is created.
  </dd>
  <dt>
    REST (REpresentational State Transfer)
  </dt>
  <dd>
    is a Web service design model, conforming to REST constraits is considered RESTful. REST is Resource based rather than Action based as opposed to SOAP. 
  </dd>
  <dt>
    Rich Object Model
  </dt>
  <dt>
    Same Origin Policy
  </dt>
  <dd>
    An important security concept used to stop Client-side programming languages accessing methods and properties across different hostnames.
  </dd>
  <dt>
    Sass
  </dt>
  <dd>
    Preproccessor for CSS, which allow you to use Variables, Functions & Calcutions, their are 2 formats the standard .Sass format and the more widely used .Scss format.
  </dd>
  <dt>
    Semantic HTML
  </dt>
  <dd>
    The use of HTML markup(tags & properties) to give meaning to the information displayed rather than just defining its presentation i.e. rather than &lt;i&gt;Yes&lt;i&gt; use "&lt;em&gt;Yes&lt;em&gt;"(emphasis) or "&lt;span class='emphasis'&gt;Yes&lt;span&gt;"
  </dd>
  <dt>
    SHA
  </dt>
  <dd>
    Secure Hash Algorithm
  </dd>
  <dt>
    Shadow DOM
  </dt>
  <dt>
    Singleton
  </dt>
  <dd>
    A programming design pattern which limits the number of instances of a particular object to just one.
  </dd>
  <dt>
    SOAP
  </dt>
  <dd>
    Simple Object Access Protocol
  </dd>
  <dt>
    Software Development Methology
  </dt>
  <dd>
    is a framework for structuring planning, controlling a software project. 
  </dd>
  <dt>
    SPA
  </dt>
  <dd>
    Single Page Application or Single-page interface (SPI). The majority of HTML/CSS & JS is obtained in a single page with the goal of providing a more fluid experience akin to a desktop application.
  </dd>
  <dt>
    SDK
  </dt>
  <dd>
    Software Development Kit is a toolkit to allow software development on a specific framework or platform.
  </dd>
  <dt>
    SSL
  </dt>
  <dd>
    Secure Sockets Layer - a internet protocol for secure communication.
  </dd>
  <dt>
    SSH
  </dt>
  <dd>
    Secure Shell - is a network protocol for secure communication over an insecure network.
  </dd>
  <dt>
    Statement
  </dt>
  <dd>
    A line of code which does something. Example: GOTO 100. An Expression is a Statement but a Statement is not necessarily an Expression.
  </dd>
  <dt>
    Strongly Typed
  </dt>
  <dd>
    Describes a programming language that requires a variable be assigned a type as apposed to Loosely Typed and throws a type error when values of different types a evaluated.
  </dd>
  <dt>
    Surface Web
  </dt>
  <dd>
    the World Wide Web that is indexable by conventional search engines as opposed to the Deep Web with is not reachable by conventional search engines.
  </dd>
  <dt>
    SVG (Scalable Vector Graphics)
  </dt>
  <dd>
    is a XML based vector graphics format with some support for interactivity and animations
  </dd>
  <dt>
    Stylus
  </dt>
  <dd>
    Another CSS preprocessor which brackets, colons, and semi-colons are all optional. Uses the .styl file extension
  </dd>
  <dt>
    Two Way Data Binding
  </dt>
  <dd>
    A feature of Silverlight & many MV* JS frameworks where changes by the user in the DOM are reflected in the JS model & changes to the model update the DOM seemlessly.
  </dd>
  <dt>
    URI
  </dt>
  <dd>
    Uniform Resource Identifier
  </dd>
  <dt>
    User Experience(UX)
  </dt>
  <dd>
    User Experience is a broader which is inclusive yet distinct from the User Interface as it encompasses the way a person feels about using a product, system or service.
  </dd>
  <dt>
    User Interface(UI)
  </dt>
  <dd>
    The User Interface are the components which users interact with.
  </dd>
  
</dl>
