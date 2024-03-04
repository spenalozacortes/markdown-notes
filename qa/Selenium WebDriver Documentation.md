# Getting started
WebDriver is an API and protocol that defines a language-neutral interface for controlling the behavior of web browsers. Each browser is backed by a specific WebDriver implementation, called a *driver*. The driver is the component responsible for delegating down to the browser, and handles communication to and from Selenium and the browser.

## First script

### Eight basic components
Everything Selenium does is send the browser commands to do something or send requests for information. 

#### 1. Start the session

```java
WebDriver driver = new ChromeDriver();
```

#### 2. Take action on browser
In this example we are navigating to a web page.

```java
driver.get("https://www.selenium.dev/selenium/web/web-form.html");
```

#### 3. Request browser information
There are a bunch of types of [information about the browser](https://www.selenium.dev/documentation/webdriver/interactions/) you can request, including window handles, browser size / position, cookies, alerts, etc.

```java
driver.getTitle();
```

#### 4. Establishing waiting strategy
Essentially you want to make sure that the element is on the page before you attempt to locate it and the element is in an interactable state before you attempt to interact with it.

An implicit wait is rarely the best solution.

```java
driver.manage().timeouts().implicitlyWait(Duration.ofMillis(500));
```

#### 5. Find an element
The majority of commands in most Selenium sessions are element based, and you can't interact with one without first finding an element.

```java
WebElement textBox = driver.findElement(By.name("my-text"));
WebElement submitButton = driver.findElement(By.cssSelector("button"));
```

#### 6. Take action on element

```java
textBox.sendKeys("Selenium");
submitButton.click();
```

#### 7. Request element information

```java
message.getText();
```

#### 8. End the session
This ends the driver process, which by default closes the browser as well. No more commands can be sent to this driver instance.

```java
driver.quit();
```

```java
package dev.selenium.getting_started;

import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.WebElement;
import org.openqa.selenium.chrome.ChromeDriver;

import java.time.Duration;

public class FirstScript {
    public static void main(String[] args) {
        WebDriver driver = new ChromeDriver();

        driver.get("https://www.selenium.dev/selenium/web/web-form.html");

        driver.getTitle();

        driver.manage().timeouts().implicitlyWait(Duration.ofMillis(500));

        WebElement textBox = driver.findElement(By.name("my-text"));
        WebElement submitButton = driver.findElement(By.cssSelector("button"));

        textBox.sendKeys("Selenium");
        submitButton.click();

        WebElement message = driver.findElement(By.id("message"));
        message.getText();

        driver.quit();
    }
}
```

## Using Selenium

### Test Runner 
Being able to use before/after hooks and run things in groups or in parallel can be very useful. Here’s an example of that code using a test runner:

```java
package dev.selenium.getting_started;

import org.junit.jupiter.api.Test;
import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.WebElement;
import org.openqa.selenium.chrome.ChromeDriver;

import java.time.Duration;

import static org.junit.jupiter.api.Assertions.assertEquals;

public class UsingSeleniumTest {

    @Test
    public void eightComponents() {
        WebDriver driver = new ChromeDriver();
        driver.get("https://www.selenium.dev/selenium/web/web-form.html");

        String title = driver.getTitle();
        assertEquals("Web form", title);

        driver.manage().timeouts().implicitlyWait(Duration.ofMillis(500));

        WebElement textBox = driver.findElement(By.name("my-text"));
        WebElement submitButton = driver.findElement(By.cssSelector("button"));

        textBox.sendKeys("Selenium");
        submitButton.click();

        WebElement message = driver.findElement(By.id("message"));
        String value = message.getText();
        assertEquals("Received!", value);

        driver.quit();
    }

}

```

# Drivers

## Driver sessions
Starting and stopping a session is for opening and closing a browser.

### Creating sessions
The session is created automatically by initializing a new Driver class object.

Each language allows a session to be created with arguments from one of these classes (or equivalent):

- **Options** to describe the kind of session you want; default values are used for local, but this is required for remote.
- Some of the **HTTP Client configuration**.
- **Listeners**.

### Quitting sessions
Important note: the `quit` method is different from the `close` method, and it is recommended to always use `quit` to end the session.

## Browser Options
These capabilities are shared by all browsers.

### browserName
Browser name is set by default when using an Options class instance.

### browserVersion
This capability is optional, this is used to set the available browser version at remote end. In recent versions of Selenium, if the version is not found on the system, it will be automatically downloaded by Selenium Manager.

### pageLoadStrategy
Three types of page load strategies are available.

|Strategy|Ready State|Notes|
|---|---|---|
|normal|complete|Used by default, waits for all resources to download|
|eager|interactive|DOM access is ready, but other resources like images may still be loading|
|none|Any|Does not block WebDriver at all|

The `document.readyState` property of a document describes the loading state of the current document.

When navigating to a new page via URL, by default, WebDriver will hold off on completing a navigation method (e.g., driver.navigate().get()) until the document ready state is complete. This _does not necessarily mean that the page has finished loading_, especially for sites like Single Page Applications that use JavaScript to dynamically load content after the Ready State returns complete. Note also that this behavior does not apply to navigation that is a result of clicking an element or submitting a form.

If a page takes a long time to load as a result of downloading assets (e.g., images, css, js) that aren’t important to the automation, you can change from the default parameter of `normal` to `eager` or `none` to speed up the session. This value applies to the entire session, so make sure that your [waiting strategy](https://www.selenium.dev/documentation/webdriver/waits/) is sufficient to minimize flakiness.

#### normal (default)
WebDriver waits until the [load](https://developer.mozilla.org/en-US/docs/Web/API/Window/load_event) event fire is returned.

```java
import org.openqa.selenium.PageLoadStrategy;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.chrome.ChromeOptions;
import org.openqa.selenium.chrome.ChromeDriver;

public class pageLoadStrategy {
  public static void main(String[] args) {
    ChromeOptions chromeOptions = new ChromeOptions();
    chromeOptions.setPageLoadStrategy(PageLoadStrategy.NORMAL);
    WebDriver driver = new ChromeDriver(chromeOptions);
    try {
      // Navigate to Url
      driver.get("https://google.com");
    } finally {
      driver.quit();
    }
  }
}
```

#### eager
WebDriver waits until [DOMContentLoaded](https://developer.mozilla.org/en-US/docs/Web/API/Document/DOMContentLoaded_event) event fire is returned.

```java
import org.openqa.selenium.PageLoadStrategy;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.chrome.ChromeOptions;
import org.openqa.selenium.chrome.ChromeDriver;

public class pageLoadStrategy {
  public static void main(String[] args) {
    ChromeOptions chromeOptions = new ChromeOptions();
    chromeOptions.setPageLoadStrategy(PageLoadStrategy.EAGER);
    WebDriver driver = new ChromeDriver(chromeOptions);
    try {
      // Navigate to Url
      driver.get("https://google.com");
    } finally {
      driver.quit();
    }
  }
}
```

#### none
WebDriver only waits until the initial page is downloaded.

```java
import org.openqa.selenium.PageLoadStrategy;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.chrome.ChromeOptions;
import org.openqa.selenium.chrome.ChromeDriver;

public class pageLoadStrategy {
  public static void main(String[] args) {
    ChromeOptions chromeOptions = new ChromeOptions();
    chromeOptions.setPageLoadStrategy(PageLoadStrategy.NONE);
    WebDriver driver = new ChromeDriver(chromeOptions);
    try {
      // Navigate to Url
      driver.get("https://google.com");
    } finally {
      driver.quit();
    }
  }
}
```

#### platformName
This identifies the operating system at the remote-end, fetching the `platformName` returns the OS name.

In cloud-based providers, setting `platformName` sets the OS at the remote-end.

#### acceptInsecureCerts
This capability checks whether an expired (or) invalid `TLS Certificate` is used while navigating during a session.

If the capability is set to `false`, an [insecure certificate error](https://developer.mozilla.org/en-US/docs/Web/WebDriver/Errors/InsecureCertificate) will be returned as navigation encounters any domain certificate problems. If set to `true`, invalid certificate will be trusted by the browser.

All self-signed certificates will be trusted by this capability by default. Once set, `acceptInsecureCerts` capability will have an effect for the entire session.

#### timeouts
A WebDriver `session` is imposed with a certain `session timeout` interval, during which the user can control the behaviour of executing scripts or retrieving information from the browser.

Each session timeout is configured with combination of different `timeouts` as described below:

##### Script Timeout
Specifies when to interrupt an executing script in a current browsing context. The default timeout **30,000** is imposed when a new session is created by WebDriver.

##### Page Load Timeout
Specifies the time interval in which web page needs to be loaded in a current browsing context. The default timeout **300,000** is imposed when a new session is created by WebDriver. If page load limits a given/default time frame, the script will be stopped by _TimeoutException_.

##### Implicit Wait Timeout
This specifies the time to wait for the implicit element location strategy when locating elements. The default timeout **0** is imposed when a new session is created by WebDriver.

#### unhandledPromptBehavior
Specifies the state of current session’s `user prompt handler`. Defaults to **dismiss and notify state**

##### User Prompt Handler
This defines what action must take when a user prompt encounters at the remote-end. This is defined by `unhandledPromptBehavior` capability and has the following states:

- dismiss
- accept
- dismiss and notify
- accept and notify
- ignore

#### setWindowRect
Indicates whether the remote end supports all of the [resizing and repositioning](https://w3c.github.io/webdriver/#resizing-and-positioning-windows) [commands](https://w3c.github.io/webdriver/#dfn-commands).

#### strictFileInteractability
This new capability indicates if strict interactability checks should be applied to _input type=file_ elements. As strict interactability checks are off by default, there is a change in behaviour when using _Element Send Keys_ with hidden file upload controls.

#### proxy
A proxy server acts as an intermediary for requests between a client and a server. In simple terms, the traffic flows through the proxy server on its way to the address you requested and back.

A proxy server for automation scripts with Selenium could be helpful for:

- Capture network traffic
- Mock backend calls made by the website
- Access the required website under complex network topologies or strict corporate restrictions/policies.

If you are in a corporate environment, and a browser fails to connect to a URL, this is most likely because the environment needs a proxy to be accessed.

Selenium WebDriver provides a way to proxy settings:

```java
import org.openqa.selenium.Proxy;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.chrome.ChromeDriver;
import org.openqa.selenium.chrome.ChromeOptions;

public class ProxyTest {
  public static void main(String[] args) {
    Proxy proxy = new Proxy();
    proxy.setHttpProxy("<HOST:PORT>");
    ChromeOptions options = new ChromeOptions();
    options.setCapability("proxy", proxy);
    WebDriver driver = new ChromeDriver(options);
    driver.get("https://www.google.com/");
    driver.manage().window().maximize();
    driver.quit();
  }
}
```

# Waits

## Waiting strategies
All navigation commands wait for a specific `readyState` value based on the [page load strategy](https://www.selenium.dev/documentation/webdriver/drivers/options/#pageloadstrategy) (the default value to wait for is `"complete"`) before the driver returns control to the code. The `readyState` only concerns itself with loading assets defined in the HTML, but loaded JavaScript assets often result in changes to the site, and elements that need to be interacted with may not yet be on the page when the code is ready to execute the next Selenium command.

Similarly, in a lot of single page applications, elements get dynamically added to a page or change visibility based on a click. An element must be both present and [displayed](https://www.selenium.dev/documentation/webdriver/elements/information/#is-displayed) on the page in order for Selenium to interact with it.

The first solution many people turn to is adding a sleep statement to pause the code execution for a set period of time. Because the code can’t know exactly how long it needs to wait, this can fail when it doesn’t sleep long enough. Alternately, if the value is set too high and a sleep statement is added in every place it is needed, the duration of the session can become prohibitive.

Selenium provides two different mechanisms for synchronization that are better.

### Implicit waits
Selenium has a built-in way to automatically wait for elements called an _implicit wait_. An implicit wait value can be set either with the [timeouts](https://www.selenium.dev/documentation/webdriver/drivers/options/#timeouts) capability in the browser options, or with a driver method (as shown below).

This is a global setting that applies to every element location call for the entire session. The default value is `0`, which means that if the element is not found, it will immediately return an error. If an implicit wait is set, the driver will wait for the duration of the provided value before returning the error. Note that as soon as the element is located, the driver will return the element reference and the code will continue executing, so a larger implicit wait value won’t necessarily increase the duration of the session.

_Warning:_ Do not mix implicit and explicit waits. Doing so can cause unpredictable wait times. For example, setting an implicit wait of 10 seconds and an explicit wait of 15 seconds could cause a timeout to occur after 20 seconds.

```java
driver.manage().timeouts().implicitlyWait(Duration.ofSeconds(2));
driver.get("https://www.selenium.dev/selenium/web/dynamic.html");
driver.findElement(By.id("adder")).click();

WebElement added = driver.findElement(By.id("box0"));
```

### Explicit waits
_Explicit waits_ are loops added to the code that poll the application for a specific condition to evaluate as true before it exits the loop and continues to the next command in the code. If the condition is not met before a designated timeout value, the code will give a timeout error. Since there are many ways for the application not to be in the desired state, so explicit waits are a great choice to specify the exact condition to wait for in each place it is needed. Another nice feature is that, by default, the Selenium Wait class automatically waits for the designated element to exist.

This example shows the condition being waited for as a _lambda_. Java also supports [Expected Conditions](https://www.selenium.dev/documentation/webdriver/support_features/expected_conditions/)

```java
WebElement revealed = driver.findElement(By.id("revealed"));
Wait<WebDriver> wait = new WebDriverWait(driver, Duration.ofSeconds(2));

driver.findElement(By.id("reveal")).click();
wait.until(d -> revealed.isDisplayed());

revealed.sendKeys("Displayed");
```

### Customization
The Wait class can be instantiated with various parameters that will change how the conditions are evaluated.

This can include:

- Changing how often the code is evaluated (polling interval)
- Specifying which exceptions should be handled automatically
- Changing the total timeout length
- Customizing the timeout message

For instance, if the _element not interactable_ error is retried by default, then we can add an action on a method inside the code getting executed (we just need to make sure that the code returns `true` when it is successful).

The easiest way to customize Waits in Java is to use the `FluentWait` class:

```java
WebElement revealed = driver.findElement(By.id("revealed"));
Wait<WebDriver> wait = new FluentWait<>(driver)
    .withTimeout(Duration.ofSeconds(2))
    .pollingEvery(Duration.ofMillis(300))
    .ignoring(ElementNotInteractableException.class);

driver.findElement(By.id("reveal")).click();
wait.until(d -> {
    revealed.sendKeys("Displayed");
    return true;
});
```

# Elements

## File upload
The file upload dialog could be handled using Selenium, when the input element is of type file. 

```java
package dev.selenium.elements;

import org.junit.jupiter.api.Test;
import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.WebElement;
import org.openqa.selenium.chrome.ChromeDriver;
import java.time.Duration;

import java.io.File;
import java.nio.file.Path;
import java.nio.file.Paths;

public class FileUploadTest {

    @Test
    public void fileUploadTest() {
    WebDriver driver = new ChromeDriver();
    driver.manage().timeouts().implicitlyWait(Duration.ofMillis(1000));
    driver.get("https://the-internet.herokuapp.com/upload");
    Path path = Paths.get("src/test/resources/selenium-snapshot.png");
    File imagePath = new File(path.toUri());

    //we want to import selenium-snapshot file.
    driver.findElement(By.id("file-upload")).sendKeys(imagePath.toString());
    driver.findElement(By.id("file-submit")).submit();
   if(driver.getPageSource().contains("File Uploaded!")) {
	System.out.println("file uploaded");
   }
   else{
        System.out.println("file not uploaded");
       }
    driver.quit();
    }
}
```

## Locators
A locator is a way to identify elements on a page. It is the argument passed to the [Finding element](https://www.selenium.dev/documentation/webdriver/elements/finders/) methods.

### Traditional Locators

|Locator|Description|
|---|---|
|class name|Locates elements whose class name contains the search value (compound class names are not permitted)|
|css selector|Locates elements matching a CSS selector|
|id|Locates elements whose ID attribute matches the search value|
|name|Locates elements whose NAME attribute matches the search value|
|link text|Locates anchor elements whose visible text matches the search value|
|partial link text|Locates anchor elements whose visible text contains the search value. If multiple elements are matching, only the first one will be selected.|
|tag name|Locates elements whose tag name matches the search value|
|xpath|Locates elements matching an XPath expression|

### Creating Locators
To work on a web element using Selenium, we need to first locate it on the web page.

```html
<html>
<body>
<style>
.information {
  background-color: white;
  color: black;
  padding: 10px;
}
</style>
<h2>Contact Selenium</h2>

<form action="/action_page.php">
  <input type="radio" name="gender" value="m" />Male &nbsp;
  <input type="radio" name="gender" value="f" />Female <br>
  <br>
  <label for="fname">First name:</label><br>
  <input class="information" type="text" id="fname" name="fname" value="Jane"><br><br>
  <label for="lname">Last name:</label><br>
  <input class="information" type="text" id="lname" name="lname" value="Doe"><br><br>
  <label for="newsletter">Newsletter:</label>
  <input type="checkbox" name="newsletter" value="1" /><br><br>
  <input type="submit" value="Submit">
</form> 

<p>To know more about Selenium, visit the official page 
<a href ="www.selenium.dev">Selenium Official Page</a> 
</p>

</body>
</html>
```

#### class name
The HTML page web element can have attribute class. We can identify these elements using the class name locator available in Selenium.

```java
driver.findElement(By.className("information"));
```

#### css selector
CSS is the language used to style HTML pages. We can use css selector locator strategy to identify the element on the page. If the element has an id, we create the locator as `css = #id`. Otherwise the format we follow is `css =[attribute=value]`.

```java
driver.findElement(By.cssSelector("#fname"));
```

#### id
We can use the ID attribute of an element in a web page to locate it. Generally the ID property should be unique for each element on the web page.

```java
driver.findElement(By.id("lname"));
```

#### name
We can use the NAME attribute of an element in a web page to locate it. Generally the NAME property should be unique for each element on the web page.

```java
driver.findElement(By.name("newsletter"));
```

#### link text
If the element we want to locate is a link, we can use the link text locator to identify it on the web page. The link text is the text displayed of the link.

```java
driver.findElement(By.linkText("Selenium Official Page"));
```

#### partial link text
If the element we want to locate is a link, we can use the partial link text locator to identify it on the web page. The link text is the text displayed of the link. We can pass partial text as value.

```java
driver.findElement(By.partialLinkText("Official Page"));
```

#### tag name
We can use the HTML TAG itself as a locator to identify the web element on the page.

```java
driver.findElement(By.tagName("a"));
```

#### xpath
A HTML document can be considered as a XML document, and then we can use xpath which will be the path traversed to reach the element of interest to locate the element. The XPath could be absolute xpath, which is created from the root of the document. Example - `/html/form/input[1]`. This will return the male radio button. Or the xpath could be relative. Example- `//input[@name=‘fname’]`. This will return the first name text box.

```java
driver.findElement(By.xpath("//input[@value='f']"));
```

### Relative Locators
**Selenium 4** introduces Relative Locators (previously called _Friendly Locators_). These locators are helpful when it is not easy to construct a locator for the desired element, but easy to describe spatially where the element is in relation to an element that does have an easily constructed locator.

Relative locator methods can take as the argument for the point of origin, either a previously located element reference, or another locator. In these examples we’ll be using locators only, but you could swap the locator in the final method with an element object and it will work the same.

![[Pasted image 20231023130321.png]]

#### Above
If the email text field element is not easily identifiable for some reason, but the password text field element is, we can locate the text field element using the fact that it is an “input” element “above” the password element.

```java
By emailLocator = RelativeLocator.with(By.tagName("input")).above(By.id("password"));
```

#### Below
If the password text field element is not easily identifiable for some reason, but the email text field element is, we can locate the text field element using the fact that it is an “input” element “below” the email element.

```java
By passwordLocator = RelativeLocator.with(By.tagName("input")).below(By.id("email"));
```

#### Left of
If the cancel button is not easily identifiable for some reason, but the submit button element is, we can locate the cancel button element using the fact that it is a “button” element to the “left of” the submit element.

```java
By cancelLocator = RelativeLocator.with(By.tagName("button")).toLeftOf(By.id("submit"));
```

#### Right of
If the submit button is not easily identifiable for some reason, but the cancel button element is, we can locate the submit button element using the fact that it is a “button” element “to the right of” the cancel element.

```java
By submitLocator = RelativeLocator.with(By.tagName("button")).toRightOf(By.id("cancel"));
```

#### Near
If the relative positioning is not obvious, or it varies based on window size, you can use the near method to identify an element that is at most `50px` away from the provided locator. One great use case for this is to work with a form element that doesn’t have an easily constructed locator, but its associated [input label element](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/label) does.

```java
By emailLocator = RelativeLocator.with(By.tagName("input")).near(By.id("lbl-email"));
```

### Chaining relative locators
You can also chain locators if needed. Sometimes the element is most easily identified as being both above/below one element and right/left of another.

```java
By submitLocator = RelativeLocator.with(By.tagName("button")).below(By.id("email")).toRightOf(By.id("cancel"));[]()
```

## Finders

```html
<ol id="vegetables">
 <li class="potatoes">…
 <li class="onions">…
 <li class="tomatoes"><span>Tomato is a Vegetable</span>…
</ol>
<ul id="fruits">
  <li class="bananas">…
  <li class="apples">…
  <li class="tomatoes"><span>Tomato is a Fruit</span>…
</ul>
```

### First matching element
Many locators will match multiple elements on the page. The singular find element method will return a reference to the first element found within a given context.

#### Evaluating entire DOM
When the find element method is called on the driver instance, it returns a reference to the first element in the DOM that matches with the provided locator. This value can be stored and used for future element actions. In our example HTML above, there are two elements that have a class name of “tomatoes” so this method will return the element in the “vegetables” list.

```java
WebElement vegetable = driver.findElement(By.className("tomatoes"));
```

#### Evaluating a subset of the DOM
Rather than finding a unique locator in the entire DOM, it is often useful to narrow the search to the scope of another located element. In the above example there are two elements with a class name of “tomatoes” and it is a little more challenging to get the reference for the second one.

One solution is to locate an element with a unique attribute that is an ancestor of the desired element and not an ancestor of the undesired element, then call find element on that object:

```java
WebElement fruits = driver.findElement(By.id("fruits"));
WebElement fruit = fruits.findElement(By.className("tomatoes"));
```

#### Optimized locator
A nested lookup might not be the most effective location strategy since it requires two separate commands to be issued to the browser.

To improve the performance slightly, we can use either CSS or XPath to find this element in a single command.

```java
WebElement fruit = driver.findElement(By.cssSelector("#fruits .tomatoes"));
```

### All matching elements
There are several use cases for needing to get references to all elements that match a locator, rather than just the first one. The plural find elements methods return a collection of element references. If there are no matches, an empty list is returned. In this case, references to all fruits and vegetable list items will be returned in a collection.

```java
List<WebElement> plants = driver.findElements(By.tagName("li"));
```

#### Get element
Often you get a collection of elements but want to work with a specific element, which means you need to iterate over the collection and identify the one you want.

```java
List<WebElement> elements = driver.findElements(By.tagName("li"));

for (WebElement element : elements) {
    System.out.println("Paragraph text:" + element.getText());
}
```

### Find Elements From Element
It is used to find the list of matching child WebElements within the context of parent element. To achieve this, the parent WebElement is chained with ‘findElements’ to access child elements.

```java
  import org.openqa.selenium.By;
  import org.openqa.selenium.WebDriver;
  import org.openqa.selenium.WebElement;
  import org.openqa.selenium.chrome.ChromeDriver;
  import java.util.List;

  public class findElementsFromElement {
      public static void main(String[] args) {
          WebDriver driver = new ChromeDriver();
          try {
              driver.get("https://example.com");

              // Get element with tag name 'div'
              WebElement element = driver.findElement(By.tagName("div"));

              // Get all the elements available with tag name 'p'
              List<WebElement> elements = element.findElements(By.tagName("p"));
              for (WebElement e : elements) {
                  System.out.println(e.getText());
              }
          } finally {
              driver.quit();
          }
      }
  }
```

### Get Active Element
It is used to track (or) find DOM element which has the focus in the current browsing context.

```java
  import org.openqa.selenium.*;
  import org.openqa.selenium.chrome.ChromeDriver;

  public class activeElementTest {
    public static void main(String[] args) {
      WebDriver driver = new ChromeDriver();
      try {
        driver.get("http://www.google.com");
        driver.findElement(By.cssSelector("[name='q']")).sendKeys("webElement");

        // Get attribute of current active element
        String attr = driver.switchTo().activeElement().getAttribute("title");
        System.out.println(attr);
      } finally {
        driver.quit();
      }
    }
  }
```

## Interactions
There are only 5 basic commands that can be executed on an element:

- [click](https://w3c.github.io/webdriver/#element-click) (applies to any element)
- [send keys](https://w3c.github.io/webdriver/#element-send-keys) (only applies to text fields and content editable elements)
- [clear](https://w3c.github.io/webdriver/#element-send-keys) (only applies to text fields and content editable elements)
- submit (only applies to form elements)
- select (see [Select List Elements](https://www.selenium.dev/documentation/webdriver/support_features/select_lists/))

### Additional validations
These methods are designed to closely emulate a user’s experience, so, unlike the [Actions API](https://www.selenium.dev/documentation/webdriver/actions_api/), it attempts to perform two things before attempting the specified action.

1. If it determines the element is outside the viewport, it [scrolls the element into view](https://w3c.github.io/webdriver/#dfn-scrolls-into-view), specifically it will align the bottom of the element with the bottom of the viewport.
2. It ensures the element is [interactable](https://w3c.github.io/webdriver/#interactability) before taking the action. This could mean that the scrolling was unsuccessful, or that the element is not otherwise displayed. If it determines an element is not in the viewport, not displayed, not [keyboard-interactable](https://w3c.github.io/webdriver/#dfn-keyboard-interactable), or not [pointer-interactable](https://w3c.github.io/webdriver/#dfn-pointer-interactable), it returns an [element not interactable](https://w3c.github.io/webdriver/#dfn-element-not-interactable) error.

### Click
The [element click command](https://w3c.github.io/webdriver/#dfn-element-click) is executed on the [center of the element](https://w3c.github.io/webdriver/#dfn-center-point). If the center of the element is [obscured](https://w3c.github.io/webdriver/#dfn-obscuring) for some reason, Selenium will return an [element click intercepted](https://w3c.github.io/webdriver/#dfn-element-click-intercepted) error.

```java
driver.get("https://www.selenium.dev/selenium/web/inputs.html");

// Click on the element 
WebElement checkInput=driver.findElement(By.name("checkbox_input"));
checkInput.click();
```

### Send keys
The [element send keys command](https://w3c.github.io/webdriver/#dfn-element-send-keys) types the provided keys into an [editable](https://w3c.github.io/webdriver/#dfn-editable) element. Typically, this means an element is an input element of a form with a `text` type or an element with a `content-editable` attribute. If it is not editable, [an invalid element state](https://w3c.github.io/webdriver/#dfn-invalid-element-state) error is returned.

```java
// Clear field to empty it from any previous data
WebElement emailInput=driver.findElement(By.name("email_input"));
emailInput.clear();
//Enter Text
String email="admin@localhost.dev";
emailInput.sendKeys(email);
```

### Clear
The [element clear command](https://w3c.github.io/webdriver/#dfn-element-clear) resets the content of an element. This requires an element to be [editable](https://w3c.github.io/webdriver/#dfn-editable), and [resettable](https://w3c.github.io/webdriver/#dfn-resettable-elements). Typically, this means an element is an input element of a form with a `text` type or an element with a`content-editable` attribute. If these conditions are not met, [an invalid element state](https://w3c.github.io/webdriver/#dfn-invalid-element-state) error is returned.

```java
//Clear Element
// Clear field to empty it from any previous data
emailInput.clear();
```

### Submit
In Selenium 4 this is no longer implemented with a separate endpoint and functions by executing a script. As such, it is recommended not to use this method and to click the applicable form submission button instead.

## Information
There are a number of details you can query about a specific element.

### Is Displayed
This method is used to check if the connected Element is displayed on a webpage. Returns a `Boolean` value, True if the connected element is displayed in the current browsing context else returns false.

```java
// Navigate to the url
driver.get("https://www.selenium.dev/selenium/web/inputs.html");

// Get boolean value for is element display
boolean isEmailVisible = driver.findElement(By.name("email_input")).isDisplayed();
```

### Is Enabled
This method is used to check if the connected Element is enabled or disabled on a webpage. Returns a boolean value, **True** if the connected element is **enabled** in the current browsing context else returns **false**.

```java
//returns true if element is enabled else returns false
boolean value = driver.findElement(By.name("button_input")).isEnabled();
```

### Is Selected
This method determines if the referenced Element is _Selected_ or not. This method is widely used on Check boxes, radio buttons, input elements, and option elements.

Returns a boolean value, **True** if referenced element is **selected** in the current browsing context else returns **false**.

```java
//returns true if element is checked else returns false
boolean value = driver.findElement(By.name("checkbox_input")).isSelected();
```

### Tag Name
It is used to fetch the [TagName](https://www.w3.org/TR/webdriver/#dfn-get-element-tag-name) of the referenced Element which has the focus in the current browsing context.

```java
String value = driver.findElement(By.name("email_input")).getTagName();
```

### Size and Position
It is used to fetch the dimensions and coordinates of the referenced element.

The fetched data body contain the following details:

- X-axis position from the top-left corner of the element
- y-axis position from the top-left corner of the element
- Height of the element
- Width of the element

```java
// Returns height, width, x and y coordinates referenced element
Rectangle res =  driver.findElement(By.name("range_input")).getRect();

// Rectangle class provides getX,getY, getWidth, getHeight methods
System.out.println(res.getX());
```

### Get CSS Value
Retrieves the value of specified computed style property of an element in the current browsing context.

```java
// Retrieves the computed style property 'color' of linktext
String cssValue = driver.findElement(By.id("namedColor")).getCssValue("background-color");
```

### Text Content
Retrieves the rendered text of the specified element.

```java
// Retrieves the text of the element
String text = driver.findElement(By.id("justanotherlink")).getText();
```

### Fetching Attributes or Properties
Fetches the run time value associated with a DOM attribute. It returns the data associated with the DOM attribute or property of the element.

```java
//identify the email text box
WebElement emailTxt = driver.findElement(By.name(("email_input")));

//fetch the value property associated with the textbox
String valueInfo = eleSelLink.getAttribute("value");
```

# Interactions

## Get browser information
### Get title
You can read the current page title from the browser:

```java
driver.getTitle();
```

### Get current URL

```java
driver.getCurrentUrl();
```

## Navigation

### Navigate to
The first thing you will want to do after launching a browser is to open your website. This can be achieved in a single line:

```java
//Convenient
driver.get("https://selenium.dev");

//Longer way
driver.navigate().to("https://selenium.dev");
```

### Back
Pressing the browser’s back button:

```java
driver.navigate().back();
```

### Forward
Pressing the browser’s forward button:

```java
driver.navigate().forward();
```

### Refresh
Refresh the current page:

```java
driver.navigate().refresh();
```

## Alerts
WebDriver provides an API for working with the three types of native popup messages offered by JavaScript. These popups are styled by the browser and offer limited customisation.

### Alerts
The simplest of these is referred to as an alert, which shows a custom message, and a single button which dismisses the alert, labelled in most browsers as OK. It can also be dismissed in most browsers by pressing the close button, but this will always do the same thing as the OK button.

WebDriver can get the text from the popup and accept or dismiss these alerts.

```java
//Click the link to activate the alert
driver.findElement(By.linkText("See an example alert")).click();

//Wait for the alert to be displayed and store it in a variable
Alert alert = wait.until(ExpectedConditions.alertIsPresent());

//Store the alert text in a variable
String text = alert.getText();

//Press the OK button
alert.accept();
```

### Confirm
A confirm box is similar to an alert, except the user can also choose to cancel the message.

This example also shows a different approach to storing an alert:

```java
//Click the link to activate the alert
driver.findElement(By.linkText("See a sample confirm")).click();

//Wait for the alert to be displayed
wait.until(ExpectedConditions.alertIsPresent());

//Store the alert in a variable
Alert alert = driver.switchTo().alert();

//Store the alert in a variable for reuse
String text = alert.getText();

//Press the Cancel button
alert.dismiss();
```

### Prompt
Prompts are similar to confirm boxes, except they also include a text input. Similar to working with form elements, you can use WebDriver’s send keys to fill in a response. This will completely replace the placeholder text. Pressing the cancel button will not submit any text.

```java
//Click the link to activate the alert
driver.findElement(By.linkText("See a sample prompt")).click();

//Wait for the alert to be displayed and store it in a variable
Alert alert = wait.until(ExpectedConditions.alertIsPresent());

//Type your message
alert.sendKeys("Selenium");

//Press the OK button
alert.accept();
```

## Cookies
A cookie is a small piece of data that is sent from a website and stored in your computer. Cookies are mostly used to recognise the user and load the stored information.

WebDriver API provides a way to interact with cookies with built-in methods:

### Add Cookie
It is used to add a cookie to the current browsing context. Add Cookie only accepts a set of defined serializable JSON object. [Here](https://www.w3.org/TR/webdriver1/#cookies) is the link to the list of accepted JSON key values.

First of all, you need to be on the domain that the cookie will be valid for. If you are trying to preset cookies before you start interacting with a site and your homepage is large / takes a while to load an alternative is to find a smaller page on the site (typically the 404 page is small, e.g. [http://example.com/some404page](http://example.com/some404page))

```java
import org.openqa.selenium.*;
import org.openqa.selenium.chrome.ChromeDriver;

public class addCookie {
    public static void main(String[] args) {
        WebDriver driver = new ChromeDriver();
        try {
            driver.get("http://www.example.com");

            // Adds the cookie into current browser context
            driver.manage().addCookie(new Cookie("key", "value"));
        } finally {
            driver.quit();
        }
    }
}
```

### Get Named Cookie
It returns the serialized cookie data matching with the cookie name among all associated cookies.

```java
public class getCookieNamed {
    public static void main(String[] args) {
        WebDriver driver = new ChromeDriver();
        try {
            driver.get("http://www.example.com");
            driver.manage().addCookie(new Cookie("foo", "bar"));

            // Get cookie details with named cookie 'foo'
            Cookie cookie1 = driver.manage().getCookieNamed("foo");
            System.out.println(cookie1);
        } finally {
            driver.quit();
        }
    }
}
```

### Get All Cookies
It returns a ‘successful serialized cookie data’ for current browsing context. If browser is no longer available it returns error.

```java
public class getAllCookies {
    public static void main(String[] args) {
        WebDriver driver = new ChromeDriver();
        try {
            driver.get("http://www.example.com");
            // Add few cookies
            driver.manage().addCookie(new Cookie("test1", "cookie1"));
            driver.manage().addCookie(new Cookie("test2", "cookie2"));

            // Get All available cookies
            Set<Cookie> cookies = driver.manage().getCookies();
            System.out.println(cookies);
        } finally {
            driver.quit();
        }
    }
}
```

### Delete Cookie
It deletes the cookie data matching with the provided cookie name.

```java
public class deleteCookie {
    public static void main(String[] args) {
        WebDriver driver = new ChromeDriver();
        try {
            driver.get("http://www.example.com");
            driver.manage().addCookie(new Cookie("test1", "cookie1"));
            Cookie cookie1 = new Cookie("test2", "cookie2");
            driver.manage().addCookie(cookie1);

            // delete a cookie with name 'test1'
            driver.manage().deleteCookieNamed("test1");

            /*
             Selenium Java bindings also provides a way to delete
             cookie by passing cookie object of current browsing context
             */
            driver.manage().deleteCookie(cookie1);
        } finally {
            driver.quit();
        }
    }
}
```

### Delete All Cookies
It deletes all the cookies of the current browsing context.

```java
public class deleteAllCookies {
    public static void main(String[] args) {
        WebDriver driver = new ChromeDriver();
        try {
            driver.get("http://www.example.com");
            driver.manage().addCookie(new Cookie("test1", "cookie1"));
            driver.manage().addCookie(new Cookie("test2", "cookie2"));

            // deletes all cookies
            driver.manage().deleteAllCookies();
        } finally {
            driver.quit();
        }
    }
}
```

### Same-Site Cookie Attribute
It allows a user to instruct browsers to control whether cookies are sent along with the request initiated by third party sites. It is introduced to prevent CSRF (Cross-Site Request Forgery) attacks.

Same-Site cookie attribute accepts two parameters as instructions:

- **Strict**: When the sameSite attribute is set as **Strict**, the cookie will not be sent along with requests initiated by third party websites.
- **Lax**: When you set a cookie sameSite attribute to **Lax**, the cookie will be sent along with the GET request initiated by third party website.

**Note**: **As of now this feature is landed in chrome(80+version), Firefox(79+version) and works with Selenium 4 and later versions.**

```java
public class cookieTest {
  public static void main(String[] args) {
    WebDriver driver = new ChromeDriver();
    try {
      driver.get("http://www.example.com");
      Cookie cookie = new Cookie.Builder("key", "value").sameSite("Strict").build();
      Cookie cookie1 = new Cookie.Builder("key", "value").sameSite("Lax").build();
      driver.manage().addCookie(cookie);
      driver.manage().addCookie(cookie1);
      System.out.println(cookie.getSameSite());
      System.out.println(cookie1.getSameSite());
    } finally {
      driver.quit();
    }
  }
}
```

## Frames
Frames are a now deprecated means of building a site layout from multiple documents on the same domain. You are unlikely to work with them unless you are working with an pre HTML5 webapp. Iframes allow the insertion of a document from an entirely different domain, and are still commonly used.

If you need to work with frames or iframes, WebDriver allows you to work with them in the same way. Consider a button within an iframe. If we inspect the element using the browser development tools, we might see the following:

```html
<div id="modal">
  <iframe id="buttonframe" name="myframe"  src="https://seleniumhq.github.io">
   <button>Click here</button>
 </iframe>
</div>
```

If it was not for the iframe we would expect to click on the button using something like:

```java
//This won't work
driver.findElement(By.tagName("button")).click();
```

However, if there are no buttons outside of the iframe, you might instead get a _no such element_ error. This happens because Selenium is only aware of the elements in the top level document. To interact with the button, we will need to first switch to the frame, in a similar way to how we switch windows. WebDriver offers three ways of switching to a frame.

### Using a WebElement
Switching using a WebElement is the most flexible option. You can find the frame using your preferred selector and switch to it.

```java
//Store the web element
WebElement iframe = driver.findElement(By.cssSelector("#modal>iframe"));

//Switch to the frame
driver.switchTo().frame(iframe);

//Now we can click the button
driver.findElement(By.tagName("button")).click();
```

### Using a name or ID
If your frame or iframe has an id or name attribute, this can be used instead. If the name or ID is not unique on the page, then the first one found will be switched to.

```java
//Using the ID
driver.switchTo().frame("buttonframe");

//Or using the name instead
driver.switchTo().frame("myframe");

//Now we can click the button
driver.findElement(By.tagName("button")).click();
```

### Using an index
It is also possible to use the index of the frame, such as can be queried using _window.frames_ in JavaScript.

```java
// Switches to the second frame
driver.switchTo().frame(1);
```

### Leaving a frame
To leave an iframe or frameset, switch back to the default content like so:

```java
// Return to the top level
driver.switchTo().defaultContent();
```

## Windows

### Windows and tabs

#### Get window handle
WebDriver does not make the distinction between windows and tabs. If your site opens a new tab or window, Selenium will let you work with it using a window handle. Each window has a unique identifier which remains persistent in a single session. You can get the window handle of the current window by using:

```java
driver.getWindowHandle();
```

#### Switching windows or tabs
Clicking a link which opens in a [new window](https://seleniumhq.github.io/) will focus the new window or tab on screen, but WebDriver will not know which window the Operating System considers active. To work with the new window you will need to switch to it. If you have only two tabs or windows open, and you know which window you start with, by the process of elimination you can loop over both windows or tabs that WebDriver can see, and switch to the one which is not the original.

However, Selenium 4 provides a new api [NewWindow](https://www.selenium.dev/documentation/webdriver/interactions/windows/#create-new-window-or-new-tab-and-switch) which creates a new tab (or) new window and automatically switches to it.

```java
//Store the ID of the original window
String originalWindow = driver.getWindowHandle();

//Check we don't have other windows open already
assert driver.getWindowHandles().size() == 1;

//Click the link which opens in a new window
driver.findElement(By.linkText("new window")).click();

//Wait for the new window or tab
wait.until(numberOfWindowsToBe(2));

//Loop through until we find a new window handle
for (String windowHandle : driver.getWindowHandles()) {
    if(!originalWindow.contentEquals(windowHandle)) {
        driver.switchTo().window(windowHandle);
        break;
    }
}

//Wait for the new tab to finish loading content
wait.until(titleIs("Selenium documentation"));
```

#### Create new window (or) new tab and switch
Creates a new window (or) tab and will focus the new window or tab on screen. You don’t need to switch to work with the new window (or) tab. If you have more than two windows (or) tabs opened other than the new window, you can loop over both windows or tabs that WebDriver can see, and switch to the one which is not the original.

**Note: This feature works with Selenium 4 and later versions.**

```java
// Opens a new tab and switches to new tab
driver.switchTo().newWindow(WindowType.TAB);

// Opens a new window and switches to new window
driver.switchTo().newWindow(WindowType.WINDOW);
```

#### Closing a window or tab
When you are finished with a window or tab _and_ it is not the last window or tab open in your browser, you should close it and switch back to the window you were using previously. Assuming you followed the code sample in the previous section you will have the previous window handle stored in a variable. Put this together and you will get:

```java
//Close the tab or window
driver.close();

//Switch back to the old tab or window
driver.switchTo().window(originalWindow);
```

Forgetting to switch back to another window handle after closing a window will leave WebDriver executing on the now closed page, and will trigger a **No Such Window Exception**. You must switch back to a valid window handle in order to continue execution.

#### Quitting the browser at the end of a session
When you are finished with the browser session you should call quit, instead of close:

```java
driver.quit();
```

Quit will:
    - Close all the windows and tabs associated with that WebDriver session
    - Close the browser process
    - Close the background driver process
    - Notify Selenium Grid that the browser is no longer in use so it can be used by another session (if you are using Selenium Grid)

Failure to call quit will leave extra background processes and ports running on your machine which could cause you problems later.

Some test frameworks offer methods and annotations which you can hook into to tear down at the end of a test.

```java
/**
 * Example using JUnit
 * https://junit.org/junit5/docs/current/api/org/junit/jupiter/api/AfterAll.html
 */
@AfterAll
public static void tearDown() {
    driver.quit();
}
```

If not running WebDriver in a test context, you may consider using `try / finally` which is offered by most languages so that an exception will still clean up the WebDriver session.

```java
try {
    //WebDriver code here...
} finally {
    driver.quit();
}
```

### Window management
Screen resolution can impact how your web application renders, so WebDriver provides mechanisms for moving and resizing the browser window.

#### Get window size
Fetches the size of the browser window in pixels.

```java
//Access each dimension individually
int width = driver.manage().window().getSize().getWidth();
int height = driver.manage().window().getSize().getHeight();

//Or store the dimensions and query them later
Dimension size = driver.manage().window().getSize();
int width1 = size.getWidth();
int height1 = size.getHeight();
```

#### Set window size
Restores the window and sets the window size.

```java
driver.manage().window().setSize(new Dimension(1024, 768));
```

#### Get window position
Fetches the coordinates of the top left coordinate of the browser window.

```java
// Access each dimension individually
int x = driver.manage().window().getPosition().getX();
int y = driver.manage().window().getPosition().getY();

// Or store the dimensions and query them later
Point position = driver.manage().window().getPosition();
int x1 = position.getX();
int y1 = position.getY();
```

#### Set window position
Moves the window to the chosen position.

```java
// Move the window to the top left of the primary monitor
driver.manage().window().setPosition(new Point(0, 0));
```

#### Maximize window
Enlarges the window. For most operating systems, the window will fill the screen, without blocking the operating system’s own menus and toolbars.

```java
driver.manage().window().maximize();
```

#### Minimize window
Minimizes the window of current browsing context. The exact behavior of this command is specific to individual window managers.

Minimize Window typically hides the window in the system tray.

**Note: This feature works with Selenium 4 and later versions.**

```java
driver.manage().window().minimize();
```

#### Fullscreen window
Fills the entire screen, similar to pressing F11 in most browsers.

```java
driver.manage().window().fullscreen();
```

#### TakeScreenshot
Used to capture screenshot for current browsing context. The WebDriver endpoint [screenshot](https://www.w3.org/TR/webdriver/#dfn-take-screenshot) returns screenshot which is encoded in Base64 format.

```java
import org.apache.commons.io.FileUtils;
import org.openqa.selenium.chrome.ChromeDriver;
import java.io.*;
import org.openqa.selenium.*;

public class SeleniumTakeScreenshot {
    public static void main(String args[]) throws IOException {
        WebDriver driver = new ChromeDriver();
        driver.get("http://www.example.com");
        File scrFile = ((TakesScreenshot)driver).getScreenshotAs(OutputType.FILE);
        FileUtils.copyFile(scrFile, new File("./image.png"));
        driver.quit();
    }
}
```

#### TakeElementScreenshot
Used to capture screenshot of an element for current browsing context. The WebDriver endpoint [screenshot](https://www.w3.org/TR/webdriver/#take-element-screenshot) returns screenshot which is encoded in Base64 format.

```java
import org.apache.commons.io.FileUtils;
import org.openqa.selenium.*;
import org.openqa.selenium.chrome.ChromeDriver;
import java.io.File;
import java.io.IOException;

public class SeleniumelementTakeScreenshot {
  public static void main(String args[]) throws IOException {
    WebDriver driver = new ChromeDriver();
    driver.get("https://www.example.com");
    WebElement element = driver.findElement(By.cssSelector("h1"));
    File scrFile = element.getScreenshotAs(OutputType.FILE);
    FileUtils.copyFile(scrFile, new File("./image.png"));
    driver.quit();
  }
}
```

#### Execute Script 
Executes JavaScript code snippet in the current context of a selected frame or window.

```java
    //Creating the JavascriptExecutor interface object by Type casting
      JavascriptExecutor js = (JavascriptExecutor)driver;
    //Button Element
      WebElement button =driver.findElement(By.name("btnLogin"));
    //Executing JavaScript to click on element
      js.executeScript("arguments[0].click();", button);
    //Get return value from script
      String text = (String) js.executeScript("return arguments[0].innerText", button);
    //Executing JavaScript directly
      js.executeScript("console.log('hello world')");
```

#### Print Page
Prints the current page within the browser.

_Note: This requires Chromium Browsers to be in headless mode_

```java
    import org.openqa.selenium.print.PrintOptions;

    driver.get("https://www.selenium.dev");
    printer = (PrintsPage) driver;

    PrintOptions printOptions = new PrintOptions();
    printOptions.setPageRanges("1-2");

    Pdf pdf = printer.print(printOptions);
    String content = pdf.getContent();
```

# Actions API
In addition to the high-level [element interactions](https://www.selenium.dev/documentation/webdriver/elements/interactions/), the [Actions API](https://w3c.github.io/webdriver/#dfn-actions) provides granular control over exactly what designated input devices can do. Selenium provides an interface for 3 kinds of input sources: a key input for keyboard devices, a pointer input for a mouse, pen or touch devices, and wheel inputs for scroll wheel devices (introduced in Selenium 4.2). Selenium allows you to construct individual action commands assigned to specific inputs and chain them together and call the associated perform method to execute them all at once.

## Pause
Pointer movements and Wheel scrolling allow the user to set a duration for the action, but sometimes you just need to wait a beat between actions for things to work correctly.

```java
WebElement clickable = driver.findElement(By.id("clickable"));
new Actions(driver)
    .moveToElement(clickable)
    .pause(Duration.ofSeconds(1))
    .clickAndHold()
    .pause(Duration.ofSeconds(1))
    .sendKeys("abc")
    .perform();
```

## Release All Actions
An important thing to note is that the driver remembers the state of all the input items throughout a session. Even if you create a new instance of an actions class, the depressed keys and the location of the pointer will be in whatever state a previously performed action left them.

There is a special method to release all currently depressed keys and pointer buttons. This method is implemented differently in each of the languages because it does not get executed with the perform method.

```java
((RemoteWebDriver) driver).resetInputState();
```

## Keyboard
There are only 2 actions that can be accomplished with a keyboard: pressing down on a key, and releasing a pressed key. In addition to supporting ASCII characters, each keyboard key has a representation that can be pressed or released in designated sequences.

### Keys
In addition to the keys represented by regular unicode, unicode values have been assigned to other keyboard keys for use with Selenium. Each language has its own way to reference these keys; the full list can be found [here](https://www.w3.org/TR/webdriver/#keyboard-actions).

Use the [Java Keys enum](https://github.com/SeleniumHQ/selenium/blob/selenium-4.2.0/java/src/org/openqa/selenium/Keys.java#L28)

### Key down

```java
new Actions(driver)
    .keyDown(Keys.SHIFT)
    .sendKeys("a")
    .perform();
```

### Key up

```java
new Actions(driver)
    .keyDown(Keys.SHIFT)
    .sendKeys("a")
    .keyUp(Keys.SHIFT)
    .sendKeys("b")
    .perform();
```

### Send keys
This is a convenience method in the Actions API that combines keyDown and keyUp commands in one action. Executing this command differs slightly from using the element method, but primarily this gets used when needing to type multiple characters in the middle of other actions.

#### Active Element

```java
new Actions(driver)
    .sendKeys("abc")
    .perform();
```

#### Designated Element

```java
new Actions(driver)
    .sendKeys(textField, "Selenium!")
    .perform();
```

### Copy and Paste
Here’s an example of using all of the above methods to conduct a copy / paste action. Note that the key to use for this operation will be different depending on if it is a Mac OS or not. This code will end up with the text: `SeleniumSelenium!`

```java
Keys cmdCtrl = Platform.getCurrent().is(Platform.MAC) ? Keys.COMMAND : Keys.CONTROL;

WebElement textField = driver.findElement(By.id("textInput"));
new Actions(driver)
    .sendKeys(textField, "Selenium!")
    .sendKeys(Keys.ARROW_LEFT)
    .keyDown(Keys.SHIFT)
    .sendKeys(Keys.ARROW_UP)
    .keyUp(Keys.SHIFT)
    .keyDown(cmdCtrl)
    .sendKeys("xvv")
    .keyUp(cmdCtrl)
    .perform();

Assertions.assertEquals("SeleniumSelenium!", textField.getAttribute("value"));
```

## Mouse
There are only 3 actions that can be accomplished with a mouse: pressing down on a button, releasing a pressed button, and moving the mouse. Selenium provides convenience methods that combine these actions in the most common ways.

### Click and hold
This method combines moving the mouse to the center of an element with pressing the left mouse button. This is useful for focusing a specific element:

```java
WebElement clickable = driver.findElement(By.id("clickable"));
new Actions(driver)
    .clickAndHold(clickable)
    .perform();
```

### Click and release
This method combines moving to the center of an element with pressing and releasing the left mouse button. This is otherwise known as “clicking”:

```java
WebElement clickable = driver.findElement(By.id("click"));
new Actions(driver)
    .click(clickable)
    .perform();
```

### Alternate Button Clicks
There are a total of 5 defined buttons for a Mouse:

- 0 — Left Button (the default)
- 1 — Middle Button (currently unsupported)
- 2 — Right Button
- 3 — X1 (Back) Button
- 4 — X2 (Forward) Button

### Context Click
This method combines moving to the center of an element with pressing and releasing the right mouse button (button 2). This is otherwise known as “right-clicking”:

```java
WebElement clickable = driver.findElement(By.id("clickable"));
new Actions(driver)
    .contextClick(clickable)
    .perform();
```

### Back Click
There is no convenience method for this, it is just pressing and releasing mouse button 3

```java
PointerInput mouse = new PointerInput(PointerInput.Kind.MOUSE, "default mouse");

Sequence actions = new Sequence(mouse, 0)
        .addAction(mouse.createPointerDown(PointerInput.MouseButton.BACK.asArg()))
        .addAction(mouse.createPointerUp(PointerInput.MouseButton.BACK.asArg()));

((RemoteWebDriver) driver).perform(Collections.singletonList(actions));
```

### Forward Click
There is no convenience method for this, it is just pressing and releasing mouse button 4

```java
PointerInput mouse = new PointerInput(PointerInput.Kind.MOUSE, "default mouse");

Sequence actions = new Sequence(mouse, 0)
        .addAction(mouse.createPointerDown(PointerInput.MouseButton.FORWARD.asArg()))
        .addAction(mouse.createPointerUp(PointerInput.MouseButton.FORWARD.asArg()));

((RemoteWebDriver) driver).perform(Collections.singletonList(actions));
```

### Double click
This method combines moving to the center of an element with pressing and releasing the left mouse button twice.

```java
WebElement clickable = driver.findElement(By.id("clickable"));
new Actions(driver)
    .doubleClick(clickable)
    .perform();
```

### Move to element
This method moves the mouse to the in-view center point of the element. This is otherwise known as “hovering.” Note that the element must be in the viewport or else the command will error.

```java
WebElement hoverable = driver.findElement(By.id("hover"));
new Actions(driver)
    .moveToElement(hoverable)
    .perform();
```

### Move by offset
These methods first move the mouse to the designated origin and then by the number of pixels in the provided offset. Note that the position of the mouse must be in the viewport or else the command will error.

#### Offset from Element
This method moves the mouse to the in-view center point of the element, then moves by the provided offset.

```java
WebElement tracker = driver.findElement(By.id("mouse-tracker"));
new Actions(driver)
    .moveToElement(tracker, 8, 0)
    .perform();
```

#### Offset from Viewport
This method moves the mouse from the upper left corner of the current viewport by the provided offset.

```java
PointerInput mouse = new PointerInput(PointerInput.Kind.MOUSE, "default mouse");

Sequence actions = new Sequence(mouse, 0)
    .addAction(mouse.createPointerMove(Duration.ZERO, PointerInput.Origin.viewport(), 8, 12));

((RemoteWebDriver) driver).perform(Collections.singletonList(actions));
```

#### Offset from Current Pointer Location
This method moves the mouse from its current position by the offset provided by the user. If the mouse has not previously been moved, the position will be in the upper left corner of the viewport. Note that the pointer position does not change when the page is scrolled.

Note that the first argument X specifies to move right when positive, while the second argument Y specifies to move down when positive. So `moveByOffset(30, -10)` moves right 30 and up 10 from the current mouse position.

```java
new Actions(driver)
    .moveByOffset(13, 15)
    .perform();
```

### Drag and Drop on Element
This method firstly performs a click-and-hold on the source element, moves to the location of the target element and then releases the mouse.

```java
WebElement draggable = driver.findElement(By.id("draggable"));
WebElement droppable = driver.findElement(By.id("droppable"));
new Actions(driver)
    .dragAndDrop(draggable, droppable)
    .perform();
```

### Drag and Drop by Offset
This method firstly performs a click-and-hold on the source element, moves to the given offset and then releases the mouse.

```java
WebElement draggable = driver.findElement(By.id("draggable"));
Rectangle start = draggable.getRect();
Rectangle finish = driver.findElement(By.id("droppable")).getRect();
new Actions(driver)
    .dragAndDropBy(draggable, finish.getX() - start.getX(), finish.getY() - start.getY())
    .perform();
```

# Support features

## Expected conditions
Expected Conditions are used with [Explicit Waits](https://www.selenium.dev/documentation/webdriver/waits/#explicit-waits). Instead of defining the block of code to be executed with a _lambda_, an expected conditions method can be created to represent common things that get waited on. Some methods take locators as arguments, others take elements as arguments.

These methods can include conditions such as:

- element exists
- element is stale
- element is visible
- text is visible
- title contains specified value

[Expected Conditions Documentation](https://www.selenium.dev/selenium/docs/api/java/org/openqa/selenium/support/ui/ExpectedConditions.html)

# Test practices

## Design patterns and development strategies

### Overview
[DomainDrivenDesign](https://www.selenium.dev/documentation/test_practices/encouraged/domain_specific_language/): Express your tests in the language of the end-user of the app. [PageObjects](https://www.selenium.dev/documentation/test_practices/encouraged/page_object_models/): A simple abstraction of the UI of your web app. LoadableComponent: Modeling PageObjects as components. BotStyleTests: Using a command-based approach to automating tests, rather than the object-based approach that PageObjects encourage
## Overview of Test Automation
Functional end-user tests such as Selenium tests are expensive to run, however. Furthermore, they typically require substantial infrastructure to be in place to be run effectively. It is a good rule to always ask yourself if what you want to test can be done using more lightweight test approaches such as unit tests or with a lower-level approach.

Once you have made the determination that you are in the web browser testing business, and you have your Selenium environment ready to begin writing tests, you will generally perform some combination of three steps:

- Set up the data
- Perform a discrete set of actions
- Evaluate the results

A distinct advantage of Selenium tests is their inherent ability to test all components of the application, from backend to frontend, from a user’s perspective. So in other words, whilst functional tests may be expensive to run, they also encompass large business-critical portions at one time.

### Let’s start with an example
Larry has written a web site which allows users to order their custom unicorns.

The general workflow (what we will call the “happy path”) is something like this:

- Create an account
- Configure the unicorn
- Add it to the shopping cart
- Check out and pay
- Give feedback about the unicorn

It would be tempting to write one grand Selenium script to perform all these operations–many will try. **Resist the temptation!** Doing so will result in a test that a) takes a long time, b) will be subject to some common issues around page rendering timing issues, and c) is such that if it fails, it will not give you a concise, “glanceable” method for diagnosing what went wrong.

The preferred strategy for testing this scenario would be to break it down to a series of independent, speedy tests, each of which has one “reason” to exist.

Let us pretend you want to test the second step: Configuring your unicorn. It will perform the following actions:

- Create an account
- Configure a unicorn

Note that we are skipping the rest of these steps, we will test the rest of the workflow in other small, discrete test cases after we are done with this one.

To start, you need to create an account. Here you have some choices to make:

- Do you want to use an existing account?
- Do you want to create a new account?
- Are there any special properties of such a user that need to be taken into account before configuration begins?

Regardless of how you answer this question, the solution is to make it part of the “set up the data” portion of the test. If Larry has exposed an API that enables you (or anyone) to create and update user accounts, be sure to use that to answer this question. If possible, you want to launch the browser only after you have a user “in hand”, whose credentials you can just log in with.

If each test for each workflow begins with the creation of a user account, many seconds will be added to the execution of each test. Calling an API and talking to a database are quick, “headless” operations that don’t require the expensive process of opening a browser, navigating to the right pages, clicking and waiting for the forms to be submitted, etc.

Ideally, you can address this set-up phase in one line of code, which will execute before any browser is launched:

```java
// Create a user who has read-only permissions--they can configure a unicorn,
// but they do not have payment information set up, nor do they have
// administrative privileges. At the time the user is created, its email
// address and password are randomly generated--you don't even need to
// know them.
User user = UserFactory.createCommonUser(); //This method is defined elsewhere.

// Log in as this user.
// Logging in on this site takes you to your personal "My Account" page, so the
// AccountPage object is returned by the loginAs method, allowing you to then
// perform actions from the AccountPage.
AccountPage accountPage = loginAs(user.getEmail(), user.getPassword());
```

As you can imagine, the `UserFactory` can be extended to provide methods such as `createAdminUser()`, and `createUserWithPayment()`. The point is, these two lines of code do not distract you from the ultimate purpose of this test: configuring a unicorn.

The intricacies of the [Page Object model](https://www.selenium.dev/documentation/test_practices/encouraged/page_object_models/) will be discussed in later chapters, but we will introduce the concept here:

Your tests should be composed of actions, performed from the user’s point of view, within the context of pages in the site. These pages are stored as objects, which will contain specific information about how the web page is composed and how actions are performed– very little of which should concern you as a tester.

What kind of unicorn do you want? You might want pink, but not necessarily. Purple has been quite popular lately. Does she need sunglasses? Star tattoos? These choices, while difficult, are your primary concern as a tester– you need to ensure that your order fulfillment center sends out the right unicorn to the right person, and that starts with these choices.

Notice that nowhere in that paragraph do we talk about buttons, fields, drop-downs, radio buttons, or web forms. **Neither should your tests!** You want to write your code like the user trying to solve their problem. Here is one way of doing this (continuing from the previous example):

```java
// The Unicorn is a top-level Object--it has attributes, which are set here. 
// This only stores the values; it does not fill out any web forms or interact
// with the browser in any way.
Unicorn sparkles = new Unicorn("Sparkles", UnicornColors.PURPLE, UnicornAccessories.SUNGLASSES, UnicornAdornments.STAR_TATTOOS);

// Since we are already "on" the account page, we have to use it to get to the
// actual place where you configure unicorns. Calling the "Add Unicorn" method
// takes us there.
AddUnicornPage addUnicornPage = accountPage.addUnicorn();

// Now that we're on the AddUnicornPage, we will pass the "sparkles" object to
// its createUnicorn() method. This method will take Sparkles' attributes,
// fill out the form, and click submit.
UnicornConfirmationPage unicornConfirmationPage = addUnicornPage.createUnicorn(sparkles);
```

Now that you have configured your unicorn, you need to move on to step 3: making sure it actually worked.

```java
// The exists() method from UnicornConfirmationPage will take the Sparkles 
// object--a specification of the attributes you want to see, and compare
// them with the fields on the page.
Assert.assertTrue("Sparkles should have been created, with all attributes intact", unicornConfirmationPage.exists(sparkles));
  
```

Note that the tester still has not done anything but talk about unicorns in this code– no buttons, no locators, no browser controls. This method of _modelling_ the application allows you to keep these test-level commands in place and unchanging, even if Larry decides next week that he no longer likes Ruby-on-Rails and decides to re-implement the entire site in the latest Haskell bindings with a Fortran front-end.

Your page objects will require some small maintenance in order to conform to the site redesign, but these tests will remain the same. Taking this basic design, you will want to keep going through your workflows with the fewest browser-facing steps possible. Your next workflow will involve adding a unicorn to the shopping cart. You will probably want many iterations of this test in order to make sure the cart is keeping its state properly: Is there more than one unicorn in the cart before you start? How many can fit in the shopping cart? If you create more than one with the same name and/or features, will it break? Will it only keep the existing one or will it add another?

Each time you move through the workflow, you want to try to avoid having to create an account, login as the user, and configure the unicorn. Ideally, you will be able to create an account and pre-configure a unicorn via the API or database. Then all you have to do is log in as the user, locate Sparkles, and add her to the cart.

### To automate or not to automate?
Is automation always advantageous? When should one decide to automate test cases?

It is not always advantageous to automate test cases. There are times when manual testing may be more appropriate. For instance, if the application’s user interface will change considerably in the near future, then any automation might need to be rewritten anyway. Also, sometimes there simply is not enough time to build test automation. For the short term, manual testing may be more effective. If an application has a very tight deadline, there is currently no test automation available, and it’s imperative that the testing gets done within that time frame, then manual testing is the best solution.
## Types of Testing

### Acceptance testing
This type of testing is done to determine if a feature or system meets the customer expectations and requirements. This type of testing generally involves the customer’s cooperation or feedback, being a validation activity that answers the question:

Are we building the **_right_** product?

For web applications, the automation of this testing can be done directly with Selenium by simulating user expected behaviour. This simulation could be done by record/playback or through the different supported languages as explained in this documentation. Note: Acceptance testing is a subtype of **_functional testing_**, which some people might also refer to.

### Functional testing
This type of testing is done to determine if a feature or system functions properly without issues. It checks the system at different levels to ensure that all scenarios are covered and that the system does _what_ it’s supposed to do. It’s a verification activity that answers the question:

Are we building the product **_right?_**

This generally includes: the tests work without errors (404, exceptions…), in a usable way (correct redirections),  
in an accessible way and matching its specifications (see **_acceptance testing_** above).

For web applications, the automation of this testing can be done directly with Selenium by simulating expected returns.  
This simulation could be done by record/playback or through the different supported languages as explained in this documentation.

### Performance testing
As its name indicates, performance tests are done to measure how well an application is performing.

There are two main sub-types for performance testing:

#### Load testing
Load testing is done to verify how well the application works under different defined loads (usually a particular number of users connected at once).

#### Stress testing
Stress testing is done to verify how well the application works under stress (or above the maximum supported load).

Generally, performance tests are done by executing some Selenium written tests simulating different users hitting a particular function on the web app and retrieving some meaningful measurements.

This is generally done by other tools that retrieve the metrics. One such tool is **_JMeter_**.

For a web application, details to measure include throughput, latency, data loss, individual component loading times…

Note 1: All browsers have a performance tab in their developers’ tools section (accessible by pressing F12)

Note 2: is a subtype of **_non-functional testing_** as this is generally measured per system and not per function/feature.

### Regression testing
This testing is generally done after a change, fix or feature addition.

To ensure that the change has not broken any of the existing functionality, some already executed tests are executed again.

The set of re-executed tests can be full or partial and can include several different types, depending on the application and development team.

### Test driven development (TDD)
Rather than a test type _per se_, TDD is an iterative development methodology in which tests drive the design of a feature.

Each cycle starts by creating a set of unit tests that the feature should eventually pass (they should fail their first time executed).

After this, development takes place to make the tests pass. The tests are executed again, starting another cycle and this process continues until all tests are passing.

This aims to speed up the development of an application based on the fact that defects are less costly the earlier they are found.

### Behavior-driven development (BDD)
BDD is also an iterative development methodology based on the above TDD, in which the goal is to involve all the parties in the development of an application.

Each cycle starts by creating some specifications (which should fail). Then create the failing unit tests (which should also fail) and then do the development.

This cycle is repeated until all types of tests are passing.

In order to do so, a specification language is used. It should be understandable by all parties and simple, standard and explicit. Most tools use **_Gherkin_** as this language.

The goal is to be able to detect even more errors than TDD, by targeting potential acceptance errors too and make communication between parties smoother.

A set of tools are currently available to write the specifications and match them with code functions, such as **_Cucumber_** or **_SpecFlow._**

A set of tools are built on top of Selenium to make this process even faster by directly transforming the BDD specifications into executable code. Some of these are **_JBehave, Capybara and Robot Framework_**.
## Encouraged behaviors

### Page object models
Within your web app’s UI, there are areas where your tests interact with. A Page Object only models these as objects within the test code. This reduces the amount of duplicated code and means that if the UI changes, the fix needs only to be applied in one place.

Page Object is a Design Pattern that has become popular in test automation for enhancing test maintenance and reducing code duplication. A page object is an object-oriented class that serves as an interface to a page of your AUT. The tests then use the methods of this page object class whenever they need to interact with the UI of that page. The benefit is that if the UI changes for the page, the tests themselves don’t need to change, only the code within the page object needs to change. Subsequently, all changes to support that new UI are located in one place.

#### Advantages 
- There is a clean separation between the test code and page-specific code, such as locators (or their use if you’re using a UI Map) and layout.
- There is a single repository for the services or operations the page offers rather than having these services scattered throughout the tests.

In both cases, this allows any modifications required due to UI changes to all be made in one place.

#### Examples
First, consider an example, typical of test automation, that does not use a page object:

```java
/***
 * Tests login feature
 */
public class Login {

  public void testLogin() {
    // fill login data on sign-in page
    driver.findElement(By.name("user_name")).sendKeys("userName");
    driver.findElement(By.name("password")).sendKeys("my supersecret password");
    driver.findElement(By.name("sign-in")).click();

    // verify h1 tag is "Hello userName" after login
    driver.findElement(By.tagName("h1")).isDisplayed();
    assertThat(driver.findElement(By.tagName("h1")).getText(), is("Hello userName"));
  }
}
```

There are two problems with this approach.

- There is no separation between the test method and the AUT’s locators (IDs in this example); both are intertwined in a single method. If the AUT’s UI changes its identifiers, layout, or how a login is input and processed, the test itself must change.
- The ID-locators would be spread in multiple tests, in all tests that had to use this login page.

Applying the page object techniques, this example could be rewritten like this in the following example of a page object for a Sign-in page.

```java
import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;

/**
 * Page Object encapsulates the Sign-in page.
 */
public class SignInPage {
  protected WebDriver driver;

  // <input name="user_name" type="text" value="">
  private By usernameBy = By.name("user_name");
  // <input name="password" type="password" value="">
  private By passwordBy = By.name("password");
  // <input name="sign_in" type="submit" value="SignIn">
  private By signinBy = By.name("sign_in");

  public SignInPage(WebDriver driver){
    this.driver = driver;
     if (!driver.getTitle().equals("Sign In Page")) {
      throw new IllegalStateException("This is not Sign In Page," +
            " current page is: " + driver.getCurrentUrl());
    }
  }

  /**
    * Login as valid user
    *
    * @param userName
    * @param password
    * @return HomePage object
    */
  public HomePage loginValidUser(String userName, String password) {
    driver.findElement(usernameBy).sendKeys(userName);
    driver.findElement(passwordBy).sendKeys(password);
    driver.findElement(signinBy).click();
    return new HomePage(driver);
  }
}
```

and page object for a Home page could look like this.

```java
/**
 * Page Object encapsulates the Home Page
 */
public class HomePage {
  protected WebDriver driver;

  // <h1>Hello userName</h1>
  private By messageBy = By.tagName("h1");

  public HomePage(WebDriver driver){
    this.driver = driver;
    if (!driver.getTitle().equals("Home Page of logged in user")) {
      throw new IllegalStateException("This is not Home Page of logged in user," +
            " current page is: " + driver.getCurrentUrl());
    }
  }

  /**
    * Get message (h1 tag)
    *
    * @return String message text
    */
  public String getMessageText() {
    return driver.findElement(messageBy).getText();
  }

  public HomePage manageProfile() {
    // Page encapsulation to manage profile functionality
    return new HomePage(driver);
  }
  /* More methods offering the services represented by Home Page
  of Logged User. These methods in turn might return more Page Objects
  for example click on Compose mail button could return ComposeMail class object */
}
```

So now, the login test would use these two page objects as follows.

```java
/***
 * Tests login feature
 */
public class TestLogin {

  @Test
  public void testLogin() {
    SignInPage signInPage = new SignInPage(driver);
    HomePage homePage = signInPage.loginValidUser("userName", "password");
    assertThat(homePage.getMessageText(), is("Hello userName"));
  }

}
```

There is a lot of flexibility in how the page objects may be designed, but there are a few basic rules for getting the desired maintainability of your test code.

#### Assertions in Page Objects
Page objects themselves should never make verifications or assertions. This is part of your test and should always be within the test’s code, never in an page object. The page object will contain the representation of the page, and the services the page provides via methods but no code related to what is being tested should be within the page object.

There is one, single, verification which can, and should, be within the page object and that is to verify that the page, and possibly critical elements on the page, were loaded correctly. This verification should be done while instantiating the page object. In the examples above, both the SignInPage and HomePage constructors check that the expected page is available and ready for requests from the test.
#### Page Component Objects
A page object does not necessarily need to represent all the parts of a page itself. This was [noted by Martin Fowler](https://martinfowler.com/bliki/PageObject.html#footnote-panel-object) in the early days, while first coining the term “panel objects”.

The same principles used for page objects can be used to create “Page _Component_ Objects”, as it was later called, that represent discrete chunks of the page and **can be included in page objects**. These component objects can provide references to the elements inside those discrete chunks, and methods to leverage the functionality or behavior provided by them.

For example, a Products page has multiple products.



### Domain specific language

### Generating application state

### Mock external services

### Improved reporting

### Avoid sharing state

### Tips on working with locators

### Test independency

### Consider using a fluent API

### Fresh browser per test





## Discouraged behaviors
