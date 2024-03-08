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

# Add an element at the end of an array(list)

```java
ArrayList<Integer> arr = new ArrayList<>();
arr.add(10);
```

```javascript
const arr = [];
arr.push(10);
```

# Get and remove the last element of an array(list)

```java
int lastElement = arr.remove(arr.size() - 1);
```

```javascript
const lastElement = arr.pop();
```

# Add an element at the beginning of an array(list)

```java
arr.add(0, 10);
```

```javascript
arr.unshift(10);
```

# Get and remove an element from the beginning of an array(list)

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

# Remove any number of consecutive elements from anywhere in an array(list)

```java
List<String> arr = new ArrayList<>(List.of("today", "was", "not", "so", "great"));
arr.subList(2, 4).clear();
```

```javascript
let arr = ['today', 'was', 'not', 'so', 'great'];
arr.splice(2, 2);
```

