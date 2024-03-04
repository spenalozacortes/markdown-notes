### Remove Items from an Array with pop() and shift()
The key difference between pop() and shift() and their cousins push() and unshift(), is that neither method takes parameters, and each only allows an array to be modified by a single element at a time.
```js
let greetings = ['whats up?', 'hello', 'see ya!'];

greetings.pop();
```
greetings would have the value ```['whats up?', 'hello']```.
```js
greetings.shift();
```
greetings would have the value ```['hello']```.

We can also return the value of the removed element with either method like this:
```js
let popped = greetings.pop();
```
greetings would have the value ```[]```, and popped would have the value hello.

### Remove Items Using splice()
What if we want to remove an element from somewhere in the middle? Or remove more than one element at once? splice() allows us to do just that: remove any number of consecutive elements from anywhere in an array.

splice() can take up to 3 parameters, but for now, we'll focus on just the first 2. The first two parameters of splice() are integers which represent indexes, or positions, of items in the array that splice() is being called upon. 

splice()'s first parameter represents the index on the array from which to begin removing elements, while the second parameter indicates the number of elements to delete.
```js
let array = ['today', 'was', 'not', 'so', 'great'];

array.splice(2, 2);
```
Here we remove 2 elements, beginning with the third element (at index 2). array would have the value ```['today', 'was', 'great']```.

splice() not only modifies the array it's being called on, but it also returns a new array containing the value of the removed elements:
```js
let array = ['I', 'am', 'feeling', 'really', 'happy'];

let newArray = array.splice(3, 2);
```
newArray has the value ```['really', 'happy']```.

### Add Items Using splice()
Remember in the last challenge we mentioned that splice() can take up to three parameters? Well, you can use the third parameter, comprised of one or more element(s), to add to the array. This can be incredibly useful for quickly switching out an element, or a set of elements, for another.
```js
const numbers = [10, 11, 12, 12, 15];
const startIndex = 3;
const amountToDelete = 1;

numbers.splice(startIndex, amountToDelete, 13, 14);
console.log(numbers);
```
The second occurrence of 12 is removed, and we add 13 and 14 at the same index. The numbers array would now be ```[ 10, 11, 12, 13, 14, 15 ]```.

Note that there can be any number of elements (separated by commas) following amountToDelete, each of which gets inserted.

### Copy Array Items Using slice()
The next method we will cover is slice(). Rather than modifying an array, slice() copies or extracts a given number of elements to a new array, leaving the array it is called upon untouched. slice() takes only 2 parameters — the first is the index at which to begin extraction, and the second is the index at which to stop extraction (extraction will occur up to, but not including the element at this index). Consider this:
```js
let weatherConditions = ['rain', 'snow', 'sleet', 'hail', 'clear'];

let todaysWeather = weatherConditions.slice(1, 3);
```
todaysWeather would have the value ```['snow', 'sleet']```, while weatherConditions would still have ```['rain', 'snow', 'sleet', 'hail', 'clear']```.

### Copy an Array with the Spread Operator
While slice() allows us to be selective about what elements of an array to copy, among several other useful tasks, ES6's new spread operator allows us to easily copy all of an array's elements, in order, with a simple and highly readable syntax. The spread syntax simply looks like this: ...

In practice, we can use the spread operator to copy an array like so:
```js
let thisArray = [true, true, undefined, false, null];
let thatArray = [...thisArray];
```
thatArray equals ```[true, true, undefined, false, null]```. thisArray remains unchanged and thatArray contains the same elements as thisArray.

### Combine Arrays with the Spread Operator
Another huge advantage of the spread operator is the ability to combine arrays, or to insert all the elements of one array into another, at any index. With more traditional syntaxes, we can concatenate arrays, but this only allows us to combine arrays at the end of one, and at the start of another. Spread syntax makes the following operation extremely simple:
```js
let thisArray = ['sage', 'rosemary', 'parsley', 'thyme'];

let thatArray = ['basil', 'cilantro', ...thisArray, 'coriander'];
```
thatArray would have the value ```['basil', 'cilantro', 'sage', 'rosemary', 'parsley', 'thyme', 'coriander']```.

Using spread syntax, we have just achieved an operation that would have been more complex and more verbose had we used traditional methods.

### Check For The Presence of an Element With indexOf()
Since arrays can be changed, or mutated, at any time, there's no guarantee about where a particular piece of data will be on a given array, or if that element even still exists. Luckily, JavaScript provides us with another built-in method, indexOf(), that allows us to quickly and easily check for the presence of an element on an array. indexOf() takes an element as a parameter, and when called, it returns the position, or index, of that element, or -1 if the element does not exist on the array.
```js
let fruits = ['apples', 'pears', 'oranges', 'peaches', 'pears'];

fruits.indexOf('dates');
fruits.indexOf('oranges');
fruits.indexOf('pears');
```
indexOf('dates') returns -1, indexOf('oranges') returns 2, and indexOf('pears') returns 1 (the first index at which each element exists).

### Check if an Object has a Property
Now we can add, modify, and remove keys from objects. But what if we just wanted to know if an object has a specific property? JavaScript provides us with two different ways to do this. One uses the hasOwnProperty() method and the other uses the in keyword. If we have an object users with a property of Alan, we could check for its presence in either of the following ways:
```js
users.hasOwnProperty('Alan');
'Alan' in users;
```
Both of these would return true.

### Iterate Through the Keys of an Object with a for...in Statement
Sometimes you may need to iterate through all the keys within an object. This requires a specific syntax in JavaScript called a for...in statement. For our users object, this could look like:
```js
for (let user in users) {
  console.log(user);
}
```
This would log Alan, Jeff, and Sarah - each value on its own line.

In this statement, we defined a variable user, and as you can see, this variable was reset during each iteration to each of the object's keys as the statement looped through the object, resulting in each user's name being printed to the console.

**NOTE**: Objects do not maintain an ordering to stored keys like arrays do; thus a key's position on an object, or the relative order in which it appears, is irrelevant when referencing or accessing that key.

### Generate an Array of All Object Keys with Object.keys()
We can also generate an array which contains all the keys stored in an object with the Object.keys() method. This method takes an object as the argument and returns an array of strings representing each property in the object. Again, there will be no specific order to the entries in the array.



