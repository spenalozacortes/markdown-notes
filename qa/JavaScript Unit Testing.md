# Why Test?

## Why Test?

### Manual Testing
_Software testing_ is the process of assessing the completeness and quality of computer software. Usually this is done by running a part of a system (like a web application) and comparing the actual behavior to the expected behavior.

One way to perform software testing is _manual testing_. Manual testing is a form of testing done by a human interacting with a system. With web apps, this might be clicking, dragging, and typing through a webpage. A list of actions and expected behaviors would be given. If the observed behavior doesn’t match the expected behavior, the application has an error.

Errors, like the ones you may have found in the provided web app, are also called _bugs_. A bug is an error, fault, or flaw in software that makes a system behave in unexpected ways.

### Automated Testing
_Automated testing_ is the use of software to control the execution of tests and the comparison of actual behavior to expected behavior.

Compared to manual testing, automated testing is

- Faster: it tests more of your product in less time.
- More reliable: it’s less prone to error than a human is .
- Maintainable: you can review, edit, and extend a collection of tests.

Rather than hire a testing team at the end of development, professional developers can run their automated tests after every change. The workflow might look like this:

1. Write code and corresponding tests
2. Enter a command into a terminal to run tests
3. If the app behaves as intended, all tests should pass. Development is complete.
4. If it does not behave as intended, at least one test should fail. Fix code and return to step 2.

### The Test Suite
Tests are written with code, just like the rest of your web app. You can refer to the code defining your app as _implementation code_, and the code defining your tests as _test code_.

A collection of tests for a web application is called a _test suite_. In the last exercise, you ran a test suite with `npm test`. In that case the test suite contained all tests for the application.

Test code is included with and structured similarly to implementation code. Often times changes to test code are associated with changes to implementation code and vice versa. Both are easier to maintain when they are stored in the same place.

For example, if implementation code is written in `index.js` then the corresponding test code may be written in `index-test.js`.

### Tests As Documentation
Documentation is any content separate from implementation code that explains how it works or how to use it. It may provide more concise summaries and explanation than the implementation code can.

Documentation can come in many forms, including plain text, diagrams…and tests! Tests as documentation provide what many other forms cannot: both human-readable text to describe the application and machine-executable code to confirm the app works as described.

This code block from the Cake Bar app describes and tests the “name” functionality.

```js
it('accepts the customer name', () => {
  const name = 'Hungry Person';

  browser.url('/');
  browser.setValue('#name', name);
  browser.click('#submit-order');
  browser.url('/');

  assert.include(browser.getText('#deliver-to'), name);
});
```

You can read the description in plain English terms: `it accepts the customer name`. You can run the test to confirm the functionality works as described.

### Regression
When adding a new feature to your product, it’s possible that something will break. If that break occurs within a feature developed earlier, it is called _regression_. When functionality previously developed and tested stops working, you may say the _functionality regressed_.

Running an automated test suite is fast and repeatable, which means you can run tests after every change to confirm that old features still work. If they have regressed, the test output should notify you.

### Review
Writing automated tests takes time, but the cost is outweighed by the benefits. Automated testing

- Increases confidence that your product works as expected (compared to manual testing)
- Improves upon documentation
- Reduces the likelihood of regression

You also learned

- Where and why test code is stored alongside implementation code
- Terms to help communicate the benefit of testing: _manual testing_, _automated testing_, _test suite_, _bug_, _documentation_, and _regression_


# Write Good Tests With Mocha

## Automate and Organize Tests

### Install Mocha
Before writing any tests you’ll need to use [Node.js and npm](https://www.codecademy.com/articles/what-is-node) to set up a JavaScript project and install Mocha.

- _Node_ allows you to run JavaScript in the terminal
- [_npm_](https://www.codecademy.com/resources/docs/javascript/npm) is a Node tool that allows you to download packages from the web, and manage them in a JavaScript project
- _Mocha_ is one of those packages and is used to test other JavaScript code

A JavaScript project is a directory of files. The following command creates a file **package.json** that can be used to manage packages for the project.

```sh
npm init
```

After running this command you will be prompted to enter information about your project. It’s okay to skip some fields if you’re not ready to enter that information.

With your project setup, you can install packages.

```sh
npm install mocha -D
```

Here’s what this command means:

- `npm install` tells npm to install a package from the internet and any other packages it depends on
- `mocha` is the package you want to download
- `-D` signifies that this package is a development dependency and will show up under the `devDependecies` section in **package.json**. This means that the package will only be included in development mode and will not be included in the production bundle.

Once you `npm install` packages, you can find the packages and all their dependencies in the **node_modules** folder. The new directory structure contains the following:

```
project
|_ node_modules
|___ .bin
|___ mocha
|___ ...
|_ package.json
```

The `...` in the file structure represents other packages that are a dependency for Mocha.

After installing Mocha as a dependency we can run it in two ways.

The first (and more tedious) method is to call it directly from **node_modules**:

```sh
 ./node_modules/mocha/bin/mocha
```

The second (and recommended) method is to add a script to **package.json**. In the `scripts` object in **package.json**, set the value of `"test"` to `mocha`. It should look like this:

```json
"scripts": {
  "test": "mocha"
}
```

Now you can call Mocha with the following command:

```sh
npm test
```

Instead of manually running each test in the **test** directory, you can use this command to run the full test suite automatically.

### describe and it blocks
In Mocha we group tests using the `describe` function and define tests using the `it` function. These two [functions](https://www.codecademy.com/resources/docs/javascript/functions) can be used to make your test suite _complete_, _maintainable_, and _expressive_ in the following ways:

- Structure your test suite: you can organize tests into nested groups that reflect the structure of your implementation code.
- Provide informative messages: you can define your tests using human-readable [strings](https://www.codecademy.com/resources/docs/javascript/strings).

If you are testing a `Math` object with the method `.max`, you could use the following test code.

```js
describe('Math', () => {
  describe('.max', () => {
    it('returns the argument with the highest value', () => {
      // Your test goes here
    });
    it('returns -Infinity when no arguments are provided', () => {
      // Your test goes here
    });
  });
});
```

Both the `describe` and `it` functions accept two parameters: a descriptive string and a callback function. Though the functions are flexible, they are commonly used in the structure above: nest `describe` blocks to resemble the structure of your implementation code and write individual tests in `it` blocks. This makes your test suite _isolated_, _maintainable_, and _expressive_.

### assert
To write the tests themselves, we can use the `assert.ok` method provided by Node.js.

In programming, a test compares an expected outcome to an actual outcome. For example, we expect the outcome of the following code…

```js
const a = 1 + 2;
```

…to be: `a` has a value of `3`.

To test the value saved to `a` with plain JavaScript, you would need to write a conditional statement comparing `a` to the expected result. Inside the statement, you would construct an error when the actual outcome does not match the expected.

```js
if (a !== 3) {
  throw 'Test failed! a is not 3'
} 
```

`assert.ok()` allows you to compare values and throw [errors](https://www.codecademy.com/resources/docs/javascript/errors) as needed using one function call. The small, human-readable format of the [functions](https://www.codecademy.com/resources/docs/javascript/functions) will help you make a more _expressive_ test suite.

As a Node module, `assert` can be imported at the top of your files with

```js
const assert = require('assert');
```

You call `assert` functions like this:

```js
assert.ok(a === 3);
```

In this case `a === 3` evaluates to `true`, so no error is thrown.

If an argument passed to `assert.ok()` evaluates to false, an `AssertionError` is thrown. The error communicates to Mocha that a test has failed, and Mocha logs the error message to the console.

### Setup, Exercise, and Verify
This distinct and well-defined separation of steps makes your test more _reliable_, _maintainable_, and _expressive_.

The phases are defined as follows:

- _Setup_ - create [objects](https://www.codecademy.com/resources/docs/javascript/objects), [variables](https://www.codecademy.com/resources/docs/javascript/variables), and set conditions that your test depends on
- _Exercise_ - execute the functionality you are testing
- _Verify_ - check your expectations against the result of the exercise phase. You can use the `assert` library here

Clear separation of each phase makes a test easier to read, change, and validate.

### Teardown
So far, we’ve been writing just one test using a single `it()` block. However, in most situations, we will need to write many tests for a particular feature that get executed in succession.

Running multiple tests can introduce issues if the tests make changes to the testing environment: changes to the environment in one test might affect the next test. Some common changes to an environment include:

- altering files and directory structure
- changing read and write permissions on a file
- editing records in a database

To address this issue, we often add a _teardown_ step to the end of our tests. The teardown phase makes our tests _isolated_ by resetting the environment before the next test runs. This provides two key benefits:

- Changes to the environment caused by one test do not affect the other tests.
- Isolated tests can be executed in any order!

**Note**: In some cases the _teardown_ phase isn’t needed because there are no conditions to reset.

---

`fs.appendFileSync(path, str)` creates a new file at `path` with the string `str` as content. If a file at `path` exists, the string `str` will be appended to the end.

`fs.readFileSync(path)` returns the contents of the file found at `path`.

The first test found in this exercise verifies that we can use `fs.appendFileSync()` to create a file called **./message.txt** with the string `'Hello Node.js'`. The second test verifies that we can do the same but with an empty string.

Add this code below `// Teardown` in both tests to delete the file after the test has completed.

```js
fs.unlinkSync(path);
```

**Why do we delete the file after the second test?** We want to ensure that the environment returns to its state before the tests were executed. This keeps the tests isolated.

```js
const assert = require('assert');
const fs = require('fs');
let path, str;
 
describe('appendFileSync', () => {
  it('creates a new file with a string of text', () => {
 
   // Setup
   path = './message.txt';
   str = 'Hello Node.js';
  
   // Exercise: write to file
   fs.appendFileSync(path, str);
 
   // Verify: compare file contents to string
   const contents = fs.readFileSync(path);
   assert.equal(contents.toString(), str);
 
   // Teardown: restore file
  fs.unlinkSync(path);
 });
 
 it('creates a new file with a string of text', () => {
 
   // Setup
   path = './message.txt';
   str = '';
  
   // Exercise: write to file
   fs.appendFileSync(path, str);
 
   // Verify: compare file contents to string
   const contents = fs.readFileSync(path);
   assert.equal(contents.toString(), str);
 
   // Teardown: restore file
  fs.unlinkSync(path);
 });
});
```

### Hooks
While execution and verification are unique to each test, setup and teardown are often similar or even identical for multiple tests within a test suite. The Mocha test framework provides [functions](https://www.codecademy.com/resources/docs/javascript/functions) that enable us to reduce repetition, simplify the scope of each test, and more finely control the execution of our tests.

These functions (also referred to as _hooks_) are:

- `beforeEach(callback)` - `callback` is run before each test
- `afterEach(callback)` - `callback` is run after each test
- `before(callback)` - `callback` is run before the first test
- `after(callback)` - `callback` is run after the last test

Each hook accepts a callback to be executed at various times during a test. The `before...` hooks naturally happen before tests and are useful for separating out the setup steps of your tests. Meanwhile, the `after...` hooks are executed after tests and are useful for separating out the teardown steps of your tests.

```js
describe('messing around with hooks', () => {

  let testValue; // Variable used by both tests

  beforeEach(() => {
    testValue = 5;
  });

  it('should add', () => {
    // testValue = 5 <-- moved to beforeEach()
    testValue = testValue + 5;
    assert.equal(testValue, 10);
  });

  it('should multiply', () => {
    // testValue = 5 <-- moved to beforeEach()
    testValue = testValue * 5;
    assert.equal(testValue, 25);
  });

});
```

Keep in mind that not all setup and teardown steps should be included in these hooks. Occasionally, you may find that you need to perform some unique setup or teardown for a single test that you don’t want to include in other tests.

### Review
- Install Mocha with npm
- Organize tests with `describe()` and `it()`
- Ensure your tests are isolated and expressive with the four phases of a test
- Ensure your tests are reliable with hooks
- Write assertions with `assert.ok()`

As you continue to write tests, remember to always evaluate them against [the characteristics of a good test](https://www.codecademy.com/articles/tdd-u1-good-test): fast, complete, reliable, isolated, maintainable, and expressive.


## Write Expressive Tests

### Introduction
An expressive test is easy to read and descriptive, making it useful as a form of documentation for your implementation code. One way to make a test more expressive is clarifying its _verify_ phase — the step where expected outcome is compared to actual outcome.

[Node.js](https://www.codecademy.com/articles/what-is-node) provides a library called `assert` with [methods](https://www.codecademy.com/resources/docs/javascript/methods) that help you write more expressive verification code. You can use the methods in this library in place of conditional [statements](https://www.codecademy.com/resources/docs/javascript/statements) to write less code and use human-readable language. It can be used within the Mocha testing framework.

### assert.ok
As a Node module, `assert` can be imported at the top of your files with

```js
const assert = require('assert');
```

The [functions in the `assert` library](https://nodejs.org/api/assert.html) compare values and throw [errors](https://www.codecademy.com/resources/docs/javascript/errors) as needed using one function call. The small, human-readable format of the [functions](https://www.codecademy.com/resources/docs/javascript/functions) will help you make a more _expressive_ test suite.

```js
assert.ok(6 - 1 === 5);
```

In this case `6 - 1 === 5` evaluates to `true`, so no error is thrown.

If an argument passed to `assert.ok()` evaluates to `false`, an `AssertionError` is thrown. The error communicates to Mocha that a test has failed, and Mocha logs the error message to the console.

### assert.equal
You can use `assert.ok()` for most verifications, but sometimes it can be difficult to determine the condition you are evaluating.

```js
const landAnimals = ['giraffe', 'squirrel'];
const waterAnimals = ['shark', 'stingray'];

landAnimals.push('frog');
waterAnimals.push('frog');

assert.ok(landAnimals[2] == waterAnimals[2]);
```

The above assertion is checking for equality. In order to understand this you must evaluate the entire expression within the parentheses of `.ok()`.

You can instead use `assert.equal()` which does the `==` comparison for us.

In the example below, the two [methods](https://www.codecademy.com/resources/docs/javascript/methods) achieve the same outcome.

```js
assert.ok(landAnimals[2] == waterAnimals[2]);
assert.equal(landAnimals[2], waterAnimals[2]);
```

The second line is more _expressive:_ instead of parsing the entire statement, a reader only needs to read the first two words to know the test is verifying equality!

---

Though your test will work regardless of the order you pass the `result` and `expected`, it is common practice to pass `result` first and `expected` second.

### assert.strictEqual
Will these assertions throw errors?

```js
const a = 3;
const b = '3';
assert.ok(a == b);
assert.ok(a === b);
```

- The first assertion will not throw an error because it uses loose (`==`) equality. It performs a type conversion when comparing two things.
- The second will throw an error because it uses strict (`===`) equality. It returns `false` if the types differ.

If you need to be strict in evaluating equality, you can use `assert.strictEqual()`.

- `assert.equal()` performs a `==` comparison
- `assert.strictEqual()` performs a `===` comparison

Compare the following code to the first example. This code performs the same verifications, but it is more _expressive_. Without parsing any logic, a reader would know the intention of your tests by reading the method names.

```js
const a = 3;
const b = '3';
assert.equal(a, b);
assert.strictEqual(a, b);
```

July 2021 Update: the [`assert` documentation](https://nodejs.org/api/assert.html#assert_assert_equal_actual_expected_message) recommends always using `assert.strictEqual()` instead of `assert.equal()`.

### assert.deepEqual
Do you think these assertions will throw errors?

```js
const a = {relation: 'twin', age: '17'};
const b = {relation: 'twin', age: '17'};
assert.equal(a, b);
assert.strictEqual(a, b);
```

Both assertions will throw an error because distinct [objects](https://www.codecademy.com/resources/docs/javascript/objects) are not considered equal when using either loose or strict equality in JavaScript.

If you need to compare the values within two objects, you can use `assert.deepEqual()`. This method compares the values of each object using loose (`==`) equality.

The following code will not throw an error…

```js
assert.deepEqual(a, b);
```

…and you can confirm by manually comparing the `relation` and `age` properties of each object.

```js
a.relation == b.relation;
a.age == b.age;
```

[Arrays](https://www.codecademy.com/resources/docs/javascript/arrays) are also objects, so `deepEqual()` also compares their values with loose equality.

```js
const arr1 = [1, 2, 3];
const arr2 = [1, 2, 3];
const arr3 = [1, 2, '3'];

assert.deepEqual(arr1, arr2); // No error
assert.deepEqual(arr1, arr3); // No error
```

If you’d like to learn more about `deepEqual()`, the documentation is available [here](https://nodejs.org/api/assert.html#assert_assert_deepequal_actual_expected_message).

### Other assert methods
Node’s `assert` library includes more than the four [methods](https://www.codecademy.com/resources/docs/javascript/methods) covered so far. You can find them all in the [Node.js documentation](https://nodejs.org/api/assert.html).

Many of the methods can be implemented using other methods, like using `assert.ok(1 == 1)` to implement `assert.equal(1,1)`. Although this can be used for many types of tests, more descriptive [functions](https://www.codecademy.com/resources/docs/javascript/functions) like `assert.equal`, `assert.strictEqual`, and `assert.deepEqual` allow us to be more _expressive:_ the expected functionality of the implementation code is clear to anyone reading your tests.

---

Note as of July 2021: While `assert.notEqual()` may accomplish a similar result, the documentation currently recommends against using it, suggesting instead to use `assert.notStrictEqual()`.

### Review
- Check for loose (`==`) equality with `assert.equal()`
- Check for strict (`===`) equality with `assert.strictEqual()`
- Check the equality of two object’s values with `assert.deepEqual()`
- Make your tests expressive by using different `assert` [methods](https://www.codecademy.com/resources/docs/javascript/methods) found in the [Node.js documentation](https://nodejs.org/api/assert.html).
 

# Learn Test-Driven Development with Mocha

## Learn TDD With Mocha

### Getting Into The Red I
When we use the red, green, refactor cycle, we:

1. Write test code that fails
2. Write implementation code to make the test pass
3. Consider refactoring the code

Imagine you were trying to create a method named `.initials,` inside of an object named `Phrase`.

The desired behavior of `.initials()` is that it should return the first letter of each word in a phrase that is passed to it as an argument.

#### Write The Test
The first step to writing a test with Mocha is to use `describe` and `it` blocks to describe the desired behavior of your code. It’s very important for tests to thoroughly describe the desired behavior with natural language. This will create the most helpful error messages and make it easy for you to understand the behavior that your test failed in executing.

Before running our test, we would use an assert statement to compare the desired result of our method with the actual result.

```js
describe('Phrase', () => {
  describe('.initials', () => {
    it('returns the first letter of each word in a phrase.', () => {
      assert.strictEqual(Phrase.initials('Nelson Mandela'), 'NM');
    })
  })
})
```

#### The test fails (yea!)
The error message tells us that the error is related to the `Phrase.initials` code block. The `ReferenceError` tells us that the error is thrown because we don’t have a `Phrase` object.

### Red To Green I
The red error messages describe the failures of our implementation code, so we can specifically address each issue that is preventing our test from passing.

Following TDD, the next step would be writing the minimum possible implementation code to make our test pass.

### Refactor I
Once all your tests pass, you can confidently refactor your code — restructure and improve it without changing its external behavior. The confidence comes from knowing that our tests will catch us if we make a misstep.

When refactoring, it’s critical to test early and often — if our tests turn red, then we know that something went wrong while we were refactoring, and we can undo those changes.

A good place to start with refactoring is to restructure tests to reflect the four phases of a good test: _setup_, _exercise_, _verification_, _teardown_.

Let’s consider the test for our `Phrase.initials` method. We could rewrite the test with setup, exercise, and verification stages to make it more expressive and maintainable.

```js
describe('Phrase', () => {
  describe('.initials', () => {
    it('returns the first letter of each word in a phrase.', () => {
      // Setup
      const inputName = 'Nelson Mandela';
      const expectedInitials = 'NM';
      // Exercise
      const result = Phrase.initials(inputName);
      // Verification
      assert.strictEqual(result, expectedInitials);
    });
  });
});

```

### Getting into the Red II
Once you have a baseline test for your feature, you can start to write additional test cases that force you to write better implementation code.

Let’s write another test that pushes us to implement a `Phrase.initials()` method that returns the first letter of each word for “Nelson Mandela” and a different name.

To do this, we will add another `it` block to our code, and inside the callback function we will again follow the setup, exercise, verification phases for writing tests. This time we will write a test based on the circumstance that the string passed to `.initials()` has three names: `'Juan Manuel Santos'`.

```js
describe('Phrase', () => {
  describe('.initials', () => {
    
    . . .
    
    it('returns the initials of a name', () => {
      const nameInput = 'Juan Manuel Santos';
      const expectedInitials = 'JMS';

      const result = Phrase.initials(nameInput);

      assert.strictEqual(result, expectedInitials);
    });
  });
});
```

### Refactor II
Sometimes refactoring can take place in test and implementation code, either one, or neither.

### Edge Case
An edge case is a problem or situation that occurs only at an extreme (maximum or minimum) operating parameter — you can think of these as special cases that you need to account for.

Take our `Phrase.initials()` example from earlier. What happens if we pass `.initials()` a number instead of a string? We could write a test and then implementation code that responds to this behavior by raising an error message that instructs you to only use [strings](https://www.codecademy.com/resources/docs/javascript/strings).

```js
it('raises an error if the parameter passed in is not a string', () => {
  // Setup
  const nameInput = 14;   
  // Exercise
  const exercise = () => { Phrase.initials(nameInput) };
  // Verification
  assert.throws(exercise, /only use string/);        
})
```

After getting our intended error message we would write just enough implementation code to pass the test. Which in this case would be adding the following to `Phrase.initials()`:

```js
if (typeof inputName !== "string") {
  throw new Error("ERROR: only use string");
}
```

### Review
**At a high-level the process is:**

- Write The Test — Start with a test describing the functionality we’d like to see.
- Fail The Test — Write code in response to the test that fails.
- Pass The Test — The tests fail and communicate feedback to developers through error messages. It’s our responsibility to read those messages, then respond by writing the minimum amount of code to address those messages.
- Refactor Your Code — See below.

**The development process is guided by the red-green-refactor cycle.**

#### Red
Write a test that covers the functionality you would like to see implemented. You don’t have to know what your code looks like at this point, you just have to know what it will do.

Run the test. You should see it fail. Most test runners will output red for failure and green for success. While we say “failure” do not take this negatively. It’s a good sign! By seeing the test fail first, we know that once we make it pass, our code works.

#### Green
Read the error message from the failing test, and write as little code as possible to fix the current error message. By only writing enough code to see our test pass, we tend to write less code as a whole. Continue this process until the test passes.

This may involve writing intermediary features covering lower level functionality which require their own Red, Green, Refactor cycle. The **edge-case** was an example of this.

Do not focus on code quality at this point. Be shameless! We simply want to get our new test passing.

#### Refactor
Clean up your code, reducing any duplication you may have introduced. This includes your code as well as your tests.

Treat your test suite with as much respect as you would your live code, as it can quickly become difficult to maintain if not handled with care. You should feel confident enough in the tests you’ve written that you can make your changes without breaking anything.
 
