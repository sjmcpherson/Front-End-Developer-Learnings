<h2>HTML Coding Tips</h2>


 - HTML5 Doctype &lt;!DOCTYPE html&gt;
 - Doctype must be first on page or IE will revert to Quirks Mode (Dreamweaver Templates can mess with this)
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
 - WebP is a new image format developed by Google, superior to PNG and JPG. It produces 24-35% lossy & lossless images, browser support is limited, but can be added with a JavaScript shim.
 - Haml (HTML Abstraction Markup Language) is a lightweight markup language. Example:  
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


<h2>HTML Performance Tips</h2>
 - Reduce unecessary html tags to improve performance
 - Reduce the total number of referenced files to css, js & images by using image sprites and combining CSS & JavaScript. HTTP Requests add to the download time and browsers limit the number of concurrent downloads per host to between 2-8. For individual browser limitations see http://www.browserscope.org/?category=network
 - Use dispersed servers for referenced files such as css, js & images,  in most circumstances this leads to quicker download speeds.
 - For common libraries use a popular CDN(such as //ajax.googleapis.com/ajax/libs/jquery/1.9.1/jquery.min.js) to enhance the chance the user has the file cached.
 - Putting stylesheets in the &lt;head&gt; allows the page to render progressively.
 - To give more control and to speed up loading time of Web Fonts use Web Font Loader, Fonts provided by Typekit, FontDeck and Google can be loaded through the script, for best performance embed the script directly after head tag and to remove FOUT add CSS for the class ".wf-loading" on the HTML element to hide text e.g. *.wf-loading{opacity(0)} the script then removes this class once fonts are loaded. https://developers.google.com/fonts/docs/webfont_loader
