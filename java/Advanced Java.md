# Parallel and Concurrent Programming

## What is Parallel and Concurrent Programming?

### Concurrent Programming
**Concurrency** is the act of processing more than one task at seemingly the same time on the same CPU, requiring the ability to switch between tasks. This means the actual processing of these tasks can’t happen at _exactly_ the same time, only seemingly.

### Parallel Programming
**Parallelism** is the act of splitting tasks into smaller subtasks and processing those subtasks in parallel, for instance across multiple CPUs at the _exact_ same time. True parallelism happens when each thread processing a designated subtask runs on a separate CPU / CPU core / GPU core.

An important distinction to note as well is the difference between parallel execution and parallelism.

**Parallel execution** is the act of processing more than one task simultaneously across more than one CPU, but with the distinction that the tasks being processed stay on their designated CPU and never leave it.

This means that a program can perform concurrent parallel execution, but not implement parallelism.

To do this, multiple CPUs are used and each CPU is processing more than one task, but each individual task remains and eventually fully processes on the CPU that started it.

An easy-to-remember distinction between concurrency and parallelism looks like this: “Concurrency is about dealing with lots of things at once. Parallelism is about doing lots of things at once.”

Or in other words, concurrency is about “structure” and parallelism is about “execution.”

### Concurrency and Parallelism Combos:

#### Concurrency without Parallelism
More than one task is processed at seemingly the same time (concurrently), but in actuality, the application is switching between making progress on each task until the tasks are done.

There is no true parallel execution in parallel threads or CPUs.

#### Parallelism without Concurrency
Only one task is worked on at a time, but that task is broken down into subtasks that are processed in parallel. This only works if each task, and its subtasks, completes before the next task is split and executed in parallel.

#### Neither Concurrent nor Parallel
Only one task is worked on at a time, and the task is never broken down into subtasks for parallel execution.

#### Concurrent and Parallel
There are two ways to do this:

- Application starts multiple threads which are then executed on multiple CPUs
- Application both works on multiple tasks concurrently and also breaks each task down into subtasks for parallel execution. However, some of the benefits unique to each case may be lost in this scenario.

### Conclusion
Humans can’t multitask. We’ve proven this by discussing the differences between concurrent and parallel programming, and we’ve seen that we’re just really good at switching tasks very quickly.

However, applying what we’ve learned about parallelism, we can extrapolate that two humans can simultaneously work on the same task and operate in parallel. An easy example of this can be found in any typical group project.

The task, to get the project done, is broken up into subtasks that are assigned to the individuals comprising the group. This means these subtasks are processed in parallel by separate individuals, or metaphorical CPUs / threads, simultaneously. And because these subtasks are all processing the same primary task, this is an example of parallelism. If we wanted to sprinkle in some concurrency, we can assign some members of this group more than one subtask to switch between.

## Threading Refresher
In Java, threads are part of a program that follow their paths of execution independently. They can improve performance for processes that can be split into code that can run concurrently.

There are two main ways to create threads:

- Extending the `Thread` class
- Implementing the `Runnable` interface

### Extending Thread
`Thread` is a built-in class that can handle threading, imported through `java.lang.Thread`. The class that extends `Thread` will become threadable and can then override the built-in `.run()` method found in the parent class.

Using this approach also comes with the ability to `.start()` and `.sleep()` the created threads.

For example, let’s say we have a custom `Factorial` class that extends `Thread`. To use this class like a thread, we can do the following:

```java
Factorial f = new Factorial(25);
Factorial g = new Factorial(10);
f.start();
g.start();
```

### Implementing Runnable
This is often the preferred method over extending `Thread` because it allows you to extend other parent classes so long as you still include the necessary `.run()` method from `Runnable`. It’s also more intuitive to implement instead of extending because we’re not trying to _extend_ the functionality of threads here, we’re just trying to _use_ the functionality of threads.

Since the class itself is no longer technically a `Thread`, we can’t use `.start()` or other thread functionality on it like we can in the previous approach. However, when creating threads, we can actually pass an object of type `Runnable` to the `Thread` class which will then be used by that thread.

Doing this grants us access to all `Thread` functionality without extending from `Thread` because we’re simply using the actual `Thread` class itself.

For example, let’s say our previous custom `Factorial` class implements `Runnable` now. To use this new class like a thread, we can do the following:

```java
Factorial f = new Factorial(25);
Factorial g = new Factorial(10);
Thread t1 = Thread(f);
Thread t2 = Thread(g);
t1.start();
t2.start();
```

### Interacting with Threads
We can use:

- `.sleep()` to pause a thread’s processing for a set amount of time
- `.wait()` to pause a thread’s processing until a condition is met
- `.isAlive()` to check if a thread is still processing or if it’s finished
- `.join()` to wait for a thread to finish and join back into the main thread
- `.notifyAll()` to unpause all waiting threads

### Managing Shared Resources
When running threads access resources, it’s important to know how to control how many threads can be interacting with and altering a resource at any given time. A program needs to account for this to prevent race conditions and other unpredictable situations that could arise.

The quickest way to achieve resources that are thread-safe is to use the `synchronized` keyword. However, also note that nonblocking algorithms can be used to avoid too much synchronization.

When using `synchronized`, Java will ensure the given instance of that object will only be accessible by one thread at a time. An entire class, method, or variable object can all be synchronized by simply adding the keyword to the object declaration.

```java
// Class
synchronized(this);
 
// Method
synchronized void method(int n) {
  // Method body
}
 
// Variable object
private final Object lock = new Object();
synchronized(lock) {
  // Lock object body
}
```

## Parallel and Concurrent Programming

### Introduction to Parallel and Concurrent Programming
Java 7 provides a Fork-Join framework to enable parallel computing, but it requires you to specify exactly how the problems are subdivided. To truly incorporate parallelism into our programs, we need to utilize multiple streams, which is a Java 8+ feature.

- **Concurrency** is the act of processing more than one task at seemingly the same time on the same CPU, requiring the ability to [switch](https://www.codecademy.com/resources/docs/java/switch) between tasks.
- **Parallelism** is the act of splitting tasks into smaller subtasks and processing those subtasks in parallel, for instance across multiple CPUs at the exact same time.

Java is very particular about how it allocates its resources for threading. For instance, the JVM understands your static `main` runner as a `main thread` whenever you run your projects. You can see a demonstration of this by implementing the following print statement into any project’s static `main` method:

```java
System.out.println(“Thread name: “ + Thread.currentThread().getName());
```

```
Thread name: main
```

Whenever we create additional threads, either through extending `Thread` or implementing `Runnable`, they will all run _concurrently_ (including the main thread). This is because the JVM likes to keep a process’s running threads in the same place by default.

It’s important to note that concurrent threading isn’t a bad thing, and parallelism should not be considered “better.” Each of these concepts has its strengths and levels of efficiency, and there will always be a tradeoff of overhead in both.

Programs that don’t need parallelism should not be forced into it, but do know that sometimes real parallelism will show very real benefits.

### What are Thread Pools
What we need is a way to create all the threads we’ll need early and just pool them together in an easily accessible place. That way, whenever our program wants to offload work onto the threads, it can just find this pool and toss whatever processing it needs threaded into it.

No need for worrying about how many threads to create for the task. No need to create any threads as it goes. No need to assign each thread what they’ll be working on.

Conveniently, Java has a way to do exactly this. It’s called a thread pool.

A _thread pool_ manages a pool of worker threads that connect to a work [queue](https://www.codecademy.com/resources/docs/java/queue) of `Runnable` tasks waiting to be executed.

In this thread pool, the added threads idle until given work. A Blocking Queue is used to manage this work, which takes a given `Runnable` object as a task to be processed and enqueues it. The idling threads, which are all watching this queue, will process the enqueued tasks on a first come first serve basis and will sort out who gets what task amongst themselves.

Once a thread finishes its task, it simply returns to watching this Blocking Queue and processes whatever tasks get enqueued next.

In other words, you enqueue a task you want processed into a thread pool’s queue, and one of the idling threads will dequeue that task and process it. This keeps your threads busy and helps with reusability, plus it adds some much-needed constraints to your memory usage when creating and using threads.

![[Pasted image 20240304201102.png]]

Now, while you can create and use a custom thread pool yourself, we’re going to look at Java’s built-in ways to utilize thread pooling. It does this through something called an `Executor`.

### The Executor Framework
The `Executor` framework implements thread pooling through an `Executor` interface. Using it is fairly intuitive and draws on already pre-existing functionality found in the Thread class, and the executor framework provides additional [interfaces](https://www.codecademy.com/resources/docs/java/interfaces) for various implementation strategies.

`Executor` interfaces include:

- `Executor`: launch a `Runnable` object task
- `ExecutorService`: manages the lifecycle of tasks in a sub-interface of `Executor`
- `ScheduledExecutor`: schedules the execution of tasks in a sub-interface of `ExecutorService`

We’ll need the following imports:

```java
import java.util.concurrent.ExecutorService;
import java.util.concurrent.Executors;
```

Additionally, since we need the tasks we enqueue into the thread pool to be `Runnable` objects, we’ll be creating a `Runnable` class accordingly. To use an executor, we need to create an `ExecutorService` object and pass it the number of threads we’ll be allotting it:

```java
private static final int N = 10;
ExecutorService executor = Executors.newFixedThreadPool(N);
```

Since the thread pool is responsible for those threads, it will automatically handle creating those and managing how they run. We just need to tell it how many to create and handle. At this point, all we need to do now is pass tasks to the executor, which we do like this (as usual, we’ll probably be putting this into a loop much like how we loop the creation and assignment of manual threads):

```java
Runnable task = new RunnableTask();
executor.execute(task);
```

In the above, `RunnableTask` is the custom class you’ll be creating that implements `Runnable`. Calling `executor.execute(task)` will enqueue the newly created `Runnable` object into the thread pool, which will be processed by one of the waiting threads. Now, thanks to the `ExecutorService` interface, we have some useful [methods](https://www.codecademy.com/resources/docs/java/methods) we can call to interact with the working threads.

If we want to prevent any new tasks from being added to our executor, we can call `executor.shutdown()`. In this case, the threads will still work and clear out the [queue](https://www.codecademy.com/resources/docs/java/queue), but this will ensure nothing new gets added after this point.

If we want to wait for the thread pool to finish executing everything in its queue, we can call `executor.awaitTermination()`.


---
`Runnable` requires all implementing classes to include a method called `public void run()`, so go ahead and add that with an attached `@Override` tag.

Calling `shutdown()` is what prevents new tasks from being enqueued. The `awaitTermination()` method will wait for an allotted amount of maximum seconds for the tasks to finish, and if they finish before that time has passed it won’t throw an error. However, if the time passes and the threads still aren’t done, an error will be thrown.

```java
// Main.java
import java.util.concurrent.ExecutorService;
import java.util.concurrent.Executors;
import java.util.concurrent.TimeUnit;

public class Main {
  private static final int N = 10;
  
  // Main method
  public static void main(String[] args) throws InterruptedException {
    ExecutorService executor = Executors.newFixedThreadPool(N);

    for (int i = 0; i < 500; i++) {
      Runnable task = new RunnableTask(10000000L + i);
      executor.execute(task);
    }

    executor.shutdown();
    executor.awaitTermination(30, TimeUnit.SECONDS);
    System.out.println("Finished all threads");
  }

}
```

```java
// RunnableTask.java
public class RunnableTask implements Runnable {
  private final long limit;
  // Constructor
  RunnableTask(long limit) {
    this.limit = limit;
  }

  @Override
  public void run() {
    long sum = 0;
    for (long i = 1; i < this.limit; i++) {
      sum += i;
    }
    System.out.println(Thread.currentThread().getName() + ": " + sum);
  }

}
```
#aqui
### The Fork-Join Framework
A similar interface to the executor service was added in Java 7 that included functionality to split a task into smaller subtasks and re-enqueue them into the thread pool. This is particularly useful for more intensive tasks and actually implements parallelism to do it.

This new interface is part of a Fork-Join framework and is called `ForkJoinPool`, which distributes a task across several worker threads and waits for a result.

Another big difference is the type of task object we’ll be passing to this pool. Instead of implementing the `Runnable` class, we’ll actually be extending either `RecursiveAction` or `RecursiveTask` depending on the implementation we want.

Here is the difference between the two:

- `RecursiveAction`: does not return any result
- `RecursiveTask`: returns a result

As the namesake suggests, the Fork-Join framework utilizes recursion to perform its subtask splitting, which we’ll limit by defining a set number of threads. This controls how many times the task is allowed to split itself since each subtask will be assigned to an individual thread.

Additionally, instead of calling `execute()` as we did before to add new tasks to the thread pool [queue](https://www.codecademy.com/resources/docs/java/queue), we’ll be calling `invoke()`. Since we’re splitting a singular task across the worker threads, we only have to call `invoke()` once, which means we can invoke the task in the same place we create the pool itself:

```java
private static final int N = 4;
ForkJoinExecutor pool = new ForkJoinPool(N);
pool.invoke(task);
```

---
The result however is so big that we need to utilize Java’s `BigInteger` class to compute and display it, otherwise the normal primitives overflow.

So, with all that uncontrollable forking, how do we actually limit how many threads exist at any given time? We’ll be using a `ForkJoinPool` to do this. Think of this like the `Executor` framework’s thread pool.

A quick way to avoid eating up too much RAM is to just make a call to the running JVM and ask it how many available processors it has. This way, the program will never try to use more resources than it has.

We can do this by calling this line and storing it in an `int` called `nThreads`:

```java
int nThreads = Runtime.getRuntime().availableProcessors();
```

```java
// Main.java
import java.math.BigInteger;
import java.time.Clock;
import java.util.concurrent.ForkJoinPool;

public class Main {
  public static void main(String[] args) {
    Clock clock = Clock.systemDefaultZone();
    long start, stop;
    MakeBigIntArray test = new MakeBigIntArray(5000);
    
    // Check the number of available processors
    int nThreads = Runtime.getRuntime().availableProcessors();
    System.out.println(nThreads);
    
    // Print outs for threaded results
    RecursiveFactorial rSum = new RecursiveFactorial(test.getList());
    ForkJoinPool pool = new ForkJoinPool(nThreads);

    start = clock.millis();
    pool.invoke(rSum);
    stop = clock.millis();

    BigInteger result = rSum.result;

    System.out.println("Time in ms: " + (stop - start));
    System.out.println("Pooled Result: " + result);

    // Print outs for sequential results
    BigInteger sum = new BigInteger("1");
    start = clock.millis();
    for (int i = 0; i < test.getList().length; i++) {
        sum = sum.multiply(test.getList()[i]);
    }
    stop = clock.millis();
    System.out.println("Time in ms: " + (stop - start));
    System.out.println("Serial Result: " + sum);
  }
}
```

```java
// MakeBigIntArray.java
import java.math.BigInteger;

public class MakeBigIntArray {
  private final BigInteger[] list;

  public MakeBigIntArray(int bounds) {
    list = new BigInteger[bounds];
    for (int i = 0; i < bounds; i++) { 
      list[i] = new BigInteger("" + (i + 1));
    }
  }

  public BigInteger[] getList() {
      return list;
  }
}
```

```java
// RecursiveFactorial.java
import java.math.BigInteger;
import java.util.Arrays;
import java.util.concurrent.RecursiveAction;

public class RecursiveFactorial extends RecursiveAction {
  private BigInteger[] list;
  public BigInteger result;

  public RecursiveFactorial(BigInteger[] array) {
      this.list = array;
  }

  @Override
  protected void compute() {
      if (list.length == 1) {
        result = list[0];
      } else {
        int midpoint = list.length / 2;
        BigInteger[] l1 = Arrays.copyOfRange(list, 0, midpoint);
        BigInteger[] l2 = Arrays.copyOfRange(list, midpoint, list.length);
        RecursiveFactorial rf1 = new RecursiveFactorial(l1);
        RecursiveFactorial rf2 = new RecursiveFactorial(l2);

        rf1.fork();
        rf2.fork();
        rf1.join();
        rf2.join();
        
        result = rf1.result.multiply(rf2.result);
      }
  }
}
```

### Parallelism
So far, we’ve seen that parallelism is hard to come by. The biggest reason for this is the innate issue of making something “thread-safe.” If something is thread-safe, then multiple threads can interact with it without causing problems.

Unfortunately, a big problem exists when trying to enforce this concept of thread-safe. [Collections](https://www.codecademy.com/resources/docs/java/collections) are not thread-safe, which include `List`s, [`Map`](https://www.codecademy.com/resources/docs/java/map)s, and [`Set`](https://www.codecademy.com/resources/docs/java/set)s.

Multiple threads can’t manipulate a collection without introducing thread interference or memory consistency [errors](https://www.codecademy.com/resources/docs/java/errors). The former occurs when one thread overwrites the results of another thread in an unpredictable way, which can cause unexpected results when reading the altered data. The latter occurs when different threads have inconsistent views of what should be the same data.

And even if we introduce synchronization to make these collections thread-safe, doing so then also introduces thread contention. And thread contention directly contradicts parallelism due to it preventing threads from interacting with a resource while it’s being used by another thread.

So… how did Fork-Join get around this?

As you saw in the previous exercise, the Fork-Join framework was the first framework we’ve worked with so far that legitimately implements parallelism into its processing. The way it does this is through something called aggregate operations, which performs all the partitioning and combining of solutions during Java runtime.

We won’t get into exactly what aggregate operations are or how they work, but just know they’re one key way to implement parallelism. Another key way, which we will get into, is something called parallel streams.

Note: remember that parallelism doesn’t automatically result in faster performance than serial processing. while aggregate operations and parallel streams more easily implement parallelism, it is still the coder’s responsibility to determine if their application is even suitable for parallelism.

### Java Streams
To explain what parallel streams are, we need to first talk about what exactly a Java Stream is. _Java Streams_ were introduced in Java 8, and are used to process a collection of objects which can be pipelined to produce a desired result.

A stream itself is not a data structure, it instead takes its input from [collections](https://www.codecademy.com/resources/docs/java/collections), [arrays](https://www.codecademy.com/resources/docs/java/arrays), or other I/O channels. Additionally, streams don’t change the original data structure and only return results based on pipelined [methods](https://www.codecademy.com/resources/docs/java/methods).

In a stream, intermediate operations are lazily executed and return results in the form of additional streams, which allow for the pipelining of those results. Terminal operations mark the end of the stream and return the final result.

An operation is _lazy_ if its value is evaluated only when it is required. The reason why it does this is to save the processing of actual stream contents until the terminal operation commences. This enables the Java [compiler](https://www.codecademy.com/resources/docs/java/compiler) and runtime to optimize how they process streams.

Let’s go over some different types of operations.

Intermediate Operations:

- [`map`](https://www.codecademy.com/resources/docs/java/map): returns a stream consisting of the results after applying a given function to the elements of this stream

```java
List numbers = Arrays.asList(1,2,3,4);
List square = numbers.stream().map(x->x*x).collect(Collectors.toList());
```

- `filter`: selects elements as per a Predicate passed as an argument

```java
List names = Arrays.asList(“Alpha”,”Beta”,”Omega”);
List find = names.stream().filter(s->s.startsWith(“O”)).collect(Collectors.toList());
```

- `sorted`: sorts the stream

```java
List names = Arrays.asList(“Omega”,”Alpha”,”Beta”);
List sorted = names.stream().sorted().collect(Collectors.toList());
```

Terminal Operations:

- `collect`: returns the result of the intermediate operations performed on the stream

```java
List numbers = Arrays.asList(1,2,3,4,2);
Set squareSet = numbers.stream().map(x->x*x).collect(Collectors.toSet());
```

- `forEach`: iterates through every element of the stream

```java
List numbers = Arrays.asList(1,2,3,4);
numbers.stream().map(x->x*x).forEach(y->System.out.println(y));
```

- `reduce`: reduces the elements of a stream to a single value (this takes a BinaryOperator as a parameter)

```java
List numbers = Arrays.asList(1,2,3,4);
int even = numbers.stream().filter(x->x%2==0).reduce(0,(ans,i)->ans+i);
```

In the above example, `ans` is a variable that is assigned the value 0 initially, then `i` is added to it.

Remember, everything a stream does has no effect on the original value of the object initially passed to it.

### Java Parallel Streams
Now that we know what Java Streams are and how they work, we can start to understand why they’re good for parallel processing. They ultimately don’t alter the original object passed to them, which helps with the thread-safe problem.

Additionally, Java normally has one stream for processing code, which uses sequential execution and is the default when performing normal [threading](https://www.codecademy.com/resources/docs/java/threading).

_Java Parallel Streams_ divide a running process into multiple streams that execute in parallel on separate cores, returning a combined result of all the individual outcomes. However, the order of execution is not under our control.

This means we want to try to only use parallel streams when the order of execution doesn’t matter.

To create a parallel stream, we need to invoke the operation `Collection.parallelStream`. 

```java
File file = new File(filePath);
List<String> textLines = Files.readAllLines(file.toPath());
textLines.parallelStream().forEach(System.out::println);
```

Alternatively, we can also invoke the operation `BaseStream.parallel`. 

```java
File file = new File(filePath);
Stream<String> textLines = Files.lines(file.toPath());
textLines.parallel().forEach(System.out::println);
textLines.close();
```

---

```java
import java.io.File;
import java.io.IOException;
import java.nio.file.Files;
import java.util.*;
import java.util.stream.Stream;

public class Main {
  public static void main(String[] args) throws IOException {
    File file = new File("test.txt");

    // Create a List using readAllLines(), which reads all lines at once
    // Note: this will maintain the original ordering of the text
    List<String> textLineList = Files.readAllLines(file.toPath());

    System.out.println("[ Parallel streaming from list: ]");
    // Create parallel streams from List to print output
    textLineList.parallelStream().forEach(System.out::println);
    
    
    // Create a Stream of string type using lines(), which reads one line at a time from the text file
    // Note: this will maintain the original ordering of the text
    Stream<String> textLineStream = Files.lines(file.toPath());

    System.out.println("[ Parallel streaming from stream: ]");
    // Uses parallel() to create multiple streams to print output
    textLineStream.parallel().forEach(System.out::println);

    // Close the stream
    textLineStream.close();
  }
}
```


# Servlets

## What Are Java Servlets?

### Servlets
A Java **servlet** is a Java class whose sole purpose is to receive a network request and response object (typically HTTP) and construct the necessary response. A servlet allows us to create dynamic responses (like a dynamic web page) based on a request sent by a client. Servlets make it easy for us to create web applications incorporated with all the benefits of Java, like its portability and security.

## Setting Up Our Environment for Servlets

### Introduction
For us to start working with Java servlets and make HTTP requests to them we’ll need a web server (to take requests and serve responses) and a servlet container (to run our servlets in). Thankfully, Tomcat (free and open-source), gives us both a web server and a servlet container.

### The Tomcat Directory
In Tomcat we’ll see the following folders:

- bin/ - Usefull Tomcat scripts and files. Includes the startup and shutdown scripts used to start and stop Tomcat.
- conf/ - Configuration (`.xml`) files for the Tomcat server like server.xml which can be used to modify the port Tomcat deploys to.
- lib/ - JAR files (like `servlet-api.jar`) required by Tomcat to run.
- logs/ - Tomcat-generated log files are kept here
- webapps/ - Deployed applications are kept here. We can place our project directory here or convert it into a `.war`, which Tomcat will unzip.

## Creating a Java Servlet

### Understanding the icecream-app
When you first open the `icecream-app/` directory, you’ll notice:

- `WEB-INF/` directory.
- HTML file(s).

The `WEB-INF/` folder contains everything needed to run our web application and consists of the following subdirectories and files:

- `src/` - Contains java source (.java) files.
- `classes/` - Contains Java bytecode (.class) files.
- `lib/` - Contains JARs needed by our web application.
- `web.xml` - An XML deployment descriptor file needed by Tomcat to deploy our servlets. We can define things like servlets, URL mappings, and more.

### Creating a Servlet
Java makes creating a servlet easy by providing the `GenericServlet` and `HttpServlet` classes which we can extend to create a custom servlet. Using a protocol-specific subclass (like `HttpServlet`) is recommended to create our servlets. We’ll start by creating a homepage for our ice cream web application.

In our text editor, let’s create a new file called `HomeServlet.java` and save it in the `src/` directory of our `WEB-INF/` directory. We’ll need to add some imports to our file in order to work with servlets, so let’s add the following imports to the top of our file:

```java
import java.io.IOException;
import java.io.PrintWriter;

import javax.servlet.ServletException;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;
import javax.servlet.http.HttpSession;
```

Now let’s define a class called `HomeServlet` that extends that `HttpServlet` class we’ve imported and a `private static final serialVersionUID`.

```java
public class HomeServlet extends HttpServlet {
  private static final long serialVersionUID = 100L;  // Used for serialization since `HttpServlet` implements `Serializable`. 
}
```

We’d like our `HomeServlet` to serve us an HTML page when we go to our URL in our browser. Recall that our browser will make a request to the server, and the server will process the request and return a response to the client. To accomplish this, we’ll need to implement the `doGet()` method of `HttpServlet` like:

```java
public void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
  PrintWriter out = response.getWriter();
  out.println("<html>");
  out.println("<head><title>My Icecream Shop!</title></head>");
  out.println("<body>");
  out.println("<h1>Welcome To My Ice Cream Parlor</h1>");
  out.println("</body></html>");
}
```

Note that our implementation of `doGet()`:

- Takes the HTTP request and response objects as parameters.
- Throws the `ServletException` (servlet was not able to handle GET request) and `IOException` (an input or output error occurred).
- Uses `PrintWriter` to create a simple HTML page with a header welcoming our visitors.

### Web.xml
In order to make a servlet “visible” to our server, we’ll need to configure a URL to the servlet so that our server knows to invoke it when a request to that URL comes in. We can do this using the `web.xml` file provided in the `WEB-INF/` directory of our `icecream-app/` directory.

The `web.xml` file is the deployment descriptor for our web application. In this file, we can register our servlet classes, define the URLs those servlets map to, and many other things.

```xml
 <servlet>
    <servlet-name>homeServlet</servlet-name>
    <servlet-class>HomeServlet</servlet-class>
  </servlet>
```

Note that to register a servlet we:

- Use the `<servlet>...</servlet>` tag.
- Define the child tag, `<servlet-name>homeServlet</servlet-name>`, which will define our reference to this servlet and can be any name.
- Define the child tag `<servlet-class>HomeServlet</servlet-class>`, which will define the class this servlet definition maps to. Note that if your servlet is in a package you need specify the package path.

Finally, we’ll need to tell our server which URL to invoke our `HomeServlet` for. Let’s do this by placing the following snippet after the `<servlet></servlet>` block we added previously in our `web.xml` file:

```xml
<servlet-mapping>
    <servlet-name>homeServlet</servlet-name>
    <url-pattern>/home</url-pattern>
  </servlet-mapping>
```

In order to map a URL to a servlet we:

- Use the `servlet-mapping>...</servlet-mapping>` tag.
- Define the child tag, `<servlet-name>homeServlet</servlet-name>`, which defines which servlet (using the name we defined using `<servlet-name>`), this URL will map to.
- Define the child tag, `<url-pattern>/home</url-pattern>`, which defines the servlet path this servlet will handle.

### Testing the Servlet
Let’s get our ice-cream app ready to deploy by first compiling `HomeServlet.java`. Let’s open the CMD (Windows) or terminal (Linux/ OS X) and change our directory to the `bin/` directory in Tomcat.

In order to compile `HomeServlet.java` file, we’ll need to use the `javac` command and specify the classpath to the Tomcat `servlet-api.jar` and specify to place the generated `.class` file in the `classes/` directory of `WEB-INF/`.

```sh
javac -cp  lib/servlet-api.jar -d webapps/icecream-app/WEB-INF/classes webapps/icecream-app/WEB-INF/src/HomeServlet.java 
```

- javac - The java compiler command-line tool.
- -cp lib/servlet-api.jar - The javac option to specify where the compiler can look for our imported classes (like `HttpServlet`).
- -d webapps/icecream-app/WEB-INF/classes - The javac option to specify where to place the generated `.class` file.
- webapps/icecream-app/WEB-INF/src/HomeServlet.java - The path to our `.java` file that we wish to compile.

At this point, we’re ready to start Tomcat and see our web page. Let’s execute the `startup.bat` (Windows) or `startup.sh` (Linux/ OS X). Once Tomcat has started let’s go to our browser and navigate to:

[http://localhost:8080/icecream-app/home](http://localhost:8080/icecream-app/home)

Note that the path to our servlet is [http://localhost:8080/icecream-app/home](http://localhost:8080/icecream-app/home) instead of [http://localhost:8080/home](http://localhost:8080/home) (this will give us a 404 not found error) because we need to specify the context path of our `/home` path we defined in our `web.xml`. The context path in this example is the name of our web application project directory, `icecream-app`.
#aqui
## Servlet Architecture and Lifecycle

### CGI vs Java Servlets
Prior to the introduction of Java servlets, a server could respond to user requests using the CGI. Like servlets, the CGI would allow our web server to build responses to client requests at specific URLs but do it by running CGI scripts.

![[Pasted image 20240219195012.png]]

The CGI architecture worked okay but had some major drawbacks like:

- CGI programs were OS-dependent scripts (`.bat` for Windows and `.sh` for Linux).
- Since client requests would require the execution of a script, a new process is created on every request.
- More memory is needed on the server as each process needs its own memory space; this causes a scalability issue.
- Since the CGI ran scripts on the web server, there was a high-security risk if any user input was not properly sanitized.

Java servlets addressed many of the issues related to CGI in the following ways:

- Being OS-independent as it runs on the JVM.
- Requests are processed in new threads, which require less overhead to create than processes.
- Less memory is needed on the webserver as threads share memory.
- Servlets are written in Java and inherit all of the built-in security features making them more resilient to attacks.

The CGI can still be used today, but it is preferred to use more modern technologies like Java servlets.

### Servlet Container
The servlet container is a program that runs on our web server, and its “job” is to run and manage our servlets. Using Tomcat provides not only the `servlet-api.jar` but also a web server and a servlet container.

The servlet container keeps track of all the servlets (and other servlet-related properties) in what is known as the servlet context.

![[Pasted image 20240219195600.png]]

The servlet container receives a request from the web server and does the necessary network and protocol (like HTTP) processing to make the request and response objects easily available to the servlet that should handle the request.

### Servlet Lifecycle
Our servlets are managed through the servlet container. The management of servlets involves initialization, invocation, and destruction. The servlet API exposes methods for the container to use like `init()`, `service()`, and `destroy()`.

![[Pasted image 20240219195738.png]]

The container will:

- Check if an instance of the requested servlet is available.
- If an instance is not available it will load the servlet class, create an instance of it, and call `init()`. Note that once a servlet is initialized it stays initialized until destroyed.
- Once an instance of a servlet is available and initialized, it will call the `service()` method which, in the case of an `HttpServlet`, takes care of calling the appropriate (GET, POST, etc) methods.

Once a servlet needs to be removed, for example when we shut down our web server, it takes care of shutting down the servlet by calling its `destroy()` method.

One final important note about a servlet’s `init()` and `destroy()` methods is that they can be overridden to implement custom initialization and destruction like setting up a database connection or removing a database connection respectively.

## Processing Requests and Building Responses

### Ice Cream Order Form
Let’s navigate to the [`icecream-app/`](https://static-assets.codecademy.com/Courses/learn-advanced-java/servlets/starter-icecream-app.zip) directory and open `form.html` in our text editor. `form.html` is an HTML page that we’ll use to display a form users can use to select various options for their ice cream order.

We specify:

- `method="post"` to direct the form to make an HTTP post request.
- `action="/icecream-app/home"` to direct the form data to our `HomeServlet` using the `/home` path. The post request to `/home` would currently fail because we have not implemented our `doPost()` method in `HomeServlet`

One final important thing to highlight is that the `WEB-INF/` directory is not publicly accessible to the client, which means that any files inside can only be accessed by the servlet. Files outside of the `WEB-INF/` can be accessed by the client directly. Notice that `form.html` is outside of the `WEB-INF/` and we do this because `form.html` is a static HTML file, doesn’t contain any sensitive information, and makes it slightly easier for our servlet to link to.

### Linking a Form
We’d like for our customers to be able to order ice cream from a link on our home page. We’ll need to add a few more things to our `HomeServlet`.

Let’s open the file `HomeServlet.java` from our `WEB-INF/src/` directory in our text editor. In our `doGet()` method we’d like to add a link to the `form.html` file provided in the `icecream-app/` directory.

```java
public void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
  PrintWriter out = response.getWriter();
  out.println("<html>");
  out.println("<head><title>My Icecream Shop!</title></head>");
  out.println("<body>");
  out.println("<h1>Welcome To My Ice Cream Parlor</h1>");
  out.println("<a href='/icecream-app/form.html'>Place An Order!</a>"); // link to form
  out.println("</body></html>");
}
```

We can now compile our servlet using the `javac` command (this command assumes our directory is at our Tomcat root folder) like:

```bash
javac -cp  lib/servlet-api.jar -d webapps/icecream-app/WEB-INF/classes webapps/icecream-app/WEB-INF/src/HomeServlet.java 
```

Let’s start our Tomcat by executing `startup.bat` (Windows) or `startup.sh` (Unix).

When we click the link we should be taken to `http://localhost:8080/icecream-app/form.html`.

### HTTP Methods
Hypertext Transfer Protocol (or HTTP) is a communication method that, at its core, is transferring data over the internet in a client-server model. HTTP provides methods for manipulating data on the server in different ways. Some of the most used methods are:

- `GET` - Used to retrieve resources/data from the server.
- `POST` - Used to create resources on the server.
- `PUT` - Used to update a resource on the server.
- `DELETE` - Used to specify a resource on a server to delete.

HTTP methods typically respond with or without data and a status code. Some of the most used status codes are:

- `200` - Successful request.
- `201` - Successful request, and a resource was created.
- `400` - Bad request; the client sent a request that has some error.
- `401` - Unauthorized; the client has not been authenticated.
- `403` - Forbidden; the client does not have the correct access rights.
- `404` - Not found; the client cannot find the requested resource.
- `500` - Internal server error because there was an error on the server side that could not be handled.

### Request Parameters and Dynamic Responses




# Sockets

## What Are Sockets in Java?

## Socket Programming in Java



# Java Native Interface (JNI)

## What is JNI?

## Java Native Interface (JNI)



# Java Database Connectivity (JDBC)

## What is JDBC?
The **JDBC**, or _Java Database Connectivity_, is a tool, or more specifically an application programming interface (API) that is used to create a connection between a Java application and anyone one of many standard database applications that are available to a programmer. It is essentially the bridge that connects your program to your back-end, in this case, a database.

### What Role Does JDBC Serve
Along with establishing the connection to our database, JDBC provides the functionality to execute SQL statements on our database as well. **SQL**, or _structured query language_, is the universal standard programming language for executing commands on a database. In a broad sense, SQL can be broken up into two high-level components:

- Data Definition Language (DDL), is used in the creation, modification, and deletion of primary structures in the database such as tables and database schema.
- Data Manipulation Language (DML), is used to insert, edit, delete and select data out of tables in the database.

JDBC allows our Java program to execute both types of commands, DDL and DML, as well as to view and modify the record sets that are returned when we query the database (ask the database to do something).

### Components / Architecture
When working inside the JDBC environment, there are five primary layers in the architecture of the program:

![[What-is-JDBC.svg]]

#### Application
This is the standard Java application that you are used to working with. It includes all the logic, user interface, and implementation of the core OOP principles.

#### JDBC API
This is a set of classes and supporting files that provide the framework for the connection to a database. The API comes standard as a part of the JDK, so you won’t need to download any additional packages, but you will need to `import` the parts of the API that you will be using into your program.

#### JDBC Driver Manager
The JDBC driver manager, normally referenced by importing and calling the class `DriverManager` class acts as the interface between you the programmer, and the actual drivers for the database. Inside the class are all the methods needed to register and deregister the specific drivers, and open and close the connection between your program and the database. One important aspect is that this class maintains a registry of all the drivers that have registered with the program. Driver registration is a mandatory part of the database connection process.

#### JDBC Drivers
This is the specific code that translates the commands sent via the JDBC into the language and syntax that the designated database works with. Most database applications, MySQL, SQLite, and Postgres for example, each provide JDBC drivers that can be downloaded from their websites. It is not uncommon for these drivers to be a blend of the Java language and some other language that is used in the database. These drivers need to be imported directly into the classpath of the program (adding the `.jar` to your program through your IDE. In older versions of Java, it was necessary to explicitly register a driver but since JDBC 4.0 the `DriverManager` is capable of detecting and loading drivers that are present at compile time.

#### Databases
These are the data storage objects used to persist data throughout your application. There are many different vendors providing data storage solutions and each has its own set of advantages and disadvantages.

### Establishing the JDBC Connection
Essentially we are filling in the layers from above and, because of the advances that have been made to the JDBC API, it takes a surprisingly little amount of code to bridge the gap between your program and a database.

#### Importing Drivers and JDBC Classes
- The very first step, and often the one that is decided for you if you are joining a team or established company, is which database(s) is/are being used for the back-end of the program. For the purposes of the accompanying lessons and project, we will be using SQLite, a lightweight and portable SQL database.
- After we know which database we’re using we need to download the proper driver. As an example, here is the [latest SQLite JDBC Driver](https://mvnrepository.com/artifact/org.xerial/sqlite-jdbc).
- Once downloaded, adding the driver jar file to the project is the next step, this varies depending on which IDE you are using.
- Once the driver is included in the classpath, it’s time to add the import statements from `java.sql`. The classes we must import every time are:
	- `java.sql.DriverManager` (Provides the methods to establish the DB connection)
	- `java.sql.SQLException` (Provides error handling when interacting with the DB)
	- `java.sql.Connection` (Manages the connection and statements)
	- `java.sql.Statement` (Executes queries on the DB)
	- `java.sql.ResultSet` (The results of a query)

#### Connecting to the Database
- To open the actual connection, the `DriverManager` needs to attempt to access the database with the `getConnection` method. This method takes a URL, username, and password as parameters and returns a `Connection` object.
- **Note:** _These connections and operations while working with the back-end database are very costly, both in network resources and program memory. It is very important to make sure they are open and closed in an efficient manner. The best practice, which we will implement throughout, is to use a [Try With Resources](https://docs.oracle.com/javase/tutorial/essential/exceptions/tryResourceClose.html) code block. This eliminates the need to add a `finally` block to our `try-catch` statements, or more realistically, fixes our mistakes automatically when we forget to add the `finally` block to close resources._

```java
import java.sql.*;

public class TryBlockExamples {
  public static void main(String[] args) {
    String url = "host:db:port";
    String userName = "admin";
    String password = "adminPassword";
    
    /*
    Try - Catch - Finally syntax. The resources are declared outside of the try block
    and then closed in the finally block. If this finally block is forgotten, the resources
    are left open.
     */
    
    Connection conn = null;
    Statement statement = null;
    ResultSet results = null;

    try {
      conn = DriverManager.getConnection(url, userName, password);
      statement = conn.createStatement();
      results = statement.executeQuery("SELECT * FROM SOMETABLE");
      // Do something with results
    } catch (SQLException e) {
      System.out.println(e.getMessage());
    } finally {
      try { results.close(); } catch (Exception e) { /* Ignored */ }
      try { statement.close(); } catch (Exception e) { /* Ignored */ }
      try { conn.close(); } catch (Exception e) { /* Ignored */ }
    }
    
    /*
    Try With Resources block, the resources are now a part of the try block itself
    and the closing of the resources is handled automatically at the end of the execution.
     */
    
    try (Connection conn1 = DriverManager.getConnection(url, userName, password); 
         Statement statement1 = conn.createStatement(); 
         ResultSet results1 = statement.executeQuery("SELECT * FROM SOMETABLE")
    ) {
      // Do something with results
    } catch (SQLException e) {
      System.out.println(e.getMessage());
    }
  }
}
```

#### Statements and Executing Queries
- In order to execute SQL statements on the database we need to create an instance of a `Statement` object from our `Connection` object. This object contains the methods required to execute SQL code, both DDL and DML types of statements, directly on our database.
- For more complex SQL operations such as passing in parameters or other logic-dependent code into your SQL statements, there is an extension of the `Statement` interface called `PreparedStatement` to handle these situations.

#### Interacting with the Results
- After we have established our connection, ensured they will also be closed, set up our statements, and executed our SQL we are given a `ResultSet` object back from the database.
- ResultSet objects can be thought of as a 2d Array that corresponds to a table from the database.
- We can use the data from the `ResultSet` in our application to set up some logic sequence, return data to our user, or even forward users over to different media sources such as images, videos, and audio files.

### Summary
The Java Database Connectivity, JDBC, is a powerful tool used to send data back and forth between the front-end and back-ends of your program.

Steps:

1. Deciding on the database and importing the drivers and JDBC classes
2. Establishing a connection to your database and ensuring resources are closed after use
3. Setting up the statement manager and executing queries
4. Operating on the `ResultSet` to send information to and from your front-end.

## SQL for JDBC

### Introduction to SQL
When data inside an application needs to _persist_, that is, be available at a later time, there are a number of options that a software engineer has at their disposal:

- Application data: this lives during the runtime of the application and is destroyed when the program is exited or the mobile app is closed
- Local drives (hard drives or memory on mobile devices): great for maintaining authentication and other small, unchanging data
- Cloud/Web storage: great for data that is updated from multiple sources and large data amounts.

Of the latter two options, the most common type of storage is a _relational_ database. You can picture these databases as a collection of related spreadsheets, called _tables_, with multiple columns and rows in each table representing the data that we store and use inside our applications.

These databases don’t understand the Java programming language that we have been using so far, instead, they communicate using the _Structured Query Language_, or SQL. SQL is a small and relatively simple language used to both create the database structures, called _data definition_, and to add, edit, and delete the data inside the database, called _data manipulation_.

The question now becomes how do we connect our Java application to these databases? The answer is, of course, the Java Database Connectivity (JDBC) library, a collection of classes that provide the framework necessary to connect and communicate across both languages.

### Data Definition (Creating the Structure)
SQL is divided into two basic subcategories, _Data Definition Language (DDL)_ and _Data Manipulation Language (DML)_. In its DDL role, SQL is responsible for the creation and updating of the database structure itself. Through these commands, databases can be created, tables can be established, and the data types, constraints, and relations of individual columns and rows can be defined.

One of the most important decisions, as you’re defining the database, is establishing the data types of the columns. These ideally are matched to the objects of your application, that is if you have a `Chair` object in your program such as below, the columns of your table should align with the data types of your object.

```java
public class Chair {
  int id;
  String name;
  String color;
  double weight;
  int quantity;
}
```

SQL data types can vary by vendor, and we’ll use SQLite as our standard vendor throughout since it is open source and free to all. Let’s take a look at the data types available in SQLite:

- `NULL`
- `INTEGER`, similar to an `int`
- `REAL`, similar to a `float` or `double`
- `TEXT`, similar to a String
- `BLOB`, a blob of data, stored exactly as it was inputted and can be binary.

Note: It is common convention to use all capital letters for names in SQL.

It is when you create a table in SQL that you must decide the data types of your columns. The syntax to create a table that matches our `Chair` object is as follows:

```sqlite
CREATE TABLE CHAIRS (
    CHAIR_ID INTEGER PRIMARY KEY,
    CHAIR_NAME STRING NOT NULL,
    CHAIR_COLOR STRING,
    CHAIR_WEIGHT REAL NOT NULL,
    CHAIR_QTY INTEGER NOT NULL
);
```

The first clause, `CREATE TABLE` lets the database know what we want to do. We then give the table a name, `CHAIRS`, because that is what the table will store. Inside the parentheses of the clause, we now list all the columns, their data types, and any constraints we want for them, each column being comma separated. Constraints are simply added parameters we want our table and columns to conform to, the most common constraint is `PRIMARY KEY` which is used to identify a table row by a unique combination of column data. Another common constraint is `NOT NULL`, which requires that something is stored into the column when it is created or manipulated.

### Data Manipulation (Querying or Modifying the Data)
After we’ve built the framework of our database, we need to fill it with our data and have it return actionable results. This is where the _Data Manipulation Language_ portion of SQL comes into play. DDL uses a series of commands to query (return information from) data from or modify the data inside our database. We’ll focus on the four fundamental actions: inserting, updating, deleting, and retrieving information, along with how to sort and filter our results.

#### The INSERT Statement
Inserting data into a database is done with the `INSERT INTO` command. The following statement inserts a chair into the `CHAIRS` table:

```sqlite
INSERT INTO CHAIRS (CHAIR_ID, CHAIR_NAME, CHAIR_COLOR, CHAIR_WEIGHT, CHAIR_QTY)
VALUES 
    (10001, "Camp Chair", "Blue", 3.7, 4);
```

The first thing we tell the database after the `INSERT INTO` is which table we are entering data into, in this case, `CHAIRS`. We then open a set of parentheses that tell the database which columns we are entering data into, in our case we list all the columns. Following the column list we use another SQL keyword, `VALUES`, which tells the database that the following list of information is the values that will be stored in the columns.

#### The UPDATE Statement
As the name suggests, an `UPDATE` statement is used to update specific rows in a table. The two primary actions are to tell the database what table we will be looking in and what column we will be updating. Additionally, we can add criteria to the statement so we only update very specific rows based on the criteria. If we wanted to update all the chairs in the `CHAIRS` table to have a zero quantity, we could write the statement like this:

```sqlite
UPDATE CHAIRS
    SET CHAIR_QTY = 0;
```

If we want to update the color of our blue camp chair to red, we have to add a conditional that searches the table and returns only our specified chair to the update. We do this through the use of the `WHERE` keyword, and it works by updating all the entries `WHERE` the entered condition is true:

```sqlite
UPDATE CHAIRS
    SET CHAIR_COLOR = "RED"
    WHERE CHAIR_ID = 10001;
```

#### The DELETE Statement
The `DELETE` statement works very similarly to the `UPDATE` statement as far as syntax, but removes data from a table based on the `WHERE` criteria instead of updating it.

```sqlite
DELETE FROM CHAIRS
    WHERE CHAIR_ID = 10001;
```

#### The SELECT Statement
The `SELECT` statement is used to return data back from a database and is the standard query used to view data. In a `SELECT` statement you specify what columns you want to retrieve and from what tables. The results are returned in the form of a temporary table that can be used by, in our case, the Java application. If we wanted to view all the chairs in the `CHAIRS` table, we could write the following statement:

```sqlite
SELECT 
    CHAIR_ID, CHAIR_NAME, CHAIR_COLOR, CHAIR_WEIGHT, CHAIR_QTY
FROM
    CHAIRS;
```

Lucky for us, there is a shortcut, the `*` symbol, that we can use when we want to grab all the columns from a given table. The following command returns the same results as the statement from above:

```sqlite
SELECT * FROM CHAIRS;
```

### Java Database Connectivity (JDBC)
Now that we have a basic understanding of Structured Query Language, it’s time to see how this functionality integrates into our Java applications. As mentioned above, Oracle provides us with the JDBC, a library that bridges the two languages and allows us to share data and logic between the two structures: the application and the database. As you’ll learn in the accompanying lesson, there are several classes inside the JDBC library that work together to connect, read, and write. The ones we’ll work with are:

- `DriverManager`, provides the methods to establish the database `Connection` object
- `Connection`, manages the connection and creates `Statement` objects
- `Statement`, executes the DDL and DML statements on the database
- `ResultSet`, a Java object that represents the results of a query
- `SQLExeception`, provides error handling when interacting with the database

## Java Database Connectivity (JDBC)

### Introduction to JDBC
The **Java Database Connectivity** (JDBC) framework is an API provided by Oracle, the parent company of the Java programming language, and is included in the JDK when you install it on your computer. This API provides a simple and consistent way to connect our Java applications to a relational database in order to persist our data.

**Persistence**, or _the ability of your data to live outside your application_, is a crucial part of software development, especially as your programs grow in size and number of users.

There are a number of different storage solutions available to a developer and JDBC provides a standard way to connect and interface with many of these options.

JDBC allows programmers to operate directly on the database by allowing the language of databases, Structured Query Language (SQL), to be written directly into your Java [files](https://www.codecademy.com/resources/docs/java/files).

All in all, between your application and the database, five layers exist in the JDBC environment:

###### 1. Your Application

- All the logic, user interface, and data contained in your Java files.

###### 2. JDBC API

- This is a set of [classes](https://www.codecademy.com/resources/docs/java/classes) and supporting files that provide the framework for the connection to a database.

###### 3. JDBC Driver Manager

- The JDBC driver manager, normally referenced by importing and calling the class `DriverManager` class acts as the interface between you the programmer, and the actual drivers for the database.

###### 4. JDBC Drivers

- This is the specific code that translates the commands sent via the JDBC into the language and syntax that the designated database works with. Most database applications, MySQL, SQLite, and Postgres for example, each provide JDBC drivers that can be downloaded from their websites.

###### 5. Databases

- These are the data storage objects used to persist data throughout your application.

### JDBC Drivers
The first layer we will set to tackle is the bottom-most, the JDBC Drivers. These are third-party [files](https://www.codecademy.com/resources/docs/java/files) that allow a specific database to extend JDBC [classes](https://www.codecademy.com/resources/docs/java/classes) and [interfaces](https://www.codecademy.com/resources/docs/java/interfaces) so that they work with that database. While SQL is the industry standard for relational database communication, its implementation is not standardized across all databases. Some databases only support certain SQL statements, some format their SQL differently, and some still may rely on SQL and some other programming language to implement their features. This variation among database providers means that each database product will have its own drivers, similar to each printer manufacturer having its own drivers. JDBC drivers are typically maintained in a repository service like [Maven](https://mvnrepository.com/open-source).

Once downloaded, the driver needs to be added to the [classpath](https://docs.oracle.com/javase/tutorial/essential/environment/paths.html) of your program. The classpath is the location where the JVM looks for `.class` files for your application when the program is run. Many IDEs have a process to do this automatically, but we will stick to adding the classpath variable through the command line interface manually.

We’ll also be using SQLite and the [SQLite JDBC Driver](https://mvnrepository.com/artifact/org.xerial/sqlite-jdbc) as our backend database. Once it is downloaded, the next step is to register the driver with the `DriverManager` class. This class is responsible for managing all the connected JDBC drivers and ensuring the necessary files are available for a successful connection. Since the 2006 release of JDBC 4.0, any driver that is placed as a classpath variable is automatically registered but since we are adding the classpath manually, it will be good practice to run through the steps to verify the driver was loaded properly. We do this by checking to see if the class exists in the program build (this occurs at runtime, not compile time) using the `Class.forName("Class Name")` method.

In the IDE on the right, you will see that we have already uploaded a copy of the latest SQLite driver (the `.jar` file) and have created a `project` folder that contains the file **ConnectionTest.java**.
 
---

Why does this “register” the driver? When you make a call to the `.forName()` method it actually returns an instance of the class, causing it to be initialized. We can technically write the syntax like this and make calls to the class using the variable name, we don’t because we don’t have any reason to in this case.

```java
Class driver = Class.forName("org.sqlite.JDBC");
```

Since there is a chance this method doesn’t find the class, it throws a `ClassNotFoundException`, for this reason, wrap the method in a `try-catch` block.

Remember, you will need to pass in the classpath variable through the command line that points to your driver. You also need to point it to your current folder.

```shell
javac ConnectionTest.java

java -classpath .:../sqlite-jdbc-3.36.0.3.jar ConnectionTest
```

Let’s look at the syntax here, it starts with a call to the JVM with `java`, then we add the `-classpath` variables which tell our program where to look for all the class files that will be used in the program. We separate the locations with a colon, `:`, `.` represents the current folder you are in, which is where the `ConnectionTest` class lives. The driver lives in the folder above the `project` folder and just like when using the CLI to navigate the file system, we use two periods to go up a folder, `../`, followed by the name of the `.jar` that the driver lives in. After the `-classpath` variables are entered, we point the JVM to the location of the class that contains the `main()` method, in this case, `ConnectionTest`.

```java
public class ConnectionTest {
  public static void main(String[] args) {
    try {
      Class.forName("org.sqlite.JDBC"); 
      System.out.println("The driver was successfully loaded.");
    } catch(ClassNotFoundException e) {
      System.out.println("The driver class was not found in the program files at runtime.");
      e.printStackTrace();
      System.exit(1);
    }
  }
}
```

### Design Principles: MVVM
For this project, we are going to follow the MVVM, or Model-View-ViewModel, architecture. Essentially we are going to organize all of our objects (called models) into one package, our views (the user interface) into another package, and the ViewModels (the business logic that interacts with models, UI, and services) into another. We will also have a separate package for our data access [classes](https://www.codecademy.com/resources/docs/java/classes), called `services`, where our data access object (the class that accesses the database) lives.

Let’s review our project environment:

- `project` -top level package
    - `models` - holds object representations (customers)
    - `views` - holds user interface [files](https://www.codecademy.com/resources/docs/java/files) (we don’t have UI yet)
    - `viewmodels` - holds business logic that uses models and interacts with other parts of the program such as UI and external resources
    - `services` - provides the `viewmodels` with a mode of communicating with external resources

```java
package models;

public class Customer {
  public Integer ID;
  public String firstName;
  public String lastName;
  public String email;
  public String cellNumber;

  public Customer(Integer ID, String firstName, String lastName, String email, String cellNumber) {
    this.ID = ID;
    this.firstName = firstName;
    this.lastName = lastName;
    this.email = email;
    this.cellNumber = cellNumber;
  }
}
```

--- 

```shell
javac $(find . -name '*.java')
```

### Establishing a Connection
The default setup of a SQLite database requires no username and password, therefore to connect to the database all we need to do is point the Java program in the right direction. To get our program to connect to a database we need to start using [classes](https://www.codecademy.com/resources/docs/java/classes) from the JDBC API, specifically the `DriverManager` and `Connection` classes.

The [`DriverManager`](https://docs.oracle.com/javase/8/docs/api/java/sql/DriverManager.html) class is the basic service used to load and manage specific JDBC drivers and to reach out to the database to obtain an initial connection.

The [`Connection`](https://docs.oracle.com/javase/8/docs/api/java/sql/Connection.html) interface manages a session with a specific database. All SQL statements and results are returned and handled within the context of a single connection. Along with managing SQL execution, a `Connection` can also provide database schema information such as overall design and specific table layouts.

The `DriverManager` has a static method that attempts to establish the initial connection and return the connection back to the user in the form of a `Connection` object. The `.getConnection()` method can either accept simply a database location such as our SQLite database, or a location, username, and password to access more secure databases. Database connections are costly to both local memory and network bandwidth and it is very important to close this resource as soon as you are finished with it.

Database locations, typically in the form of a URL, follow a generic pattern, especially when using a JDBC connection. For example, the address for our SQLite database is: `jdbc:sqlite:mysteryBusiness.db`.

- The first part refers to the type of service used to connect to the database, in our case `jdbc`.
- The second part is the type or vendor of the database. We are using `sqlite` but if you are using a MySQL database it would be `mysql` or on a Microsoft SQL Server it would be `sqlserver`.
- The last part is the path to the database and any extra parameters such as usernames and passwords. Once again, our SQLite database is fairly barebones and requires only the location in the file system of the database.

Connections are also subject to failure, which can lead to other [errors](https://www.codecademy.com/resources/docs/java/errors) in our program. For this reason, a failed connection will throw a `SQLException` and needs to be wrapped in a `try-catch-finally` block or a `try-with-resources` block, the latter being preferred because it automatically closes any open resources.

```java
try (put resources you want to open here) {
  // Do something with the resources here
} catch (exceptions here) {
  // Do something when the try block fails, typically alert the user
}
```

**Note:** _SQLite will create a database with the database name you give it if you request to open a database that doesn’t exist. This can make it appear like you are connected to the proper database even though you are not. Using a username/password will help eliminate this problem, as well as double-checking your code._

---

Make it `final` as well, that way we can’t accidentally change the database in our logic.

As always, we will follow best practices, which means while it may not be necessary to put method and/or variable modifiers in a specific order, convention follows the order:

```
@Annotation [public | protected | private] abstract [transient | volatile] static final synchronized native strictfp
```

### Creating a Statement Manager
Now that we have connected to the database, it is time to begin communicating with it.

JDBC provides a very straightforward class to take care of executing static SQL queries, the `Statement` interface. A `Statement` is generated from a call to the `Connection` method, `.createStatement()`.

```java
Connection connection = DriverManager.getConnection(url);
Statement statement = connection.createStatement();
```

Once a `Statement` object is created it can be used to execute SQL queries and return a `ResultSet` object, which is essentially a Java representation of a table from the database. The `ResultSet` can then be used in the logic of your program.

These `Statement` objects, just like `Connection` objects, also need to be closed when you are finished using them and are best included inside the same `try-with-resources` block that a `Connection` is opened in.

There is also an extension of `Statement` called `PreparedStatement` that is used to execute a precompiled SQL statement multiple times and with greater efficiency. As your program interacts more and more with the database you may find that a `PreparedStatement` might improve your performance.

---

Inside the resources you are opening in the `try-with-resources` block you can add multiple items to open. Each standard line of code is separated by a `;` like normal, except the last item, the semicolon is redundant there as the trailing parenthesis signifies the end of the block.

```java
try (
  // Multiple Resources in the same 'resources' block
  FileReader fr = new FileReader("someFile.txt");
  BufferedReader br = new BufferedReader(fr)
) {
  // Do something with the BufferedReader (ie. read the file)
} catch (Exception e) {
  System.out.println(e);
}
```

### Executing SQL Through JDBC
Now that we have firmly established a connection with our database and successfully created a statement manager, it is time to begin blending SQL into our program.

As a reminder, SQL is the language of relational databases. The term “relation” is just a fancy word for a table and how the data across multiple tables can be related to each other. All data in a relational database is stored inside these tables, broken down into columns and rows.

In SQL, we use the command “CREATE TABLE” followed by the table name and then the column names and [data types](https://www.codecademy.com/resources/docs/java/data-types).

### Storing a Customer List
Creating databases and tables is all good and well but our core functionality is actually turning our Java data into data that we can store in our tables and then retrieving it back out of the database at a later [date](https://www.codecademy.com/resources/docs/java/date).

This is done with the SQL `INSERT INTO` statement. We `INSERT` a set of values, in the same order as the columns of our table, `INTO` our table. We will continue to use the `Statement` interface to implement this SQL command, although we challenge you to browse the [PreparedStatement Documentation](https://docs.oracle.com/javase/tutorial/jdbc/basics/prepared.html) to see how you can implement a more efficient solution on your own.

Let’s take a look at a sample insert statement in SQLite:

```sqlite
INSERT INTO CUSTOMERS
  VALUES (1010, "Jack", "Delangey", "jack@mysterybusiness.com", "555-867-5309");
```

We don’t want to hardcode values into our SQL expression like the example above though, we want our `CustomerDaoService` to contain the logic to substitute each of these values for the properties of our `Customer` class. The whole command will be concatenated together into a String that we can execute on our database using our `Statement` object.

---

You may have noticed that the first variable, `customer.ID` is wrapped in the SQL function `CAST()`, which will convert it from the String format back to an `INTEGER` in the database.

You will notice we have added a helper method to the `CustomerDaoService` class, `.resetDatabase()`. This helper method deletes the `CUSTOMER` table so that you can start with a fresh table each time, helping eliminate some errors as we run these setup methods over and over again.

### Operating on a ResultSet
Everything we’ve done so far has revolved around pushing data to our database, an important skill, but only half of the story.

In JDBC, the data that is sent back to the Java application from a database comes in the form of a `ResultSet` and is returned by a query on the database from a `Statement` object. This `ResultSet` object, just like `Connection` and `Statement` needs to be closed when finished, meaning it belongs with the other resources in our `try-with-resources` block.

A `ResultSet` object is a [collection](https://www.codecademy.com/resources/docs/java/collection) of rows and columns that represent a table from the database. There is a “cursor” that points to the current row, from which we can access columns by the column’s index (which, unlike other Java data structures, begins with index 1).

```java
Statement statement = connection.createStatement();
ResultSet results = statement.executeQuery("SQL QUERY");
```

You may have noticed in the code example that we are now calling the `.executeQuery()` method instead of the `.executeUpdate()` method, the difference being that a query returns a `ResultSet`.

Once we have injected the SQL into the database and received the result as a `ResultSet`, we can use regular ol’ Java code to work through the results and present them to the user.

---

The `.next()` method of the `ResultSet` class moves the current row cursor down by one each time, returning a boolean if the row it moved to exists or not. The nice thing about `.next()` is that it begins with the cursor pointing `before the first row` so that its first call with move the cursor to the first row in the `ResultSet`. The query you executed may not have returned any rows of data, so this technique is very useful when moving through a data set of unknown size.

The `.getString(int columnIndex)` method takes a column index and converts the value in the column to a String object for use in Java.

### Creating a Customer from a ResultSet
A `ResultSet` is all good and dandy, but what we really need back into our program is `Customer` objects! In the previous exercise, we used the `.getString()` method to pull data from a column and convert it to a string for use in printing. The `ResultSet` class has a wide range of other `get` [methods](https://www.codecademy.com/resources/docs/java/methods) that will return nearly any data from a column if of course that data type can be converted to the requested type.

Our `Customer` class stores its `ID` as an integer and the rest of the properties are [strings](https://www.codecademy.com/resources/docs/java/strings), making our implementation fairly easy so, we’ll stick to just two methods: `.getInt()` and `.getString()`. Here are some of the other options available:

- `.getBoolean()`
- `.getArray()`
- [`.getTime()`](https://www.codecademy.com/resources/docs/java/calendar/getTime)
- `.getDouble()`
- `.getBlob()`

There is a generic `.getObject()` method as well that returns the default Java object type corresponding to the column’s SQL type, following the mapping for built-in types specified in the JDBC specification.

### Review
- The five-layered structure of JDBC implementation
- Downloading third-party JDBC drivers
- Specifying multiple classpaths for our program to include at runtime
- Building code in line with a design principle: MVVM and Data Access Objects
- Verifying and Registering JDBC drivers with the `DriverManager`
- Establishing a `Connection` to a database and managing the opening and closing of resources in a responsible way
- Creating a `Statement` in JDBC to manage our SQL injections to the database
- Converting Java [data types](https://www.codecademy.com/resources/docs/java/data-types) to SQL and vice versa in order to save objects to a database and then retrieve them out of the same database
- Creating a `ResultSet` from a SQL query and how to iterate through the rows and columns of the `ResultSet`


```java
package models;

public class Customer {
  public Integer ID;
  public String firstName;
  public String lastName;
  public String email;
  public String cellNumber;

  public Customer(Integer ID, String firstName, String lastName, String email, String cellNumber) {
    this.ID = ID;
    this.firstName = firstName;
    this.lastName = lastName;
    this.email = email;
    this.cellNumber = cellNumber;
  }

  @Override
  public String toString() {
    return "Customer {" +
      "ID = " + ID +
      ", firstName = '" + firstName + '\'' +
      ", lastName = '" + lastName + '\'' +
      ", email = '" + email + '\'' +
      ", cellNumber = '" + cellNumber + '\'' +
      '}';
  }
}
```

```java
package services;

import models.Customer;

import java.sql.*;
import java.util.ArrayList;
import java.util.List;

public class CustomerDaoService {
  private static final String url = "jdbc:sqlite:resources/MYSTERY_BUSINESS.db";

  /*
  Method to test the drivers are found in the classpath
   */
  public static void loadDriver() {
    try {
      Class.forName("org.sqlite.JDBC");
      System.out.println("The driver was successfully loaded.");
      Thread.sleep(1000);
    } catch (ClassNotFoundException | InterruptedException e) {
      System.out.println("The driver class was not found in the program files at runtime.");
      System.out.println(e);
      System.exit(1);
    }
  }

  /*
  Method to test the connection to the database
   */
  public static void testDatabaseConnection() {
    try (Connection connection = DriverManager.getConnection(url)) {
      System.out.println("The connection to the SQLite database was successful!");
      Thread.sleep(1000);
    } catch (SQLException | InterruptedException e) {
      System.out.println("The connection to the database was unsuccessful!");
      System.out.println(e);
    }
  }

  /*
  Method to reset the database
   */
  public static void resetDatabase() {
    try (
      Connection connection = DriverManager.getConnection(url);
      Statement statement = connection.createStatement();
    ) {
      statement.executeUpdate("DROP TABLE CUSTOMERS");
      System.out.println("The database has been reset!!");
      Thread.sleep(1000);
    } catch (SQLException | InterruptedException e) {
      System.out.println("The database was not reset.");
      System.out.println(e);
    }
  }

  /*
  Method to create the CUSTOMER table in the database
   */
  public static void createTable() {
    String createTableStatement = "CREATE TABLE CUSTOMERS ("
      + "CUST_ID INTEGER PRIMARY KEY,"
      + "CUST_F_NAME TEXT NOT NULL,"
      + "CUST_L_NAME TEXT NOT NULL,"
      + "CUST_EMAIL TEXT NOT NULL,"
      + "CUST_CELL_NUM TEXT NOT NULL"
      + ");";

    try (
      Connection connection = DriverManager.getConnection(url);
      Statement statement = connection.createStatement();
    ) {
      statement.executeUpdate(createTableStatement);
      System.out.println("The CUSTOMER table has been created.");
      Thread.sleep(1000);
    } catch (SQLException | InterruptedException e) {
      System.out.println("There was an error with your request.");
      System.out.println(e);
    }
  }

  /*
  Method to save a list of customers to the CUSTOMER table
   */
  public static void saveCustomers(List<Customer> customers) {
    try (
      Connection connection = DriverManager.getConnection(url);
      Statement statement = connection.createStatement();
    ) {
      for (Customer customer : customers) {
        String insertIntoCustomer = "INSERT INTO CUSTOMERS VALUES ("
          + "CAST('" + customer.ID + "' AS INTEGER),\""
          + customer.firstName + "\",\""
          + customer.lastName + "\",\""
          + customer.email + "\",\""
          + customer.cellNumber
          + "\");";
        statement.executeUpdate(insertIntoCustomer);
      }
      System.out.println("The customers have been saved to the CUSTOMER table.");
      Thread.sleep(1000);
    } catch (SQLException | InterruptedException e) {
      System.out.println("There was an error with your request.");
      System.out.println(e);
    }
  }

  /*
  Method to load all customers from the CUSTOMER table
   */
  public static List<Customer> loadAllCustomers() {
    List<Customer> allCustomers = new ArrayList<>();
    System.out.println("Trying to load all customers from the database...\n");

    try (
      Connection connection = DriverManager.getConnection(url);
      Statement statement = connection.createStatement();
      ResultSet results = statement.executeQuery("SELECT * FROM CUSTOMERS;")
    ) {
      Thread.sleep(1000);
      while (results.next()) {
        // Save customer variables here:
        int ID = results.getInt(1);
        String firstName = results.getString(2);
        String lastName = results.getString(3);
        String email = results.getString(4);
        String cellNumber = results.getString(5);

        // Add a new customer to allCustomers here:
        allCustomers.add(new Customer(ID, firstName, lastName, email, cellNumber));
      }
      System.out.println("All customers were loaded from the database.");
    } catch (SQLException | InterruptedException e) {
      System.out.println("There was an error with your request.");
      System.out.println(e);
    }

    return allCustomers;
  }
}
```

```java
package viewmodels;

import services.CustomerDaoService;
import models.Customer;

import java.util.ArrayList;
import java.util.List;

public class BusinessLogic {
  static List<Customer> customerList = new ArrayList<>();

  public static void main(String[] args) throws InterruptedException {

    BusinessLogic mysteryBusiness = new BusinessLogic();
    // Do a bunch of business things for your business
    mysteryBusiness.addCustomer(new Customer(1001, "Keir", "Whitehouse", "k.whitehouse@mysterybusiness.com", "555-555-5000"));
    mysteryBusiness.addCustomer(new Customer(1002, "Anna", "Jenkins", "a.jenkins@mysterybusiness.com", "555-555-5001"));
    mysteryBusiness.addCustomer(new Customer(1003, "Evan", "Huang", "e.huang@mysterybusiness.com", "555-555-5002"));
    mysteryBusiness.addCustomer(new Customer(1004, "Yasser", "Salter", "y.salter@mysterybusiness.com", "555-555-5003"));
    mysteryBusiness.addCustomer(new Customer(1005, "Dawson", "Rangel", "d.rangel@mysterybusiness.com", "555-555-5004"));
    CustomerDaoService.resetDatabase();
    CustomerDaoService.createTable();
    CustomerDaoService.saveCustomers(customerList);

    System.out.println("Clearing out the 'customerList' variable now that all entries have been saved to the database.");
    Thread.sleep(1500);
    customerList.clear();
    System.out.println("There are currently " + customerList.size() + " elements in the 'customerList'.");

    System.out.println("Loading all customers from the database back into the 'customerList':");
    customerList = CustomerDaoService.loadAllCustomers();
    Thread.sleep(1000);
    customerList.forEach(System.out::println);
  }

  public void addCustomer(Customer customer) {
    customerList.add(customer);
  }
}
```