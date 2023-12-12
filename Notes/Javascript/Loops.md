- Most of the time when you use a loop, you will have a collection of items and want to do something with every item.
	- Arrays, sets and maps are a few types of collections that you can use in javascript
- `for...of` loops
	- most basic type of loop 
	```javascript
	const cats = ["Leopard", "Serval", "Jaguar", "Tiger", "Caracal", "Lion"];

	for (const cat of cats) {
	  console.log(cat);
	}
```
	- this example is saying:
		1. Given the collection `cats`, get the first item in the collection.
		2. Assign it to the variable `cat` and then run the code between the curly braces `{}`.
		3. Get the next item, and repeat (2) until you've reached the end of the collection.
- `map()` and `filter()` are more specialized loops
	- `map()` can be used to do something to each item in a collection and create a new collection containing the changed items
		 ```javascript
		 function toUpper(string) {
		  return string.toUpperCase();
		}

		const cats = ["Leopard", "Serval", "Jaguar", "Tiger", "Caracal", "Lion"];

		const upperCats = cats.map(toUpper);

		console.log(upperCats);
		// [ "LEOPARD", "SERVAL", "JAGUAR", "TIGER", "CARACAL", "LION" ]
```
		- Here we pass a function into `cats.map()` and `map()` calls the function once for each item in the array, passing in the item. It then adds the return value from each function call to a new array, and finally returns the new array. In this case the function we provide converts the item to uppercase, so the resulting array contains all our cats in uppercase.
	- You can use `filter()` to test each item in a collection, and create a new collection containing only items that match:
		 ```javascript
		 function lCat(cat) {
		  return cat.startsWith("L");
		}

		const cats = ["Leopard", "Serval", "Jaguar", "Tiger", "Caracal", "Lion"];

		const filtered = cats.filter(lCat);

		console.log(filtered);
		// [ "Leopard", "Lion" ]
```
		- This looks a lot like `map()`, except the function we pass in returns a boolean if it returns `true`, then the item is included in the new array. Our function tests that the item starts with the letter "L", so the result is an array containing only cats whose names start with "L"
	- note that `map()` and `filter()` are both often used with _function expressions_,
- `for` loops
	- for loops are expressed as:
	- `for (initializer; condition; final-expression)
	1. The keyword `for`, followed by some parentheses.
	2. Inside the parentheses we have three items, separated by semicolons:
		1. An **initializer** — this is usually a variable set to a number, which is incremented to count the number of times the loop has run. It is also sometimes referred to as a **counter variable**.
		2. A **condition** — this defines when the loop should stop looping. This is generally an expression featuring a comparison operator, a test to see if the exit condition has been met.
		3. A **final-expression** — this is always evaluated (or run) each time the loop has gone through a full iteration. It usually serves to increment (or in some cases decrement) the counter variable, to bring it closer to the point where the condition is no longer `true`.
	3. Some curly braces that contain a block of code — this code will be run each time the loop iterates.
	 ```javascript
		 const results = document.querySelector("#results");

		function calculate() {
	  for (let i = 1; i < 10; i++) {
	    const newResult = `${i} x ${i} = ${i * i}`;
	    results.textContent += `${newResult}\n`;
		  }
		  results.textContent += "\nFinished!";
		}

		const calculateBtn = document.querySelector("#calculate");
		const clearBtn = document.querySelector("#clear");

		calculateBtn.addEventListener("click", calculate);
		clearBtn.addEventListener("click", () => (results.textContent = ""));
		//1 x 1 = 1
		//2 x 2 = 4
		//3 x 3 = 9
		//4 x 4 = 16
		//5 x 5 = 25
		//6 x 6 = 36
		//7 x 7 = 49
		//8 x 8 = 64
		//9 x 9 = 81

		//Finished!
```
	-  This code calculates squares for the numbers from 1 to 9, and writes out the result. The core of the code is the `for` loop that performs the calculation.
	- the `for (let i = 1; i < 10; i++)` 
		1. `let i = 1`: the counter variable, `i`, starts at `1`. Note that we have to use `let` for the counter, because we're reassigning it each time we go round the loop.
		2. `i < 10`: keep going round the loop for as long as `i` is smaller than `10`.
		3. `i++`: add one to `i` each time round the loop.
	- Inside the loop, we calculate the square of the current value of `i`, that is: `i * i`. We create a string expressing the calculation we made and the result, and add this string to the output text. We also add `\n`, so the next string we add will begin on a new line. So:
		1. During the first run, `i = 1`, so we will add `1 x 1 = 1`.
		2. During the second run, `i = 2`, so we will add `2 x 2 = 4`.
		3. And so on…
		4. When `i` becomes equal to `10` we will stop running the loop and move straight to the next bit of code below the loop, printing out the `Finished!` message on a new line.
	- You can use a `for` loop to iterate through a collection, instead of a `for...of` loop.
	- instead of using the `for...of` loop in the example above you can do the following:
	```javascript
	const cats = ["Leopard", "Serval", "Jaguar", "Tiger", "Caracal", "Lion"];

	for (let i = 0; i < cats.length; i++) {
	  console.log(cats[i]);
	}
```
- while this works, it is generally better to use `for...of` loops, since there is less chance of introducing bugs to your code. it is sometimes necessary to use a `for` loop to iterate through an array
	 ```javascript
	 const cats = ["Pete", "Biggles", "Jasmine"];

	let myFavoriteCats = "My cats are called ";

	for (const cat of cats) {
	  myFavoriteCats += `${cat}, `;
	}

	console.log(myFavoriteCats);
	 // "My cats are called Pete, Biggles, Jasmine, "
```
	```javascript
	const cats = ["Pete", "Biggles", "Jasmine"];

	let myFavoriteCats = "My cats are called ";

	for (let i = 0; i < cats.length; i++) {
	  if (i === cats.length - 1) {
	    // We are at the end of the array
	    myFavoriteCats += `and ${cats[i]}.`;
	  } else {
	    myFavoriteCats += `${cats[i]}, `;
	  }
	}

	console.log(myFavoriteCats);
	 // "My cats are called Pete, Biggles, and Jasmine."
```
	- while the first example works, it doesn't look as good as the second. by using a `for` loop we can can set the final loop iteration and thus add a period at the end
- if you want to exit a loop before all iterations have been completed you can use the `break` statement
	- `break` statements will immediately exit the loop and make the browser move on to any code that follows it
	- for example, if we wanted to search through an array for a a specific contact and phone number we can do so by using `break` 
		 ```javascript
		const contacts = [
	    "nick: 1234567",
	    "amber: 5342871",
	    "mimi: 0984763",
	    "chicken: 9487562",
	    "poop: 3986754",
	];
	
	let searchName = "nick"
	for (const contact of contacts) {
	    const splitContact = contact.split(":");
	    if (splitContact[0].toLowerCase() === searchName) {
	        console.log(`${splitContact[0]}'s phone number is ${splitContact[1]}`);
	        break;
	    }
	}
	//nick's phone number is 124567
```
	an example with html could look like:
	```html
	<label for="search">Search by contact name: </label>
	<input id="search" type="text" />
	<button>Search</button>

	<p></p>
```
	```javascript
	const contacts = [
	  "Chris:2232322",
	  "Sarah:3453456",
	  "Bill:7654322",
	  "Mary:9998769",
	  "Dianne:9384975",
	];
	const para = document.querySelector("p");
	const input = document.querySelector("input");
	const btn = document.querySelector("button");
	
	btn.addEventListener("click", () => {
	  const searchName = input.value.toLowerCase();
	  input.value = "";
	  input.focus();
	  para.textContent = "";
	  for (const contact of contacts) {
	    const splitContact = contact.split(":");
	    if (splitContact[0].toLowerCase() === searchName) {
	      para.textContent = `${splitContact[0]}'s number is ${splitContact[1]}.`;
	      break;
	    }
	  }
	  if (para.textContent === "") {
	    para.textContent = "Contact not found.";
	  }
	});

```
1. First of all, we have some variable definitions — we have an array of contact information, with each item being a string containing a name and phone number separated by a colon.
2. Next, we attach an event listener to the button (`btn`) so that when it is pressed some code is run to perform the search and return the results.
3. We store the value entered into the text input in a variable called `searchName`, before then emptying the text input and focusing it again, ready for the next search. Note that we also run the [`toLowerCase()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/toLowerCase) method on the string, so that searches will be case-insensitive.
4. Now on to the interesting part, the `for...of` loop:
    1. Inside the loop, we first split the current contact at the colon character, and store the resulting two values in an array called `splitContact`.
    2. We then use a conditional statement to test whether `splitContact[0]` (the contact's name, again lower-cased with [`toLowerCase()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/toLowerCase)) is equal to the inputted `searchName`. If it is, we enter a string into the paragraph to report what the contact's number is, and use `break` to end the loop.
5. After the loop, we check whether we set a contact, and if not we set the paragraph text to "Contact not found.".
- the  `continue` statement is similar to `break`, but instead of breaking out the loop entirely, it skips to the next iteration
	```javascript
	let text = '';

	for (let i = 0; i < 10; i++) {
	  if (i === 3) {
	    continue;
	  }
	  text = text + i;
	}

	console.log(text);
	// Expected output: "012456789"
```
	- in the above example, 3 isn't printed since the `text = text + 1;` is terminated and the next iteration of the loop is started
- `While` loops are similar to to `for` loops except that the initializer variable is set before the loop, and the final-expression is included inside the loop after the code to run, rather than these two items being included inside the parenthesis:
	 ```javascript
	 initializer
	while (condition) {
	  // code to run

	  final-expression
	}
	 ```
	 - our cat list example from earlier can be rewritten using a while loop:
		  ```javascript
		  const cats = ["Pete", "Biggles", "Jasmine"];

		let myFavoriteCats = "My cats are called ";
		
		let i = 0;
		
		while (i < cats.length) {
		  if (i === cats.length - 1) {
		    myFavoriteCats += `and ${cats[i]}.`;
		  } else {
		    myFavoriteCats += `${cats[i]}, `;
		  }
		
		  i++;
		}
		
		console.log(myFavoriteCats); 
		// "My cats are called Pete, Biggles, and Jasmine."
```
	- the `do...while` loop is also similar, but provides a variation on the while structure:
		 ```javascript
		 initializer
		do {
		  // code to run
		
		  final-expression
		} while (condition)
```
		- The main difference between a `do...while` loop and a `while` loop is that _the code inside a `do...while` loop is always executed at least once_.
		- That's because the condition comes after the code inside the loop. So we always run that code, then check to see if we need to run it again. In `while` and `for` loops, the check comes first, so the code might never be executed.
		- the cat example can again be rewritten:
		 ```javascript
		 const cats = ["Pete", "Biggles", "Jasmine"];

		let myFavoriteCats = "My cats are called ";
		
		let i = 0;
		
		do {
		  if (i === cats.length - 1) {
		    myFavoriteCats += `and ${cats[i]}.`;
		  } else {
		    myFavoriteCats += `${cats[i]}, `;
		  }
		
		  i++;
		} while (i < cats.length);
		
		console.log(myFavoriteCats); 
		// "My cats are called Pete, Biggles, and Jasmine."
```
