
+ One action, or method, that is built into the `console` object is the `.log()` method. When we write `console.log()` what we put inside the parentheses will get printed, or logged, to the console.
	+ When to use single quotes (’ ') and when double (" ")?
	+  Does numbers include negative?
+  What is the difference between a property and a method?
	+  A method is an attribute, but that does not make an attribute a method. A method is function, so performs some task. `.length` is a value, only.
	+  Properties of an object can be either a value, or a method (a function only accessible to an instance of the object).

	We _poll_ values, and _call_ (or invoke) methods.
	
	+ JavaScript is case sensitive so all methods and functions must be written the way they appear in the specs
	+ When to use `var`, when to use `let`?
	+ The `let` keyword signals that the variable can be reassigned a different value.
	+ However, a `const` variable cannot be reassigned because it is _constant_. If you try to reassign a `const` variable, you’ll get a `TypeError`. They must be assigned when they are declared.
	+ we can insert, or _interpolate_, variables into strings using _template literals_.
	+ Why template literals?
	+ `===` vs `==`?
	+ truthy and falsey
	+ Hoisting functions, what
	+ parameters, arguments, identifiers
	+ function expressions
	+ Can you change parameters on constant functions?
	+ Arrow functions remove the need to type out the keyword `function` every time you need to create a function
	+ implicit return

![](jsf1.png)
![](jsf2.png)

+ _global namespace_.
+ Variables declared with the `const` keyword cannot be reassigned. However, elements in an array declared with `const` remain mutable.
+ In JavaScript, functions are _first class objects_. This means that, like other objects you’ve encountered, JavaScript functions can have properties and methods.

Since functions are a type of object, they have properties such as `.length` and `.name` and methods such as `.toString()`.

- ![](js3.png)
- `.map()` works in a similar manner to `.forEach()`— the major difference is that `.map()` returns a new array.
- And then there's a bunch of other iterators
- There are only seven fundamental data types in JavaScript, and six of those are the primitive data types: string, number, boolean, null, undefined, and symbol. With the seventh type, objects, we open our code to more complex possibilities.
- A property is what an object has, while a method is what an object does.
- That’s because you’ve been using them all along! For example `console` is a global javascript object and `.log()` is a method on that object. `Math` is also a global javascript object and `.floor()` is a method on it.
- Objects are _passed by reference_. This means when we pass a variable assigned to an object into a function as an argument, the computer interprets the parameter name as pointing to the space in memory holding that object. As a result, functions which change object properties actually mutate the object permanently (even when the object is assigned to a `const` variable).

> However, reassignment of the `spaceship` variable wouldn’t work in the same way:

```
let spaceship = {  homePlanet : 'Earth',  color : 'red'};
let tryReassignment = obj => 
	{  obj = {    identified : false,     'transport type' : 'flying'  } 
	console.log(obj) // Prints {'identified': false, 'transport type': 'flying'} };tryReassignment(spaceship) // The attempt at reassignment does not work.spaceship // Still returns {homePlanet : 'Earth', color : 'red'}; spaceship = {  identified : false,   'transport type': 'flying'}; // Regular reassignment still works.
```

Let’s look at what happened in the code example:

-   We declared this `spaceship` object with `let`. This allowed us to reassign it to a new object with `identified` and `'transport type'` properties with no problems.
-   When we tried the same thing using a function designed to reassign the object passed into it, the reassignment didn’t stick (even though calling `console.log()` on the object produced the expected result).
-   When we passed `spaceship` into that function, `obj` became a reference to the memory location of the `spaceship` object, but _not_ to the `spaceship` variable. This is because the `obj` parameter of the `tryReassignment()` function is a variable in its own right. The body of `tryReassignment()` has no knowledge of the `spaceship` variable at all!
-   When we did the reassignment in the body of `tryReassignment()`, the `obj` variable came to refer to the memory location of the object `{'identified' : false, 'transport type' : 'flying'}`, while the `spaceship` variable was completely unchanged from its earlier value.
- Objects are collections of related data and functionality. We store that functionality in methods on our objects:
- **The `this` keyword references the _calling object_ which provides access to the calling object’s properties.**
- Arrow functions inherently _bind_, or tie, an already defined `this` value to the function itself that is NOT the calling object. In the code snippet above, the value of `this` is the _global object_, or an object that exists in the global scope, which doesn’t have a `dietType` property and therefore returns `undefined`.
- ![](js4.png)
- However, there are cases in which we don’t want other code simply accessing and updating an object’s properties. When discussing _privacy_ in objects, we define it as the idea that only certain properties should be mutable or able to change in value.
-  Getters can return the value of internal properties and setters can safely reassign property values.
-  So far we’ve been creating objects individually, but there are times where we want to create many instances of an object quickly. Here’s where _factory functions_ come in. A real world factory manufactures multiple copies of an item quickly and on a massive scale. A factory function is a function that returns an object and can be reused to make multiple object instances. Factory functions can also have parameters allowing us to customize the object that gets returned.
-  ES6 introduced some new shortcuts for assigning properties to variables known as _destructuring_.
-   _destructured assignment_
-   Class method and getter syntax is the same as it is for objects **except you can not include commas between methods**.


- 1.  Notice that, when we use named exports, we are not setting the properties on an object. Each export is stored in its own variable.
2.  `specialty` is a string object, while `isVegetarian` and `isLowSodium` are objects in the form of functions. Recall that in JavaScript, every function is in fact a function object.
3.  
```

```

![](arrow_func_js.png)