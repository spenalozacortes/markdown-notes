# Types

## Types
#aqui
### From JavaScript to TypeScript
Invented in 1995, JavaScript was designed as a small scripting language for simple web pages in browsers. It wasn’t until 1999 that JavaScript was capable of supporting the kinds of dynamic web pages we see today, and using JavaScript that way wasn’t common practice until 2005.

To serve its original use-case, JavaScript was designed to be very flexible and easy to use for small applications. These features make JavaScript a great first language to learn, but they also make it less-than-ideal for building larger-scale applications with hundreds or even thousands of files. Stricter programming languages will inform the developer when they change one area of code in a way that will break other areas. JavaScript will not, which often leads to unexpected behavior at runtime.

To address these shortcomings, Microsoft developed TypeScript and released publicly in 2012 to blend the flexibility of JavaScript with the advantages of a stricter language.

TypeScript is a programming language that adds _types_ to JavaScript. It allows us to write JavaScript with a set of tools called a _type system_ that can spot potential bugs in, clarify the structure of, and help refactor our code. In addition, TypeScript added newer JavaScript language features, such as arrow [functions](https://www.codecademy.com/resources/docs/typescript/functions) and [classes](https://www.codecademy.com/resources/docs/typescript/classes), years before they were added to JavaScript officially.

### What is TypeScript?

- First, we write TypeScript code in files with the extension **.ts**.
- Next, we run our code through the TypeScript [transpiler](https://en.wikipedia.org/wiki/Source-to-source_compiler). The transpiler will check that the code adheres to TypeScript’s standards, and it will display errors when it does not.
- If the TypeScript code can be converted into working JavaScript, the transpiler will output a JavaScript version of the file (**.js**).

TypeScript code is a _superset_ of JavaScript code—it has all the features of traditional JavaScript but adds some new features.

Given this TypeScript code as input:

```ts
let firstName = 'Anders';
```

The TypeScript transpiler would output this JavaScript code:

```js
let firstName = 'Anders';
```

That’s right, they’re the same! TypeScript code generally looks roughly the same as the equivalent JavaScript.

---

The TypeScript transcompiler can be used on the command line by running the `tsc` command:

```shell
tsc
```

This will create an equivalent **.js** file in the same directory as well as surface any errors found by the TypeScript transcompiler.

Run the resultant JavaScript file with the `node` command:

```shell
node index.js
```

### Type Inferences
JavaScript allows us to assign any value to any variable. That makes it very flexible to use, which can be good for getting started quickly in coding. In practice, [variables](https://www.codecademy.com/resources/docs/typescript/variables) that are assigned values of multiple types throughout a program can be very confusing or lead to bugs.

One of the first things we’ll discover with TypeScript is that when we declare a variable with an initial value, the variable can never be reassigned a value of a different data type. This is an example of _type inference_: everywhere in our program, TypeScript expects the data type of the variable to match the type of the value initially assigned to it at declaration.


TypeScript recognizes JavaScript’s built-in “primitive” data types:

- boolean
- number
- null
- string
- undefined

If we try to reassign a variable to a value of a different type, TypeScript will surface an error.

```ts
let order = 'first';

order = 1;
```

Running the TypeScript code above will result in the following error being surfaced in the terminal: `Type 'number' is not assignable to type 'string'`.

We can fix this complaint by changing the new value to be the expected `string` type:

```ts
let order = 'first';

order = '1';
```

### Type Shapes
Because TypeScript knows what _types_ our objects are, it also knows what _shapes_ our objects adhere to. An object’s shape describes, among other things, what properties and methods it does or doesn’t contain.

The built-in types in JavaScript each have known properties and methods that always exist. All `string`s, for example, are known to have a `.length` property and `.toLowerCase()` method.

```js
"OH".length; // 2
"MY".toLowerCase(); // "my"
```

TypeScript’s `tsc` command will let you know if your code tries to access properties and methods that don’t exist:

```ts
"MY".toLowercase();
// Property 'toLowercase' does not exist on type '"MY"'.
// Did you mean 'toLowerCase'?
```

### Any
There are some places where TypeScript will not try to infer what type something is—generally when a variable is declared without being assigned an initial value. In situations where it isn’t able to infer a type, TypeScript will consider a variable to be of type `any`.

Variables of type `any` can be assigned to _any_ value and TypeScript won’t give an error if they’re reassigned to a different type later on.

```ts
let onOrOff;

onOrOff = 1;
onOrOff = false;
```

### Variable Type Annotations
In some situations, we’d like to declare a variable without an initial value while still ensuring that it will only ever be assigned values of a certain type. If left as `any`, TypeScript won’t be able to protect us from accidentally assigning a variable to an incorrect type that could break our code.

We can tell TypeScript what type something is or will be by using a _type annotation_.

Variables can have _type annotations_ (also known as type declarations) added just after their names. We provide a type annotation by appending a variable with a colon (`:`) and the type (e.g., `number`, `string`, or `any`).

```ts
let mustBeAString : string;
mustBeAString = 'Catdog';

mustBeAString = 1337;
// Error: Type 'number' is not assignable to type 'string'
```

### Review

- _TypeScript_ is a superset of JavaScript that adds types.
- The _type system_ refers to TypeScript’s understanding of how your code is meant to function: mainly what data types should be stored under your [variables](https://www.codecademy.com/resources/docs/typescript/variables).
- TypeScript expects the data type of the variable to match the type of the value initially assigned to it at its declaration—this is known as _type inference_.
- An object’s _shape_ describes, among other things, what properties and methods it does or doesn’t contain. TypeScript knows not only what type something is but also what shape that type has.
- When it isn’t able to infer a type, TypeScript will consider a variable to be of type `any`.
- _Type annotations_ are little pieces of code that indicate what type a variable is meant to be.

```ts
let youAreAwesome: boolean;
youAreAwesome = true;
```

## The tsconfig.json File
Sometimes, you don’t want all the [default rules](https://www.typescriptlang.org/docs/handbook/compiler-options.html) that TypeScript is trying to enforce — and that’s fine. That’s one reason why providing a **tsconfig.json** file is useful. Additionally, you get perks like telling the TypeScript compiler what files to run on and more!

### Sample tsconfig.json and Breakdown
The **tsconfig.json** file is always placed in the root of your project and you can customize what rules you want the TypeScript compiler to enforce.

```json
{
  "compilerOptions": {
    "target": "es2017",
    "module": "commonjs",
    "strictNullChecks": true
  },
  "include": ["**/*.ts"]
}
```

In the JSON, there are several properties:

- `"compilerOptions"`, which is a nested object that contains the rules for the TypeScript compiler to enforce.
    - `"target"`, the value `"es2017"` means the project will be using the 2017 version of EcmaScript standards for JavaScript.
    - `"module"`, this project will be using `"commonjs"` syntax to import and export modules.
    - `"strictNullChecks"`, variables can only have `null` or `undefined` values if they are explicitly assigned those values.
- `"include"` that determines what files the compiler applies the rules to. In this case `["**/*.ts"]` means the compiler should check every single file that has a **.ts** extension.

### Usage
Another neat addition is that by including a **tsconfig.json** file, you can now use the command `tsc` without any arguments in your terminal! The compiler will automatically recognize from your **tsconfig.json** file, what specific files to run on. You can still provide specific files like `tsc fileName.ts` if that’s the only file you want the compiler to check.

Check out TypeScript’s [compiler option documentation](https://www.typescriptlang.org/docs/handbook/compiler-options.html) for even more information.

# Functions

## Functions

### Introduction
When we declare a function in JavaScript, we often expect it to be invoked with arguments of a certain type. JavaScript does not share our expectations: its type flexibility often allows [functions](https://www.codecademy.com/resources/docs/typescript/functions) to be invoked with unexpected argument types. Even when this doesn’t result in thrown errors, there can be negative consequences:

```js
function printLengthOfText(text) {
  console.log(text.length);
}

printLengthOfText(3); // Prints: undefined
```

JavaScript developers have found error-handling solutions to avoid such undesirable effects, but these techniques can be cumbersome:

```js
function printLengthOfText(text) {
  if (typeof text !== 'string') {
    throw new Error('Argument is not a string!');
  }

  console.log(text.length);
}

printLengthOfText(3); // Error: Argument is not a string!
```

### Parameter Type Annotations
In TypeScript, function parameters may be given [type annotations](https://www.codecademy.com/resources/docs/typescript/type-annotations) with the same syntax as variable declarations: a colon next to the name. The type annotations ensure that the parameters are of the correct type:

```ts
function greet(name: string) {
  console.log(`Hello, ${name}!`);
}

greet('Katz'); // Prints: Hello, Katz  

greet(1337); // Error: argument '1337' is not assignable to parameter of type 'string'
```

Parameters that we do not provide type annotations for are assumed to be of type `any`—the same way [variables](https://www.codecademy.com/resources/docs/typescript/variables) are.

```ts
function printKeyValue(key: string, value) {
  console.log(`${key}: ${value}`);
}

printKeyValue('Courage', 1337); // Prints: Courage: 1337
printKeyValue('Mood', 'scared'); // Prints: Mood: scared
```

### Optional Parameters
TypeScript normally gives an error if we don’t provide a value for all arguments in a function. This isn’t always desirable; sometimes we’d like to skip providing values.

```ts
function greet(name: string) {
  console.log(`Hello, ${name || 'Anonymous'}!`);
}

greet('Anders'); // Prints: Hello, Anders!
greet(); // TypeScript Error: Expected 1 arguments, but got 0.
```

To indicate that a parameter is intentionally optional, we add a `?` after its name. This tells TypeScript that the parameter is allowed to be `undefined` and doesn’t always have to be provided.

```ts
function greet(name?: string) {
  console.log(`Hello, ${name|| 'Anonymous'}!`);
}

greet(); // Prints: Hello, Anonymous!
```






# Complex Types

## Arrays

## Custom Types









# Union Types

## Union Types







# Type Narrowing

## Type Narrowing







# Advanced Object Types

## Advanced Object Types


