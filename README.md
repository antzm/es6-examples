# ES6 examples

## `let` and `const`
`let` and `const` should not be mixed with `var`.
If your code has all the variables declared with `var`, maybe it would be better to leave everything as it is.
Simply replacing every `var` with `let`, doesn't necessarily mean that your code will work.
For example, if you declared twice a variable with `var`, there is no problem, but replacing those two `var` declarations with `let` will cause an error, because you can only declare a certain variable only once when using `let` or `const`.

example:

```
var pet = "dog";
var pet = "cat";

// it would not produce an error, although the correct declaration
// for cat would have been:

pet = "cat";
```

On the other hand, if you write:

```
let pet = "hamster";
let pet = "fish";

// you will get the following error:
// Uncaught SyntaxError: Identifier 'pet' has already been declared
// thus, the only way to assign the value fish to the variable pet is:

pet = "fish";
```
Although everyone advices to use `let` and `const` nowadays, it may be preferable to use `var` when you simply test various scripts in the console log and every time you run the script you declare the same variables. This would help you to simplify and speed up things a little bit because you would only use one browser tab to test your code, while you will need a new browser tab every time you run a script that contains `let` or `const`.

### Performance issues between `let`, `const` and `var`
It may sound strange but there are performance issues in the current browsers, because intensive calculations using `let` and `const` run much faster compared to using `var`.
This is not something standard though, as it depends largely on the code and the browser. In any case, it looks like the current browsers are better optimized for `let` and `const` and less optimized for `var`.

To test these differences in the performance between `let` and `var`, you may try running the code below, which gives an approximation of PI, first with `let`, and then by replacing `let` with `var`.

```
console.time('Total time for Pi calculation: ');
let n=0, sum=0;
for (let i=1; i<1000000; i++) {
	n = 1 / (i*i);
	sum += n;
};
console.log("pi approximation = " + Math.sqrt(sum*6));
console.timeEnd('Total time for Pi calculation: ');
```
Try also to run the code in different browsers, so to compare the results between the browsers.

## Destructuring values from an array

Destructuring allows to easily extract values from an array and assign them to variables:

```
const data =  [12, 23, 15, -18, 36, 7, 10];

const [ , , x, , , y, , ] = data;
console.log(x, y); // 15 7

const [ , z] = data;
console.log(z); // 23
```
## Destructuring values from an object

In a similar way, destructuring allows to extract values from an object:
```
const pet = {
	species: "dog",
	name: "Merfys",
	color: "brown - white",
	birthday: "June 14th",
	age: 10,
	weight: 28
};

const {name, birthday} = pet;

console.log(name, birthday);

// Merfys June 14th
```
## The `for...of` loop
The `for...of` loop is a new addition to the JavaScript language and is a concise form of loop that can be used to loop any data that is iterable (i.e. string, array, map and set) as in the example below:
```
const pets = ["dog", "cat", "hamster", "fish"];

for (const pet of pets) {
	console.log(pet);
};

// dog
// cat
// hamster
// fish
```
## Arrow Functions
Here's a script that capitalizes the names of the pets using a regular function:
```
const pets = ["dog", "cat", "hamster", "fish"];

const upperizedPets = pets.map(function(pet) {
	return pet.toUpperCase();
});

for (const upperizedPet of upperizedPets) {
	console.log(upperizedPet);
};

// DOG
// CAT
// HAMSTER
// FISH
```
And here is the same script where the regular function has been replaced by an Arrow Function, which is a new addition to the ES6:
```
const pets = ["dog", "cat", "hamster", "fish"];

const upperizedPets = pets.map(
	pet => pet.toUpperCase()
);

for (const upperizedPet of upperizedPets) {
	console.log(upperizedPet);
};

// DOG
// CAT
// HAMSTER
// FISH
```
## The Spread `...` Operator
The spread operator is written with three dots `...` and is used to expand (spread) arrays (or more general, iterable objects) into multiple elements.
```
const pets = ["dog", "cat", "hamster", "fish"];
console.log(...pets);

// dog cat hamster fish
```
The spread operator can also be used to combine two or more arrays into one (instead of using concat).
```
const pets = ["dog", "cat", "hamster", "fish"];
const names =["Merfys", "Gatoulis", "Grizel", "Fegarenia"];

const petsNames = [...pets, ...names];

console.log(petsNames);

// ["dog", "cat", "hamster", "fish", "Merfys", "Gatoulis", "Grizel", "Fegarenia"]
```
## The Rest `...` parameter
The Rest parameter, represented also with three dots `...`, can be used in various ways.

In JavaScript, we may have functions that don't have any parameters but when we call them, we could call them with as many parameters as we would like. Everything would work just fine, although no parameters will pass into the function.
In a similar way, we could use e.g. 10 parameters to call a function which uses only two. In such a case, only the first two parameters will pass into the function and the rest will be ignored.

But what happens with the parameters which are not used by a function? Well, all those parameters can be stored in an array using the rest `...` parameter.

The rest parameter allows us also to call a function with as many parameters as we want, with no need to specify the number of those parameters.
```
housePets("dog", "cat", "hamster", "fish");
function housePets(...pets) {
	const ourPets = [];
	for (const pet of pets) {
		ourPets.push(pet);
	}
	console.log(ourPets)
}

//  ["dog", "cat", "hamster", "fish"]
```
In the above example, we called the function `housePets` with 4 parameters, but we could have used as many parameters as we would like. Using the rest parameter `...pets`, we take all the parameters and one by one we push them to the array `ourPets`.

In a similar way, we can use the rest parameter to pass into a function any number of parameters we need, like an unlimited numbers of parameters in order to calculate their sum, as in the following example:
```
function total(...prices) {
	let sum = 0;
	for (const price of prices) {
		sum += price;
	}
	console.log(sum);
}

total(1.25, 2.12, 3.25, 5.18, 4.36);

// 16.16
```
