# Print to console

```java
System.out.println("Hello, World!");
```

```javascript
console.log("Hello, World!");
```

# Get the length of a string

```java
int lengthOfString = myString.length();
```

```javascript
const lengthOfString = myString.length;
```

# Get a character at a specific position in a string

```java
char charAtIndex7 = myString.charAt(7);
```

```javascript
const charAtIndex7 = myString[7];
```

# Create an array

```java
int[] arr1 = new int[5];
int[] arr2 = {1, 2, 3, 4, 5};
```

```javascript
const arr1 = [];
const arr2 = [1, 2, 3, "four", true];
```

# Add an element at the end of an array

```java
ArrayList<Integer> arr = new ArrayList<>();
arr.add(10);
```

```javascript
const arr = [];
arr.push(10);
```

# Get and remove the last element of an array

```java
int lastElement = arr.remove(arr.size() - 1);
```

```javascript
const lastElement = arr.pop();
```

# Add an element at the beginning of an array

```java
arr.add(0, 10);
```

```javascript
arr.unshift(10);
```

# Get and remove an element from the beginning of an array

```java
int removedElement = arr.remove(0);
```

```javascript
const removedElement = arr.shift();
```

# Create a dictionary-like data structure

```java
HashMap<String, Integer> ages = new HashMap<>();

ages.put("John", 30);
ages.put("Jane", 25);
ages.put("Bob", 35);
```

```javascript
let person = {
    name: "John",
    age: 30,
    city: "New York"
};
```

# Get a value 

```java
int johnsAge = ages.get("John");
```

```javascript
const age1 = person.age;
const age2 = person['age'];
```

# Delete a key-value pair

```java
ages.remove("Jane");
```

```javascript
delete person.age;
```

# Check if a key exists

```java
ages.containsKey("Jane")
```

```javascript
person.hasOwnProperty("age")
"age" in person
```

# Generate a random integer within a range

```java
Random random = new Random();
int min = 1;
int max = 100;
int randomInRange = random.nextInt(max - min + 1) + min;
```

```javascript
const min = 1;
const max = 100;
const randomInRange = Math.floor(Math.random() * (max - min + 1)) + min;
```

# Convert a string to an integer

```java
String numericString = "42";
int intValue = Integer.parseInt(numericString);
```

```javascript
const stringNumber = "42";
const integerNumber1 = parseInt(stringNumber);
// also:
const integerNumber2 = Number(stringNumber);
```

# Set default parameters for a function/method

```java
public class GreetExample {

    public static void greet() {
        greet("Guest", "Hello");
    }

    public static void greet(String name, String greeting) {
        System.out.println(greeting + ", " + name + "!");
    }

    public static void main(String[] args) {
        greet(); // Output: Hello, Guest!
        greet("John", "Hi"); // Output: Hi, John!
    }
}
```

```javascript
function greet(name = "Guest", greeting = "Hello") {
    console.log(`${greeting}, ${name}!`);
}

greet(); // Output: Hello, Guest!
greet("John", "Hi"); // Output: Hi, John!
```

# Take a variable number of arguments into a function/method

```java
public class HowManyExample {

    public static String howMany(Object... args) {
        return "You have passed " + args.length + " arguments.";
    }

    public static void main(String[] args) {
        System.out.println(howMany(0, 1, 2));
    }
}
```

```javascript
function howMany(...args) {
  return "You have passed " + args.length + " arguments.";
}

console.log(howMany(0, 1, 2));
```

# String interpolation

```java
String name = "John";
int age = 30;
String message = String.format("Hello, %s! You are %d years old.", name, age);
```

```javascript
const name = "John";
const age = 30;
const message = `Hello, ${name}! You are ${age} years old.`;
```

# Create objects from a class

```java
class SpaceShuttle {
    private String targetPlanet;

    public SpaceShuttle(String targetPlanet) {
        this.targetPlanet = targetPlanet;
    }

    public void takeOff() {
        System.out.println("To " + this.targetPlanet + "!");
    }
}

class Rocket {
    public void launch() {
        System.out.println("To the moon!");
    }
}

public class Main {
    public static void main(String[] args) {
        SpaceShuttle zeus = new SpaceShuttle("Jupiter");
        zeus.takeOff();

        Rocket atlas = new Rocket();
        atlas.launch();
    }
}
```

```javascript
class SpaceShuttle {
  constructor(targetPlanet) {
    this.targetPlanet = targetPlanet;
  }
  takeOff() {
    console.log("To " + this.targetPlanet + "!");
  }
}

class Rocket {
  launch() {
    console.log("To the moon!");
  }
}

const zeus = new SpaceShuttle('Jupiter');
zeus.takeOff();

const atlas = new Rocket();
atlas.launch();
```

# Use getters and setters

```java
public class Book {
    private String author;

    public Book(String author) {
        this.author = author;
    }

    public String getWriter() {
        return this.author;
    }

    public void setWriter(String updatedAuthor) {
        this.author = updatedAuthor;
    }

    public static void main(String[] args) {
        Book novel = new Book("anonymous");
        System.out.println(novel.getWriter()); 

        novel.setWriter("newAuthor");
        System.out.println(novel.getWriter()); 
    }
}
```

```javascript
class Book {
  constructor(author) {
    this._author = author;
  }
  
  get writer() {
    return this._author;
  }

  set writer(updatedAuthor) {
    this._author = updatedAuthor;
  }
}

const novel = new Book('anonymous');
console.log(novel.writer);

novel.writer = 'newAuthor';
console.log(novel.writer);
```

# Test if regex is present

```java
String testStr = "freeCodeCamp";
String testRegex = "Code";
boolean matchFound = testStr.matches(".*" + regex + ".*");
```

```javascript
let testStr = "freeCodeCamp";
let testRegex = /Code/;
let matchFound = testRegex.test(testStr);
```

# Extract matches with regex

```java
String testStr = "Repeat, Repeat, Repeat";
String ourRegex = "Repeat";

Pattern pattern = Pattern.compile(ourRegex);
Matcher matcher = pattern.matcher(testStr);

List<String> matches = new ArrayList<>();
while (matcher.find()) {
	matches.add(matcher.group());
}
```

```javascript
let testStr = "Repeat, Repeat, Repeat";
let ourRegex = /Repeat/;
let matches = testStr.match(ourRegex);
```

# Check type of a variable

```java
String str = "";
System.out.println(str.getClass().getSimpleName());
```

```javascript
console.log(typeof "");
```

# Remove any number of consecutive elements from anywhere in an array

```java
List<String> arr = new ArrayList<>(List.of("today", "was", "not", "so", "great"));
arr.subList(2, 4).clear();
```

```javascript
let arr = ['today', 'was', 'not', 'so', 'great'];
arr.splice(2, 2);
```

# Extract a portion of an array

```java
List<String> weatherConditions = new ArrayList<>(List.of("rain", "snow", "sleet", "hail", "clear"));
List<String> todaysWeather = weatherConditions.subList(1, 3);
```

```javascript
let weatherConditions = ['rain', 'snow', 'sleet', 'hail', 'clear'];
let todaysWeather = weatherConditions.slice(1, 3);
```

# Copy an array

```java
boolean[] thisArray = {true, true, false};
boolean[] thatArray = Arrays.copyOf(thisArray, thisArray.length);
```

```javascript
let thisArray = [true, true, false];
let thatArray = [...thisArray];
```

# Combine arrays

```java
List<String> thisArray = new ArrayList<>(Arrays.asList("sage", "rosemary", "parsley", "thyme"));
List<String> thatArray = new ArrayList<>(Arrays.asList("basil", "cilantro", "coriander"));
thatArray.addAll(2, thisArray);
```

```javascript
let thisArray = ['sage', 'rosemary', 'parsley', 'thyme'];
let thatArray = ['basil', 'cilantro', ...thisArray, 'coriander'];
```

# Check for the presence of an element in an array

```java
List<String> fruits = new ArrayList<>(Arrays.asList("apples", "pears", "oranges", "peaches", "pears"));

int indexDates = fruits.indexOf("dates");
int indexOranges = fruits.indexOf("oranges");
```

```javascript
let fruits = ['apples', 'pears', 'oranges', 'peaches', 'pears'];

let indexDates = fruits.indexOf('dates');
let indexOranges = fruits.indexOf('oranges');
```

# Get the keys

```java
Set<String> keys = users.keySet();
```

```javascript
const keys = Object.keys(users);
```

# Iterate through keys

```java
for (String user : users.keySet()) {
    System.out.println(user);
}
```

```javascript
for (let user in users) {
  console.log(user);
}
```

# Examples

- Return an array consisting of the largest number from each provided sub-array. For simplicity, the provided array will contain exactly 4 sub-arrays.

```java
public class Examples {

    public static List<Integer> largestOfFour(List<List<Integer>> arr) {
        List<Integer> newArr = new ArrayList<>();
        for (List<Integer> row : arr) {
            Integer largest = row.get(0);
            for (Integer element : row) {
                if (element > largest) {
                    largest = element;
                }
            }
            newArr.add(largest);
        }
        return newArr;
    }

    public static void main(String[] args) {
        List<List<Integer>> arr = Arrays.asList(
                Arrays.asList(4, 5, 1, 3),
                Arrays.asList(13, 27, 18, 26),
                Arrays.asList(32, 35, 37, 39),
                Arrays.asList(1000, 1001, 857, 1)
        );

        List<Integer> largestInts = largestOfFour(arr);
        System.out.println(largestInts);
    }
}
```

```javascript
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

- Truncate a string (first argument) if it is longer than the given maximum string length (second argument). Return the truncated string with a ... ending.

```java
public class Examples {

    public static String truncateString(String str, int num) {
        if (num >= str.length()) {
            return str;
        } else {
            return str.substring(0, num) + "...";
        }
    }

    public static void main(String[] args) {
        String truncatedString = truncateString("A-tisket a-tasket A green and yellow basket", "A-tisket a-tasket A green and yellow basket".length() + 2);
        System.out.println(truncatedString);
    }
}
```

```javascript
function truncateString(str, num) {
  if (num >= str.length) {
    return str;
  } else {
    return str.slice(0, num) + "...";
  }
}

truncateString("A-tisket a-tasket A green and yellow basket", "A-tisket a-tasket A green and yellow basket".length + 2);
```

- Return true if the string in the first element of the array contains all of the letters of the string in the second element of the array.

```java
public class Examples {

    public static boolean mutation(String[] arr) {
        String target = arr[0].toLowerCase();
        String test = arr[1].toLowerCase();
        for (int i = 0; i < test.length(); i++) {
            if (target.indexOf(test.charAt(i)) == -1) {
                return false;
            }
        }
        return true;
    }

    public static void main(String[] args) {
        System.out.println(mutation(new String[] {"Alien", "line"}));
    }
}
```

```javascript
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

- Write a function that splits an array (first argument) into groups the length of size (second argument) and returns them as a two-dimensional array.

```java
public class Examples {

    public static List<List<String>> chunkArrayInGroups(List<String> arr, int size) {
        List<List<String>> newArr = new ArrayList<>();
        for (int i = 0; i < arr.size(); i += size) {
            newArr.add(arr.subList(i, i + size));
        }
        return newArr;
    }

    public static void main(String[] args) {
        List<String> arr = new ArrayList<>(Arrays.asList("a", "b", "c", "d"));
        System.out.println(chunkArrayInGroups(arr, 2));
    }
}
```

```javascript
function chunkArrayInGroups(arr, size) {
  let newArr = [];

  for (let i = 0; i < arr.length; i += size) {
    newArr.push(arr.slice(i, i + size));
  }

  return newArr;
}

chunkArrayInGroups(["a", "b", "c", "d"], 2);
```

# Create a method

```java
public class Duck {

    private String name = "Aflac";
    private int numLegs = 2;

    public String sayName() {
        return "The name of this duck is " + this.name + ".";
    }

    public static void main(String[] args) {
        Duck duck = new Duck();
        System.out.println(duck.sayName());
    }
}
```

```javascript
let duck = {
  name: "Aflac",
  numLegs: 2,
  sayName: function() {return "The name of this duck is " + duck.name + ".";}
};

duck.sayName();
```

# Achieve inheritance

```java
public class Animal {
    public void eat() {
        System.out.println("nom nom nom");
    }
}

public class Bird extends Animal {
	public void fly() {
        System.out.println("I'm flying!");
    }
}

public class Main {
    public static void main(String[] args) {
        Bird duck = new Bird();
        duck.eat(); 
        duck.fly();
    }
}
```

```javascript
function Animal() { }
Animal.prototype.eat = function() {
  console.log("nom nom nom");
};

function Bird() { }
Bird.prototype = Object.create(Animal.prototype);
Bird.prototype.fly = function() {
  console.log("I'm flying!");
};

let duck = new Bird();
duck.eat();
duck.fly();
```

# Override inherited methods

```java
public class Animal {
    public String eat() {
        return "nom nom nom";
    }
}

public class Bird extends Animal {
    @Override
    public String eat() {
        return "peck peck peck";
    }
}
```

```javascript
function Animal() { }
Animal.prototype.eat = function() {
  return "nom nom nom";
};

function Bird() { }
Bird.prototype = Object.create(Animal.prototype);
Bird.prototype.eat = function() {
  return "peck peck peck";
};
```

# Achieve encapsulation

```java
public class Bird {
    private int hatchedEgg = 10;

    public int getHatchedEggCount() {
        return hatchedEgg;
    }
}
```

```javascript
function Bird() {
  let hatchedEgg = 10;

  this.getHatchedEggCount = function() { 
    return hatchedEgg;
  };
}
```

# Produce a new array transforming each element given a function

```java
List<String> words = Arrays.asList("apple", "banana", "cherry");
List<String> uppercaseWords = words.stream()
    .map(String::toUpperCase)
    .collect(Collectors.toList()); // [APPLE, BANANA, CHERRY]
```

```javascript
const words = ["apple", "banana", "cherry"];
const uppercaseWords = words.map(word => word.toUpperCase());
```

# Filter elements of an array based on a specified condition

```java
List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5, 6, 7, 8, 9, 10);
List<Integer> evenNumbers = numbers.stream()
    .filter(n -> n % 2 == 0)
    .collect(Collectors.toList()); // [2, 4, 6, 8, 10]
```

```javascript
const numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];
const evenNumbers = numbers.filter(n => n % 2 == 0);
```

# Reduce an array to a single value

```java
int[] numbers = {1, 2, 3, 4, 5};
int sum = Arrays.stream(numbers)
    .reduce(0, (accumulator, currentValue) -> accumulator + currentValue);
```

```javascript
const numbers = [1, 2, 3, 4, 5];
const sum = numbers.reduce((accumulator, currentValue) => accumulator + currentValue, 0);
```

# Sort an array

```java
int[] arr = {1, 5, 2, 3, 4};
Arrays.sort(arr);
```

```java
Integer[] arr = {1, 5, 2, 3, 4};
Arrays.sort(arr, Comparator.reverseOrder());
```

```javascript
function ascendingOrder(arr) {
  return arr.sort(function(a, b) {
    return a - b;
  });
}

ascendingOrder([1, 5, 2, 3, 4]);
```

```javascript
function descendingOrder(arr) {
  return arr.sort(function(a, b) {
    return b - a;
  });
}

descendingOrder([1, 5, 2, 3, 4]);
```

# Split a string into an array of substrings

```java
String str = "Hello World";
String[] bySpace = str.split(" ");
```

```java
String str = "How9are7you2today";
String[] byDigits = str.split("[0-9]");
```

```javascript
const str = "Hello World";
const bySpace = str.split(" ");
```

```javascript
const str = "How9are7you2today";
const byDigits = str.split(/\d/);
```

# Combine an array into a string

```java
String[] arr = {"Hello", "World"};
String str = String.join(" ", arr);
```

```javascript
const arr = ["Hello", "World"];
const str = arr.join(" "); // Hello World
```

# Check that every element in an array meets a criteria

```java
int[] numbers = {1, 5, 8, 0, 10, 11};
boolean result = Arrays.stream(numbers).allMatch(currentValue -> currentValue < 10);
```

```javascript
const numbers = [1, 5, 8, 0, 10, 11];
let result = numbers.every(currentValue => currentValue < 10);
```

# Check that any elements in an array meet a criteria

```java
int[] numbers = {10, 50, 8, 220, 110, 11};
boolean result = Arrays.stream(numbers).anyMatch(currentValue -> currentValue < 10);
```

```javascript
const numbers = [10, 50, 8, 220, 110, 11];
let result = numbers.some(currentValue => currentValue < 10);
```

# Compare two strings

```java
String string1 = "hello";
String string2 = "world";

if (string1.equals(string2)) {
    System.out.println("Strings are equal.");
} else {
    System.out.println("Strings are not equal.");
}
```

```javascript
const string1 = "hello";
const string2 = "world";

if (string1 === string2) {
    console.log("Strings are equal.");
} else {
    console.log("Strings are not equal.");
}
```

# Declare a constant variable

```java
final int yearBorn = 1968;
```

```javascript
const yearBorn = 1968;
```


