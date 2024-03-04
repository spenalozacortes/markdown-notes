**An algorithm is a series of step-by-step instructions that describe how to do something.**

# Return Largest Numbers in Arrays
Return an array consisting of the largest number from each provided sub-array. For simplicity, the provided array will contain exactly 4 sub-arrays.
```js
function largestOfFour(arr) {
  let newArr = [];

  for (let i = 0; i < arr.length; i++) {
    let largest = arr[i][0];
    for (let j = 0; j < arr[i].length; j++) {
      if (arr[i][j] > largest) {
        largest = arr[i][j];
      }
    }
    newArr.push(largest);
  }
  return newArr;
}

largestOfFour([[4, 5, 1, 3], [13, 27, 18, 26], [32, 35, 37, 39], [1000, 1001, 857, 1]]);
```

# Truncate a String
Truncate a string (first argument) if it is longer than the given maximum string length (second argument). Return the truncated string with a ... ending.
```js
function truncateString(str, num) {
  if (num >= str.length) {
    return str;
  } else {
    return str.slice(0, num) + "...";
  }
}

truncateString("A-tisket a-tasket A green and yellow basket", "A-tisket a-tasket A green and yellow basket".length + 2);
```

# Slice and Splice
You are given two arrays and an index.

Copy each element of the first array into the second array, in order.

Begin inserting elements at index n of the second array.

Return the resulting array. The input arrays should remain the same after the function runs.
```js
function frankenSplice(arr1, arr2, n) {
  let arr2copy = [...arr2];
  
  for (let i = arr1.length - 1; i >= 0; i--) {
    arr2copy.splice(n, 0, arr1[i]);
  }

  return arr2copy;
}

frankenSplice([1, 2, 3], [4, 5, 6], 1);
```
Title Case a Sentence*
Where do I Belong*

# Mutations
Return true if the string in the first element of the array contains all of the letters of the string in the second element of the array.

For example, ```["hello", "Hello"]```, should return true because all of the letters in the second string are present in the first, ignoring case.

The arguments ```["hello", "hey"]``` should return false because the string hello does not contain a y.

Lastly, ```["Alien", "line"]```, should return true because all of the letters in line are present in Alien.
```js
function mutation(arr) {
  const test = arr[1].toLowerCase();
  const target = arr[0].toLowerCase();

  for (let i = 0; i < test.length; i++) {
    if (target.indexOf(test[i]) == -1) {
      return false;
    }
  }
  return true;
}

mutation(["hello", "hey"]);
```
# Chunky Monkey
Write a function that splits an array (first argument) into groups the length of size (second argument) and returns them as a two-dimensional array.
```js
function chunkArrayInGroups(arr, size) {
  let newArr = [];

  for (let i = 0; i < arr.length; i += size) {
    newArr.push(arr.slice(i, i + size));
  }

  return newArr;
}

chunkArrayInGroups(["a", "b", "c", "d"], 2);
```









