<h2>Abbreviations/Terms:</h2>

- Abstraction - A process of structuring code to be more readable by making functions shorter and code reuseable. Object-Oriented Programming is an approach to Abstraction.
- API – Application Programming Interface is a specification for combining software components.
- AJAX an acronym for Asynchronous JavaScript and XML. Despite the name, the use of XML is not required as JSON is often used instead. With AJAX, web applications can send data, and retrieve data from, a server asynchronously (in the background therefore creating a new code thread) without interfering with the display and behavior of the existing page.
- Associative Array - abstract data type composed of a collection of  pairs, such that each 
- Asynchronous vs Synchronous, Asynchronouse permits other processing to continue while a transmission is being processed.
- CDN – Content Delivery Network is a large distributed system of servers hosting content with high availability and download speeds.
- CRUD - Create, Read, Update, Delete (Also BREAD - Browse, Read, Edit, Add, Delete) The major functions that are implemented in relational database applications
- Data Binding - Syncronises data between UI components which are bound to the data source
- Declarative Programming seeks to make you coding more descriptive by using techniques to show what is done rather than how is done. This is opposed to Imperative Programming.
- Dependency Injection(DI) is a software design pattern that deals with providing the dependencies that an object needs instead of having it construct them itself. AngularJS utilizes this pattern.
- Document-oriented Database – A collection of independent documents. E.g CouchDB, MongoDB
- DRY(Don't Repeat Yourself) is a principle of software development aimed at reducing repetition of information of all kinds, by making components reuseable.
- Explicit Iteration vs Implicit Iteration - In jQuery:
- Encapsulation is a feature of OOP, that allows for separation of an objects implementation and its interface by defining its variables an methods as either public or private.

```javascript
// Explicit iteration with the jQuery .each() method
$( "li" ).each(function() {
    $(this).addClass( "foo" );
});
// jQuery Implicit Iteration
    $( "li" ).addClass( "bar" );
```
- Falsy - Term for a value which returns 'false' although not nessaarily of boolean type when using Equal/Not Equal operands. i.e. In JavaScript null,false,"",undefined and 0 are Falsy while all other values including Objects are Truthy, So '1 == true' would return true
- Functional Programming
- Graceful Degradation - Follows a top down approach to dealing with features and performance, building with latest technologies first then applying fallbacks for technologies that don't support the features used. 
- Hash Table - 
- IDE – Integrated Development Enviroment is a software application that provides computer programmers with a facility to edit, debug and/or compile source code.
- Loose Coupling - Coupling measures the degree to which program modules rely on other modules. Loose coupling implies each component can operate or be tested independently of other components.
- Loosely Typed - Describes a programming language whereby it is not necessary to create a variable with a type as apposed to Strongly Typed e.g JavaScript
- MVC stands for Model View Controller
- MVVM stands for Model View ViewModel based on the MVC(Model View Controller) pattern, the difference being the ViewModel is more separated from the Data so that its commands can function without having to know where the data is coming from.
- MVW stands for Model View Whatever termed to avoid developers arguing over which category MV* Frameworks fall over.
- Progressive Enhancement – Uses a bottom up approach to development, aiming to meet a minium requirements then enhancing for more modern technologies.
- Relational Database – built on tables, fields & keys e.g MySQL, SQL Server.
- Race Condition - Are issues that arise when software depends on specific timing of threads to be functional i.e. When an AJAX request a seperate thread is created.
- REST – REpresentational State Transfer is a Web service design model, conforming to REST constraits is considered RESTful.
- Same Origin Policy - An important security concept used to stop Client-side programming languages accessing methods and properties across different hostnames.
- Semantic HTML - The use of HTML markup(tags & properties) to give meaning to the information displayed rather than just defining its presentation i.e. rather than "<i>Yes</i>" use "<em>Yes</em>"(emphasis) or "<span class='emphasis'>Yes</span>"
- SPA - Single Page Application or Single-page interface (SPI). The majority of HTML/CSS & JS is obtained in a single page with the goal of providing a more fluid experience akin to a desktop application.
- SDK – Software Development Kit is a toolkit to allow software development on a specific framework or platform.
- Strongly Typed - Describes a programming language that requires a variable be assigned a type as apposed to Loosely Typed and throws a type error when values of different types a evaluated.
- Surface Web - the World Wide Web that is indexable by conventional search engines as opposed to the Deep Web with is not reachable by conventional search engines.
- UI - User Interface are the components by which users interact with.
- UX - User Experience is a broader term which is distinct from UI as it encompasses the way a person feels about using a product, system or service.
