
- At the most basic level, CSS is made up of various rules. These rules are made up of a selector (more on this in a bit) and a semi-colon separated list of declarations, with each of those declarations being made up of a property: value pair
- A ``<div>`` is one of the basic HTML elements. It is simply an empty container. In general, it is best to use other tags such as ``<h1>`` or ``<p>`` for content in your projects, but as we learn more about CSS you’ll find that there are many cases where the thing you need is just a container for other elements. Many of our exercises use plain ``<div>``s for simplicity
- **Selectors** 
	- Selectors simply refer to the HTML elements to which CSS rules apply; they’re what is actually being “selected” for each rule.
	- The universal selector will select elements of any type, hence the name “universal”, and the syntax for it is a simple asterisk.
		- ``* {color: purple;}``
	- A type selector (or element selector) will select all elements of the given element type, and the syntax is just the name of the element.
		- ```html
			<div>Hello, World!</div>
			<div>Hello again!</div>
			<p>Hi...</p>			
			<div>Okay, bye.</div>
			}
			/*styles.css*
			div {
			color: white;
			}
		
	- Class selectors will select all elements with the given class, which is just an attribute you place on an HTML element
		- ```html
			<div class="alert-text">
			  Please agree to our terms of service.
			</div>```
		
	   - ```css
			.alert-text {
			  color: red;
			}```
		- Note the syntax for class selectors: a period immediately followed by the case-sensitive value of the class attribute. Classes aren’t required to be unique, so you can use the same class on as many elements as you want.
		- Another thing you can do with the class attribute is to add multiple classes to a single element as a space-separated list, such as ``class="alert-text severe-alert"``. Since whitespace is used to separate class names like this, you should never use spaces for multi-worded names and should use a hyphen instead.
	- ID Selectors
		- ID selectors are similar to class selectors. They select an element with the given ID, which is another attribute you place on an HTML element:
			- ```html
			<div id="title">My Awesome 90's Page</div>```
			- ```css
			#title {
			  background-color: red;
			}```
		- Instead of a period, we use a hashtag immediately followed by the case-sensitive value of the ID attribute.
		- people often overuse these, and should only really be used when taking advantage of specificity or having links redirect to a section on the current page.
		- The major difference between classes and IDs is that an element can only have **one** ID. An ID cannot be repeated on a single page, and the ID attribute should not contain any whitespace at all.
	- Grouping Selectors
		- can group together multiple selectors
			- ```css
				.read,
				.unread {
				  color: white;
				  background-color: black;
				}
				
				.read {
				  /* several unique declarations */
				}
				
				.unread {
				  /* several unique declarations */
				}```
	- Chaining Selectors
		- chain together multiple selectors as a list
			- ```html
			<div>
			 <div class="subsection header">Latest Posts</div>
			  <p class="subsection preview">This is where a preview for a post might go.</p>
			</div>```
		- We have two elements with the `subsection` class that have some sort of unique styles, but what if we only want to apply a separate rule to the element that also has `header` as a second class? Well, we could chain both the class selectors together in our CSS like so:
			- ```css
			.subsection.header {
			  color: red;
			}```
		- What `.subsection.header` does is it selects any element that has both the `subsection` _and_ `header` classes. Notice how there isn’t any space between the `.subsection` and `.header` class selectors. This syntax basically works for chaining any combination of selectors, except for chaining more than one [type selector](https://www.theodinproject.com/lessons/foundations-css-foundations#type-selectors).
		- This can also be used to chain a class and an ID, as shown below:
			- ```html
			<div>
			  <div class="subsection header">Latest Posts</div>
			  <p class="subsection" id="preview">This is where a preview for a post might go.</p>
			</div>```
		- You can take the two elements above and combine them with the following:
			- ```css
			.subsection.header {
			  color: red;
			}
			
				.subsection#preview {
				  color: blue;
				}```
				
		- In general, you can’t chain more than one type selector since an element can’t be two different types at once. For example, chaining two type selectors like `div` and `p` would give us the selector `divp`, which wouldn’t work since the selector would try to find a literal `<divp>` element, which doesn’t exist.
- **Combiners**
	- Combinators allow us to combine multiple selectors differently than either grouping or chaining them, as they show a relationship between the selectors. There are four types of combinators in total, but for right now we’re going to only show you the descendant combinator, which is represented in CSS by a single space between selectors
	- Descendent Combiner
		- A descendant combinator will only cause elements that match the last selector to be selected if they also have an ancestor (parent, grandparent, etc.) that matches the previous selector.
		- So something like `.ancestor .child` would select an element with the class `child` if it has an ancestor with the class `ancestor`
		- Another way to think of it is that `child` will only be selected if it is nested inside `ancestor`, regardless of how deep that nesting is.
- **Properties to get started with**
	- Color and background color
		- The `color` property sets an element’s text color, while `background-color` sets, the background color of an element
		- Almost. Both of these properties can accept one of several kinds of values. A common one is a keyword, such as an actual color name like `red` or the `transparent` keyword
		- They also accept HEX, RGB, and HSL values
			- `color: #1100ff;
			- `color: rgb(100, 0, 127);
			- `color: hsl(15, 82%, 56%);`
	- Typography basics and text-align
		- `font-family` can be a single value or a comma-separated list of values that determine what font an element uses
			- Each font will fall into one of two categories, either a “font family name” like `"Times New Roman"` (we use quotes due to the whitespace between words) or a “generic family name” like `sans-serif` (generic family names never use quotes).
			- If a browser cannot find or does not support the first font in a list, it will use the next one, then the next one and so on until it finds a supported and valid font. This is why it’s best practice to include a list of values for this property
		- `font-size` will, as the property name suggests, set the size of the font
			- When giving a value to this property, the value should not contain any whitespace, e.g. `font-size: 22px` has no space between “22” and “px”.
		- `font-weight` affects the boldness of text, assuming the font supports the specified weight.
			- This value can be a keyword, e.g. `font-weight: bold`, or a number between 1 and 1000, e.g. `font-weight: 700` (the equivalent of `bold`)
		- `text-align` will align text horizontally within an element, and you can use the common keywords you may have come across in word processors as the value for this property, e.g. `text-align: center`
	- Image height and width
		- Images aren’t the only elements that we can adjust the height and width on, but we want to focus on them specifically in this case.
		- By default, an `<img>` element’s `height` and `width` values will be the same as the actual image file’s height and width. If you wanted to adjust the size of the image without causing it to lose its proportions, you would use a value of “auto” for the `height` property and adjust the `width` value:
			- `image {height: auto; width: 500px;}`
			- For example, if an image’s original size was 500px height and 1000px width, using the above CSS would result in a height of 250px.
		- It’s best to include both of these properties for `<img>` elements, even if you don’t plan on adjusting the values from the image file’s original ones. When these values aren’t included, if an image takes longer to load than the rest of the page contents, the image won’t take up any space on the page at first, but will suddenly cause a drastic shift of the other page contents once it does load in. Explicitly stating a `height` and `width` prevents this from happening, as space will be “reserved” on the page and will just appear as a blank space until the image loads.
- **Adding CSS to HTML**
	- External CSS
		- most common method, involves creating a separate file for the CSS and linking it inside of the HTML's opening and closing `<head>` tags with a self closing `<link> element.
		- ```html
		<head>
			<link rel="stylesheet" href="styles.css" />
		<head/>```
		- ```CSS
		div {
		color: white;
		background-color: black;
		}
		
		p {
		color: red;
		}```
		- First, we add a self-closing `<link>` element inside of the opening and closing `<head>` tags of the HTML file. The `href` attribute is the location of the CSS file, either an absolute URL or, what you’ll be utilizing, a URL relative to the location of the HTML file. In our example above, we are assuming both files are located in the same directory. The `rel` attribute is required, and it specifies the relationship between the HTML file and the linked file.
		- Then inside of the newly created `styles.css` file, we have the selector (the `div` and `p`), followed by a pair of opening and closing curly braces, which create a “declaration block”. Finally, we place any declarations inside of the declaration block. `color: white;` is one declaration, with `color` being the property and `white` being the value, and `background-color: black;` is another declaration.
		- A note on file names: `styles.css` is just what we went with as the file name here. You can name the file whatever you want as long as the file type is `.css`, though “style” or “styles” is most commonly used.
		- A couple pros to this method ae
			- It keeps our HTML and CSS separated, which results in the HTML file being smaller and making things look cleaner.
			- We only need to edit the CSS in _one_ place, which is especially handy for websites with many pages that all share similar styles.
	- Internal CSS
		- The css is embedded into the HTML file itself.
		- place all CSS rules inside of opening and closing `<style>` tags, which are then placed inside of the opening and closing `<head>` tags of your HTML file
		- Syntax is exactly the same as external css
			- ```html
			<head>
				<style>
					div {
						color: white;
						background-color: black;
						}
						p {
						color: red;
						}
						<style/>
					<head/>
					<body>
					...
					<body/>```
		- this method is useful if you want to add unique styles to a single page of a website, but it doesn’t keep things separate like the external method, and depending on how many rules and declarations there are it can cause the HTML file to get pretty big
- **The Cascade of CSS**
	- the cascade is what determines which rules actually get applied to our html
	- specificity
		- The most specific CSS declaration takes the most precedence
			- specificity priority is 
				- 1. ID selectors
				- 2. Class selectors
				- 3. Type selectors
		- specificity is only taken into account when an element has multiple, conflicting declarations targeting it
		- When no declaration has a selector with a higher specificity, a larger amount of a single selector will beat a smaller amount of that same selector.
	- Inheritance
		- Inheritance refers to certain CSS properties that, when applied to an element, are inherited by that element’s descendants, even if we don’t explicitly write a rule for those descendants.
		- Typography based properties (`color`, `font-size`, `font-family`, etc.) are usually inherited, while most other properties aren’t.
		- The exception to this is when directly targeting an element, as this always beats inheritance.
	- Rule Order
		- The final factor, the end of the line, the tie-breaker of the tie-breaker. Let’s say that after every other factor has been taken into account, there are still multiple conflicting rules targeting an element. How does the cascade determine which rule to apply? The answer, whichever rule was the _last_ defined is the winner.
- **The Box Model**
	- The most important thing to understand in CSS is the box model. very single thing on a webpage is a rectangular box.
	- he only real complication here is that there are many ways to manipulate the size of these boxes, and the space between them, using `padding`, `margin`, and `border`
		- -`padding` increases the space between the border of a box and the content of the box.
		-  `margin` increases the space between the borders of a box and the borders of adjacent boxes.
			- Margin collapses between two elements that are next to each other, and the largest margin is always used. for example if two boxes right next to each other both have a margin of 60px, there would only be 60px of margin between them instead of 120px. similarly, If one box has a margin of 70px, and the other 60px, there would be 70px of margin between them.
			- some items, such as `ul` and `ol` will have default margin and padding applied to them that isn't just 0. lists have a top and bottom margin of 16px ( 1em ) and a padding-left of 40px ( 2.5em ).
		-  `border` adds space (even if it’s only a pixel or two) between the margin and the padding.
	- the total height of your object is the height and width of the object itself, plus the padding and border of the object. For example, a 100x100 object with a padding of 10px and a border of 30px would actually be 180x180. Margin does not factor into size of object by default.
		- you can use change the `box-sizing:` to `border-box;` in order to height and width of an object account for the padding and border. when using border box, the actual size of the content is subtracted out of the border and padding. For example if you have an element that is 100x100 with the padding and boarder both set to 10px, the object would shrink down to 60x60 with if using `border-box;`
	- https://developer.mozilla.org/en-US/docs/Learn/CSS/Building_blocks/The_box_model
- **Block and Inline Boxes**
	- By default, block elements will appear on the page stacked atop each other, each new element starting on a new line. most of the basic elements of CSS are block elements, their default style is `display: bloc
	- Inline elements do not start on a new line, they appear in line with whatever elements are placed beside them.
		- an example of this would be the link `<a>` tag. if you were to use this tag in the middle of a paragraph, it will behave like a part of the paragraph of text. 
		- padding and margin behave differently on inline elements. In general, you do not want to try to put extra padding or margin on inline elements.
	- Inline-block elements behave like inline elements, but with block-style padding and margin. `display: inline-block` is a useful tool to know about, but in practice, you’ll probably end up reaching for flexbox more often if you’re trying to line up a bunch of boxes.
	- Divs and Spans
		- divs and spans give no particular meaning to their content. They are just generic boxes that can contain anything.
		- this is very useful because, we will often need elements that serve no other purpose than to be “hook” elements
		- We can give an id or class to target them for styling with CSS
		- Another use case we will face regularly is grouping related elements under one parent element to correctly position them on the page. Divs and spans provide us with the ability to do this.
		- Div is a block-level element by default. It is commonly used as a container element to group other elements. Divs allow us to _divide_ the page into different blocks and apply styling to those blocks.
		- Span is an inline element by default. It can be used to group text content and inline HTML elements for styling and should only be used when no other semantic HTML element is appropriate.
			- an example of when you'd want to use a span is for something like highlighting text
		- The HTML for this could look like:
		- ```html
		<div class="introduction">
		   <h2>Introduction</h2>
		   </div>
		    
		    <div class="main-content">
		       <h2>Main Content</h2>
		       </div>
		       
		 <div class="contact-us">
			 <h2>Contact Us</h2>
		</div> 
		- The CSS for this could look like:
		- ```css
		div {
			padding: 30px;
			text-allign: center;
			margin-bottom: 10px
			color: #EEEEE;
		}
		.introduction {
			background-color: #548CA8;
		}
		.main-content {
			background-color: #476072
		}
		.contact-us {
			background-color: #334257;
		}
		- this would make it so that all the margins, borders, and padding of the boxes is the same, but the colors can be changed
- 