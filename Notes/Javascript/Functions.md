- Functions that are part of objects are called methods
- Invoking a function is done by including the name of the function followed by parentheses
	- This form of creating a function is also known as _function declaration_. It is always hoisted, so you can call function above function definition and it will work fine.
- Some functions require **parameters** to be specified when you are invoking them — these are values that need to be included inside the function parentheses, which it needs to do its job properly.
	- Parameters are sometimes called arguments, properties, or even attributes.
	- when you need to specify multiple parameters, they are separated by a comma.
	- Sometimes parameters are optional — you don't have to specify them. If you don't, the function will generally adopt some kind of default behavior.
	- If you're writing a function and want to support optional parameters, you can specify default values by adding `=` after the name of the parameter, followed by the default value:
	```Javascript
	function hello(name = "Chris") {
	  console.log(`Hello ${name}!`);
	}

	hello("Ari"); // Hello Ari!
	hello(); // Hello Chris!
```
- **Function Scope**
	- When you create a function, the variables and other things defined inside the function are inside their own separate **scope**, meaning that they are locked away in their own separate compartments, unreachable from code outside the functions.
	- The top level outside all your functions is called the global scope. Values defined in the global scope are accessible from everywhere in the code.
	- JavaScript is set up like this for various reasons — but mainly because of security and organization. Sometimes you don't want variables to be accessible from everywhere in the code — external scripts that you call in from elsewhere could start to mess with your code and cause problems because they happen to be using the same variable names as other parts of the code, causing conflicts. This might be done maliciously, or just by accident.
		- For example, say you have an HTML file that is calling in two external JavaScript files, and both of them have a variable and a function defined that use the same name:
		```HTML
		<!-- Excerpt from my HTML -->
		<script src="first.js"></script>
		<script src="second.js"></script>
		<script>
		  greeting();
		</script>
		```
		```Javascript
		// first.js
		const name = "Chris";
		function greeting() {
		  alert(`Hello ${name}: welcome to our company.`);
		}
		```
		```Javascript
		// second.js
		const name = "Zaptec";
		function greeting() {
		  alert(`Our company is called ${name}.`);
		}
		```
		- Both functions you want to call are called `greeting()`, but you can only ever access the `first.js` file's `greeting()` function (the second one is ignored). In addition, an error results when attempting (in the `second.js` file) to assign a new value to the `name` variable — because it was already declared with `const`, and so can't be reassigned.
		- Keeping parts of your code locked away in functions avoids such problems, and is considered the best practice.
	- **Return Values**
		- **Return values** are just what they sound like — the values that a function returns when it completes.
		- Some functions don't return any value. (In these cases, our reference pages list the return value as `void` or `undefined`.)