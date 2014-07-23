<h2>CSS Coding Tips</h2>

<h3>Advanced CSS Selectors</h3>
 - X:first-letter/:first-line IE6+ apply to block level elements compatible with all browser versions
 - ul > li{} IE7+ targets direct children
 - ul ~ p{} IE7+ targets p tags after ul tag in DOM
 - h1 + p{} IE7+ targets adjacent p tags directly after h1 tags
 - a[data-info~="image"]{} IE7+ selects all elements that have a data-info of “image” including multiple values such as  data-info="external image"
 - :first-child{} IE7+ targets the first child element
 - :last-child{} IE9+ targets the last child element
 - X[href^="http"] IE7+ You can use 'a[href$='index.html'] {color: green;}' to set the active navigation item in a menu.
 - :after{content:"more";} & :before{} IE8+ Allows you to add content before/after an element. CSS3 syntax is double colon "::" although this is not supported by IE8. Input elements are not supported.
 - X:nth-child(3) & X:nth-last-child(2) IE9+ 
 - X:nth-of-type(n) IE9+ rather than selecting a child, targets according to the type of element. Because of this targeting the type of element you will encounter issues when using a class as the selector.
 - :first-of-type & :last-of-type IE9+ i.e. .active:last-of-type{} Would select the element if it was the last-child and had the class 'active' Not what would be expect as the last element with the class 'active'.
 - X:not(selector) IE9+ targets all elements that don't match the selector i.e. div:not(#container) selects all divs that don't have a ID of "container".
 - :empty IE9+ targets elements with no children
 - :only-child IE9+ targets elements that are the only child of their parent

<h3>Uncommon CSS Properties</h3>
 - position: sticky - a new way to position elements and is conceptually similar to position: fixed. The difference is that an element with position: sticky behaves like position: relative within its parent, until a given offset threshold is met in the viewport. 
 - 'counter-increment' (IE8+) Used to display a incremented value, set & reset via the 'counter-reset' property. http://codepen.io/sjmcpherso/pen/eILwf

```CSS
h1 {counter-reset: section;}
h2:before {counter-increment: section;content: counter(section) ". ";}
```

 - 'image-set' (Safari 6+ and Chrome 21+ ONLY) Used to display High Pixel Resolution background images "background-image: image-set(url("test.png") 1x, url("test-2x.png") 2x);"
 - 'background-clip', 'background-origin' and 'background-size' IE9+
 - '-flex' The new Flexible Box layout Module for fluid layouts - http://html5-demos.appspot.com/static/css/flexbox/index.html IE10+ includes '-order': for ordering structure elements '-justify-content': for aligning structure elements horizontally, 'align-items' for vertical alignment  and '-webkit-flex-direction': for positioning 
 - '-column-count' Multi-column Wrapping Text layouts with "div{-column-count: 3;}" IE10+
 - '-calc' Dynamic css calculations "div{width: +calc(100% - 4em);}"
 - Box Sizing - 'box-sizing:border-box' (IE8+) forces the browser to render the box with the specific width & height, placing borders & padding inside of the box. Very helpful when working with 100% widths. Use the value 'content-box' to revert to the default setting.
 - CSS Regions - A specification that enables rich, magazine-like text column layouts that can resize based on the browser width although not perceived by most to be part of Responsive Web Design. IE10+ & Safari 6.1+ ONLY, Google has advised that it will not be adding support to Chrome in the forseable future due to performance. Article on the Limitations of CSS Regions http://alistapart.com/blog/post/css-regions-considered-harmful Article on Google dumping CSS Regions http://arstechnica.com/information-technology/2014/01/google-plans-to-dump-adobe-css-tech-to-make-blink-fast-not-rich/
 - Pointer Events - 'pointer-events:none' Disables mouse/touch events (hover, click, drag) including JS event listeners on an element. E.g Disable a semitransparent element with a higher Z-index so the element below is clicked. SVG IE9+, HTML Elements IE11+

<h4>Media Queries</h4>
 - 'max-width' - '@media screen and (max-width: 600px) {}' Will apply CSS if the viewing area is less than 600px.
 - 'min-width' - '@media screen and (min-width: 900px) {}' Will apply CSS if the viewing area is greater than 900px.
 - 'max-device-width' - '@media screen and (max-device-width: 480px) {}' Will apply CSS if the resolution is greater than 480px as max-device-width means the actual resolution of the device rather than just the viewing area resolution.
 - 'min-device-pixel-ratio' - '@media only screen and (min-device-pixel-ratio : 2){}' For 2x pixel density resolutions like the Retina display.
 - 'only' in '@media only screen..' stops older browsers parsing the remander of the selector

<h3>General Coding Tips</h3>
 - Its important when working in a team of developers on a project that they all abide to a similar syntax and format with their stylesheets, this is important specifically in large projects to keep stylesheets maintainable, readable and scalable. Often its important to agree on a CSS Guideline which states what file structure, preprocessor, font-sizing unit, spacing etc that should be adhered to. A very detailed one can be found here: https://github.com/csswizardry/CSS-Guidelines
 - Work around for lack of :nth-child support in IE7 & IE8 using adjacent selector: ul>li+li+li
 - HasLayout - The single most important thing you need to know about fixing bugs in <IE8, Giving an element "Layout" will fix 99% of IE rendering bugs, as if by magic. The other 1% will most likely be related to position: relative; or floats. Use "zoom: 1" as a trigger for whatever IE versions need it. Eg .ie6 #myElement, .ie7 #myElement { zoom: 1 }
 - If you're floating an inline element, it's treated as block, so no need to include "display:block" in your stylesheet.
 - Avoid using IDs as they decrease portability
 - IE7 fix for display:inline-block is "display:inline-block;*display: inline;zoom: 1;"
 - Backgrounds can be animated with @Keyframes and CSS Animations:

```CSS
@keyframes animatedBackground {
        to { background-position-x:100%;}
}
#animate-area	{ 
        width: 560px; 
        height: 400px; 
        background: url(bg-clouds.png) 0px 0px repeat-x;
        animation: animatedBackground 40s linear infinite;
}
```

<h3>Font size units</h3>
 - em - Calculates the font size based on the Parent font size which compounds down the tree
 
```CSS
html {font-size: 0.625em;}
ul { font-size: 2.4em; } /* =24px */
ul li  { font-size: 1em; } /* =24px */
ul li  { font-size: 1.05em; } /* =25px */
```

 - rem - Which stands for Root EM calculates the font size relative to the Root element
 
```CSS
html {font-size: 0.625rem;}
ul { font-size: 2.4rem; } /* =24px */
ul li { font-size: 1.4rem; } /* =14px */
```



i.e. html{font-size:62.5%}

 - px,pt,em,rem,%.


<h3>Font Rendering</h3>
 - http://webdesign.tutsplus.com/articles/a-web-designers-typographic-boilerplate--webdesign-15234?utm_content=buffer1e888&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer
 - http://aestheticallyloyal.com/public/optimize-legibility/
 - "font-weight:bold" is the same "font-weight:700" & "font-weight:normal" is the same as font-weight:normal" this is important when using webfonts which are downloaded at a specific weight as most browsers will try and render the wrong weight if set incorrectly resulting in blurry text.

<h2>CSS Code Snippets</h2>
 - Vertical align text or imaages inside a element. http://codepen.io/sebastianekstrom/pen/kzEhe

 ```CSS
.holder p {
    position: relative;
    top: 50%;
    transform: translateY(-50%);
}
```
 - Cross Browser Sticky Footer

```HTML
 <div class='page-wrap'><h1>Content Area</h1></div>
 <footer class='site-footer'>Sticky Footer.</footer>
```
```CSS
 * {margin: 0;}
 html, body {height: 100%;}
 .page-wrap { min-height: 100%; /* equal to footer height */	margin-bottom: -142px;}
 .page-wrap:after {content: "";display: block;}
 .site-footer, .page-wrap:after {/* .push must be the same height as footer */height: 142px;}
 .site-footer { background: orange;}
```

 - Spaced and indented paragraph
```CSS
p{
  margin-bottom:20px;
}
p+p{
  text-indent:2em;
  margin-top:-20px;
}
```

<h2>CSS Performance</h2>
 - Limit Browser rendering by limiting CSS Box-shadows & CSS Gradients
 - Minify CSS (Removes whitespace/linebreaks reducing file size)
 - Combine CSS files (Reduces the amount of HTTP Requests)
 - *{} targets every element (Not recommend adds performance issues)
 - Avoid unnecessary tag identifiers for performance (short selectors load faster) i.e. ul#navigation,ul.menu{} replace #navigation,.menu{}
 - Avoid using ancestors html div tr td{} Most modern browsers work from the right & work them way up
 - Chaining can mean loss of performance so when you do chain use the least used first i.e. use #foo.bar instead of .bar#foo
 - Versions of Chrome & Safari change the anti-alias of text during CSS animations fix with body{-webkit-backface-visibility: hidden;} or on the problematic area (causes WebKit to use hardware acceleration for the animations)
 - Use CSS Animtaions & Transitions rather than JavaScript where possible as browsers utilize the devices hardware acceleration improving performance making CSS Transitions/Animation smoother. 
