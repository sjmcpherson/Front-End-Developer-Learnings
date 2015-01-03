#Cascading Style Sheets

##CSS Selectors


###Element Selectors
 - * - Selects all elements (use carefully as can be expensive performance wise)
 - element, element - Targets both elements
 - element element - Targetd children of the first element
 - element > element - IE7+ targets direct children e.g ul > li{}
 - element ~ element - IE7+ targets p tags after ul tag in DOM e.g ul ~ p{} 
 - element + element - IE7+ targets adjacent p tags directly after h1 tags e.g h1 + p{}

###Attribute Selectors
 - Targets an elements attributes, __All attribute selectors are IE7+__
 - element[attribute ^= value] - IE7+ selects elements with a attribute value that begins with the characters e.g a[href^="http"]{}
 - element[attribute *= value] - IE7+ selects elements matching the characters e.g a[data-info *= "image"]{}
 - element[attribute ~= value] - IE7+ selects elements matching the whole word, a stricter version of "*="
 - have a data-info of "image" including multiple values such as  data-info="external image" e.g a[data-info~="image"]{}
 - element[attribute $= value] - IE7+ selects elements matching 

###Pseudo Selectors
 - element:first-letter/:first-line - IE6+ apply to block level elements compatible with all browser versions e.g p:first-letter{}. NOTE: Doesn't work on display:inline; elements.
 - element:after{content:"";} & element:before - IE8+ Allows you to add content before/after an element. CSS3 syntax is double colon "::" although this is not supported by IE8. Note: <b>Input elements are not supported</b>.
 - element:first-child - IE7+ targets the first child element
 - element:last-child - IE9+ targets the last child element
 - element:nth-child(3)/:nth-last-child(2) - IE9+ 
 - element:nth-of-type(n) - IE9+ rather than selecting a child, targets according to the type of element. Because of targeting the type of element you will encounter issues when using a class as the selector.
 - element:first-of-type/:last-of-type - IE9+ i.e. .active:last-of-type{} Would select the element if it was the last-child and had the class 'active' Not what would be expect as the last element with the class 'active'.
 - element:not(selector) - IE9+ targets all elements that don't match the selector i.e. div:not(#container) selects all divs that don't have a ID of "container".
 - element:empty - IE9+ targets elements with no children
 - element:only-child - IE9+ targets elements that are the only child of their parent
 - element:checked - for radio and checkbox
 - element:target{} - IE9+ A powerful selector for single page apps, targets an element with the same ID as the hash in the URL. Note setting the URL this way triggers Bookmark like behaviour: Affecting browser history and scrolling the window to element behavior
```HTML
<a href="#page1">Page 1</a>
<section id="page1"> 
   Content
</section>
```
```CSS
section{display:none;}
:target {display:block;}
```



###CSS Opacity
- 'property:rgba(255,255,255,100);' - Red, Green, Blue & Alpha Transparency can be used for almost any color attribute but is not supported by <IE9
- Completed crossbrowser CSS Opacity

```CSS
/* Theoretically for IE 8 & 9 (more valid) but not required as filter works too should come BEFORE filter */
-ms-filter:"progid:DXImageTransform.Microsoft.Alpha(Opacity=50)";
/* This works in IE 8 & 9 too but also 5, 6, 7 */
filter: alpha(opacity=50);
/* Older than Firefox 0.9 */
-moz-opacity:0.5;
/* Safari 1.x (pre WebKit!) */
-khtml-opacity: 0.5;
/* Modern! Firefox 0.9+, Safari 2?, Chrome any?, Opera 9+, IE 9+ */
opacity: 0.5;

/* Recommended Usage for Today */
.transparent {
	zoom: 1;
	filter: alpha(opacity=50);
	opacity: 0.5;
}	
```

###Backgrounds
 - background-size: cover;contain;width height; - 'cover' scales up background image so the <em>lesser</em> dimension matches the window size; 'contain' scales up to the <em>greater</em> dimension, meaning some background will not be covered by the image. 


###Media Queries
 - 'max-width' - '@media screen and (max-width: 600px) {}' Will apply CSS if the viewing area is less than 600px.
 - 'min-width' - '@media screen and (min-width: 900px) {}' Will apply CSS if the viewing area is greater than 900px.
 - 'max-device-width' - '@media screen and (max-device-width: 480px) {}' Will apply CSS if the resolution is greater than 480px as max-device-width means the actual resolution of the device rather than just the viewing area resolution.
 - 'min-device-pixel-ratio' - '@media only screen and (min-device-pixel-ratio : 2){}' For 2x pixel density resolutions like the Retina display.
 - 'only' in '@media only screen..' stops older browsers parsing the remander of the selector

###General Coding Tips
 - Its important when working in a team of developers on a project that they all abide to a similar syntax and format with their stylesheets, this is important specifically in large projects to keep stylesheets maintainable, readable and scalable. Often its important to agree on a CSS Guideline which states what file structure, preprocessor, font-sizing unit, spacing etc that should be adhered to. A very detailed one can be found here: https://github.com/csswizardry/CSS-Guidelines
 - Avoid using IDs as they decrease portability


###Font size units
 - em - Calculates the font size based on the Parent font size which compounds down the tree
 
```CSS
html {font-size: 0.625em;}
ul { font-size: 2.4em; } /* =24px */
ul li  { font-size: 1em; } /* =24px */
ul li  { font-size: 1.05em; } /* =25px */
```

 - rem - Which stands for Root EM calculates the font size relative to the Root element. IE9+ with some limitations (See http://caniuse.com/#feat=rem).
 
```CSS
html {font-size: 0.625rem;}
ul { font-size: 2.4rem; } /* =24px */
ul li { font-size: 1.4rem; } /* =14px */
```
i.e. html{font-size:62.5%}

 - px,pt,em,rem,%.


###Font Rendering
 - http://webdesign.tutsplus.com/articles/a-web-designers-typographic-boilerplate--webdesign-15234?utm_content=buffer1e888&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer
 - http://aestheticallyloyal.com/public/optimize-legibility/
 - "font-weight:bold" is the same "font-weight:700" & "font-weight:normal" is the same as font-weight:300" this is important when using webfonts which are downloaded at a specific weight as most browsers will try and render the wrong weight if set incorrectly resulting in blurry text.


###Structure & Positioning
 - IE7 fix for display:inline-block is "display:inline-block;*display: inline;zoom: 1;"
 - If you're floating an inline element, it's treated as block, so no need to include "display:block" in your stylesheet.
 - Box Sizing('box-sizing:border-box') - IE8+ forces the browser to render the box with the specific width & height, placing borders & padding inside of the box. Very helpful when working with 100% widths. Use the value 'content-box' to revert to the default setting.
 - Flex Box Module('display:flex;') - IE10+ For fluid layouts - http://html5-demos.appspot.com/static/css/flexbox/index.html includes '-order': for ordering structure elements '-justify-content': for aligning structure elements horizontally, 'align-items' for vertical alignment  and '-webkit-flex-direction': for positioning 
 - Multicolumn Module('column-count:value') - IE10+ Multi-column Wrapping Text layouts with "div{column-count: 3;column-width:30px;column-gap:5px;column-rule:solid 1px #ccc;}" IE10+ 
 - CSS Regions Module - A specification that enables rich, magazine-like text column layouts that can resize based on the browser width although not perceived by most to be part of Responsive Web Design. IE10+ & Safari 6.1+ ONLY, Google has advised that it will not be adding support to Chrome in the forseable future due to performance. Article on the Limitations of CSS Regions http://alistapart.com/blog/post/css-regions-considered-harmful Article on Google dumping CSS Regions http://arstechnica.com/information-technology/2014/01/google-plans-to-dump-adobe-css-tech-to-make-blink-fast-not-rich/
 - position:sticky - a new way to position elements and is conceptually similar to position: fixed. The difference is that an element with position: sticky behaves like position: relative within its parent, until a given offset threshold is met in the viewport. Little to no support caniuse.com/css-sticky



###CSS3 Animations & Transitions
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

- To get the best performance from transitions & animations use Opacity or CSS3 Transform (i.e transform:translate(0,0)) other properties are likely to give lower frame rates. 
- Transition-timing-function presets are ease, linear, ease-in, ease-out and ease-in-out. For custom easing use cubic-bezier(point1, point2, point3, point4), i.e cubic-bezier(0.5, -0.5, 0.5, 1.5) will give a bounce effect. Its helpful to use a tool such as www.cubic-bezier.com to generate & test.

###Other CSS Properties

 - CSS Counter(counter-increment:value) - IE8+ Used to display a incremented value, set & reset via the 'counter-reset' property. http://codepen.io/sjmcpherso/pen/eILwf
```CSS
h1 {counter-reset: section;}
h2:before {counter-increment: section;content: counter(section) ". ";}
```
 - 'image-set' (Safari 6+ and Chrome 21+ ONLY) Used to display High Pixel Resolution background images "background-image: image-set(url("test.png") 1x, url("test-2x.png") 2x);"
 - 'background-clip', 'background-origin' and 'background-size' IE9+
 - Calculations('property:calc()') - IE9+ Dynamic css calculations "width:calc(100% - 4em);"
 - Pointer Events('pointer-events:none') - Disables mouse/touch events (hover, click, drag) including JS event listeners on an element. E.g Disable a semitransparent element with a higher Z-index so the element below is clicked. SVG IE9+, HTML Elements IE11+
 - 'background-blend-mode:value' - Photoshop like image/svg blending with values including screen, overlay, darken, lighten, color-dodge, color-burn, hard-light, soft-light, difference, exclusion, hue, saturation, color, and luminosity
 - 'backface-visibility: hidden/visible' - Defines whether the element should be visible when the opposite side is facing i.e. When rotateX(180) is used to flip the element.

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

 - Alternate Rows (:nth-child IE9+)
```CSS 
tbody tr:nth-child(odd) {
	background-color: lightblue;
}
```

##CSS Performance

###CSS Selector Performance
 - For most web sites, the possible performance gains from optimizing CSS selectors will be small, and are not worth the costs. Although be careful with *{} which targets every element.
 - The key to optimizing CSS selectors is to focus on the rightmost selector, also called the Key Selector. Here’s a much more expensive selector: A.class0007 * {} Although this selector might look simpler, it’s more expensive for the browser to match. Because the browser moves right to left, it starts by checking all the elements that match the key selector, “*“. This means the browser must try to match this selector against all elements in the page.
 - Avoid unnecessary tag identifiers for performance (short selectors load faster) i.e. ul#navigation,ul.menu{} replace #navigation,.menu{}
- Avoid using ancestors html div tr td{} Most modern browsers work from the right & work them way up
 - Chaining can mean loss of performance so when you do chain use the least used first i.e. use #foo.bar instead of .bar#foo

###Rendering Performance 
 - Optimizing browser rendering by reducing use of CSS Box-shadows & CSS Gradients
 - Use CSS Animations & Transitions rather than JavaScript where possible as browsers utilize the devices hardware acceleration making CSS Transitions/Animation smoother. Be aware CPU usage can climb quite heavily because of the hardware acceleration.
 - Versions of Chrome & Safari change the anti-alias of text during CSS animations fix with body{-webkit-backface-visibility: hidden;} or on the problematic area (causes WebKit to use hardware acceleration for the animations)

###Download Optimisation
 - Minify CSS (Removes whitespace/linebreaks reducing file size)
 - Combine CSS files (Reduces the amount of HTTP Requests)
 - Avoid unnecessary tag identifiers to reduce file size i.e. ul#navigation,ul.menu{} replace #navigation,.menu{}
 - The browser will still download images that are hidden with display:none although with some browsers i.e Firefox, background-images will not be downloaded.
