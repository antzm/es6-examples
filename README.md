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

for (upperizedPet of upperizedPets) {
	console.log(upperizedPet);
};

// DOG
// CAT
// HAMSTER
// FISH
```
And here is the same script where the regular function has been replaced by an Arrow Function:
```
const pets = ["dog", "cat", "hamster", "fish"];

const upperizedPets = pets.map(
	pet => pet.toUpperCase()
);

for (upperizedPet of upperizedPets) {
	console.log(upperizedPet);
};

// DOG
// CAT
// HAMSTER
// FISH
```
