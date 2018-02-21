# Cascading Style Sheets

<!-- doctoc HTML.md JavaScript.md CSS.md -->
<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
### Contents

- [CSS Selectors](#css-selectors)
  - [Element Selectors](#element-selectors)
  - [Attribute Selectors](#attribute-selectors)
  - [Pseudo-class Selectors](#pseudo-class-selectors)
- [Units/Measurements](#unitsmeasurements)
  - [Absolute length units](#absolute-length-units)
  - [Relative length units](#relative-length-units)
  - [Viewport-percentage lengths](#viewport-percentage-lengths)
- [Design](#design)
  - [Backgrounds](#backgrounds)
  - [Gradients](#gradients)
  - [CSS Opacity](#css-opacity)
- [Structure & Positioning](#structure--positioning)
  - [Important base attributes](#important-base-attributes)
  - [CSS Columns/Multi-column Layouts](#css-columnsmulti-column-layouts)
  - [CSS Grid Layout](#css-grid-layout)
  - [Other CSS Structure & Positioning](#other-css-structure--positioning)
- [Font](#font)
  - [Font size units](#font-size-units)
  - [Font Rendering](#font-rendering)
- [Animation & Transitions](#animation--transitions)
  - [Transitions](#transitions)
  - [Animations](#animations)
- [Advanced Modules](#advanced-modules)
  - [Media Queries](#media-queries)
  - [Calc Function](#calc-function)
  - [Source Maps](#source-maps)
  - [CSS Variables](#css-variables)
  - [@supports](#supports)
  - [Other CSS Properties](#other-css-properties)
- [CSS Performance](#css-performance)
  - [CSS Selector Performance](#css-selector-performance)
  - [Rendering Performance](#rendering-performance)
  - [Download Optimisation](#download-optimisation)
- [Helpful CSS Code Snippets](#helpful-css-code-snippets)
- [General Coding Tips](#general-coding-tips)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

## CSS Selectors

### Element Selectors

- *- Selects all elements (use carefully as can be expensive performance wise)
- element, element - Targets both elements
- element element - Targets children of the first element
- element > element - targets direct children e.g ul > li{}
- element ~ element - targets all adjacent & child elements after the first element. e.g ul ~ p{}
- element + element - targets adjacent elements directly after the first element. e.g h1 + p{}

### Attribute Selectors

- Targets an elements attributes, __All attribute selectors are IE7+__
- Asterix attribute selector(element[attribute*=value]) - selects elements matching the characters e.g a[class *= "asterix"]{} selects class='more asterix' & class='moreasterix'
- Tilde selector(element[attribute~=value]) - selects elements matching the whole word, a stricter version of "*=" e.g a[data-info~="tilde"]{} selects data-info="external tilde" but not data-info="bigtilde" or data-info="big-tilde"
- Pipe selector(element[attribute |= value]) - selects elements starting with the specified whole word & can be hyphenated. i.e [class|=pipe]{} would select class='pipe' & class='pipe-header' but not class='pipeheader' or class='header pipe'.
- Caret selector(element[attribute ^= value]) - selects elements that begins with the characters and does not need to be a whole word. e.g a[href^="http"]{} would select <a href="http://www.google.com"></a> but not <a href="www.google.com&var=http"></a>
- Dollar selector(element[attribute $= value]) - selects elements that ends with the characters and does not need to be a whole word. e.g the opposite to the Caret selector

### Pseudo-class Selectors

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

## Units/Measurements

### Absolute length units

 - <strong>Pixels (px)</strong> - Relative to the viewing device. For screen display, typically one device pixel (dot) of the display.
 - <strong>Points/Picas (pt & pc)</strong> - Used for Print Stylesheets, 1pc == 12pt
 - <strong>Inches (in) and Centimeters (cm)</strong> - Used for Print Stylesheets

### Relative length units

 - <strong>Percentage (%)</strong> - Defines a measurement as a percentage relative to another value, typically an enclosing parent element.
 - <strong>em</strong> - This unit represents the calculated font-size of the element. If used on the font-size property itself, it represents the inherited font-size of the element.
 - <strong>rem (Root EM)</strong> - This unit represents the font-size of the root element (e.g. the font-size of the <html> element). When used on the font-size on this root element, it represents its initial value.
 - <strong>ex & ch</strong> - ex(x-height): a measurement based on the height of the lower case 'x' character. ch: measurement based on the width of the '0' character.

### Viewport-percentage lengths

 - <strong>vh & vw</strong> - 1% of viewport width/height
 - <strong>vmin & vmax</strong> - vmin: 1vw or 1vh, whichever is smaller, IE9+. vmax: 1vw or 1vh, whichever is larger, No IE support


## Design

### Backgrounds

 - background-size: cover;contain;width height; - 'cover' scales up background image so the <em>lesser</em> dimension matches the window size; 'contain' scales up to the <em>greater</em> dimension, meaning some background will not be covered by the image.
 - background-attachment:scroll;fixed;local; - 'fixed' background will not move (problems in Chrome with position relative among others)
 - 'background-clip', 'background-origin' IE9+
 - 'background-blend-mode:value' - Photoshop like image/svg blending with values including screen, overlay, darken, lighten, color-dodge, color-burn, hard-light, soft-light, difference, exclusion, hue, saturation, color, and luminosity
 - 'image-set' (Safari 6+ and Chrome 21+ ONLY) Used to display High Pixel Resolution background images "background-image: image-set(url("test.png") 1x, url("test-2x.png") 2x);"

### Gradients

- Use a gradient generator to build complex gradients i.e. http://www.colorzilla.com/gradient-editor/
- Completed cross-browser CSS Linear Gradient

```CSS
	background: #e56464; /* Old browsers */
	background: -ms-linear-gradient(top, #e56464 0%,#a80000 100%); /* IE10+ */
	background: linear-gradient(to bottom, #e56464 0%,#a80000 100%); /* W3C */
	filter: progid:DXImageTransform.Microsoft.gradient( startColorstr='#e56464', endColorstr='#a80000',GradientType=0 ); /* IE6-9 */
```

### CSS Opacity

- 'property:rgba(255,255,255,100);' - Red, Green, Blue & Alpha transparency can be used for almost any color attribute, IE9+
- Cross-browser CSS Opacity

```CSS
.transparent {
	filter: alpha(opacity=50); // IE9 & below
	opacity: 0.5; // IE10+
}
```

## Structure & Positioning

### Important base attributes

 - <strong>Block & Inline Elements</strong> - Native elements tag like 'div', 'p' & 'section' are Block elements i.e. their Display attibute is set to 'block' by default, whereas Inline elements like 'span', 'a' & 'li' are set to 'display:inline' by default. Note: If you're floating an inline element, it's treated as block, so no need to include "display:block" in your stylesheet.
 - <strong>Box Sizing Attribute</strong> - By default elements Box-sizing value is 'content-box' by setting it to 'border-box'(IE8+) the browser renders an elements borders & padding inside of the specified width & height. Very helpful when working with 100% widths. *{box-sizing:border-box;} is often used to convert all elements to 'border-box'. Also the can be set to the value 'padding-box'(Very limited support) which only includes 'padding' inside the specified height/width. Example of 'border-box' value i.e.

```CSS
  div{width:100%;padding:10px;border:1px;} //Would be 22px larger than its parent element
  div{box-sizing:border-box;width:100%;padding:10px;border:1px;} //Would be the same width as its parent element
```

### CSS Columns/Multi-column Layouts

 - A CSS module to divide the flow of content into columns, mimicking magazine/newspaper style layouts. Very useful when displaying hierarchical lists in columns. IE10+

 ```CSS
.newspaper {
    column-count: 3;
    column-gap: 40px;
    column-rule: 1px solid #ccc;
}
 ```
 ### Flexbox Model

 - Flex Box Module('display:flex;') - Very powerful fluid layouts api, IE10+ - http://html5-demos.appspot.com/static/css/flexbox/index.html includes '-order': for ordering structure elements '-justify-content': for aligning structure elements horizontally, 'align-items' for vertical alignment  and '-webkit-flex-direction': for positioning

- <strong>Flexbox Issues</strong> - In IE10-11 flex-basis doesn't account for box-sizing:border-box therefore overflows can occur. Theres are anumber of workarounds for this see https://github.com/philipwalton/flexbugs#7-flex-basis-doesnt-account-for-box-sizingborder-box

```CSS
  div{
  	flex:0 0 100%;
  	padding:0 10px;//IE10-11 will cause overflow issues
  	max-width:100%;//Potential IE10-11 workaround
  }
```

### CSS Grid Layout
 
 - A powerful module to create rows & columns in many different layouts, controlling size, position and layers(elements can be set to overlap). Partial IE support.
 
 - The Below CSS Grid example defines a simple 4x3 Sectioned Grid, A full width 'header' section followed by a 25% or 1/4 width 'sidebar' that aligns to the left of the 'main' section and 'footer' section.
 
```CSS
.header{ grid-area: header; }
.sidebar { grid-area: sidebar; }
.main { grid-area: main; }
.footer { grid-area: footer; }
.grid-container {
  display: grid;
  grid-template-areas:
    'header header header header'
    'sidebar main main main'
    'sidebar footer footer footer';
  grid-gap: 10px;
}
```

### Other CSS Structure & Positioning

 - <strong>CSS Regions Module</strong> - Abandoned layout module for flowing content into multiple elements. Chrome & Firefox will not be building support.
 - <strong>position:sticky</strong> - a new way to position elements and is conceptually similar to position: fixed. The difference is that an element with position: sticky behaves like position: relative within its parent, until a given offset threshold is met in the viewport. Little support, Safari & Firefox only. caniuse.com/css-sticky
 
 
## Font

### Font size units

 - em - Calculates the font size based on the Parent font size which compounds down the tree

```CSS
html {font-size: 0.625em;}
ul { font-size: 2.4em; } /* =24px */
ul li  { font-size: 1em; } /* =24px */
ul li  { font-size: 1.05em; } /* =25px */
```

 - rem - Which stands for Root EM calculates the font size relative to the Root element. IE10+ with partial support in IE9 (See http://caniuse.com/#feat=rem).

```CSS
html {font-size: 0.625rem;}
ul { font-size: 2.4rem; } /* =24px */
ul li { font-size: 1.4rem; } /* =14px */
```
i.e. html{font-size:62.5%}

 - px,pt,em,rem,%.


### Font Rendering

 - http://webdesign.tutsplus.com/articles/a-web-designers-typographic-boilerplate--webdesign-15234?utm_content=buffer1e888&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer
 - http://aestheticallyloyal.com/public/optimize-legibility/
 - "font-weight:bold" is the same "font-weight:700" & "font-weight:normal" is the same as font-weight:300" this is important when using webfonts which are downloaded at a specific weight as most browsers will try and render the wrong weight if set incorrectly resulting in blurry text.


## Animation & Transitions

- To get the best performance from transitions & animations use Opacity or CSS3 Transform (i.e transform:translate(0,0)) other properties are likely to give lower frame rates.

### Transitions

- Transition-timing-function presets are ease, linear, ease-in, ease-out and ease-in-out. For custom easing use cubic-bezier(point1, point2, point3, point4), i.e cubic-bezier(0.5, -0.5, 0.5, 1.5) will give a bounce effect. Its helpful to use a tool such as www.cubic-bezier.com to generate & test.

### Animations
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

## Advanced Modules

### Media Queries

 - 'max-width' - '@media screen and (max-width: 600px) {}' Will apply CSS if the viewing area is less than 600px.
 - 'min-width' - '@media screen and (min-width: 900px) {}' Will apply CSS if the viewing area is greater than 900px.
 - 'max-device-width' - '@media screen and (max-device-width: 480px) {}' Will apply CSS if the resolution is greater than 480px as max-device-width means the actual resolution of the device rather than just the viewing area resolution.
 - 'min-device-pixel-ratio' - '@media only screen and (min-device-pixel-ratio : 2){}' For 2x pixel density resolutions like the Retina display.
 - 'only' in '@media only screen..' stops older browsers parsing the remander of the selector
 
### Calc Function

 - 'property:calc()' IE9+ Dynamic css calculations "width:calc(100% - 4em);"
  
### Source Maps

 - When using a pre-processor you can generate a Source Map in addition to the compiled CSS, the Source Map

### CSS Variables

- Unlike preprocessed variables, CSS Variables are scoped to an element. Very limited support, Firefox only.   

```CSS
html {
    var-primary-color: #333;
}
body {
    background-color: var(primary-color);
}
```

### @supports

 - Allows conditional CSS to be applyed based on the browser support for a CSS property or properties. Limited Browser Support
 - Accompaning JS Method CSS.supports() i.e. var result = CSS.supports("display", "flex");

```CSS
@supports (display: flex) {
	div { display: flex; }
}
@supports not (display: flex) {
	div { float: left; } /* alternative styles */
}
@supports (display: flex) and (display: -webkit-flex) and (display: -moz-flex){
	div { display: flex; }
}
@supports (display: flex) or (display: -webkit-flex) or (display: -moz-flex){
	div { display: flex; }
}
```

### Other CSS Properties

 - CSS Counter(counter-increment:value) - IE8+ Used to display a incremented value, set & reset via the 'counter-reset' property. http://codepen.io/sjmcpherso/pen/eILwf
```CSS
h1 {counter-reset: section;}
h2:before {counter-increment: section;content: counter(section) ". ";}
```
 - Pointer Events('pointer-events:none') - Disables mouse/touch events (hover, click, drag) including JS event listeners on an element. E.g Disable a semitransparent element with a higher Z-index so the element below is clicked. SVG IE9+, HTML Elements IE11+
 - 'backface-visibility: hidden/visible' - Defines whether the element should be visible when the opposite side is facing i.e. When rotateX(180) is used to flip the element.



## CSS Performance

### CSS Selector Performance
 - For most web sites, the possible performance gains from optimizing CSS selectors will be small, and are not worth the costs. Although be careful with *{} which targets every element.
 - The key to optimizing CSS selectors is to focus on the rightmost selector, also called the Key Selector. Here’s a much more expensive selector: A.class0007 * {} Although this selector might look simpler, it’s more expensive for the browser to match. Because the browser moves right to left, it starts by checking all the elements that match the key selector, “*“. This means the browser must try to match this selector against all elements in the page.
 - Avoid unnecessary tag identifiers for performance (short selectors load faster) i.e. ul#navigation,ul.menu{} replace #navigation,.menu{}
- Avoid using ancestors html div tr td{} Most modern browsers work from the right & work them way up
 - Chaining can mean loss of performance so when you do chain use the least used first i.e. use #foo.bar instead of .bar#foo

### Rendering Performance
 - Optimizing browser rendering by reducing use of CSS Box-shadows & CSS Gradients
 - Use CSS Animations & Transitions rather than JavaScript where possible as browsers utilize the devices hardware acceleration making CSS Transitions/Animation smoother. Be aware CPU usage can climb quite heavily because of the hardware acceleration.
 - Versions of Chrome & Safari change the anti-alias of text during CSS animations fix with body{-webkit-backface-visibility: hidden;} or on the problematic area (causes WebKit to use hardware acceleration for the animations)

### Download Optimisation
 - Minify CSS (Removes whitespace/linebreaks reducing file size)
 - Combine CSS files (Reduces the amount of HTTP Requests)
 - Avoid unnecessary tag identifiers to reduce file size ei.e. ul#navigation,ul.menu{} replace #navigation,.menu{}
 - The browser will still download images that are hidden with display:none although with some browsers i.e Firefox, background-images will not be downloaded.


## Helpful CSS Code Snippets
 - Vertical & Horizontal centering via translate. IE9+.

```CSS
.child {
	position: relative;
	left: 50%;
	top: 50%;
	-ms-transform: translate(-50%,-50%); //IE9
	transform: translate(-50%,-50%);
}
```
 - Vertical & Horizontal centering via Flexbox. IE10+.

```CSS
.parent {
  display: flex;
  justify-content: center;
  align-items: center;
}
```

 - Elipise/Concat a single line of text IE8+ http://codepen.io/sjmcpherso/pen/vEZdRw

```CSS
p {
	width:200px;
	text-overflow: ellipsis;
	white-space: nowrap;
	overflow: hidden;
}
```

 - Cross Browser Sticky Footer IE8+
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

 - Contain the caption in the bounds of a variable width image and display at the bottom
```HTML
<figure>
  <img src="img_pulpit.jpg" alt="The Pulpit Rock" width="304" height="228">
  <figcaption>Fig.1 - A view of the pulpit rock in Norway.</figcaption>
</figure>
```
```CSS
figure{display:table;}
figcaption{display:table-caption;caption-side:bottom;}
```


## General Coding Tips

 - Its important when working in a team of developers on a project that they all abide to a similar syntax and format with their stylesheets, this is important specifically in large projects to keep stylesheets maintainable, readable and scalable. Often its important to agree on a CSS Guideline which states what file structure, preprocessor, font-sizing unit, spacing etc that should be adhered to. A very detailed one can be found here: https://github.com/csswizardry/CSS-Guidelines
 - Avoid using IDs as they decrease portability

