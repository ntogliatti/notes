- An array is a ordered collection of items(Strings, numbers, or other things). They are especially useful when dealing with large/complex amounts of data
- An array can hold many values under a single name, and you can access the values by referring to an index number.
- Arrays are declared in the same way as lists, but with `[]`
	- It is common practice to declare arrays using the `const` variable
- spaces and line breaks are no important for arrays, they can span multiple lines.
- you can create an array an then provide the elements like so:
 ```Javascript
 const cars = [];
cars[0]= "Saab";
cars[1]= "Volvo";
cars[2]= "BMW";
```
- You can access the elements in an array by referring to the index number; note that arrays begin with `0` 
	 ```javascript
	const cars = ["Saab", "Volvo", "BMW"];
	let car = cars[0];
```
- You can change the elements of an array by doing the following:
	 ```Javascript
	const cars = ["Saab", "Volvo", "BMW"];
	cars[0] = "Opel";
```
- you can convert arrays into a string of comma separated array values by using the method `toString()`:
	```javascript
	const fruits = ["apple", "banana", "grapefruit","mango"]
	let fruit = fruits.toString();
	console.log(fruit)
	```
- Full arrays can be accessed by referring to the array name
- Arrays are classified as objects in Javascript. in order to access the elements of an array you use numbers `example[0]` would access the first element  of the array `example`
- Arrays always use numbered indexes and objects always use named indexes
- Arrays can have variables of different types within the same array
	- For example you an have functions, objects,  or even arrays in a single array
- Arrays are especially useful for the built-in properties and methods.
- **USEFUL ARRAY METHODS**
	- `toString()` converts an array to a string of comma separated values
		- `join()` can also do this
		 ```javascript
		 const fruits = ["Banana", "Orange", "Apple", "Mango"];  
		document.getElementById("demo").innerHTML = fruits.join(" * ");
		//returns Banana * Orange * Apple * Mango
```
	- 
	- the `length` property returns the length of an array, it is called like so: `example.length`
	- you can access the first element of an array by using `example[0]`
	- similarly the last object can be accessed by using `example[-1]`
	- you can loop through an array using a `for` loop
	 ```javascript
	const fruits = ["Banana", "Orange", "Apple", "Mango"];  
	let fLen = fruits.length;  
  
	let text = "<ul>";  
	for (let i = 0; i < fLen; i++) {  
	  text += "<li>" + fruits[i] + "</li>";  
	}  
	text += "</ul>";
```
	- you can also achieve this by using `Array.forEach()`:
	 ```javascript
	const fruits = ["Banana", "Orange", "Apple", "Mango"];

	let text = "<ul>";
	fruits.forEach(myFunction);
	text += "</ul>";
	
	function myFunction(value) {
	  text += "<li>" + value + "</li>";
	}
```
	- The easiest way to add a new element to an array is using the `push()` method:
	 ```javascript
	 const fruits = ["Banana", "Orange", "Apple"];  
	fruits.push("Lemon"); 
	 // Adds a new element (Lemon) to fruits
```
	- This can also be done using the `length` property
	 ```javascript
	const fruits = ["Banana", "Orange", "Apple"];
	fruits[fruits.length] = "Lemon"; 
	 // Adds "Lemon" to fruits
```
	- the `pop()` method removes the last element in an array:
		 ```javascript
		 const fruits = ["Banana", "Orange", "Apple", "Mango"];  
		fruits.pop();
		//removes "Mango"
```
		- it can also return the value that was popped out
		 ```javascript
		 const fruits = ["Banana", "Orange", "Apple", "Mango"];  
		let fruit = fruits.pop();
		//fruit = "Mango"
```
	- the `shift()` is the same as `pop()`, but removes the first element and then shifts all the other elements to a lower index
	- The `unshift()` method adds a new element to an array (at the beginning), and "unshifts" older elements:
	 ```javascript
	 const fruits = ["Banana", "Orange", "Apple", "Mango"];  
	fruits.unshift("Lemon");
	//returns the new array length
```
	- Adding elements with high indexes can create undefined "holes" in an array:
		 ```javascript
		 const fruits = ["Banana", "Orange", "Apple"];
		fruits[6] = "Lemon"; 
		 // Creates undefined "holes" in fruits
```
- you can change an array element by using their array number
	- `example [0] = 'new element'` changes the first element in the array to `new element` 
- the `concat()` method creates a new array by merging (concatenating) existing arrays
	 ```javascript
	const myGirls = ["Cecilie", "Lone"];  
	const myBoys = ["Emil", "Tobias", "Linus"];  
  
	const myChildren = myGirls.concat(myBoys);
```
	- this method does not change the existing arrays, it always returns a new array
	- it can also take strings as arguments
- Flattening an array is the process of reducing the dimensionality of an array. The flat() method creates a new array with sub-array elements concatenated to a specified depth.
	 ```javascript
	 const myArr = [[1,2],[3,4],[5,6]];  
	const newArr = myArr.flat();
```
- `splice()` method adds new items to an array
	 ```javascript
	 const months = ['Jan', 'March', 'April', 'June'];
		months.splice(1, 0, 'Feb');
		// Inserts at index 1
		console.log(months);
		// Expected output: Array ["Jan", "Feb", "March", "April", "June"]

		months.splice(4, 1, 'May');
		// Replaces 1 element at index 4
		console.log(months);
		// Expected output: Array ["Jan", "Feb", "March", "April", "May"]
```
	- you can delete with `splice()` without leaving holes in your array
		 ```javascript
		 const fruits = ["Banana", "Orange", "Apple", "Mango"];  
		fruits.splice(0, 1);
		//will remove "banana"
```
- the `slice()` method slices out a piece of an array and put it into a new one
	 ```javascript
	const fruits = ["Banana", "Orange", "Lemon", "Apple", "Mango"];  
	const citrus = fruits.slice(1);
	//slices out everything after "orange"
```
	- you can use 2 arguments for `splice()` and the method will start removing from your first index and remove the amount that you specify in the 2nd argument.
		- `array.splice(3,1)` will just remove the 4th item in the array, while `array.splice(3,2)` will remove the 4th and 5th items
	- this is also true for the `slice()` method, however for `slice()`, the second number is where the method stops removing items. this means `slice()` starts at the first number, and removes until, but not including, the second number
- since arrays are technically defined as `objects`, we can't use the `typeof` operator. we get around this by using `Array.isArray()`
	- you can also use `instanceof` operator, which can be used for more than just arrays:
		- `instanceof Array`