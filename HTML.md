<h2>HTML Coding Tips</h2>

 - HTML5 Doctype &lt;!doctype html&gt;
 - Doctype must be first on page or IE will revert to Quirks Mode
 - In HTML4, there are 2 types of elements: Block and Inline. HTML5 emphasizes semantics and structure, so it has organized its elements into the categories of metadata, flow, sectioning, heading, phrasing, interactive & embedded
 - The Protocol-relative URL &lt;img src="//domain.com/img/logo.png"&gt; Note: Avoid using protocol relative URLs for stylesheets as IE7 & 8 will download the file twice. For More Info http://paulirish.com/2010/the-protocol-relative-url/
 - HTML5 Inputs with graceful degredation: type=search, email, url, number, and tel
 - Use input[placeholder] with IE&lt;10 polyfill fallback jquery-placeholder.js
 - &lt;meter value="2" min="0" max="10"&gt;2 out of 10&lt;/meter&gt; tag defines a measurement within a known range, or a fractional value.
 - The "download" attribute forces browser to invoke download dialog &lt;a href="logo.png" download="Logo.png"&gt;download me&lt;/a&gt; Chrome Only
 - &lt;datalist&gt; Databinding Autocomplete. IE10+, No Safari support. Example:

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
 - WebP is a new image format developed by Google, superior to PNG and JPG. It produces 24-35% lossy & lossless images, browser support is limited to Chrome, Opera & Android but can be added with a JavaScript shim.
 - HAML (HTML Abstraction Markup Language) is a lightweight markup language. Example:

```HTML
  %body
    #header
      %h1 BoBlog
```
Would Produce:
```HTML
  <body>
    <div id='header'>
      <h1>BoBlog</h1>
    </div>
```

- The recommened viewport setting for responsive design '<meta name="viewport" content="width=device-width">' this allows the user to zoom.
- To disable zooming use '<meta name="viewport" content="maximum-scale=1">' this would be recommend for a Mobile Web App.
- Alternatively to disable a responsive design use '<meta name="viewport" content="width=1200">' the width being the size of your outer container.
- The attribute contenteditable="true" used to allow text elements the abilty to be typed into like a textbox e.g. http://jsfiddle.net/sjmcpherso/q3kWw/. Similarly the CSS attribute -user-input can be use to replicate but with limited support.
- CDATA witten in HTML as <![CDATA[]]> is a section of element content that is marked for the parser to interpret as only character data, not markup i.e. Like a comment although is still part of the document and therefore can be read from JS.
- Cookies vs sessionStorage vs localStorage - Cookies are for storing small amounts of website data, such as a username. HTML5 Web Storage is a faster and larger method created by the browser, sessionsStorage expires after the browser window closes, and localStorage is for persistant data.
- Application Cache (AppCache) 
- Web Components a collection standards (like HTML imports) in development for allowing encapsulation of HTML, CSS & JS into custom HTML tags. 

```HTML
  <link rel="import" href="import.html">
```


<h2>SEO Optimization</h2>
- Include descriptive terms to your URLs and create a easily to understand hierarchy, i.e. List of Products at “www.yoursite.com/products/” individual products at “www.yoursite.com/products/descriptive-product-name/”
- Make use of header tag. h1,h2,h3,h4,h5 tags to emphasize important text but use sparingly across the page.
- Place links on descriptive wording rather than text such as "Click Here" and load the Title attribute with info about the link i.e

```HTML
To read our View our website, click <a href="http://www.instantshift.com">here</a>. <!- Not terrible ->
  
Visit <a href="http://www.smashdynamic.com" title="Visit Smash Dynamic magazine, Web Development">Smash Dynamic, web design & development specialists</a>. <!- Much better ->
```

- When using images add a description to the “Alt” tag of the image markup.
- Create unique meta title tags for each page which are brief but descriptive (info on Meta Tags here) https://support.google.com/webmasters/answer/79812?hl=en&ref_topic=2371375
- Include important keywords in your text but don’t overdo it as Google will see this as content manipulation. And of course you should always be thinking of your audience not just your page ranking.
- You may find the need to abreviate important terms to make you content more concise use the 'abbr' tag to get the best of both worlds i.e. <abbr title="Front End Developer">FED</abbr>
- Use the Microdata specification to add metadata to content i.e
```HTML
<section itemscope itemtype="http://schema.org/Person"> 
        Hello, my name is 
        <span itemprop="name">John Doe</span>, 
        I am a 
        <span itemprop="jobTitle">graduate research assistant</span> 
        at the 
        <span itemprop="affiliation">University of Dreams</span>. 
        My friends call me 
        <span itemprop="additionalName">Johnny</span>. 
        You can visit my homepage at 
        <a href="http://www.JohnnyD.com" itemprop="url">www.JohnnyD.com</a>. 
        <section itemprop="address" itemscope itemtype="http://schema.org/PostalAddress">
                I live at 
                <span itemprop="streetAddress">1234 Peach Drive</span>,
                <span itemprop="addressLocality">Warner Robins</span>,
                <span itemprop="addressRegion">Georgia</span>.
       </section>
</section>
```

<h2>HTML Performance Tips</h2>
 - Reduce unecessary html tags to improve performance
 - Reduce the total number of referenced files to css, js & images by using image sprites and combining CSS & JavaScript. HTTP Requests add to the download time and browsers limit the number of concurrent downloads per host to between 2-8. For individual browser limitations see http://www.browserscope.org/?category=network
 - Use dispersed servers for referenced files such as css, js & images,  in most circumstances this leads to quicker download speeds.
 - For common libraries use a popular CDN(such as //ajax.googleapis.com/ajax/libs/jquery/1.9.1/jquery.min.js) to enhance the chance the user has the file cached.
 - Putting stylesheets in the &lt;head&gt; allows the page to render progressively.
 - To give more control and to speed up loading time of Web Fonts use Web Font Loader, Fonts provided by Typekit, FontDeck and Google can be loaded through the script, for best performance embed the script directly after head tag and to remove FOUT add CSS for the class ".wf-loading" on the HTML element to hide text e.g. *.wf-loading{opacity(0)} the script then removes this class once fonts are loaded. https://developers.google.com/fonts/docs/webfont_loader
 - Place Google Analytics code at bottom even though Google recommends placing in the head, as pageviews will be tracked even if they leave the page before fully loaded also keeps the all the scripts together.
 - Use Link Prefetching (limited browser support) to preload whole pages or just images, css etc.

```HTML
<!-- full page -->
<link rel="prefetch" href="http://davidwalsh.name/css-enhancements-user-experience" />
<!-- just an image -->
<link rel="prefetch" href="http://davidwalsh.name/wp-content/themes/walshbook3/images/sprite.png" />
```

- Compress Your Images - Photoshop does a fairly decent job at optimizing images but their are other tools that can take you files and compress them even further. Yahoo's www.smushit.com does a good job with PNG's & GIF's & theres also FileOptimizer a Desktop app that compresses images and a number of other file formats.
