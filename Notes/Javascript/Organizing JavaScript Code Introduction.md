- Linting(looking at code and checking for errors, can also be configured for a certain style)
	- https://gomakethings.com/javascript-linters/
	- https://hackernoon.com/how-linting-and-eslint-improve-code-quality-fa83d2469efe
	- https://eslint.org/ 
	- https://prettier.io/
- Strings with spaces must be accessed through bracket notation as well as strings within a variable
- Objects created using object literal are singletons, this means when a change is made to the object, it affects the object entire the script. Whereas if an object is created using constructor function and a change is made to it, that change won't affect the object throughout the script
- object constructor - function that is used to make objects.
	- constructor function should start with a capital letter and is named after the object it constructs.
		- ex. fuction Player() is named so because it is constructing a player type object.
	- object constructor can be seen as a blueprint for creating many objects of the same type
		- this blueprint is constructed using what is called an object constructor function
		- In a constructor function 'this' does not have a value. It is a substitute for the new object. The value of 'this' will become the new object when a new object is created.
			- ex.  function Player(name, marker) {
			  this.name = name
			  this.marker = marker 
			  }
		- objects of the same type are called using the 'new' keyword
			- const player = new Player('steve', 'X')
		- we can use the call method to copy over properties from one constructor into another constructor
			- ex. name and level are defined in a previous constructor:
			- function Healer(name, level, spell) { Hero.call(this, name, level) this.spell = spell:}
			- to add new method we can then use something like this ex. Warrior.prototype.attack = function () {
			- return `${this.name} attacks with the ${this.weapon}.`;
			- Prototype properties and methods are not automatically linked when you use call() to chain constructors. We will use Object.setPropertyOf() to link the properties in the Hero constructor to the Warrior and Healer constructors, making sure to put it before any additional methods.
			- Object.setPrototypeOf(Warrior.prototype, Hero.prototype);
		-
```






