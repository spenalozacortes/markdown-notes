#java 
#aqui 
# Getting Started with Data Structures

## Welcome to Interview Prep in Java

### Why Data Structures?

#### What even are data structures?
At the backbone of every program or piece of software are two entities: data and algorithms. Algorithms transform data into something a program can effectively use. Therefore, it is important to understand how to structure data so algorithms can maintain, utilize, and iterate through data quickly.

Data structures are the way we are able to store and retrieve data.

#### How are data structures used?
Data structures handle four main functions for us:

- Inputting information
- Processing information
- Maintaining information
- Retrieving information

Inputting is largely concerned with how the data is received. What kind of information can be included? Will the new data be added to the beginning, end, or somewhere in the middle of the existing data? Does an existing point of data need to be updated or destroyed?

Processing gets at the way that data is manipulated in the data structure. This can occur concurrently or as a result of other processes that data structures handle. How does existing data that has been stored need to change to accommodate new, updated, or removed data?

Maintaining is focused on how the data is organized within the structure. Which relationships need to be maintained between pieces of data? How much memory must the system reserve (_allocate_) to accommodate the data?

Retrieving is devoted to finding and returning the data that is stored in the structure. How can we access that information again? What steps does the data structure need to take to get the information back to us?

Different types and use cases for data will be better suited to different manners of inputting, processing, storing, and retrieving.

#### Choosing the best data structure
Choosing the wrong data structure can result in slow or unresponsive code (and mess up your program!), so it’s important to consider a few factors as you make your decision:

1. What is the intended purpose for the data? Do any data structures have built-in functionality that is ideally suited for this purpose? Do you want to search, sort, or iterate data in a way in which certain data structures would be better suited than others?
2. Do you want or need control over how memory is set aside to store your data? Data structures that use _static memory allocation_ (e.g., stacks or arrays) will manage memory for you and assume a fixed amount of memory upon instantiation with a cap on how much data may be added. Data structures that utilize _dynamic memory allocation_ (e.g., heaps or linked lists) allow you to allocate and reallocate memory within the life of the program.
3. How long will it take different data structures to accomplish various tasks relative to other data structures? Technically, two data structures may both be able to accomplish the same task for you, but one may be quite a bit faster.

## Java Review

### Scope in Java

#### Intro to Scope
In Java, _scope_ defines where a certain variable or method is accessible in a program. Variables can be defined as having one of three types of scope:

1. **Class level scope** (instance variables): any variable declared within a class is accessible by all methods in that class. Depending on its _access modifier_ (ie. `public` or `private`), it can sometimes be accessed outside the class.

```java
public class Car {
    public String color;
    private int speed;

    public Car(String color, int speed) {
        // Variables color and speed accessible here
    }

    public void drive(boolean fourWheel) {
        // Variables color and speed accessible here
    }
}

public class BuyCar {
    public static void main(String[]args) {
        Car carObject = new Car("blue", 70);
        // Can access the public variable, color, in this class
        String carColor = carObject.color;
        // Can’t access the private variable, speed, in this class
        // int carSpeed = carObject.speed -- This results in an error, can’t access speed here
    }
}
```

2. **Method level scope** (local variables): any variable declared within a method, arguments included, is NOT accessible outside that method.

```java
public class Car {
    public String color;
    private int speed;

    public void drive(boolean fourWheel) {
        String tires = "wide";
        // fourWheel and tires are only accessible here
        // fourWheel and tires are destroyed after drive() finishes
    }

    public void paint(String newColor, String oldColor) {
        // newColor and oldColor are only accessible here
        // newColor and oldColor are destroyed after paint() finishes
    }
}

public class PaintCar {
    // The only variable from Car accessible in this class is color
    // None of the variables declared in Car methods are accessible in this class
}
```

3. **Block scope** (loop variables): any variable declared in a `for` loop condition is not accessible after the loop, unless you defined it beforehand.

```java
public class Car {
    public void changeTires() {
        int numTires = 4;
        int changedTires = 0;
        for (i = 0; i < numTires; i++) {
            changedTires += 1;
        }
        // numTires and changedTires are accessible here, i is not
    }
}
```

#### Access Modifiers
In Java, there are four _access modifiers_ that restrict the accessibility of the method or variable to which the modifier is applied. They are only used within classes, not within methods.

- `private`: The **most** restrictive modifier. It limits access to methods and variables to the class in which they are declared. `private` is chosen when there is no need to use certain methods or variables outside the class.
- `default`: Allows access only from within the current package. If there is no specified access modifier, the method or variable will take on this one.
- `protected`: Allows access to a method or variable only from within the current package, unless it is accessed through a child class outside of the package.
- `public`: The **least** restrictive modifier. It allows access to a class, method or variable not only from within the class in which it is declared, but outside as well.

The `.bubbleUp()` method is `private` because “bubbling up”, or adjusting a heap after adding an element, is an internal process, not something that needs to be performed outside the `MinHeap` class. `.add()` on the other hand is a basic min-heap function so should be made `public`.

```java
public class MinHeap {
    public ArrayList<Integer> heap;
    public int size;

    public MinHeap() {
        // body of constructor
    }
    public void add(int value) {
        heap.add(value);
        size++;
        bubbleUp();
    }
    private void bubbleUp() {
        // body of bubbleUp() method
    }
}

public class TrackAges {
    public static void main(String[]args) {
        MinHeap ages = new MinHeap();
        // Can call public MinHeap add() method here
        ages.add(42);
        ages.add(15);
        ages.add(27);
        // Can’t call private MinHeap bubbleUp() method here
        // Don’t need to because add() calls bubbleUp()!    
    }
}
```

#### Static
`static` is a keyword that can be added after the access modifier of a method or variable. It indicates that the declared entity is the same across all instances of that class and that it can be accessed even before an object of that class is created. `static` methods and variables are initialized only once upon execution and are shared by all instances of the class. You may have noticed that the `.main()` method of a class is always declared as `static`; this is because this method is the starting point of the program. The compiler needs to be able to call the `.main()` method before the creation of an instance of that class, so it’s declared `static`.

#### Method Overriding and Method Overloading
**Method overriding** is a feature in Java that allows a subclass to have a method with the same name and parameters as one declared in its parent class. This is handy because it allows a subclass to implement a specific behavior for that method. The version of the method used is determined by the object that is used to call it.

**Method overloading** is similar to overriding in that it involves methods with the same name. However with overloading, a single Java class can have multiple methods with the same name if they have **different** parameter lists. Overloaded methods are distinguished by their number and type of parameters.

**Constructor overloading** is a type of method overloading in which there are multiple constructors in a class. This gives the option to instantiate an object with different sets of arguments.

#### Instance Variables
_Instance variables_, also called _instance fields_, are data associated with a class object. They make up the state that each instance will possess.

```java
public class Car {
    public String color;
    public int speed;

    public Car(String carColor, int carSpeed) {
        // Instantiate instance variables in constructor
        color = carColor;
        speed = carSpeed;
    }
    public static void main(String[]args) {
        Car carObject = new Car("red", 50);
    }
}
```

`this` is used within any class method or constructor to reference the **current** object. You can reference any instance variable of a class, from within the class, using `this`. It cannot be used in a `static` context. Using `this` easily clarifies which variables are being referenced.

```java
public class Car {
    public String color;
    public int speed;

    public Car(String color, int speed) {
        // Use keyword this to instantiate variables
        this.color = color;
        this.speed = speed;
    }
}
```

Here are two other frequent uses of `this`:

1. Call a current class method with `this.`

```java
public class Car {
    public String color;
    public int speed;
    
    public Car(String color, int speed) {
        this.color = color;
        this.speed = speed;
        // Use keyword this to call class method, race()
        this.race(speed);
    }

    public void race(int speed) {
        System.out.println("Raced at " + speed + " mph");
    }
}
```

2. Call a current class constructor using `this()` (constructor overloading)

```java
public class Car {
    public String color;
    public int speed;
    public static String defaultColor = "black";
    public static int defaultSpeed = 30;

    public Car() {
        this(defaultColor, defaultSpeed);
    }

    public Car(String color, int speed) {
        this.color = color;
        this.speed = speed;
    }
}
```

`this()` must be the first line in the constructor since it is creating the class instance. The variables `defaultColor` and `defaultSpeed` are declared `static` because we want them to have the same values across all instances of the `Car` class. This allows us to reference them in our call to the second constructor using `this()`. These `static` variables belong to the `Car` class, not its instances.

You can also send `this` in as an argument to a class method or return `this`, the current class instance, in a method. These are [less common uses](https://www.javatpoint.com/this-keyword) of `this`. When you start using `this`, you may run into a message that says “`this` cannot be referenced from a static context”. This likely means you tried to use `this` in your `.main()` method or another `static` method. As with variables, a `static` method belongs to the class, not its instances. Therefore it can only access `static` variables and call `static` methods. However, if an instance is created within a `static` method, that instance’s non-static variables and methods can be called using `theInstanceName.variable` or `theInstanceName.method()`.

```java
public class Car {
    public String color;
    public int speed;
    public static String defaultColor = "black";
    public static int defaultSpeed = 30;

    public Car() {
        this(defaultColor, defaultSpeed);
    }

    public Car(String color, int speed) {
        this.color = color;
        this.speed = speed;
    }
    
    public static void main(String[]args) {
        Car carObject = new Car();
        String staticColor = defaultColor; // static variable directly accessible from static context
        String instanceColor = carObject.color; // non-static variable accessible using instance, carObject
    }
}
```

### Additional Important Java Topics

#### Casting
**Type casting** is the process of converting a value of one primitive data type to another primitive data type. Data types are classified as “lower” if they hold less data and “higher” if they hold more data.

```
Lowest to highest primitive data types: Byte-->Short-->Int-->Long-->Float-->Double
```

**Narrowing type casting (explicit)**: Manually convert a higher data type to a lower one ie. `double` to `int`. There is a loss in data so the conversion is not automatic.

```java
public class Main {
    public static void main(String[]args) {
        // double to int
        double doubleNum = 19.97;
        System.out.println("The double value: " + doubleNum);
        // Need explicit casting because the double, doubleNum, cannot automatically fit into the int, intNum
        int intNum = (int) doubleNum;
        System.out.println("The int value: " + intNum);
    }
}
```

```
The double value: 19.97
The int value: 19
```

**Widening type casting (implicit)**: Java automatically converts a lower data type to a higher one ie. `int` to `double`. There is no loss in data.

```java
public class Main {
    public static void main(String[]args) {
        // int to double
        int intNum = 19;
        System.out.println("The int value: " + intNum);
        // No need for explicit casting because the int, intNum, can automatically fit into the double, doubleNum
        double doubleNum = intNum;
        System.out.println("The double value: " + doubleNum);
    }
}
```

```
The int value: 19
The double value: 19.0
```

**Other types of casting**
Casting can also be performed on variables that are not a primitive type such as `String` or `Object`. An important thing to remember with this type of casting is that every class in Java is implicitly a subclass of the `Object` class. We can do this given the `Car` class, which is descended from `Object`:

```java
Object o = new Car();
```

A `Car` is an `Object` but an `Object` is not necessarily always a `Car`. This is an example of **implicit** casting. Say we wrote the line:

```java
Car c = o;
```

This would cause a compile-time error since the compiler does not know that `o` is an instance of `Car` since it is stored above as an `Object`. We need **explicit** casting to remedy this:

```java
Car c = (Car) o;
```

A `String` that holds an integer value can be converted to an `int` using the `Integer` class method `.parseInt()`:

```java
public class Main {
    public static void main(String[]args) {
        // String to int
        String s = "12";
        System.out.println("The string value: " + s);
        int intNum = Integer.parseInt(s);
        System.out.println("The int value: " + intNum);
    }
}
```

```
The string value: 12
The int value: 12
```

An `int` value can be converted to a `String` using the `String` class method `.valueOf()`:

```java
public class Main {
    public static void main(String[]args) {
        // int to string
        int intNum = 12;
        System.out.println("The int value: " + intNum);
        String s = String.valueOf(intNum);
        System.out.println("The String value: " + s);  
    }
}
```

```
The int value: 12
The string value: 12
```

#### Dictionaries
In Java, a _Dictionary_ is an abstract class that stores key-value pairs. Given a key, you can retrieve the value associated with that key. Dictionaries are instantiated with one data type for the keys and one for the values, both of which can be any data type. Every key is associated with at most one value.

`Dictionary` is the abstract parent class of `Hashtable`, a data structure that stores key-value pairs.

`Hashtable` is a data structure that stores key-value pairs in a hashtable, very similar to `HashMap`. One difference is that `Hashtable` does not allow any `null` key or value. In a `Hashtable`, each key is hashed (using a hash function) to get a hash code, which is then used as the index at which the corresponding value is stored in the hashtable.

Here, the keys are of data type `String`, and values are of data type `Integer`:

```java
Dictionary<String, Integer> dict = new Hashtable<>();
```

You can see how key-value pairs are stored in the `Hashtable`:

```java
public class DictionaryCreation {
    public static void main(String[]args) {
        Dictionary<Integer,String> dict = new Hashtable<>();
        // Add key-value pairs to dict
        dict.put(1, "hello");
        dict.put(5, "goodbye");
        // Access the values using the keys
        System.out.println("Value at key 1: " + dict.get(1));
        System.out.println("Value at key 5: " + dict.get(5));
    }
}
```

```
Value at key 1: hello
Value at key 5: goodbye
```

An _interface_ is a collection of abstract methods which lay out the required behavior of any class that implements it. Recently, a `Map` interface was created; it maps keys to values in a similar manner to `Dictionary`. This more robust interface was created for data structures such as `HashMap` and `Hashtable` to implement. It can only be used with a class that implements its interface.

```java
Map<String, Integer> m1 = new Hashtable<>();
Map<String, Integer> m2 = new HashMap<>();
```

Because `Hashtable` is the only subclass of `Dictionary` and `Hashtable` implements `Map`, the `Dictionary` class has now become somewhat obsolete in the wake of the more versatile and applicable `Map` interface.

## Nodes

### Nodes: Conceptual

#### Nodes Introduction
Nodes are the fundamental building blocks of many computer science [data structures](https://www.codecademy.com/resources/docs/general/data-structures). They form the basis for linked lists, stacks, queues, trees, and more.

An individual node contains data and links to other nodes. Each data structure adds additional constraints or behavior to these features to create the desired structure.

![[Pasted image 20240304113922.png]]

#### Nodes Detail
The data contained within a node can be a variety of types, depending on the language you are using. In the previous example, it was an integer (the number `5`), but it could be a [string](https://www.codecademy.com/resources/docs/general/data-types/string) (`"five"`), decimal (`5.1`), an [array](https://www.codecademy.com/resources/docs/general/data-structures/array) (`[5,3,4]`) or nothing (`null`).

The link or links within the node are sometimes referred to as _pointers_. This is because they “point” to another node.

Typically, [data structures](https://www.codecademy.com/resources/docs/general/data-structures) implement nodes with one or more links. If these links are `null`, it denotes that you have reached the end of the particular node or link path you were previously following.

![[Pasted image 20240304114132.png]]

#### Node Linking
Often, due to the data structure, nodes may only be linked to from a single other node. This makes it very important to consider how you implement modifying or removing nodes from a data structure.

If you inadvertently remove the single link to a node, that node’s data and any linked nodes could be “lost” to your application. When this happens to a node, it is called an _orphaned_ node.

#### Nodes Review
Nodes:

- Contain data, which can be a variety of data types
- Contain links to other nodes. If a node has no links, or they are all `null`, you have reached the end of the path you were following.
- Can be orphaned if there are no existing links to them

### Nodes: Java

#### Constructor and Instance Variables
We will create a basic node class that contains data and a link to the next node. Our node’s data will be specified as a [`String`](https://www.codecademy.com/resources/docs/general/data-types/string), but the same class could easily be changed to hold any other data type. Remember that a node’s link to the next node is `null` when there are no more nodes to traverse.

```java
public class Node {
	public String data;
	public Node next;

	public Node(String data) {
		this.data = data;
		this.next = null;
	}

	public static void main(String[] args) {
		Node firstNode = new Node("I am a Node!");
	    System.out.println(firstNode.data);
	    System.out.println(firstNode.next);
	}
}
```

#### Setting the Next Node
Currently, when a `Node` is created, its `next` `Node` is set to `null`. However, we want to allow the `next` property to be updated so a sequence of nodes can be traversed and used in more complex [data structures](https://www.codecademy.com/resources/docs/general/data-structures). For this, we will create a setter [method](https://www.codecademy.com/resources/docs/general/method) to modify the `this.next` property.

```java
public class Node {

  public String data;
  public Node next;	

  public Node(String data) {
    this.data = data;
    this.next = null;
  }

  public void setNextNode(Node node) {
    this.next = node;
  }

  public static void main(String[] args) {
    Node firstNode = new Node("I am a Node!");
    Node secondNode = new Node("I am the second Node!");

    firstNode.setNextNode(secondNode);

    System.out.println(firstNode.next.data);
  }
}
```

#### Getting the Next Node
While we could continue accessing the `next` node property directly it’s safer to have important variables only accessible through methods.

```java
public class Node {

  public String data;
  private Node next;	

  public Node(String data) {
    this.data = data;
    this.next = null;
  }

  public void setNextNode(Node node) {
    this.next = node;
  }

  public Node getNextNode() {
    return this.next;
  }

  public static void main(String[] args) {
    Node firstNode = new Node("I am the first Node!");
    Node secondNode = new Node("I am the second Node!");
    firstNode.setNextNode(secondNode);

    System.out.println(firstNode.getNextNode().data);
  }
}
```

#### Implementation
Imagine we are working at an ice cream shop that sells three flavors: strawberry, banana, and coconut. The signature fruity sundae is made of these three flavors, but our new hires have a hard time remembering the order.

```java
public class Node {

  public String data;
  private Node next;	

  public Node(String data) {
    this.data = data;
    this.next = null;
  }

  public void setNextNode(Node node) {
    this.next = node;
  }

  public Node getNextNode() {
    return this.next;
  }

  public static void main(String[] args) {
    Node strawberry = new Node("Berry Tasty");
    Node banana = new Node("Banana-rama");
    Node coconut = new Node("Nuts for Coconut");

    strawberry.setNextNode(banana);
    banana.setNextNode(coconut);

    Node currentNode = strawberry;
    while (currentNode != null) {
      System.out.println(currentNode.data);
      currentNode = currentNode.getNextNode();
    }
  }
}
```

# Linear Data Structures

## Linked Lists

### Linear Data Structures

#### Linked Lists
Linking together nodes using their `next` property creates a singly linked list. Like nodes, these lists are used as foundations for future data structures and are an alternative to arrays when trying to store information in a linear way.

#### Doubly Linked Lists
While a singly linked list consists of nodes with links from the one node to the next, a doubly linked list also has a link to the node before it. These `previous` links, along with the added `tail` property, allow you to iterate backward through the list as easily as you could iterate forward through the singly linked list.

#### Queues
A queue is a linear collection of nodes that exclusively adds (enqueues) nodes to the tail, and removes (dequeues) nodes from the head of the queue. They can be implemented using different underlying data structures, but one of the more common methods is to use a singly linked list, which is what you will be using for your `Queue` class. Think of the queue data structure as an actual queue, or line, in a grocery store. The person at the front gets to leave the line first, and every person who joins the line has to join in the back.

#### Stacks
Stacks are another data structure with a perfectly descriptive name. Like a queue, a stack is a linear collection of nodes that adds (pushes) data to the head, or top, of the stack. However, unlike a queue, a stack removes data (pops) from the head of the stack. Think of it as a stack of books, where you can only pick up the top book, and add a new book to the top.

### Linked Lists: Conceptual

#### Linked List Introduction
The list is comprised of a series of nodes as shown in the diagram. The head node is the node at the beginning of the list. Each node contains data and a link (or pointer) to the next node in the list. The list is terminated when a node’s link is null. This is called the tail node.

Since the nodes use links to denote the next node in the sequence, the nodes are not required to be sequentially located in memory. These links also allow for quick insertion and removal of nodes as you will see in future exercises.

Common operations on a linked list may include:

- adding nodes
- removing nodes
- finding a node
- traversing (or traveling through) the linked list

Linked lists typically contain unidirectional links (next node), but some implementations make use of bidirectional links (next and previous nodes).

![[Pasted image 20240304124353.png]]

#### Linked List Example

![[Pasted image 20240304124459.png]]

#### Linked Lists Adding and Removing Nodes
With linked lists, because nodes are linked to from only one other node, you can’t just go adding and removing nodes willy-nilly without doing a bit of maintenance.

##### Adding a new node
Adding a new node to the beginning of the list requires you to link your new node to the current head node.

##### Removing a node
If you accidentally remove the single link to a node, that node’s data and any following nodes could be lost to your application, leaving you with orphaned nodes.

To properly maintain the list when removing a node from the middle of a linked list, you need to be sure to adjust the link on the previous node so that it points to the following node.

Depending on the language, nodes which are not referenced are removed automatically. “Removing” a node is equivalent to removing all references to the node.

![[Pasted image 20240304124639.png]]

In order to remove `node_b`, you must first link `node_a` to `node_c` (where `node_b` was linking).

Then you can remove `node_b`.

#### Linked List Review
Linked Lists:

- Are comprised of nodes
- The nodes contain a link to the next node (and also the previous node for bidirectional linked lists)
- Can be unidirectional or bidirectional
- Are a basic data structure, and form the basis for many other data structures
- Have a single head node, which serves as the first node in the list
- Require some maintenance in order to add or remove nodes

### Linked Lists: Java

#### Constructor and Adding to the Head
For our use, we want to be able to:

- add a new node to the beginning (head) of the list
- add a new node to the end (tail) of the list
- remove a node from the beginning (head) of the list
- print out the nodes in the list in order from head to tail

```java
public class LinkedList {
  public Node head;

  public LinkedList() {
    this.head = null;
  }

  public void addToHead(String data) {
    Node newHead = new Node(data);
    Node currentHead = this.head;
    this.head = newHead;
    if (currentHead != null) {
      this.head.setNextNode(currentHead);
    }
  }

  public static void main(String []args) {
    
  }

}
```

#### Adding to the Tail
Now that we can add to the head of the linked list, the next step is to be able to add to the tail.

```java
  public void addToTail(String data) {
    Node tail = this.head;
    if (tail == null) {
      this.head = new Node(data);
    } else {
      while (tail.getNextNode() != null) {
        tail = tail.getNextNode();
      }
      tail.setNextNode(new Node(data));
    }
  }
```

#### Removing the Head
Now we’re going to learn how to remove from the head of the list. To do this, we are first going to check to see if the list has a head. If it doesn’t, there is nothing to return. If there is a head, we will remove it by setting the list’s head equal to the original head’s next node, and then return that original head.

```java
  public String removeHead() {
    Node removedHead = this.head;
    if (removedHead == null) {
      return null;
    }
    this.head = removedHead.getNextNode();
    return removedHead.data;
  }
```

#### Printing
Our `.printList()` method is going to create a [`String`](https://www.codecademy.com/resources/docs/general/data-types/string) that holds the data from every node in the list. We’ll start at the list’s head and iterate through the list, adding to our `String` as we go.

```java
  public String printList() {
    String output = "<head> ";
    Node currentNode = this.head;
    while (currentNode != null) {
      output += currentNode.data + " ";
      currentNode = currentNode.getNextNode();
    }
    output += "<tail>";
    System.out.println(output);
    return output;
  }
```

#### Implementation

```java
public class LinkedList {

  public static void main(String []args) {
    // Write your code here:    
    LinkedList seasons = new LinkedList();
    seasons.printList();
    seasons.addToHead("summer");
    seasons.addToHead("spring");
    seasons.printList();
    seasons.addToTail("fall");
    seasons.addToTail("winter");
    seasons.printList();
    seasons.removeHead();
    seasons.printList();
  }

	public Node head;

	public LinkedList() {
		this.head = null;
	}

  public void addToHead(String data) {
    Node newHead = new Node(data);
    Node currentHead = this.head;
    this.head = newHead;
    if (currentHead != null) {
      this.head.setNextNode(currentHead);
    }
  }

  public void addToTail(String data) {
    Node tail = this.head;
    if (tail == null) {
      this.head = new Node(data);
    } else {
      while (tail.getNextNode() != null) {
        tail = tail.getNextNode();
      }
        tail.setNextNode(new Node(data));
    }
  }  

  public String removeHead() {
    Node removedHead = this.head;
    if (removedHead == null) {
      return null;
    }
    this.head = removedHead.getNextNode();
    return removedHead.data;
  }

  public String printList() {
    String output = "<head> ";
    Node currentNode = this.head;
    while (currentNode != null) {
      output += currentNode.data + " ";
      currentNode = currentNode.getNextNode();
    }
    output += "<tail>";
    System.out.println(output);
    return output;
  }  

}
```

## Doubly Linked Lists

### Doubly Linked Lists: Conceptual

#### Doubly Linked Lists Introduction
Like a singly linked list, a doubly linked list is comprised of a series of nodes. Each node contains data and two links (or pointers) to the next and previous nodes in the list. The head node is the node at the beginning of the list, and the tail node is the node at the end of the list. The head node’s previous pointer is set to `null` and the tail node’s next pointer is set to `null`.

Common operations on a doubly linked list may include:

- adding nodes to both ends of the list
- removing nodes from both ends of the list
- finding, and removing, a node from anywhere in the list
- traversing (or traveling through) the list

![[Pasted image 20240304154207.png]]

#### Adding to the List
In a doubly linked list, adding to the list is a little complicated as we have to keep track of and set the node’s previous pointer as well as update the tail of the list if necessary.

##### Adding to the Head



### Doubly Linked Lists: Java




## Linked List Practice

## Searching Arrays

## Queues

## Stacks




# Hash Maps

# Algorithmic Concepts

# Nonlinear Data Structures

# Sorting Algorithms

# Graph Data Structures

