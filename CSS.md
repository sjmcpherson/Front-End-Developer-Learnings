<h2>CSS Coding Tips</h2>

<h3>Uncommon CSS Selectors</h3>
 - X:first-letter/:first-line IE6+ apply to block level elements compatible with all browser versions
 - ul > li{} IE7+ targets direct children
 - ul ~ p{} IE7+ targets p tags after ul tag in DOM
 - h1 + p{} IE7+ targets adjacent p tags directly after h1 tags
 - a[data-info~="image"]{} IE7+ selects all elements that have a data-info of “image” including multiple values such as  data-info="external image"
 - :first-child{} IE7+ targets the first child element
 - X[href^="http"] IE7+
 - :after{content:"more";} & :before{} IE8+ Allows you to add content before/after an element
 - :last-child{} IE9+ targets the last child element
 - X:nth-child(3) & X:nth-last-child(2) IE9+ 
 - X:nth-of-type(n) IE9+ rather than selecting a child, targets according to the type of element. Because of this targeting the type of element you will encounter issues when using a class as the selector
 - X:not(selector) IE9+ targets all elements that don't match the selector i.e. div:not(#container) selects all divs that don't have a ID of "container".
 - :empty IE9+ targets elements with no children
 - :only-child IE9+ targets elements that are the only child of their parent

<h3>Uncommon CSS Properties</h3>
 - 'counter-increment' (IE8+) Used to display a incremented value, set & reset via the 'counter-reset' property. http://codepen.io/sjmcpherso/pen/eILwf

```CSS
h1 {counter-reset: section;}
h2:before {counter-increment: section;content: counter(section) ". ";}
```

 - 'image-set' (Safari 6+ and Chrome 21+ ONLY) Used to display High Pixel Resolution background images "background-image: image-set(url("test.png") 1x, url("test-2x.png") 2x);"
 - 'background-clip', 'background-origin' and 'background-size' IE9+
 - '-flex' The new Flexible Box layout Module for fluid layouts - http://html5-demos.appspot.com/static/css/flexbox/index.html IE10+ includes '-order': for ordering structure elements '-justify-content': for aligning structure elements and '-webkit-flex-direction': for positioning 
 - '-column-count' Multi-column Wrapping Text layouts with "div{-column-count: 3;}" IE10+
 - '-calc' Dynamic css calculations "div{width: +calc(100% - 4em);}"
 - 'box-sizing:border-box' (IE8+) forces the browser to render the box with the specific width & height, placing borders & padding inside of the box. Very helpful when working with 100% widths. Use the value 'content-box' to revert to the default setting.

<h3>General Coding Tips</h3>
 - Its important when working in a team of developers on a project that they all abide to a similar syntax and format with their stylesheets, this is important specifically in large projects to keep stylesheets maintainable, readable and scalable. Often its important to agree on a CSS Guideline which states what file structure, preprocessor, font-sizing unit, spacing etc that should be adhered to.
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
- Font size units - px,pt,em,rem,%


<h2>CSS Performance</h2>
 - Limit Browser rendering by limiting CSS Box-shadows & CSS Gradients
 - Minify CSS (Removes whitespace/linebreaks reducing file size)
 - Combine CSS files (Reduces the amount of HTTP Requests)
 - *{} targets every element (Not recommend adds performance issues)
 - Avoid unnecessary tag identifiers for performance (short selectors load faster) i.e. ul#navigation,ul.menu{} replace #navigation,.menu{}
 - Avoid using ancestors html div tr td{} Most modern browsers work from the right & work them way up
 - Chaining can mean loss of performance so when you do chain use the least used first i.e. use #foo.bar instead of .bar#foo
 - Versions of Chrome & Safari change the anti-alias of text during CSS animations fix with body{-webkit-backface-visibility: hidden;} or on the problematic area (causes WebKit to use hardware acceleration for the animations)

