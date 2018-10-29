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
It may sound strange but there are performance issues in the current browsers because intensive calculations using `let` and `const` run much faster compared to using `var`.
This is not something standard though, as it depends largely on the code and the browser. In any case, it looks like the current browsers are better optimized for `let` and `const` and less optimized for `var`.
