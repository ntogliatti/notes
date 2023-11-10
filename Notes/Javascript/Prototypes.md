https://www.digitalocean.com/community/tutorials/understanding-prototypes-and-inheritance-in-javascript
-Stated simply, the prototype is another object that the original object _inherits_ from, which is to say, the original object has access to all of its prototype’s methods and properties.
-each object has access to the prototypes of the object below it;
	- ex. since function is below an array in the chain, it has access to all the prototype methods of itself, as well as the prototype methods of a function and so on. 
	- the chain of prototypes ends with object.prototype, which is null
-you are capable of adding an object constructor function to whatever prototype level you want, so that it will be available to everything above it 
	- ex. Object.getPrototypeOf(Array.prototype).dingDong = function dingDong(){
  alert('DING DONG')
  }

