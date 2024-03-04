#java #seleniumwebdriver #seleniumgrid #selenium  #jenkins #cucumber #mysql #chromedevtools #maven
# Install Java & Selenium

```bash
ls /usr/lib/jvm/
nano ~/.bashrc
```

## Understanding the core concept of Browser driver classes and Webdriver Interface

```java
import org.openqa.selenium.chrome.ChromeDriver;

ChromeDriver driver = new ChromeDriver();
```

**What is interface in Java?**
An interface is a group of related methods with empty bodies.
It's class responsibility to implement the methods declared in the interface.
When class agreed to implement the interface, they must need to provide implementation/bodies to all the defined methods in interface.
In simple terms, interface enforces the contract to class to follow.

**WebDriver is an interface which provides set of browser automation methods with empty bodies (abstract methods)**
Classes like ChromeDriver, FirefoxDriver, MicrosoftEdgeDriver, SafariDriver, etc implement the WebDriver interface and provide their own implementation to the WebDriver methods.

**We need to create the object of the class to access the methods present in the class**

```java
ChromeDriver driver = new ChromeDriver();
```

`driver` object here has access to all the methods of Chrome driver.

```java
WebDriver driver = new ChromeDriver();
```

`driver` object here has access to the methods of the Chrome driver which are defined in WebDriver interface.

## How to run tests in Google Chrome & Importance of Chromedriver.exe file

Selenium Manager

```java
System.setProperty("webdriver.chrome.driver", "/home/fanjo/Downloads/chromedriver-linux64");
```

## Getting Started with basic Selenium WebDriver methods

Load a new web page in the current browser window.

```java
driver.get("url");
```

Get the title of the current page.

```java
driver.getTitle();
```

Get a string representing the current URL that the browser is looking at.

```java
driver.getCurrentUrl();
```

Close the current window, quitting the browser if it's the last window currently open.

```java
driver.close();
```

Quits this driver, closing every associated window.

```java
driver.quit();
```

## How to run tests in Firefox and Edge browser with Gecko and edge drivers

GeckoDriver

```java
System.setProperty("webdriver.gecko.driver", "/home/fanjo/Documents/geckodriver");
WebDriver driver = new FirefoxDriver();
```

```java
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.chrome.ChromeDriver;
import org.openqa.selenium.edge.EdgeDriver;
import org.openqa.selenium.firefox.FirefoxDriver;

public class Intro {

	public static void main(String[] args) {
		// Selenium Manager
		// ChromeDriver
		
		// System.setProperty("webdriver.chrome.driver", "/home/fanjo/Downloads/chromedriver-linux64/chromedriver");
		// WebDriver driver = new ChromeDriver();
		
		// GeckoDriver
		// System.setProperty("webdriver.gecko.driver", "/home/fanjo/Documents/geckodriver");
		// WebDriver driver = new FirefoxDriver();
		
		// Microsoft Edge Driver
		//System.setProperty("webdriver.edge.driver", "/home/fanjo/Documents/msedgedriver");
		WebDriver driver = new EdgeDriver();
		
		driver.get("https://github.com/spenalozacortes");
		System.out.println(driver.getTitle());
		System.out.println(driver.getCurrentUrl());
		driver.close();
		// driver.quit();
	}

}
```

# Locator Techniques & Tools Used to Identify Objects

## Importance of locators in Selenium WebDriver to identify the elements

**Selenium WebDriver Locators**
- As part of automation, Selenium performs actions (such as click, typing) on the page HTML elements.
- The locators are the way to identify an HTML element on a web page. Selenium WebDriver uses any of the below locators to identify the element on the page and performs the action:
	- ID
	- Xpath
	- CSS selector
	- name
	- Class name
	- Tag name
	- Link text
	- Partial link text

## Identifying the Web elements with id and name locators

Find the first WebElement using the given method. 

```java
driver.findElement(By.id("inputUsername"));
```

Use this method to simulate typing into an element, which may set its value.

```java
driver.findElement(By.id("inputUsername")).sendKeys("text");
```

```java
driver.findElement(By.name("inputPassword"));

driver.findElement(By.className("signInBtn")).click();
```

## Introducing Class name and Css Selector locators to identify elements

SelectorsHub
CrhoPath

```
tagname[attribute='value']

input[placeholder='Username']
```

Get the visible (i.e. not hidden by CSS) text of this element, including sub-elements.

```java
driver.findElement(By.cssSelector("p.error")).getText();
```

## Browser plugins- Selectorshub to identify and validate the elements on the page

Specifies the amount of time the driver should wait when searching for an element if it is not immediately present.

```java
import java.time.Duration;

driver.manage().timeouts().implicitlyWait(Duration.ofSeconds(5));
```

Console:

```
$('p.error')
```

```java
driver.findElement(By.linkText("Forgot your password?")).click();
```

**XPath**

```
//tagname[@attribute='value']

//input[@placeholder='Username']
```

```java
driver.findElement(By.xpath("//input[@placeholder='Name']")).sendKeys("Stephan");
```

Console:

```
$x('//input[@placeholder="Name"]')
```

## Building Customized Xpath and Css Selector locators based on html attributes

```java
driver.findElement(By.cssSelector("input[placeholder='Email'")).sendKeys("aba@gmail.com");
```

If this element is a form entry element, this will reset its value.

```java
driver.findElement(By.cssSelector("input[placeholder='Email'")).clear();
```

```
//tagname[@attribute='value'][index]

//input[@type='text'][2]
```

```
tagname[attribute='value']:nth-child(index)

input[type='text']:nth-child(2)
```
 
## Generating xpaths with parent to child tags traverse techniques

```
//parentTagname/childTagname

//form/input[3]
```

```java
driver.findElement(By.xpath("//form/input[3]")).sendKeys("123456789");
```

```
parentTagname childTagname

form p
```

# Advanced Locators Identification & Interview Questions on Parsing Text

## Generating Css selectors based on regular expressions

Causes the currently executing thread to sleep (temporarily cease execution) for the specified number of milliseconds, subject to the precision and accuracy of system timers and schedulers.

```java
Thread.sleep(1000);
```

```
input[type*='pass']

//button[contains(@class,'submit')]
```

```java
import java.time.Duration;

import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.chrome.ChromeDriver;

public class Locators {

	public static void main(String[] args) throws InterruptedException {
		// System.setProperty("webdriver.chrome.driver", "/home/fanjo/Documents/drivers/chromedriver");
		WebDriver driver = new ChromeDriver();
		
		// implicit wait
		driver.manage().timeouts().implicitlyWait(Duration.ofSeconds(5));
		
		driver.get("https://rahulshettyacademy.com/locatorspractice/");
		
		driver.findElement(By.id("inputUsername")).sendKeys("stephan");
		driver.findElement(By.name("inputPassword")).sendKeys("hello123");
		driver.findElement(By.className("signInBtn")).click();
		System.out.println(driver.findElement(By.cssSelector("p.error")).getText());
		
		driver.findElement(By.linkText("Forgot your password?")).click();
		Thread.sleep(1000);
		driver.findElement(By.xpath("//input[@placeholder='Name']")).sendKeys("Stephan");
		driver.findElement(By.cssSelector("input[placeholder='Email'")).sendKeys("aba@gmail.com");
		// driver.findElement(By.cssSelector("input[placeholder='Email'")).clear();
		driver.findElement(By.xpath("//form/input[3]")).sendKeys("123456789");
		driver.findElement(By.cssSelector(".reset-pwd-btn")).click();
		System.out.println(driver.findElement(By.cssSelector("form p")).getText());
		
		driver.findElement(By.xpath("//div[@class='forgot-pwd-btn-conainer']/button[1]")).click();
		Thread.sleep(1000);
		driver.findElement(By.cssSelector("#inputUsername")).sendKeys("rahul");
		driver.findElement(By.cssSelector("input[type*=pass]")).sendKeys("rahulshettyacademy");
		driver.findElement(By.id("chkboxOne")).click();
		driver.findElement(By.xpath("//button[contains(@class,'submit')]")).click();
	}

}
```

## Identifying web elements based on unique Tag name locators 

```java
driver.findElement(By.tagName("p")).getText()
```

```java
import org.testng.Assert;

Assert.assertEquals(driver.findElement(By.tagName("p")).getText(), "You are successfully logged in.");
```

```
tagname
h2

//tagname
//h2
```

## Generating xpaths based on the button texts on the page

Only xpath:

```
//button[text()='Log Out']
//*[text()='Log Out']
```

## Identify locators using siblings with Xpath traverse

```
//header/div/button[1]/following-sibling::button[1]
```

## How to traverse from child element to parent element with xpath

```
//header/div/button[1]/parent::div
```

## Automate browser navigations and window properties with Selenium WebDriver

- `manage()`: Gets the Options interface
- `window()`: the interface for managing the current window
- `maximize()`: maximizes the current window if it's not already maximized

```java
driver.manage().window().maximize();
```

- `navigate()`: an abstraction allowing the driver to access the browser's history and to navigate to a given URL
- `to(url)`: load a new web page in the current browser window

```java
driver.navigate().to(url);
```

- `back()`: move back a single item in the browser's history

```java
driver.navigate().back();
```

- `forward()`: Move a single item forward in the browser's history. Does nothing if we are on the latest page viewed.

```java
driver.navigate().forward();
```

```java
public class WindowsActivities {

	public static void main(String[] args) {
		WebDriver driver = new ChromeDriver();
		
		driver.manage().window().maximize();
		driver.get("https://www.google.com");
		driver.navigate().to("https://rahulshettyacademy.com/");
		driver.navigate().back();
		driver.navigate().forward();
	}
}
```

# Selenium WebDriver -> Techniques to automate web elements

## Handling static dropdowns with Select WebDriver API

- `selectByIndex`: Select the option at the given index. This is done by examining the "index" attribute of an element, and not merely by counting.

```java
WebElement staticDropdown = driver.findElement(By.id("ctl00_mainContent_DropDownListCurrency"));
Select dropdown = new Select(staticDropdown);
dropdown.selectByIndex(3);
```

- `selectByVisibleText`: Select all options that display text matching the argument. That is, when given "Bar" this would select an option like `<option value='foo'>Bar</option>`

```java
dropdown.selectByVisibleText("AED");
```

- `selectByValue`: Select all options that have a value matching the argument. That is, when given "foo" this would select an option like: `<option value="foo">Bar</option>`

```java
dropdown.selectByValue("INR");
```

```java
public class StaticDropdown {

	public static void main(String[] args) {
		WebDriver driver = new ChromeDriver();
		
		driver.get("https://rahulshettyacademy.com/dropdownsPractise/");
        WebElement staticDropdown = driver.findElement(By.id("ctl00_mainContent_DropDownListCurrency"));
		
        Select dropdown = new Select(staticDropdown);
        dropdown.selectByIndex(3);
        System.out.println(dropdown.getFirstSelectedOption().getText());
        dropdown.selectByVisibleText("AED");
        System.out.println(dropdown.getFirstSelectedOption().getText());
        dropdown.selectByValue("INR");
        System.out.println(dropdown.getFirstSelectedOption().getText());
	}
}
```

## Latest dropdown looping UI

```java
public class UpdatedDropdown {

	public static void main(String[] args) throws InterruptedException {
		WebDriver driver = new ChromeDriver();
		driver.get("https://rahulshettyacademy.com/dropdownsPractise/");
		
		driver.findElement(By.id("divpaxinfo")).click();
		Thread.sleep(2000L);
		System.out.println(driver.findElement(By.id("divpaxinfo")).getText());
		int i = 1;
		while(i < 5) {
			driver.findElement(By.id("hrefIncAdt")).click();
			i++;
		}
		driver.findElement(By.id("btnclosepaxoption")).click();
		System.out.println(driver.findElement(By.id("divpaxinfo")).getText());

	}
}
```

## Handle dynamic dropdowns with WebDriver API

```
(//a[@value='MAA'])[2]
```

```java
public class Dropdown {

	public static void main(String[] args) throws InterruptedException {
		WebDriver driver = new ChromeDriver();
		driver.get("https://rahulshettyacademy.com/dropdownsPractise/");
		
		driver.findElement(By.id("ctl00_mainContent_ddl_originStation1_CTXT")).click();
		driver.findElement(By.xpath("//a[@value='BLR']")).click();
		Thread.sleep(2000L);
		driver.findElement(By.xpath("(//a[@value='MAA'])[2]")).click();
	}
}
```

## Parent-child relationship locator to identify the objects uniquely

```
//div[@id='ctl00_mainContent_ddl_originStation1_CTNR'] //a[@value='BLR']
```

```java
public class Dropdown {

	public static void main(String[] args) throws InterruptedException {
		WebDriver driver = new ChromeDriver();
		driver.get("https://rahulshettyacademy.com/dropdownsPractise/");
		
		driver.findElement(By.id("ctl00_mainContent_ddl_originStation1_CTXT")).click();
		driver.findElement(By.xpath("//a[@value='BLR']")).click();
		Thread.sleep(2000L);
		driver.findElement(By.xpath("//div[@id='glsctl00_mainContent_ddl_destinationStation1_CTNR'] //a[@value='MAA']")).click();
	}
}
```

## Handling AutoSuggestive dropdowns using Selenium

- `findElements()`: Find all elements within the current page using the given mechanism.

```java
List<WebElement> options = driver.findElements(By.cssSelector("li[class='ui-menu-item'] a"));
```

```java
public class AutoSuggestive {

	public static void main(String[] args) throws InterruptedException {
		WebDriver driver = new ChromeDriver();
		driver.get("https://rahulshettyacademy.com/dropdownsPractise/");
		
		driver.findElement(By.id("autosuggest")).sendKeys("ind");
		Thread.sleep(3000);
		List<WebElement> options = driver.findElements(By.cssSelector("li[class='ui-menu-item'] a"));
		
		for(WebElement option: options) {
			if(option.getText().equalsIgnoreCase("India")) {
				option.click();
				break;
			}
		}
	}
}
```

## Handling checkbox and getting the size of them with Selenium

- `isSelected()`: Determine whether this element is selected or not. This operation only applies to input elements such as checkboxes, options in a select and radio buttons.

```java
driver.findElement(By.cssSelector("input[id*=SeniorCitizenDiscount]")).isSelected();
```

- `size()`: Returns the number of elements in this list.

```java
driver.findElements(By.cssSelector("input[type='checkbox']")).size();
```

```java
public class Checkbox {

	public static void main(String[] args) throws InterruptedException {
		WebDriver driver = new ChromeDriver();
		driver.get("https://rahulshettyacademy.com/dropdownsPractise/");
		
		System.out.println(driver.findElement(By.cssSelector("input[id*=SeniorCitizenDiscount]")).isSelected());
		driver.findElement(By.cssSelector("input[id*=SeniorCitizenDiscount]")).click();
		System.out.println(driver.findElement(By.cssSelector("input[id*=SeniorCitizenDiscount]")).isSelected());
		
		System.out.println(driver.findElements(By.cssSelector("input[type='checkbox']")).size());
	}
}
```

## Importance of assertions in automation testing and how to use them

- `assertFalse()`: Asserts that a condition is false. If it isn't, an AssertionError is thrown.

```java
Assert.assertFalse(driver.findElement(By.cssSelector("input[id*=SeniorCitizenDiscount]")).isSelected());
```

- `assertTrue()`: Asserts that a condition is true. If it isn't, an AssertionError is thrown.

```java
Assert.assertTrue(driver.findElement(By.cssSelector("input[id*=SeniorCitizenDiscount]")).isSelected());
```

- `assertEquals(actual, expected)`: Asserts that two Strings are equal. If they are not, an AssertionError is thrown.

```java
Assert.assertEquals(driver.findElement(By.id("divpaxinfo")).getText(), "5 Adult");
```

```java
public class Assertions {

	public static void main(String[] args) throws InterruptedException {
		WebDriver driver = new ChromeDriver();
		driver.get("https://rahulshettyacademy.com/dropdownsPractise/");
		
		Assert.assertFalse(driver.findElement(By.cssSelector("input[id*=SeniorCitizenDiscount]")).isSelected());
		driver.findElement(By.cssSelector("input[id*=SeniorCitizenDiscount]")).click();
		Assert.assertTrue(driver.findElement(By.cssSelector("input[id*=SeniorCitizenDiscount]")).isSelected());
		
		driver.findElement(By.id("divpaxinfo")).click();
		Thread.sleep(2000L);
		System.out.println(driver.findElement(By.id("divpaxinfo")).getText());
		int i = 1;
		while(i < 5) {
			driver.findElement(By.id("hrefIncAdt")).click();
			i++;
		}
		driver.findElement(By.id("btnclosepaxoption")).click();
		Assert.assertEquals(driver.findElement(By.id("divpaxinfo")).getText(), "5 Adult");
	}
}
```

## Handling calendar UI in travel websites using Selenium

```
.ui-state-default.ui-state-highlight
```

```java
driver.findElement(By.cssSelector(".ui-state-default.ui-state-highlight")).click();
```

## Validating if UI elements are disabled or enabled with attributes

- `isEnabled()`: Is the element currently enabled or not? This will generally return true for everything but disabled input elements.

```java
driver.findElement(By.name("ctl00$mainContent$view_date2")).isEnabled();
```

- `getAttribute()`: Get the value of the given attribute of the element. Will return the current value, even if this has been modified after the page has been loaded.

More exactly, this method will return the value of the property with the given name, if it exists. If it does not, then the value of the attribute with the given name is returned. If neither exists, null is returned.

```java
driver.findElement(By.id("Div1")).getAttribute("style");
```

```java
public class Enabled {

	public static void main(String[] args) throws InterruptedException {
		WebDriver driver = new ChromeDriver();
		driver.get("https://rahulshettyacademy.com/dropdownsPractise/");
		
		// System.out.println(driver.findElement(By.name("ctl00$mainContent$view_date2")).isEnabled());
		driver.findElement(By.id("ctl00_mainContent_rbtnl_Trip_1")).click();
		// System.out.println(driver.findElement(By.name("ctl00$mainContent$view_date2")).isEnabled());
		if(driver.findElement(By.id("Div1")).getAttribute("style").contains("1")) {
			Assert.assertTrue(true);
		} else {
			Assert.assertFalse(false);
		}
	}
}
```

## End to End Automation using all UI Elements with selenium

```java
public class e2e {

	public static void main(String[] args) throws InterruptedException {
		System.setProperty("webdriver.chrome.driver", "C://work//chromedriver.exe");
		WebDriver driver =new ChromeDriver();

		driver.get("http://spicejet.com"); //URL in the browser
		driver.findElement(By.id("ctl00_mainContent_rbtnl_Trip_0")).click();
		driver.findElement(By.id("ctl00_mainContent_ddl_originStation1_CTXT")).click();
		driver.findElement(By.xpath("//a[@value='DEL']")).click();
		Thread.sleep(2000);
		driver.findElement(By.xpath("//div[@id='glsctl00_mainContent_ddl_destinationStation1_CTNR'] //a[@value='MAA']")).click();
		driver.findElement(By.cssSelector(".ui-state-default.ui-state-highlight.ui-state-active")).click();
		if(driver.findElement(By.id("Div1")).getAttribute("style").contains("0.5")) {
		System.out.println("its disabled");
		Assert.assertTrue(true);
	} else {
		Assert.assertTrue(false);
	}

		driver.findElement(By.cssSelector("input[id*='SeniorCitizenDiscount']")).click();
		driver.findElement(By.id("divpaxinfo")).click();
		Thread.sleep(2000L);
		for(int i=1;i<5;i++) {
			driver.findElement(By.id("hrefIncAdt")).click();
		}

		driver.findElement(By.id("btnclosepaxoption")).click();
		Assert.assertEquals(driver.findElement(By.id("divpaxinfo")).getText(), "5 Adult");
		System.out.println(driver.findElement(By.id("divpaxinfo")).getText());

		// driver.findElement(By.cssSelector("#ctl00_mainContent_btn_FindFlights")).click();
		driver.findElement(By.cssSelector("input[value='Search']")).click();
		// driver.findElement(By.xpath("//input[@value='Search']")).click();
		// driver.findElement(By.name("ctl00$mainContent$btn_FindFlights")).click();
	}
}
```

## Handling Java alerts using Selenium WebDriver

- `switchTo()`: Send future commands to a different frame or window.
- `alert()`: Switches to the currently active modal dialog for this particular driver instance.
- `accept()`

```java
driver.switchTo().alert().getText();
driver.switchTo().alert().accept();
```

- `dismiss()`

```java
driver.switchTo().alert().dismiss();
```

# Deep dive into functional testing with Selenium

## Sending array of products to car for checkout

- `get()`: Returns the element at the specified position in this list.

```java
driver.findElements(By.xpath("//button[text()='ADD TO CART']")).get(i).click();
```

## Building programming logic to process items in array for cart

```java
public class WindowsActivities {

	public static void main(String[] args) throws InterruptedException {

		WebDriver driver = new ChromeDriver();
		
		String[] itemsNeeded = { "Cucumber", "Brocolli", "Beetroot" };

		driver.get("https://rahulshettyacademy.com/seleniumPractise/");

		Thread.sleep(3000);

		addItems(driver, itemsNeeded);

	}

	public static void addItems(WebDriver driver, String[] itemsNeeded) {
		int j = 0;
		List<WebElement> products = driver.findElements(By.cssSelector("h4.product-name"));

		for (int i = 0; i < products.size(); i++) {

//Brocolli - 1 Kg

//Brocolli,    1 kg

			String[] name = products.get(i).getText().split("-");
			String formattedName = name[0].trim();

//format it to get actual vegetable name

//convert array into array list for easy search

//  check whether name you extracted is present in arrayList or not-

			List itemsNeededList = Arrays.asList(itemsNeeded);

			if (itemsNeededList.contains(formattedName)) {
				j++;
//click on Add to cart

				driver.findElements(By.xpath("//div[@class='product-action']/button")).get(i).click();

				if (j == itemsNeeded.length) {
					break;
				}
			}
		}
	}
}
```

# Synchronization usage in Selenium WebDriver

- Implicit wait.
- Explicit wait
- Thread.sleep
- Fluent wait
## What is implicit wait? 
Define a wait time globally. Hey wait for n number of seconds before you throw exception. Maximum time limit. Listens to DOM.
## What is explicit wait?
Target specific element.

## Practical examples on implicit wait

```java
driver.manage().timeouts().implicitlyWait(5, TimeUnit.SECONDS);
```

Pros:
- Readable code

Cons:
- Performance cause issues are not caught

## Practical examples on explicit waits

- `until()`: Repeatedly applies this instance's input value to the given function until one of the following occurs:

1. the function returns neither null nor false
2. the function throws an unignored exception
3. the timeout expires
4. the current thread is interrupted

- `visibilityOfElementLocated(By locator)`: An expectation for checking that an element is present on the DOM of a page and visible. Visibility means that the element is not only displayed but also has a height and width that is greater than 0.

```java
WebDriverWait w = new WebDriverWait(driver, Duration.ofSeconds(5));
w.until(ExpectedConditions.visibilityOfElementLocated(By.cssSelector("span.promoInfo")));
```

Pros:
- Wait is applied only at targeted elements, so no performance issues

Cons:
- More code

```java
	public static void main(String[] args) throws InterruptedException {
		WebDriver driver = new ChromeDriver();
		// driver.manage().timeouts().implicitlyWait(5, TimeUnit.SECONDS);
		WebDriverWait w = new WebDriverWait(driver, Duration.ofSeconds(5));
		
		String[] itemsNeeded = { "Cucumber", "Brocolli", "Beetroot" };
		driver.get("https://rahulshettyacademy.com/seleniumPractise/");
		Thread.sleep(3000);
		addItems(driver, itemsNeeded);
		
		driver.findElement(By.cssSelector("img[alt='Cart']")).click();
		driver.findElement(By.xpath("//button[contains(text(), 'PROCEED TO CHECKOUT')]")).click();
		
		w.until(ExpectedConditions.visibilityOfElementLocated(By.cssSelector("input.promoCode")));
		driver.findElement(By.cssSelector("input.promoCode")).sendKeys("rahulshettyacademy");
		driver.findElement(By.cssSelector("button.promoBtn")).click();
		
		w.until(ExpectedConditions.visibilityOfElementLocated(By.cssSelector("span.promoInfo")));
		
		System.out.println(driver.findElement(By.cssSelector("span.promoInfo")).getText());
	}
```

## What is fluent wait? Its advantages
Explicit wait can be achieved in 2 ways

1. WebDriverWait
2. FluentWait

### How different it is from WebDriverWait?
Fluent wait finds the web element repeatedly at regular intervals of time until the timeout or till the object gets found.

Unlike WebDriverWait, we need to build customized wait methods based on condition.

## Building customized methods using Fluent wait
Both WaitDriverWait and FluentWait classes implement Wait interface.

- `.withTimeout(Duration timeout)`: Sets how long to wait for the evaluated condition to be true.
- `pollingEvery(Duration interval)`: Sets how often the condition should be evaluated.

```java
Wait<WebDriver> wait = new FluentWait<WebDriver>(driver)
	.withTimeout(Duration.ofSeconds(30))
	.pollingEvery(Duration.ofSeconds(3))
	.ignoring(NoSuchElementException.class);

WebElement foo = wait.until(new Function<WebDriver, WebElement>() {
	public WebElement apply(WebDriver driver) {
		return driver.findElement(By.cssSelector("[id='finish'] h4"));
	}
});
```

```java
WebElement foo = wait.until(new Function<WebDriver, WebElement>() {
	public WebElement apply(WebDriver driver) {
		if(driver.findElement(By.cssSelector("[id='finish'] h4")).isDisplayed()) {
			return driver.findElement(By.cssSelector("[id='finish'] h4"));
		} else {
			return null;
		}
	}
});
```

# Techniques to automate Ajax calls, child windows and iFrames

## Handling Ajax/Mouse interactions

### Actions

- How to mouseover on object with Selenium?
- Performing mouse and keyboard interactions with Selenium
- Context click on element
- Double click on element
- Drag and drop the element

- `Actions`: The user-facing API for emulating complex user gestures. Use this class rather than using the Keyboard or Mouse directly.
- `moveToElement(WebElement target)`: Moves the mouse to the middle of the element.
- `build()`: Generates a composite action containing all actions so far, ready to be performed (and resets the internal builder state, so subsequent calls to this method will contain fresh sequences).

```java
Actions a = new Actions(driver);
a.moveToElement(driver.findElement(By.cssSelector("a[id='nav-link-accountList']"))).build().perform();
```

## Actions class

- `keyDown(CharSequence key)`: Performs a modifier key press. Does not release the modifier key - subsequent interactions may assume it's kept pressed.
- `doubleClick()`: Performs a double-click at the current mouse location.

```java
a.moveToElement(driver.findElement(By.id("twotabsearchtextbox"))).click().keyDown(Keys.SHIFT).sendKeys("hello").doubleClick().build().perform();
```

- `.contextClick()`: Performs a context-click at the current mouse location.

```java
a.moveToElement(move).contextClick().build().perform();
```

```java
public static void main(String[] args) throws InterruptedException {
	WebDriver driver = new ChromeDriver();
	driver.manage().window().maximize();
	driver.get("https://www.amazon.com/ref=nav_bb_logo");
		
	Actions a = new Actions(driver);
	WebElement move = driver.findElement(By.cssSelector("a[id='nav-link-accountList']"));

	a.moveToElement(driver.findElement(By.id("twotabsearchtextbox"))).click().keyDown(Keys.SHIFT).sendKeys("hello").doubleClick().build().perform();
	a.moveToElement(move).contextClick().build().perform();
}
```
## Window handle concepts

- `getWindowHandles()`: Return a set of window handles which can be used to iterate over all open windows of thisWebDriver instance by passing them to switchTo().Options.window() 

```java
Set<String> windows = driver.getWindowHandles();
```

- `.window(String nameOrHandle)`: Switch the focus of future commands for this driver to the window with the given name/handle.
- `iterator()`: Returns an iterator over the elements in this set. The elements are returned in no particular order (unless this set is an instance of some class that provides a guarantee).
- `next()`: Returns the next element in the iteration.

```java
Iterator<String> it = windows.iterator();
String parentId = it.next();
String childId = it.next();
driver.switchTo().window(childId);
```

```java
public static void main(String[] args) throws InterruptedException {
	WebDriver driver = new ChromeDriver();
	driver.get("https://rahulshettyacademy.com/loginpagePractise/");
		
	driver.findElement(By.cssSelector(".blinkingText")).click();
	Set<String> windows = driver.getWindowHandles();
	Iterator<String> it = windows.iterator();
	String parentId = it.next();
	String childId = it.next();
	driver.switchTo().window(childId);
	System.out.println(driver.findElement(By.cssSelector(".im-para.red")).getText());
	String emailId = driver.findElement(By.cssSelector(".im-para.red")).getText().split("at")[1].trim().split(" ")[0];
	driver.switchTo().window(parentId);
	driver.findElement(By.id("username")).sendKeys(emailId);
}
```

## Frames techniques

- `.frame(WebElement frameElement)`: Select a frame using its previously located WebElement. 

```java
driver.switchTo().frame(driver.findElement(By.cssSelector("iframe.demo-frame")));
```

```java
driver.switchTo().frame(0);
```

- `.dragAndDrop(WebElement source, WebElement target)`: A convenience method that performs click-and-hold at the location of the source element, moves to the location of the target element, then releases the mouse.

```java
a.dragAndDrop(source, target).build().perform();
```

- `defaultContent()`: Selects either the first frame on the page, or the main document when a page contains iframes.

```java
driver.switchTo().defaultContent();
```

```java
public static void main(String[] args) throws InterruptedException {
	WebDriver driver = new ChromeDriver();
	driver.get("https://jqueryui.com/droppable/");
		
	System.out.println(driver.findElements(By.tagName("iframe")).size());
		
	driver.switchTo().frame(0);
	// driver.switchTo().frame(driver.findElement(By.cssSelector("iframe.demo-frame")));
	// driver.findElement(By.id("draggable")).click();
		
	Actions a = new Actions(driver);
	WebElement source = driver.findElement(By.id("draggable"));
	WebElement target = driver.findElement(By.id("droppable"));
		
	a.dragAndDrop(source, target).build().perform();
		
	driver.switchTo().defaultContent();
}
```

# Real time exercises (end to end programming)

## How to open the links in separate tabs - optimized solution

- `Keys`: Representations of pressable keys that aren't text.
- `chord(CharSequence... value)`: Simulate pressing many keys at once in a "chord". Takes a sequence of Keys.XXXX or strings; appends each of the values to a string, and adds the chord termination key (Keys.NULL) and returns the resultant string.

```java
String clickonlinkTab = Keys.chord(Keys.CONTROL, Keys.ENTER);
```

## Getting the titles of child tabs with optimized while loop

- `Iterator.hasNext()`: Returns true if the iteration has more elements.(In other words, returns true if next wouldreturn an element rather than throwing an exception.)

```java
while (it.hasNext()) {
	driver.switchTo().window(it.next());
	System.out.println(driver.getTitle());
}
```

```java
public static void main(String[] args) throws InterruptedException {
	//1. Give me the count of links on the page.
	// 2. Count of footer section-
	WebDriver driver = new ChromeDriver();

	driver.get("http://qaclickacademy.com/practice.php");

	System.out.println(driver.findElements(By.tagName("a")).size());

	WebElement footerdriver = driver.findElement(By.id("gf-BIG"));// Limiting webdriver scope

	System.out.println(footerdriver.findElements(By.tagName("a")).size());

	// 3-
	WebElement coloumndriver = footerdriver.findElement(By.xpath("//table/tbody/tr/td[1]/ul"));
	System.out.println(coloumndriver.findElements(By.tagName("a")).size());

	// 4- click on each link in the coloumn and check if the pages are opening-
	for (int i = 1; i < coloumndriver.findElements(By.tagName("a")).size(); i++) {
		String clickonlinkTab = Keys.chord(Keys.CONTROL, Keys.ENTER);

		coloumndriver.findElements(By.tagName("a")).get(i).sendKeys(clickonlinkTab);
		Thread.sleep(5000L);

	} // opens all the tabs
	Set<String> abc = driver.getWindowHandles();// 4
	Iterator<String> it = abc.iterator();

	while (it.hasNext()) {
		driver.switchTo().window(it.next());
		System.out.println(driver.getTitle());
	}
}
```

```java
public static void main(String[] args) {
	WebDriver driver = new ChromeDriver();
	driver.get("https://www.path2usa.com/travel-companions");
	// April 23
	driver.findElement(By.xpath(".//*[@id='travel_date']")).click();

	while (!driver.findElement(By.cssSelector("[class='datepicker-days'] [class='datepicker-switch']")).getText()
				.contains("May")) {
		driver.findElement(By.cssSelector("[class='datepicker-days'] th[class='next']")).click();
	}

	List<WebElement> dates = driver.findElements(By.className("day"));
	// Grab common attribute//Put into list and iterate
	int count = driver.findElements(By.className("day")).size();

	for (int i = 0; i < count; i++) {
		String text = driver.findElements(By.className("day")).get(i).getText();
		if (text.equalsIgnoreCase("21")) {
			driver.findElements(By.className("day")).get(i).click();
			break;
		}
	}
}
```
 
# Practical problems and methods to handle with Selenium

## How to perform scrolling with table and window level using JavaScriptExecutor

- `JavascriptExecutor`: Indicates that a driver can execute JavaScript, providing access to the mechanism to do so.
- -`JavascriptExecutor.executeScript(String script, Object... args)`: Executes JavaScript in the context of the currently selected frame or window.

```java
JavascriptExecutor js = (JavascriptExecutor)driver;
js.executeScript("window.scrollBy(0,500)");	
js.executeScript("document.querySelector(\".tableFixHead\").scrollTop=5000");
```

```java
public static void main(String[] args) throws InterruptedException {
	WebDriver driver = new ChromeDriver();
	driver.get("https://rahulshettyacademy.com/AutomationPractice/");
		
	JavascriptExecutor js = (JavascriptExecutor)driver;
		
	js.executeScript("window.scrollBy(0,500)");		
	Thread.sleep(3000);
	js.executeScript("document.querySelector(\".tableFixHead\").scrollTop=5000");
		
	List<WebElement> values = driver.findElements(By.cssSelector(".tableFixHead td:nth-child(4)"));
		
	int sum = 0;
	for(int i = 0; i < values.size(); i++) {
		sum = sum + Integer.parseInt(values.get(i).getText());
	}
		
	System.out.println(sum);
		
	int total = Integer.parseInt(driver.findElement(By.cssSelector(".totalAmount")).getText().split(":")[1].trim());
		
	Assert.assertEquals(sum, total);
}
```

# Miscellaneous topics in Selenium WebDriver

## Handling HTTPS certifications in automated browsers

- `ChromeOptions`: Class to manage options specific to ChromeDriver. 

```java
ChromeOptions options = new ChromeOptions();
options.setAcceptInsecureCerts(true);
WebDriver driver = new ChromeDriver(options);
```

## Explore Chrome options to set proxies, plugins & paths on Chrome Browser

```java
options.addExtensions(new File("file"));
```

- `Proxy`: Configuration parameters for using proxies in WebDriver.
- `Proxy.setHttpProxy(String httpProxy)`: Specify which proxy to use for HTTP connections.

```java
Proxy proxy = new Proxy();
proxy.setHttpProxy("ipaddress:4444");
options.setCapability("proxy", proxy);
```

## Maximizing window and deleting cookies

- `Options.deleteAllCookies()`: Delete all the cookies for the current domain.

```java
driver.manage().deleteAllCookies();
```

- `Options.deleteCookieNamed(String name)`: Delete the named cookie from the current domain. This is equivalent to setting the namedcookie's expiry date to some time in the past. 

```java
driver.manage().deleteCookieNamed("asdf");
```

## How to take screenshots in Selenium

- `TakesScreenshot`: Indicates a driver or an HTML element that can capture a screenshot and store it in different ways.
- `TakesScreenshot.getScreenshotAs(OutputType<File> target)`: Capture the screenshot and store it in the specified location.
- `.OutputType<T>`: Defines the output type for a screenshot.

```java
File src = ((TakesScreenshot)driver).getScreenshotAs(OutputType.FILE);
```

```java
import org.apache.commons.io.FileUtils;

FileUtils.copyFile(src, new File("C:\\Users\\Stephan\\screenshot.png"));
```

```java
public static void main(String[] args) throws InterruptedException, IOException {
	WebDriver driver = new ChromeDriver();
	driver.get("http://google.com");
	File src = ((TakesScreenshot)driver).getScreenshotAs(OutputType.FILE);
	FileUtils.copyFile(src, new File("C:\\Users\\Stephan\\screenshot.png"));
}
```

## Open connection method to identify status codes of the links

- `HttpURLConnection`: A URLConnection with support for HTTP-specific features.
- `URL(String spec)`: Creates a `URL` object from the `String` representation.
- `URL.openConnection()`: Returns a URLConnection instance that represents a connection to the remote object referred to by the URL. 

```java
HttpURLConnection conn = (HttpURLConnection)new URL(url).openConnection();
```

- `HttpURLConnection.setRequestMethod(String method)`: Set the method for the URL request, one of:

- GET
- POST
- HEAD
- OPTIONS
- PUT
- DELETE
- TRACE

are legal, subject to protocol restrictions. The default method is GET.
- `URLConnection.connect()`: Opens a communications link to the resource referenced by this URL, if such a connection has not already been established.
- `HttpURLConnection.getResponseCode()`: Gets the status code from an HTTP response message.

```java
conn.setRequestMethod("HEAD");
conn.connect();
int responseCode = conn.getResponseCode();
```

## Importance of soft assertions in Selenium WebDriver

- `SoftAssert`: When an assertion fails, don't throw an exception but record the failure. Calling `assertAll()` will cause an exception to be thrown if at least one assertion failed.

```java
SoftAssert a = new SoftAssert();
```

```java
public static void main(String[] args) throws InterruptedException, IOException {
	WebDriver driver = new ChromeDriver();
		
	driver.get("https://rahulshettyacademy.com/AutomationPractice/");
		
	List<WebElement> links = driver.findElements(By.cssSelector("li[class=\"gf-li\"] a"));
	SoftAssert a = new SoftAssert();
		
	for(WebElement link: links) {
		String url = link.getAttribute("href");
		HttpURLConnection conn = (HttpURLConnection)new URL(url).openConnection();
		conn.setRequestMethod("HEAD");
		conn.connect();
		int responseCode = conn.getResponseCode();
			
		a.assertTrue(responseCode<400, "The link with text " + link.getText() + " is broken with code " + responseCode);
	}	
		
	a.assertAll();
}
```

# Selenium Java Streams - Automate sort, pagination, filtering web tables

## Learn everything about Java Streams

### What are streams?
Stream API is new feature available from Java 8.

By using streams, we can perform various aggregate operations on the data returned from collection classes by drastically reducing the complexity of code.

### What is lambda expression?
Lambda expressions introduce the new arrow operator `->` into Java. It divides the lambda expressions in two parts:

1. The left side specifies the parameters required by the expression, which could also be empty if no parameters are required.
2. The right side is the lambda body which specifies the actions of the lambda expression.

### The working of stream

1. Create a stream
2. Perform intermediate operations on the initial stream to transform it into another stream and so on on further intermediate operations.
3. Perform terminal operation on the final stream to get the result.

An important characteristic of intermediate operations is laziness. When executing this code snippet, nothing is printed to the console. That is because intermediate operations will only be executed when a terminal operation is present.

Note: The aggregate operations that we perform on the collection, array or any other data source do not change the data of the source, they simply return a new stream.

- `Collection.stream()`: Returns a sequential `Stream` with this collection as its source.
- `.Stream.filter(Predicate<? super String> predicate)`: Returns a stream consisting of the elements of this stream that match the given predicate.
- `String.startsWith(String prefix)`: Tests if this string starts with the specified prefix.
- `Stream.count()`: Returns the count of elements in this stream.

```java
Long c = names.stream().filter(s -> s.startsWith("A")).count();
```

- `Stream<T>`: A sequence of elements supporting sequential and parallel aggregate operations.
- `Stream.of(String... values)`: Returns a sequential ordered stream whose elements are the specified values.

```java
Long d = Stream.of("Aba", "Bba", "Cba", "Anita", "Abuna").filter(s -> 
	{
		return s.startsWith("A");
	}).count();
```

- `Stream.forEach(Consumer<? super String> action)`: Performs an action for each element of this stream. 

This is a terminal operation. 

```java
names.stream().filter(s -> s.length() > 4).forEach(s -> System.out.println(s));
```

- `Stream.limit(long maxSize)`: Returns a stream consisting of the elements of this stream, truncated to be no longer than `maxSize` in length.

```java
names.stream().filter(s -> s.length() > 4).limit(1).forEach(s -> System.out.println(s));
```

- `String.endsWith(String suffix)`: Tests if this string ends with the specified suffix.
- `Stream.map(Function<? super String, ? extends String> mapper)`: Returns a stream consisting of the results of applying the given function to the elements of this stream.

```java
Stream.of("Ab", "Bba", "Cba", "Anita", "Abun").filter(s -> s.endsWith("a")).map(s -> s.toUpperCase()).forEach(s -> System.out.println(s));
```

- `Stream.sorted()`: Returns a stream consisting of the elements of this stream, sorted according to natural order.

```java
names.stream().filter(s -> s.startsWith("A")).sorted().map(s -> s.toUpperCase()).forEach(s -> System.out.println(s));
```

- `Stream.concat(Stream<? extends String> a, Stream<? extends String> b)`: Creates a lazily concatenated stream whose elements are all the elements of the first stream followed by all the elements of the second stream.

```java
Stream<String> newStream = Stream.concat(names.stream(), names1.stream());
```

- `Stream.anyMatch(Predicate<? super String> predicate)`: Returns whether any elements of this stream match the provided predicate.

```java
boolean flag = newStream.anyMatch(s -> s.equalsIgnoreCase("Adam"));
```

- `Stream.collect(Collector<? super String, Object, List<String>> collector)`: Performs a mutable reduction operation on the elements of this stream using a Collector.
- `stream.Collectors`: Implementations of Collector that implement various useful reduction operations, such as accumulating elements into collections, summarizing elements according to various criteria, etc. 
- `Collectors.toList()`: Returns a `Collector` that accumulates the input elements into a new `List`.

```java
List<String> ls = Stream.of("Ab", "Bba", "Cba", "Anita", "Abun").filter(s -> s.endsWith("a")).map(s -> s.toUpperCase()).collect(Collectors.toList());
```

- `Stream.distinct()`: Returns a stream consisting of the distinct elements (according to Object.equals(Object)) of this stream. 

```java
numbers.stream().distinct().forEach(s -> System.out.println(s));
```

## Perform web table sorting using Selenium Java streams

```java
public static void main(String[] args) throws InterruptedException, IOException {
	WebDriver driver = new ChromeDriver();
		
	driver.get("https://rahulshettyacademy.com/seleniumPractise/#/offers");
	driver.findElement(By.xpath("//tr/th[1]")).click();
		
	List<WebElement> elementsList = driver.findElements(By.xpath("//tr/td[1]"));
		
	List<String> originalList = elementsList.stream().map(s -> s.getText()).collect(Collectors.toList());
		
	List<String> sortedList = originalList.stream().sorted().collect(Collectors.toList());
		
	Assert.assertTrue(originalList.equals(sortedList));
}
```

## Build custom Selenium methods using Streams mapper

```java
public static void main(String[] args) throws InterruptedException, IOException {
	WebDriver driver = new ChromeDriver();
		
	driver.get("https://rahulshettyacademy.com/seleniumPractise/#/offers");
	driver.findElement(By.xpath("//tr/th[1]")).click();
		
	List<WebElement> elementsList = driver.findElements(By.xpath("//tr/td[1]"));
		
	List<String> originalList = elementsList.stream().map(s -> s.getText()).collect(Collectors.toList());
		
	List<String> sortedList = originalList.stream().sorted().collect(Collectors.toList());
		
	Assert.assertTrue(originalList.equals(sortedList));
		
	List<String> price = elementsList.stream()
		.filter(s -> s.getText().contains("Beans"))
		.map(s -> getPriceVeggie(s))
		.collect(Collectors.toList());
		
	price.forEach(a -> System.out.println(a));
	}

private static String getPriceVeggie(WebElement s) {
	String pricevalue = s.findElement(By.xpath("following-sibling::td[1]")).getText();
	return pricevalue;
}
```

## Automating pagination scenarios to search the data using do while loop

```java
public static void main(String[] args) throws InterruptedException, IOException {
	WebDriver driver = new ChromeDriver();
		
	driver.get("https://rahulshettyacademy.com/seleniumPractise/#/offers");
	driver.findElement(By.xpath("//tr/th[1]")).click();
		
	List<String> price;
	do
	{
		List<WebElement> elementsList = driver.findElements(By.xpath("//tr/td[1]"));
		price = elementsList.stream()
			.filter(s -> s.getText().contains("Rice"))
			.map(s -> getPriceVeggie(s))
			.collect(Collectors.toList());
			
		price.forEach(a -> System.out.println(a));
			
		if(price.size() < 1) {
			driver.findElement(By.cssSelector("[aria-label='Next']")).click();
		}
	} while(price.size() < 1);
}

private static String getPriceVeggie(WebElement s) {
	String pricevalue = s.findElement(By.xpath("following-sibling::td[1]")).getText();
	return pricevalue;
}
```

## Filter the web table using Selenium Java streams

```java
public static void main(String[] args) throws InterruptedException, IOException {
	WebDriver driver = new ChromeDriver();
		
	driver.get("https://rahulshettyacademy.com/seleniumPractise/#/offers");
		
	driver.findElement(By.id("search-field")).sendKeys("Rice");
	List<WebElement> veggies = driver.findElements(By.xpath("//tr/td[1]"));
	List<WebElement> filteredList = veggies.stream().filter(veggie -> veggie.getText().contains("Rice")).collect(Collectors.toList());
		
	Assert.assertEquals(veggies.size(), filteredList.size());
}
```

# Selenium 4.0 Latest features

## Introduction to relative locators

- `above()`: Element located above with respect to the specified element
- `below()`: Element located below with respect to the specified element
- `toLeftOf()`: Element located to the left of specified element
- `toRightOf()`: Element located to the right of the specified element

Syntax:

```
driver.findElement(withTagName("XX").above(WebElement))
```

```java
import static org.openqa.selenium.support.locators.RelativeLocator.*;
```

- `RelativeLocator.with(By by)`: Start of a relative locator, finding elements by tag name.

```java
driver.findElement(with(By.tagName("label")).above(nameEditBox)).getText();
```

```java
public static void main(String[] args) throws InterruptedException, IOException {
	WebDriver driver = new ChromeDriver();
		
	driver.get("https://rahulshettyacademy.com/angularpractice/");
		
	WebElement nameEditBox = driver.findElement(By.cssSelector("[name='name']"));
	System.out.println(driver.findElement(with(By.tagName("label")).above(nameEditBox)).getText());
		
	WebElement dateOfBirth = driver.findElement(By.cssSelector("[for='dateofBirth']"));
	driver.findElement(with(By.tagName("input")).below(dateOfBirth)).click();
		
	WebElement iceCreamLabel = driver.findElement(By.xpath("//label[text()='Check me out if you Love IceCreams!']"));
	driver.findElement(with(By.tagName("input")).toLeftOf(iceCreamLabel)).click();
		
	WebElement rdb = driver.findElement(By.id("inlineRadio1"));
	System.out.println(driver.findElement(with(By.tagName("label")).toRightOf(rdb)).getText());	
}
```

## Invoking multiple windows/tabs from Selenium

- `TargetLocator.newWindow(WindowType typeHint)`: Creates a new browser window and switches the focus for future commands of this driver to the new window.

```java
driver.switchTo().newWindow(WindowType.TAB);
```

```java
public static void main(String[] args) throws InterruptedException, IOException {
	WebDriver driver = new ChromeDriver();
		
	driver.get("https://rahulshettyacademy.com/angularpractice/");
	driver.switchTo().newWindow(WindowType.WINDOW);
	Set<String> handles = driver.getWindowHandles();
	Iterator<String> it = handles.iterator();
	String parentWindowId = it.next();
	String childWindowId = it.next();
		
	driver.switchTo().window(childWindowId);
	driver.get("https://rahulshettyacademy.com/");
	String courseName = driver.findElements(By.cssSelector("a[href*='courses.rahulshettyacademy.com/p']")).get(1).getText();
		
	driver.switchTo().window(parentWindowId);
	driver.findElement(By.cssSelector("[name='name']")).sendKeys(courseName);
	driver.quit();
}
```

## Taking WebElement partial screenshot with Selenium

```java
WebElement name = driver.findElement(By.cssSelector("[name='name']"));
name.sendKeys(courseName);
File file = name.getScreenshotAs(OutputType.FILE);
FileUtils.copyFile(file, new File("logo.png"));
```

## Capturing height and width of WebElement for UX validation

- `WebElement.getRect()`: Returns the location and size of the rendered element.

```java
name.getRect().getDimension().getHeight();
name.getRect().getDimension().getWidth();
```

# Framework Part 1 - TestNG

## Running testcases in TestNG without Java compiler

- `@Test`: Mark a class or a method as part of the test.

```java
import org.testng.annotations.Test;

public class TestDemo {

    @Test
    public void demo() {
        System.out.println("hola testng");
    }
}
```

- You need to have `@Test` annotation followed by method
- You can define multiple tests from single class
## Importance of xml file in TestNG configuration

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE suite SYSTEM "http://testng.org/testng-1.0.dtd">
<suite name="All Test Suite">
    <test name="pruebaTestNG">
        <classes>
            <class name="test.TestDemo"/>
            <class name="test.Test2"/>
        </classes>
    </test>
</suite>
```
 
## Prioritizing the test cases with TestNG
rahulonlinetutor@gmail.com

- You can modularize the test cases based on functionality and trigger them accordingly

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE suite SYSTEM "http://testng.org/testng-1.0.dtd">
<suite name="All Test Suite">
    <test name="prueba 3">
        <classes>
            <class name="test.Test3"/>
        </classes>
    </test>

    <test name="prueba 4">
        <classes>
            <class name="test.Test4"/>
        </classes>
    </test>
</suite>
```

## Include and exclude mechanism to control test cases

- You can also get a control on running specific methods from test case.

```xml
<class name="test.Test3">
    <methods>
        <exclude name="mobileLogin1"/>
    </methods>
 </class>
```

```xml
<class name="test.Test4">
    <methods>
        <include name="WebLogin2"/>
    </methods>
</class>
```

## Executing the test cases at package level with regex

```xml
<methods>
    <exclude name="mobile.*"/>
</methods>
```

```xml
<test name="prueba package">
    <packages>
        <package name="test"/>
    </packages>
</test>
```

## TestNG annotations

```java
public class Test2 {

    @AfterTest
    public void lastExecution() {
        System.out.println("I will execute last");
    }
    
    @Test
    public void prueba() {
        System.out.println("probando");
    }

    @BeforeTest
    public void prerequisite() {
        System.out.println("I will execute first");
    }

}
```

```java
@BeforeSuite
public void BfSuite() {
    System.out.println("I am no 1");
}

@AfterSuite
public void afSuite() {
    System.out.println("I am the very last");
}
```

```java
@BeforeMethod
public void beforeEvery() {
    System.out.println("Before each 1");
}

@AfterMethod  
public void afterEvery() {  
    System.out.println("After each 1");  
}
```

## Usage of groups functionality in TestNG

```java
@BeforeClass
public void beforeClass() {
    System.out.println("Before any methods in this class 1");
}

@AfterClass
public void afterClass() {
    System.out.println("After all methods in this class 1");
}
```

```java
@Test(groups = {"Smoke"})
```

```xml
<test name="Regression">
    <groups>
        <run>
            <include name="Smoke"/>
        </run>
    </groups>
    <classes>
        <class name="test.Test2"/>
        <class name="test.Test3"/>
        <class name="test.Test4"/>
        <class name="test.TestDemo"/>
    </classes>
</test>
```

## Annotations helper attributes

The list of methods this method depends on. There is no guarantee on the order on which the methods depended upon will be run, but you are guaranteed that all these methods will be run before the test method that contains this annotation is run:

```java
@Test(dependsOnMethods = {"WebLogin1", "mobileSignOut1"})
```

Whether methods on this class/method are enabled:

```java
@Test(enabled = false)
```

The maximum number of milliseconds this test should take. If it hasn't returned after this time, it will be marked as a FAIL:

```java
@Test(timeOut = 4000)
```

## Parameterising from TestNG xml file

```xml
<parameter name="URL" value="qaclickacademy.com"/>
```

```java
@Parameters({"URL"})
@Test
public void mobileLogin1(String url) {
    System.out.println("Mobile login 1");
    System.out.println(url);
}
```

## DataProvider annotation - Parameterizing test cases

```xml
<test name="prueba 3">
    <parameter name="URL" value="loan.com"/>
    <parameter name="APIkey" value="123456"/>
    <classes>
        <class name="test.Test3"/>
    </classes>
</test>
```

```java
@Parameters({"URL", "APIkey"})
@Test
public void mobileLogin1(String url, String key) {
    System.out.println("Mobile login 1");
    System.out.println(url);
    System.out.println(key);
}
```

```java
@Test(dataProvider = "getData")
public void mobileLogin2(String username, String password) {
    System.out.println("Mobile login 2");
    System.out.println(username);
    System.out.println(password);
}
    
@DataProvider
public Object[][] getData() {
    Object[][] data = new Object[3][2];
    // 1st set
    data[0][0] = "firstUsername";
    data[0][1] = "firstPassword";

    // 2nd set
    data[1][0] = "secondUsername";
    data[1][1] = "secondPassword";

    // 3rd set
    data[2][0] = "thirdUsername";
    data[2][1] = "thirdPassword";

    return data;
}
```

## Listeners interface in TestNG framework
ITestListener interface which implements TestNG listeners

```java
public class Listeners implements ITestListener {

}
```

```xml
<listeners>
    <listener class-name="test.Listeners"/>
</listeners>
```

## Running tests in parallel and generating reports

- `ITestResult`: This class describes the result of a test.
- `getName()`: The name of this TestResult, typically identical to the name of the method.

```java
@Override
public void onTestFailure(ITestResult result) {
    System.out.println("Failed Listeners: " + result.getName());
}
```

```xml
<suite name="All Test Suite" parallel="tests" thread-count="2">

	<test name="prueba 2" parallel="classes" thread-count="2">
```

# Learn Java object oriented principles needed for framework development

## How TestNG annotations help with inheritance to remove boiler plate code in Test

```java
public class PS {

    public void doThis() {
        System.out.println("I am here");
    }

    @BeforeMethod
    public void beforeRun() {
        System.out.println("Run me first");
    }

    @AfterMethod
    public void afterRun() {
        System.out.println("Run me last");
    }
}
```

```java
public class PS1 extends PS {

    @Test
    public void testRun() {
        doThis();
    }

}
```

## How to pass values from test through parameterized constructor and this keyword

```java
public class PS2 {

    int a;

    public PS2(int a) {
        this.a = a;
    }

    public int increment() {
        a = a + 1;
        return a;
    }

    public int decrement() {
        a = a - 1;
        return a;
    }
}
```

```java
public class PS1 extends PS {

    @Test
    public void testRun() {
        PS2 ps2 = new PS2(3);
        int a = 3;
        doThis();
        System.out.println(ps2.increment());
        System.out.println(ps2.decrement());
    }
}
```

## Usage of super keyword in the constructor to pass values to parent class

```java
public class PS3 {
    int a;

    public PS3(int a) {
        this.a = a;
    }

    public int multiplyTwo() {
        a = a * 2;
        return a;
    }

    public int multiplyThree() {
        a = a * 3;
        return a;
    }
}
```

```java
public class PS2 extends PS3 {

    int a;

    public PS2(int a) {
        super(a); // parent constructor is invoked
        this.a = a;
    }

    public int increment() {
        a = a + 1;
        return a;
    }

    public int decrement() {
        a = a - 1;
        return a;
    }
}
```

```java
public class PS1 extends PS {

    @Test
    public void testRun() {
        PS2 ps2 = new PS2(3);
        int a = 3;
        doThis();
        System.out.println(ps2.increment());
        System.out.println(ps2.decrement());

        System.out.println(ps2.multiplyThree());
    }
}
```

# Framework Part 1 - Create Maven project and prepare functional end to end test

- `Stream<T>.findFirst()`: Returns an Optional describing the first element of this stream, or an empty Optional if the stream is empty. 
- `Optional<T>.orElse()`: If a value is present, returns the value, otherwise returns other.

```java
public class StandAloneTest {
    public static void main(String[] args) throws InterruptedException {
        WebDriverManager.chromedriver().setup();
        WebDriver driver = new ChromeDriver();
        driver.manage().timeouts().implicitlyWait(Duration.ofSeconds(10));
        driver.manage().window().maximize();
        driver.get("https://rahulshettyacademy.com/client");

        driver.findElement(By.id("userEmail")).sendKeys("miestasfanjo@gmail.com");
        driver.findElement(By.id("userPassword")).sendKeys("Abita123!");
        driver.findElement(By.id("login")).click();

        String productName = "zara coat 3";

        WebDriverWait wait = new WebDriverWait(driver, Duration.ofSeconds(5));

        wait.until(ExpectedConditions.visibilityOfElementLocated(By.cssSelector(".mb-3")));
        List<WebElement> products = driver.findElements(By.cssSelector(".mb-3"));

        WebElement prod = products.stream()
                .filter(product -> product.findElement(By.cssSelector("b")).getText().equalsIgnoreCase(productName))
                .findFirst().orElse(null);

        prod.findElement(By.cssSelector(".card-body button:last-of-type")).click();

        wait.until(ExpectedConditions.visibilityOfElementLocated(By.cssSelector("#toast-container")));
        wait.until(ExpectedConditions.invisibilityOf(driver.findElement(By.cssSelector(".ng-animating"))));
        driver.findElement(By.cssSelector("[routerlink*='cart']")).click();

        List<WebElement> cartProducts = driver.findElements(By.cssSelector(".cartSection h3"));
        boolean match = cartProducts.stream()
                .anyMatch(product -> product.getText().equalsIgnoreCase(productName));
        Assert.assertTrue(match);
        driver.findElement(By.cssSelector(".totalRow button")).click();

        Actions a = new Actions(driver);
        a.sendKeys(driver.findElement(By.cssSelector("[placeholder='Select Country']")), "india").build().perform();

        wait.until(ExpectedConditions.visibilityOfElementLocated(By.cssSelector(".ta-results")));
        driver.findElement(By.xpath("(//button[contains(@class,'ta-item')])[2]")).click();
        driver.findElement(By.cssSelector(".action__submit")).click();

        String confirmMessage = driver.findElement(By.cssSelector(".hero-primary")).getText();
        Assert.assertTrue(confirmMessage.equalsIgnoreCase("THANKYOU FOR THE ORDER."));

        driver.close();
    }
```

# Framework Part 2 - Design pattern - Page object & factory implementation

## Creating Page object classes for login screen and migrate the test

```java
// SubmitOrderTest.java
LandingPage landingPage = new LandingPage(driver);
```

```java
// LandingPage.java
public class LandingPage {

    WebDriver driver;

    public LandingPage(WebDriver driver) {
        this.driver = driver;
        PageFactory.initElements(driver, this);
    }
    // WebElement userEmail =  driver.findElement(By.id("userEmail"));

    // PageFactory
    @FindBy(id="userEmail")
    WebElement userEmail;

    @FindBy(id="userPassword")
    WebElement password;

    @FindBy(id="login")
    WebElement submit;
}
```

## Implementing action methods for page factory web elements to implement logic

```java
// LandingPage.java
public void goTo() {
    driver.get("https://rahulshettyacademy.com/client");
}

public void loginApp(String email, String password) {
    userEmail.sendKeys(email);
    passwordElement.sendKeys(password);
    submit.click();
}
```

```java
// SubmitOrderTest.java
LandingPage landingPage = new LandingPage(driver);
landingPage.goTo();
landingPage.loginApp("miestasfanjo@gmail.com", "Abita123!");
```

```java
// ProductCatalog.java
@FindBy(css=".mb-3")
List<WebElement> products;
```

## Creating abstract components to reuse the common methods/code in framework

```java
// AbstractComponent.java
public void waitForElementToAppear(By findBy) {
    WebDriverWait wait = new WebDriverWait(driver, Duration.ofSeconds(5));
    wait.until(ExpectedConditions.visibilityOfElementLocated(findBy));
}
```

```java
// ProductCatalog.java
public class ProductCatalog extends AbstractComponent {

    WebDriver driver;

    public ProductCatalog(WebDriver driver) {
        super(driver);
        this.driver = driver;
        PageFactory.initElements(driver, this);
    }

    @FindBy(css=".mb-3")
    List<WebElement> products;

    By productsBy = By.cssSelector(".mb-3");

    public List<WebElement> getProductList() {
        waitForElementToAppear(productsBy);
        return products;
    }
}
```

```java
// SubmitOrderTest.java
ProductCatalog productCatalog = new ProductCatalog(driver);
List<WebElement> products = productCatalog.getProductList();
```
 
## Page object class implementation for product catalogue page and update test

```java
// AbstractComponent.java
public void waitForElementToDisappear(WebElement element) {
    WebDriverWait wait = new WebDriverWait(driver, Duration.ofSeconds(5));
    wait.until(ExpectedConditions.invisibilityOf(element));
}
```

```java
// ProductCatalog.java
By addToCart = By.cssSelector(".card-body button:last-of-type");
By toastMessage = By.cssSelector("#toast-container");

public WebElement getProductByName(String productName) {
    return getProductList().stream()
                .filter(product -> product.findElement(By.cssSelector("b")).getText().equalsIgnoreCase(productName))
                .findFirst().orElse(null);
    }

public void addProductToCart(String productName) {
    WebElement prod = getProductByName(productName);
    prod.findElement(addToCart).click();
    waitForElementToAppear(toastMessage);
    waitForElementToDisappear(spinner);
}
```

```java
// SubmitOrderTest.java
productCatalog.addProductToCart(productName);
```

## Creating methods to abstract component and extending it in page classes

```java
// AbstractComponent.java
public AbstractComponent(WebDriver driver) {
        this.driver = driver;
        PageFactory.initElements(driver, this);
    }

@FindBy(css = "[routerlink*='cart']")
WebElement cartHeader;

public void goToCartPage() {  
    cartHeader.click();  
}
```

```java
// SubmitOrderTest.java

productCatalog.goToCartPage();

CartPage cartPage = new CartPage(driver);
Boolean match = cartPage.verifyProductDisplay(productName);
Assert.assertTrue(match);
cartPage.goToCheckout();
```

Validations cannot go in page object files. Page object files should only have the code to perform actions.

## Wrapping up the whole test with complete refactor into page object model

```java
// SubmitOrderTest.java
public class SubmitOrderTest {
    public static void main(String[] args) throws InterruptedException {
        WebDriverManager.chromedriver().setup();
        WebDriver driver = new ChromeDriver();
        driver.manage().timeouts().implicitlyWait(Duration.ofSeconds(10));
        driver.manage().window().maximize();
        WebDriverWait wait = new WebDriverWait(driver, Duration.ofSeconds(5));

        String productName = "zara coat 3";

        LandingPage landingPage = new LandingPage(driver);
        landingPage.goTo();
        ProductCatalog productCatalog = landingPage.loginApp("miestasfanjo@gmail.com", "Abita123!");

        List<WebElement> products = productCatalog.getProductList();
        productCatalog.addProductToCart(productName);
        CartPage cartPage = productCatalog.goToCartPage();

        Boolean match = cartPage.verifyProductDisplay(productName);
        Assert.assertTrue(match);

        CheckoutPage checkoutPage = cartPage.goToCheckout();
        checkoutPage.selectCountry("india");
        ConfirmationPage confirmationPage = checkoutPage.submitOrder();

        String confirmMessage = confirmationPage.getConfirmationMessage();
        Assert.assertTrue(confirmMessage.equalsIgnoreCase("THANKYOU FOR THE ORDER."));

        driver.close();
    }
}
```

```java
// AbstractComponent.java
public class AbstractComponent {

    WebDriver driver;

    public AbstractComponent(WebDriver driver) {
        this.driver = driver;
        PageFactory.initElements(driver, this);
    }

    @FindBy(css = "[routerlink*='cart']")
    WebElement cartHeader;

    public void waitForElementToAppear(By findBy) {
        WebDriverWait wait = new WebDriverWait(driver, Duration.ofSeconds(5));
        wait.until(ExpectedConditions.visibilityOfElementLocated(findBy));
    }

    public void waitForElementToDisappear(WebElement element) {
        WebDriverWait wait = new WebDriverWait(driver, Duration.ofSeconds(5));
        wait.until(ExpectedConditions.invisibilityOf(element));
    }

    public CartPage goToCartPage() {
        cartHeader.click();
        CartPage cartPage = new CartPage(driver);
        return cartPage;
    }
}
```

```java
// LandingPage.java
public class LandingPage extends AbstractComponent {

    WebDriver driver;

    public LandingPage(WebDriver driver) {
        super(driver);
        this.driver = driver;
        PageFactory.initElements(driver, this);
    }
    // WebElement userEmail =  driver.findElement(By.id("userEmail"));

    // PageFactory
    @FindBy(id="userEmail")
    WebElement userEmail;

    @FindBy(id="userPassword")
    WebElement passwordElement;

    @FindBy(id="login")
    WebElement submit;

    public void goTo() {
        driver.get("https://rahulshettyacademy.com/client");
    }
    public ProductCatalog loginApp(String email, String password) {
        userEmail.sendKeys(email);
        passwordElement.sendKeys(password);
        submit.click();
        ProductCatalog productCatalog = new ProductCatalog(driver);
        return productCatalog;
    }
}
```

```java
// ProductCatalog.java
public class ProductCatalog extends AbstractComponent {

    WebDriver driver;

    public ProductCatalog(WebDriver driver) {
        super(driver);
        this.driver = driver;
        PageFactory.initElements(driver, this);
    }

    @FindBy(css=".mb-3")
    List<WebElement> products;

    @FindBy(css = ".ng-animating")
    WebElement spinner;

    By productsBy = By.cssSelector(".mb-3");
    By addToCart = By.cssSelector(".card-body button:last-of-type");
    By toastMessage = By.cssSelector("#toast-container");

    public List<WebElement> getProductList() {
        waitForElementToAppear(productsBy);
        return products;
    }

    public WebElement getProductByName(String productName) {
        return getProductList().stream()
                .filter(product -> product.findElement(By.cssSelector("b")).getText().equalsIgnoreCase(productName))
                .findFirst().orElse(null);
    }

    public void addProductToCart(String productName) {
        WebElement prod = getProductByName(productName);
        prod.findElement(addToCart).click();
        waitForElementToAppear(toastMessage);
        waitForElementToDisappear(spinner);
    }
}
```

```java
// CartPage.java
public class CartPage extends AbstractComponent {

    WebDriver driver;

    @FindBy(css = ".totalRow button")
    WebElement checkoutButton;

    @FindBy(css = ".cartSection h3")
    List<WebElement> cartProducts;

    public CartPage(WebDriver driver) {
        super(driver);
        this.driver = driver;
        PageFactory.initElements(driver, this);
    }

    public Boolean verifyProductDisplay(String productName) {
        return cartProducts.stream()
                .anyMatch(product -> product.getText().equalsIgnoreCase(productName));
    }

    public CheckoutPage goToCheckout() {
        checkoutButton.click();
        return new CheckoutPage(driver);
    }
}
```

```java
// CheckoutPage.java
public class CheckoutPage extends AbstractComponent {

    WebDriver driver;

    @FindBy(css = "[placeholder='Select Country']")
    WebElement country;

    @FindBy(css = ".action__submit")
    WebElement submit;

    @FindBy(xpath = "//button[contains(@class,'ta-item')])[2]")
    WebElement selectCountry;

    By results = By.cssSelector(".ta-results");

    public CheckoutPage(WebDriver driver) {
        super(driver);
        this.driver = driver;
        PageFactory.initElements(driver, this);
    }

    public void selectCountry(String countryName) {
        Actions a = new Actions(driver);
        a.sendKeys(country, countryName).build().perform();
        waitForElementToAppear(results);
        selectCountry.click();
    }

    public ConfirmationPage submitOrder() {
        submit.click();
        return new ConfirmationPage(driver);
    }
}
```

```java
// ConfirmationPage.java
public class ConfirmationPage extends AbstractComponent {

    WebDriver driver;
    public ConfirmationPage(WebDriver driver) {
        super(driver);
        this.driver = driver;
        PageFactory.initElements(driver, this);
    }

    @FindBy(css = ".hero-primary")
    WebElement confirmationMessage;

    public String getConfirmationMessage() {
        return confirmationMessage.getText();
    }
}
```
 
# Framework Part 3 - Test configuration methods & global properties & parallel runs

## Creating Base test which holds common test configuration methods

```
browser=chrome
```

```java
public class BaseTest {

    public WebDriver driver;

    public void initializeDriver() throws IOException {
        Properties prop = new Properties();
        FileInputStream fis = new FileInputStream(System.getProperty("user.dir") + "\\src\\main\\java\\resources\\GlobalData.properties");
        prop.load(fis);
        String browserName = prop.getProperty("browser");

        if(browserName.equalsIgnoreCase("chrome")) {
            WebDriverManager.chromedriver().setup();
            driver = new ChromeDriver();

        } else if(browserName.equalsIgnoreCase("firefox")) {
            // Firefox
        }

        driver.manage().timeouts().implicitlyWait(Duration.ofSeconds(10));
        driver.manage().window().maximize();
    }
}
```

## Initialize driver and create utility to launch app with BeforeMethod annotation

```java
// BaseTest.java
public LandingPage launchApplication() throws IOException {
    driver = initializeDriver();
    LandingPage landingPage = new LandingPage(driver);
    landingPage.goTo();
    return landingPage;
}
```

## Create new error validation test as per framework standards 

```java
// SubmitOrderTest.java
public class SubmitOrderTest extends BaseTest {

    @Test
    public void submitOrder() throws IOException {
        String productName = "zara coat 3";
        ProductCatalog productCatalog = landingPage.loginApp("miestasfanjo@gmail.com", "Abita123!");

        List<WebElement> products = productCatalog.getProductList();
        productCatalog.addProductToCart(productName);
        CartPage cartPage = productCatalog.goToCartPage();

        Boolean match = cartPage.verifyProductDisplay(productName);
        Assert.assertTrue(match);

        CheckoutPage checkoutPage = cartPage.goToCheckout();
        checkoutPage.selectCountry("india");
        ConfirmationPage confirmationPage = checkoutPage.submitOrder();

        String confirmMessage = confirmationPage.getConfirmationMessage();
        Assert.assertTrue(confirmMessage.equalsIgnoreCase("THANKYOU FOR THE ORDER."));
    }
}
```

```java
// BaseTest.java
public class BaseTest {

    public WebDriver driver;
    public LandingPage landingPage;

    public WebDriver initializeDriver() throws IOException {
        Properties prop = new Properties();
        FileInputStream fis = new FileInputStream(System.getProperty("user.dir") + "\\src\\main\\java\\resources\\GlobalData.properties");
        prop.load(fis);
        String browserName = prop.getProperty("browser");

        if(browserName.equalsIgnoreCase("chrome")) {
            WebDriverManager.chromedriver().setup();
            driver = new ChromeDriver();

        } else if(browserName.equalsIgnoreCase("firefox")) {
            // Firefox
        }

        driver.manage().timeouts().implicitlyWait(Duration.ofSeconds(10));
        driver.manage().window().maximize();
        return driver;
    }

    @BeforeMethod
    public LandingPage launchApplication() throws IOException {
        driver = initializeDriver();
        landingPage = new LandingPage(driver);
        landingPage.goTo();
        return landingPage;
    }

    @AfterMethod
    public void teardown() {
        driver.close();
    }
}
```

```java
// LandingPage.java
@FindBy(css = "[class*='flyInOut']")
WebElement errorMessage;

public String getErrorMessage() {
    waitForWebElementToAppear(errorMessage);
    return errorMessage.getText();
}
```

```java
// ErrorValidations.java
@Test
public void submitOrder() throws IOException {
    landingPage.loginApp("miestasfanjo@gmail.com", "Abita123");
    Assert.assertEquals(landingPage.getErrorMessage(), "Incorrect email or password.");
    }
```

## Create new test methods with dependency attribute based on test strategy design

```java
// SubmitOrderTest.java
@Test(dependsOnMethods = {"submitOrder"})
public void orderHistoryTest() {
    ProductCatalog productCatalog = landingPage.loginApp("miestasfanjo@gmail.com", "Abita123!");
    OrderPage ordersPage = productCatalog.goToOrdersPage();
    Assert.assertTrue(ordersPage.verifyOrderDisplay(productName));
}
```

## How to run tests/classes in parallel & apply groups using testng.xml

```java
// BaseTest.java
@BeforeMethod(alwaysRun = true)
```

```xml
<suite name="All Test Suite" parallel="tests">
    <groups>
        <run>
            <include name="ErrorHandling"/>
        </run>
    </groups>
```

# Framework part 4 - Test strategy - Control tests execution - Run parallel tests

## Integration of hashmap to data provider to send the data as one hash object

```java
// SubmitOrderTest.java
public class SubmitOrderTest extends BaseTest {
    String productName = "zara coat 3";

    @Test(dataProvider = "getData", groups = {"Purchase"})
    public void submitOrder(HashMap<String, String> input) throws IOException {
        ProductCatalog productCatalog = landingPage.loginApp(input.get("email"), input.get("password"));

        List<WebElement> products = productCatalog.getProductList();
        productCatalog.addProductToCart(input.get("product"));
        CartPage cartPage = productCatalog.goToCartPage();

        Boolean match = cartPage.verifyProductDisplay(input.get("product"));
        Assert.assertTrue(match);

        CheckoutPage checkoutPage = cartPage.goToCheckout();
        checkoutPage.selectCountry("india");
        ConfirmationPage confirmationPage = checkoutPage.submitOrder();

        String confirmMessage = confirmationPage.getConfirmationMessage();
        Assert.assertTrue(confirmMessage.equalsIgnoreCase("THANKYOU FOR THE ORDER."));
    }

    @Test(dependsOnMethods = {"submitOrder"})
    public void orderHistoryTest() {
        ProductCatalog productCatalog = landingPage.loginApp("miestasfanjo@gmail.com", "Abita123!");
        OrderPage ordersPage = productCatalog.goToOrdersPage();
        Assert.assertTrue(ordersPage.verifyOrderDisplay(productName));
    }

    @DataProvider
    public Object[][] getData() {
        HashMap<String, String> map = new HashMap<String, String>();
        map.put("email", "miestasfanjo@gmail.com");
        map.put("password", "Abita123!");
        map.put("product", "zara coat 3");

        HashMap<String, String> map1 = new HashMap<String, String>();
        map1.put("email", "shetty@gmail.com");
        map1.put("password", "Iamking@000");
        map1.put("product", "adidas original");

        return new Object[][] {
                {map},
                {map1}
        };
    }
}
```

## How to read the data from JSON files and create the list of hashmaps for testing

```json
[
  {
    "email": "miestasfanjo@gmail.com",
    "password": "Abita123!",
    "product": "ZARA COAT 3"
  },
  {
    "email": "shetty@gmail.com",
    "password": "Iamking@000",
    "product": "ADIDAS ORIGINAL"
  }
]
```

```xml
<!-- https://mvnrepository.com/artifact/com.fasterxml.jackson.core/jackson-databind -->
<dependency>
    <groupId>com.fasterxml.jackson.core</groupId>
    <artifactId>jackson-databind</artifactId>
    <version>2.16.0-rc1</version>
</dependency>
```

```java
// DataReader.java
public List<HashMap<String, String>> getJsonDataToMap(String filePath) throws IOException {
    String jsonContent = FileUtils.readFileToString(new File(filePath), StandardCharsets.UTF_8);
    ObjectMapper mapper = new ObjectMapper();
    List<HashMap<String, String>> data = mapper.readValue(jsonContent, new TypeReference<List<HashMap<String, String>>>(){});
    return data;
}
```

```java
// SubmitOrderTest.java
@DataProvider
public Object[][] getData() throws IOException {
    List<HashMap<String, String>> data = getJsonDataToMap(System.getProperty("user.dir") + "/src/test/java/data/PurchaseOrder.json");
    return new Object[][] { {data.get(0)}, {data.get(1)} };
}
```

## How to create screenshot utility in BaseTest class for catching failed tests

```java
// SubmitOrderTest.java
public String getScreenshot(String testCaseName) throws IOException {
    TakesScreenshot ts = (TakesScreenshot)driver;
    File source = ts.getScreenshotAs(OutputType.FILE);
    File file = new File(System.getProperty("user.dir") + "//reports//" + testCaseName + ".png");
    FileUtils.copyFile(source, file);
    return System.getProperty("user.dir") + "//reports//" + testCaseName + ".png";
}
```

# Framework part 5 - Extent HTML reports & TestNG listeners & thread safe execution

## What are extent reports?

```java
public class ExtentReportDemo {
    ExtentReports extent;

    @BeforeTest
    public void config() {
        String path = System.getProperty("user.dir")+"\\reports\\index.html";
        ExtentSparkReporter reporter = new ExtentSparkReporter(path);
        reporter.config().setReportName("Web Automation Results");
        reporter.config().setDocumentTitle("Test Results");

        extent = new ExtentReports();
        extent.attachReporter(reporter);
        extent.setSystemInfo("Tester", "Stephanie");
    }

    @Test
    public void initialDemo() {
        ExtentTest test = extent.createTest("Initial Demo");

        WebDriver driver = new ChromeDriver();
        driver.get("https://rahulshettyacademy.com");
        System.out.println(driver.getTitle());

        extent.flush();
    }
}
```

## Attaching screenshot to reports from Listeners on automatic test failures

```java
// ExtentReporterNG.java
public class ExtentReporterNG {
    public static ExtentReports getReportObject() {
        String path = System.getProperty("user.dir")+"\\reports\\index.html";
        ExtentSparkReporter reporter = new ExtentSparkReporter(path);
        reporter.config().setReportName("Web Automation Results");
        reporter.config().setDocumentTitle("Test Results");

        ExtentReports extent = new ExtentReports();
        extent.attachReporter(reporter);
        extent.setSystemInfo("Tester", "Stephanie");
        return extent;
    }
}
```

```java
// Listeners.java
public class Listeners extends BaseTest implements ITestListener {

    ExtentTest test;
    ExtentReports extent = ExtentReporterNG.getReportObject();

    @Override
    public void onTestStart(ITestResult result) {
        test = extent.createTest(result.getMethod().getMethodName());
    }

    @Override
    public void onTestSuccess(ITestResult result) {
        test.log(Status.PASS, "Test Passed");
    }

    @Override
    public void onTestFailure(ITestResult result) {
        test.fail(result.getThrowable());
        try {
            driver = (WebDriver) result.getTestClass().getRealClass().getField("driver").get(result.getInstance());
        } catch (Exception e) {
            e.printStackTrace();
        }

        String filePath = null;
        try {
            filePath = getScreenshot(result.getMethod().getMethodName(), driver);
        } catch (IOException e) {
            throw new RuntimeException(e);
        }
        test.addScreenCaptureFromPath(filePath, result.getMethod().getMethodName());
    }

    @Override
    public void onFinish(ITestContext context) {
        extent.flush();
    }
}
```

## Concurrency problem - Implement ThreadLocal class to avoid sync issues in tests

```java
// Listeners.java
public class Listeners extends BaseTest implements ITestListener {

    ExtentTest test;
    ExtentReports extent = ExtentReporterNG.getReportObject();
    ThreadLocal<ExtentTest> extentTest = new ThreadLocal<ExtentTest>();

    @Override
    public void onTestStart(ITestResult result) {
        test = extent.createTest(result.getMethod().getMethodName());
        extentTest.set(test);
    }

    @Override
    public void onTestSuccess(ITestResult result) {
        extentTest.get().log(Status.PASS, "Test Passed");
    }

    @Override
    public void onTestFailure(ITestResult result) {
        extentTest.get().fail(result.getThrowable());
        try {
            driver = (WebDriver) result.getTestClass().getRealClass().getField("driver").get(result.getInstance());
        } catch (Exception e) {
            e.printStackTrace();
        }

        String filePath = null;
        try {
            filePath = getScreenshot(result.getMethod().getMethodName(), driver);
        } catch (IOException e) {
            throw new RuntimeException(e);
        }
        extentTest.get().addScreenCaptureFromPath(filePath, result.getMethod().getMethodName());
    }

    @Override
    public void onFinish(ITestContext context) {
        extent.flush();
    }
}
```

## IRetry analizer to rerun the flaky failed Selenium tests in the framework

```java
// ErrorValidationTests.java
@Test(groups={"ErrorHandling"}, retryAnalyzer = Retry.class)
    public void loginErrorValidation() {
        landingPage.loginApp("miestasfanjo@gmail.com", "Abita123");
        Assert.assertEquals(landingPage.getErrorMessage(), "Incorrect email  password.");
    }
```

```java
// Retry.java
public class Retry implements IRetryAnalyzer {

    int count = 0;
    int maxTry = 1;

    @Override
    public boolean retry(ITestResult result) {
        if(count < maxTry) {
            count++;
            return true;
        }
        return false;
    }
}
```

# Framework part 6 - Test execution from Maven & integration with Jenkins CI/CD

## How to run tests in the framework from terminal using Maven commands

```xml
<profiles>
    <profile>
        <id>Regression</id>
        <build>
            <pluginManagement>
                <plugins>
                    <plugin>
                        <groupId>org.apache.maven.plugins</groupId>
                        <artifactId>maven-surefire-plugin</artifactId>
                        <version>3.2.2</version>
                        <configuration>
	                        <suiteXmlFiles>
	                            <suiteXmlFile>testSuites/testng.xml</suiteXmlFile>
	                        </suiteXmlFiles>
                        </configuration>
                    </plugin>
                </plugins>
            </pluginManagement>
        </build>
    </profile>
</profiles>
```

```shell
mvn test -PRegression
```

## Set global parameters using Maven commands and update tests at run time

```java
// BaseTest.java
String browserName = System.getProperty("browser") != null ? System.getProperty("browser") : prop.getProperty("browser");
```

```shell
mvn test -Dbrowser=firefox
```

## Install Jenkins in the local system for CI/CD

Generic Java package (.war)

```shell
java -jar jenkins.war --httpPort=9090
```

## Integrate the Selenium framework with Jenkins and parameterize Jenkins job

Freestyle -> Advanced -> Use custom workspace -> Build -> Invoke top-level Maven targets -> `test -PRegression -Dbrowser=firefox`

This project is parameterized -> Choice parameter
Name: browserName
Choices: chrome firefox edge

`test -P"$Profile" -Dbrowser="$browserName"`

## How to run tests in headless mode and integrate the parameter in Jenkins

```java
// BaseTest.java
if(browserName.contains("chrome")) {
    ChromeOptions options = new ChromeOptions();
    WebDriverManager.chromedriver().setup();
    if(browserName.contains("headless")) {
        options.addArguments("headless");
    }

    driver = new ChromeDriver(options);
    driver.manage().window().setSize(new Dimension(1440, 900));
}
```

## Schedule Jenkin jobs with regular expressions and trigger nightly automation jobs

Build triggers -> Build periodically -> `H 5 * * *`

# Framework part 7 - Integrating Cucumber Wrapper into Selenium framework

## Introduction to Cucumber and its terminologies

**What is Gherkin?**
It is a business readable, domain specific language that lets you describe software's behavior. 

Example: pop up message is displayed when buttons are clicked and errors are gone

**Keywords used in Cucumber**
Scenario, Feature, Feature file, Scenario outline, Step definition

**Scenarios**
In Cucumber test cases are represented as Scenarios.

Scenarios contain steps which are equivalent to test steps and use the following keywords (Gherkin syntax) to denote them: Given, When, Then, But, and And (case sensitive).

**Given**: Preconditions are mentioned in the Given keyword.
**When**: The purpose of the When steps is to describe the user action.
**Then**: The purpose of the Then steps is to observer the expected output. The observations should be related to the business value/benefit of your Feature description.

**Scenario**: Make minimum due payment
**Given** user is on pay credit card page
**When** user fills all details and selects minimum amount option
**And** user clicks on pay button
**Then** credit card confirmation page is displayed

When we specify a business requirement sometimes there are multiple preconditions, user actions, and expected outcomes. We are going to add one more Scenario and will use the And and But keywords.

**And**: This is used for statements that are an addition to the previous steps and represent positive statements.
**But**: This is used for statements that are in addition to previous steps and represent negative statements.

**Feature and Feature File**
**Feature** represents business requirement.
**Feature File** acts as a Test Suite which consists of all Scenarios.

In Cucumber, Feature files contain Scenarios. We can simply create feature file with feature extension. Scenarios belonging to specific area of application will be grouped into one Feature file.

The text that immediately follows the Feature keyword, and is in the same line, is the Title of the Feature file.

Feature file should contain either Scenario or Scenario Outline. The naming conventions for Feature files should be lowercase with feature extension.

**Feature**: Credit card payment
In order to test credit card payment functionality
As a CC user
I want to complete the payment through online

**Scenario**: Make minimum due payment
**Given** user is on pay credit card page
**When** user fills all details and selects minimum amount option
**And** user clicks on pay button
**Then** credit card confirmation page is displayed

**Scenario**: Pay statement balance
**Given** user is on pay credit card page
**When** user fills all details and selects statement balance option
**And** user clicks on pay button
**Then** credit card confirmation page is displayed

**Scenario**: Enter another amount as 0
**Given** user is on pay credit card page
**When** user fills all details and selects other amount and enters 0
**And** user clicks on pay button
**Then** credit card confirmation page is not displayed
**But** error message is displayed

**Scenario Outline**: Check if string is palindrome
	**Given** I entered `<wordToTest>`
	**When** I test it for palindrome
	**Then** the output should be `<output>`
	**Examples**:
	| wordToTest | output |
	| "Refer" | "true" |
	| "Coin" | "false" |
	| "Space" | "false" |
	| "racecar" | "true" |

## Setting up cucumber dependencies into framework and create feature files

Cucumber JVM: Java
Cucumber JVM: TestNG

```gherkin
@tag
  Feature: Purchase the order from ecommerce website
    
    Background: 
    Given I landed on ecommerce page

    @tag2
    Scenario Outline: Positive test of submitting the order
      Given logged in with username <name> and password <password>
      When I add product <productName> from cart
      And checkout <productName> and submit the order
      Then "THANKYOU FOR THE ORDER." message is displayed on confirmation page

      Examples:
      | name                    | password  | productName |
      | miestasfanjo@gmail.com  | Abita123! | ZARA COAT 3 |
```

## Implement step definitions for features and understand regular expressions

```java
// StepDefinition.java
public class StepDefinition extends BaseTest {

    public LandingPage landingPage;
    ProductCatalog productCatalog;

    @Given("I landed on ecommerce page")
    public void I_landed_on_ecommerce_page() throws IOException {
        landingPage = launchApplication();
    }

    @Given("^Logged in with username (.+) and password (.+)$")
    public void logged_in_username_and_password(String username, String password) {
        productCatalog = landingPage.loginApp(username, password);
    }

    @When("^I add product (.+) from cart$")
    public void I_add_product_to_car(String productName) {
        List<WebElement> products = productCatalog.getProductList();
        productCatalog.addProductToCart(productName);
    }
}
```

## Inject Selenium code in step definition and introduction to Tidy Gherkin plugin

```java
// StepDefinition.java
@When("^Checkout (.+) and submit the order$")
public void checkout_submit_order(String productName) {
    CartPage cartPage = productCatalog.goToCartPage();
	Boolean match = cartPage.verifyProductDisplay(productName);
    Assert.assertTrue(match);
	CheckoutPage checkoutPage = cartPage.goToCheckout();
    checkoutPage.selectCountry("india");
    confirmationPage = checkoutPage.submitOrder();
    }

@Then("{string} message is displayed on confirmation page")
public void message_displayed_confirmationPage(String string) {
    String confirmMessage = confirmationPage.getConfirmationMessage();
    Assert.assertTrue(confirmMessage.equalsIgnoreCase(string));
}
```

## Introduction to TestNG Test Runner to run Cucumber feature files

```java
// TestNGTestRunner.java
@CucumberOptions(features = "src/test/java/cucumber", glue = "stepDefinitions",
monochrome = true, plugin = {"html:target/cucumber.html"})
public class TestNGTestRunner extends AbstractTestNGCucumberTests {
    
}
```

## Control the Cucumber feature files execution with tags and background keywords

```gherkin
@tag
  Feature: Error validation

    @ErrorValidation
    Scenario Outline: Title
      Given I landed on ecommerce page
      When Logged in with username <name> and password <password>
      Then "Incorrect email or password." message is displayed

      Examples:
        | name                    | password  |
        | miestasfanjo@gmail.com  | Abita123  |
```

```java
// TestNGTestRunner.java
@CucumberOptions(features = "src/test/java/cucumber", glue = "stepDefinitions",
monochrome = true, tags = "@Regression", plugin = {"html:target/cucumber.html"})
public class TestNGTestRunner extends AbstractTestNGCucumberTests {

}
```

```xml
<profile>
    <id>CucumberTests</id>

    <build>
        <pluginManagement>
            <plugins>
                <plugin>
                    <groupId>org.apache.maven.plugins</groupId>
                    <artifactId>maven-surefire-plugin</artifactId>
                    <version>3.2.2</version>
                    <configuration>
                        <includes>
                            <include>**/TestNGTestRunner.java</include>
                        </includes>
                    </configuration>
                </plugin>
            </plugins>
        </pluginManagement>
    </build>
</profile>
```

```shell
mvn test -PCucumberTests
```

# CI/CD integration of Selenium framework with Jenkins & GitHub

## What is Continuous Integration & Delivery

![[Pasted image 20240214114539.png]]

## Install fresh Jenkins war & configure necessary plugins & create Selenium job

```
.jenkins
```

Jenkins credentials provider: Jenkins
Kind: Secret text

GitHub: Settings -> Developer Settings -> Personal access tokens -> Tokens (classic) -> Generate new token
Select all permissions

## Understand GitHub Webhook trigger & configure it to activate Selenium Jenkins job

GitHub: Repo -> Settings -> Webhooks -> Add Webhook -> Payload URL
Jenkins: System -> GitHub -> Advanced -> Override Hook URL -> Specify another hook URL for GitHub configuration
Job -> Build Triggers -> GitHub hook trigger for GITScm polling

ngrok

```bash
ngrok http http://localhost:9090
```

# Understand Excel data driven testing functions

## Integrating Excel to DataProvider to parameterize data

```java
public class DataProvide {

    DataFormatter formatter = new DataFormatter();

    @Test(dataProvider = "driveTest")
    public void testCaseData(String greeting, String communication, String id) {
        System.out.println(greeting + " " + communication + " " + id);
    }

    @DataProvider(name = "driveTest")
    public Object[][] getData() throws IOException {
        FileInputStream fis = new FileInputStream("C:\\Users\\Stephan\\Documents\\datadriven.xlsx");
        XSSFWorkbook wb = new XSSFWorkbook(fis);
        XSSFSheet sheet = wb.getSheetAt(0);
        int rowCount = sheet.getPhysicalNumberOfRows();
        XSSFRow row = sheet.getRow(0);
        int colCount = row.getLastCellNum();
        Object[][] data = new Object[rowCount - 1][colCount];
        for (int i = 0; i < rowCount - 1; i++) {
            row = sheet.getRow(i  + 1);
            for (int j = 0; j < colCount; j++) {
                XSSFCell cell = row.getCell(j);
                data[i][j] = formatter.formatCellValue(cell);
            }
        }
        return data;
    }
}
```

# Upload Download functionalities with Selenium using external Excel files

## Download and upload file using file attribute sendKeys with Selenium

```java
WebElement upload = driver.findElement(By.cssSelector("input[type='file']"));
upload.sendKeys("C:\\Users\\Stephan\\Downloads\\download.xlsx");
```

## End to end solution for updating Excel and uploading the file with validations

```java
FileInputStream fis = new FileInputStream(fileName);  
XSSFWorkbook workbook = new XSSFWorkbook(fis);  
  
XSSFSheet sheet = workbook.getSheet("Sheet1");
Row rowField = sheet.getRow(row-1);
Cell cellField = rowField.getCell(col-1);
cellField.setCellValue(updatedValue);

FileOutputStream fos = new FileOutputStream(fileName);
workbook.write(fos);
workbook.close();
fis.close();
```

```java
public class UploadDownload {

    public static void main(String[] args) throws IOException {

        WebDriver driver = new ChromeDriver();
        driver.manage().timeouts().implicitlyWait(Duration.ofSeconds(7));

        driver.get("https://rahulshettyacademy.com/upload-download-test/index.html");

        driver.findElement(By.cssSelector("#downloadButton")).click();
        
        String fileName = "C:\\Users\\Stephan\\Downloads\\download.xlsx";
        String updatedValue = "599";
        String fruitName = "Apple";
        int col = getColumnNumber(fileName, "Price");
        int row = getRowNumber(fileName, "Apple");
        Assert.assertTrue(updateCell(fileName, row, col, updatedValue));
        
        WebElement upload = driver.findElement(By.cssSelector("input[type='file']"));
        upload.sendKeys(fileName);

        By toastLocator = By.cssSelector(".Toastify__toast-body div:nth-child(2)");
        WebDriverWait wait = new WebDriverWait(driver, Duration.ofSeconds(10));
        wait.until(ExpectedConditions.visibilityOfElementLocated(toastLocator));
        String toastText = driver.findElement(toastLocator).getText();
        Assert.assertEquals(toastText, "Updated Excel Data Successfully.");
        wait.until(ExpectedConditions.invisibilityOfElementLocated(toastLocator));

        String priceColumn = driver.findElement(By.xpath("//div[text()='Price']")).getAttribute("data-column-id");
        String actualPrice = driver.findElement(By.xpath("//div[text()='"+fruitName+"']/parent::div/parent::div/div[@id='cell-"+priceColumn+"-undefined']")).getText();
        Assert.assertEquals(actualPrice, updatedValue);
    }

    private static boolean updateCell(String fileName, int row, int col, String updatedValue) throws IOException {
        FileInputStream fis = new FileInputStream(fileName);
        XSSFWorkbook workbook = new XSSFWorkbook(fis);

        XSSFSheet sheet = workbook.getSheet("Sheet1");
        Row rowField = sheet.getRow(row-1);
        Cell cellField = rowField.getCell(col-1);
        cellField.setCellValue(updatedValue);

        FileOutputStream fos = new FileOutputStream(fileName);
        workbook.write(fos);
        workbook.close();
        fis.close();
        return true;
    }

    private static int getRowNumber(String fileName, String text) throws IOException {
        FileInputStream fis = new FileInputStream(fileName);
        XSSFWorkbook workbook = new XSSFWorkbook(fis);

        XSSFSheet sheet = workbook.getSheet("Sheet1");
        Iterator<Row> rows = sheet.iterator();
        int k = 1;
        int rowIndex = -1;
        while (rows.hasNext()) {
            Row row = rows.next();
            Iterator<Cell> cells = row.cellIterator();
            while (cells.hasNext()) {
                Cell cell = cells.next();
                if (cell.getCellType() == CellType.STRING && cell.getStringCellValue().equalsIgnoreCase(text)) {
                    rowIndex = k;
                }
            }
            k++;
        }
        return rowIndex;
    }

    private static int getColumnNumber(String fileName, String colName) throws IOException {
        FileInputStream fis = new FileInputStream(fileName);
        XSSFWorkbook workbook = new XSSFWorkbook(fis);

        XSSFSheet sheet = workbook.getSheet("Sheet1");
        Iterator<Row> rows = sheet.iterator();
        Row firstRow = rows.next();
        Iterator<Cell> cells = firstRow.cellIterator();
        int k = 1;
        int column = 0;
        while (cells.hasNext()) {
            Cell cell = cells.next();
            if (cell.getStringCellValue().equalsIgnoreCase(colName)) {
                column = k;
            }
            k++;
        }
        return column;
    }
}
```

# Cross Browser Testing with Selenium Grid

## What is Selenium Grid? Its advantages of bringing down execution time

**What is Selenium Grid?**
Selenium Grid is a smart proxy server that makes it easy to run tests in parallel on multiple machines.

![[Pasted image 20240125164920.png]]

![[Pasted image 20240125165230.png]]

## Getting started with Grid infrastructure setup - Create components

**Selenium Grid Setup Instructions**
- Download the Selenium Server
- Download Browser drivers and place in the same path where Selenium server is located
- Start the Hub, which eventually starts Router, Distributor, Session Map, New Session Queue, Event Bus  `java -jar <SeleniumJarName> hub`
- Start the node in same machine where Hub is running `java -jar <SeleniumJarName> node --detect-drivers true`
- Start the node in different physical machine `java -jar <SeleniumJarname> node --detect-drivers true --publish-events tcp://<ipaddressofhub> --subscribe-events tcp://<ipaddressofhub>`

## Create Selenium TestNG tests with desired capabilities & remote WebDriver class

```java
public class GoogleTest {

    @Test
    public void homePageCheck() throws MalformedURLException {
        DesiredCapabilities caps = new DesiredCapabilities();
        caps.setBrowserName("chrome");
//        caps.setCapability(CapabilityType.BROWSER_NAME, "chrome");
//        caps.setCapability(CapabilityType.ACCEPT_INSECURE_CERTS, true);

        WebDriver driver = new RemoteWebDriver(new URL("http://192.168.1.9:4444"), caps);
        driver.get("http://google.com");
        System.out.println(driver.getTitle());
        driver.findElement(By.name("q")).sendKeys("hola");
        driver.close();
    }
}
```

# Selenium 4 Chrome Dev tools Protocol (CDP) integration concepts

## What are Chrome Dev Tools? Why do we need this for Selenium testing?

**What are ChromeDevTools?**
Chrome DevTools is a set of web developer tools built directly into the Google Chrome browser.

With Chrome DevTools developers have deeper access to the applications which render on browser.

**What is Chrome DevTools Protocol (CDP)?**
The Chrome DevTools Protocol provide tools to instrument, inspect, debug and profile Chromium, Chrome and other Blink-based browsers.

Selenium 4 introduces powerful commands which are wrapper around the CDP domains to grant access to Chrome DevTools directly from your automated tests.

With this CDP support, Selenium opens up the possibilities of out of box testing with the complete access and control to the browser features within the test.

Examples:
- Capture, monitor and stub the network requests and responses
- Inject session cookies and perform basic auth
- Mock device coordinates for mobile/tabs view
- Check and monitor the site's performance
- Mock geolocations of the user
- Block the network requests
- Mock faster/slower network speeds
- Execute and debug JavaScript
- View console logs

## Understand device metrics override function to simulate browser as mobile

Chromium Driver class has predefined methods to access DevTools.

- `Emulation.setDeviceMetricsOverride`: Overrides the values of device screen dimensions.

```java
ChromeDriver driver = new ChromeDriver();
DevTools devTools = driver.getDevTools();
devTools.createSession();
devTools.send(Emulation.setDeviceMetricsOverride(600, 1000, 50, true, Optional.empty(), Optional.empty(), Optional.empty(), Optional.empty(), Optional.empty(), Optional.empty(), Optional.empty(), Optional.empty()));
driver.get("https://rahulshettyacademy.com/angularAppdemo/");
driver.findElement(By.cssSelector(".navbar-toggler")).click();
Thread.sleep(3000);
driver.findElement(By.linkText("Library")).click();
```

## Importance of executeCdpCommand to construct own CDP functions

```java
ChromeDriver driver = new ChromeDriver();
DevTools devTools = driver.getDevTools();
devTools.createSession();
Map deviceMetrics = new HashMap();
deviceMetrics.put("width", 600);
deviceMetrics.put("height", 1000);
deviceMetrics.put("deviceScaleFactor", 50);
deviceMetrics.put("mobile", true);
driver.executeCdpCommand("Emulation.setDeviceMetricsOverride", deviceMetrics);
driver.get("https://rahulshettyacademy.com/angularAppdemo/");
driver.findElement(By.cssSelector(".navbar-toggler")).click();
Thread.sleep(3000);
driver.findElement(By.linkText("Library")).click();
```

## Localization testing with Selenium 4 using ChromeDevTools protocols

- `Emulation.setGeolocationOverride`: Overrides the Geolocation Position or Error. Omitting any of the parameters emulates position unavailable.

```java
ChromeDriver driver = new ChromeDriver();
DevTools devTools = driver.getDevTools();
devTools.createSession();

Map<String, Object> coordinates = new HashMap<>();
coordinates.put("latitude", 55);
coordinates.put("longitude", 37);
coordinates.put("accuracy", 1);

driver.executeCdpCommand("Emulation.setGeolocationOverride", coordinates);
driver.get("http://google.com");
driver.findElement(By.name("q")).sendKeys("netflix", Keys.ENTER);
Thread.sleep(3000);
driver.findElements(By.cssSelector(".LC20lb")).get(0).click();
String title = driver.findElement(By.cssSelector(".default-ltr-cache-jpuyb8")).getText();
System.out.println(title);
```

## How to extract network responses and status codes with Selenium CDP Listeners

- `Network.enable`: Enables network tracking, network events will now be delivered to the client.

```java
devTools.send(Network.enable(Optional.empty(), Optional.empty(), Optional.empty()));
```

- `Network.responseReceived`: Fired when HTTP response is available.

```java
devTools.addListener(Network.responseReceived(), response -> {
	Response res = response.getResponse();
    System.out.println(res.getUrl());
    System.out.println(res.getStatus());
});
```

- `Network.requestWillBeSent`: Fired when page is about to send HTTP request.

```java
devTools.addListener(Network.requestWillBeSent(), request -> {
    Request req = request.getRequest();
    System.out.println(req.getUrl());
});
```

```java
public class NetworkLogActivity {

    public static void main(String[] args) {

        ChromeDriver driver = new ChromeDriver();
        DevTools devTools = driver.getDevTools();
        devTools.createSession();
        devTools.send(Network.enable(Optional.empty(), Optional.empty(), Optional.empty()));

        devTools.addListener(Network.requestWillBeSent(), request -> {
            Request req = request.getRequest();
            System.out.println(req.getUrl());
        });

        devTools.addListener(Network.responseReceived(), response -> {
            Response res = response.getResponse();
            if (res.getStatus().toString().startsWith("4")) {
                System.out.println(res.getUrl() + " is failing with status code " + res.getStatus());
            }
        });

        driver.get("https://rahulshettyacademy.com/angularAppdemo/");
        driver.findElement(By.cssSelector("button[routerlink*='library']")).click();
    }
}
```

## Intercept network/API responses with Selenium Chrome DevTools

**Fetch Domain**
A domain for letting clients substitute browser's network layer with client code.

- `Fetch.enable`: Enables issuing of requestPaused events. A request will be paused until client calls one of failRequest, fulfillRequest or continueRequest/continueWithAuth.

```java
devTools.send(Fetch.enable(Optional.empty(), Optional.empty()));
```

- `Fetch.requestPaused`: Issued when the domain is enabled and the request URL matches the specified filter. The request is paused until the client responds with one of continueRequest, failRequest or fulfillRequest.
- `Fetch.continueRequest`: Continues the request, optionally modifying some of its parameters.

```java
 devTools.addListener(Fetch.requestPaused(), request -> {
	if (request.getRequest().getUrl().contains("shetty")) {
        String mockUrl = request.getRequest().getUrl().replace("=shetty", "=BadGuy");
        devTools.send(Fetch.continueRequest(request.getRequestId(), Optional.of(mockUrl), Optional.of(request.getRequest().getMethod()),
                Optional.empty(), Optional.empty(), Optional.empty()));
    } else {
        devTools.send(Fetch.continueRequest(request.getRequestId(), Optional.of(request.getRequest().getUrl()), Optional.of(request.getRequest().getMethod()),
                Optional.empty(), Optional.empty(), Optional.empty()));
            }
});
```

```java
public class NetworkMocking {

    public static void main(String[] args) throws InterruptedException {
        ChromeDriver driver = new ChromeDriver();

        DevTools devTools = driver.getDevTools();
        devTools.createSession();

        devTools.send(Fetch.enable(Optional.empty(), Optional.empty()));
        devTools.addListener(Fetch.requestPaused(), request -> {
            if (request.getRequest().getUrl().contains("shetty")) {
                String mockUrl = request.getRequest().getUrl().replace("=shetty", "=BadGuy");
                devTools.send(Fetch.continueRequest(request.getRequestId(), Optional.of(mockUrl), Optional.of(request.getRequest().getMethod()),
                        Optional.empty(), Optional.empty(), Optional.empty()));
            } else {
                devTools.send(Fetch.continueRequest(request.getRequestId(), Optional.of(request.getRequest().getUrl()), Optional.of(request.getRequest().getMethod()),
                        Optional.empty(), Optional.empty(), Optional.empty()));
            }
        });

        driver.get("https://rahulshettyacademy.com/angularAppdemo/");
        driver.findElement(By.cssSelector("button[routerlink*='library']")).click();
        Thread.sleep(3000);
        System.out.println(driver.findElement(By.cssSelector("p")).getText());
    }
}
```

## How to test failed network requests calls with Selenium CDP commands

```java
Optional<List<RequestPattern>> patterns = Optional.of(Arrays.asList(new RequestPattern(Optional.of("*GetBook*"), Optional.empty(), Optional.empty())));
devTools.send(Fetch.enable(patterns, Optional.empty()));
```

- `Fetch.failRequest`: Causes the request to fail with specified reason.

```java
devTools.send(Fetch.failRequest(request.getRequestId(), ErrorReason.FAILED));
```

```java
public class NetworkFailedRequest {

    public static void main(String[] args) {
        ChromeDriver driver = new ChromeDriver();

        DevTools devTools = driver.getDevTools();
        devTools.createSession();

        Optional<List<RequestPattern>> patterns = Optional.of(Arrays.asList(new RequestPattern(Optional.of("*GetBook*"), Optional.empty(), Optional.empty())));
        devTools.send(Fetch.enable(patterns, Optional.empty()));

        devTools.addListener(Fetch.requestPaused(), request -> {
            devTools.send(Fetch.failRequest(request.getRequestId(), ErrorReason.FAILED));
        });

        driver.get("https://rahulshettyacademy.com/angularAppdemo/");
        driver.findElement(By.cssSelector("button[routerlink*='library']")).click();
    }
}
```

## Blocking unwanted network request calls to speed up the execution with Selenium

- `Network.setBlockedURLs`: Blocks URLs from loading.

```java
devTools.send(Network.setBlockedURLs(ImmutableList.of("*.jpg", "*.css")));
```

```java
public class BlockNetworkRequests {

    public static void main(String[] args) {
        ChromeDriver driver = new ChromeDriver();

        DevTools devTools = driver.getDevTools();
        devTools.createSession();

        devTools.send(Network.enable(Optional.empty(), Optional.empty(), Optional.empty()));
        devTools.send(Network.setBlockedURLs(ImmutableList.of("*.jpg", "*.css")));

        driver.get("https://rahulshettyacademy.com/angularAppdemo/");
        driver.findElement(By.linkText("Browse Products")).click();
        driver.findElement(By.linkText("Selenium")).click();
        driver.findElement(By.cssSelector(".add-to-cart")).click();
        System.out.println(driver.findElement(By.cssSelector("p")).getText());
    }
}
```
## How to emulate network speed with Selenium ChromeDevTools integration

- `Network.emulateNetworkConditions`: Activates emulation of network conditions.

```java
devTools.send(Network.emulateNetworkConditions(false, 3000, 20000, 100000, Optional.of(ConnectionType.ETHERNET)));
```

- `Network.loadingFailed`: Fired when HTTP request has failed to load.

```java
devTools.addListener(Network.loadingFailed(), loadingFailed -> {
    System.out.println(loadingFailed.getErrorText());
});
```

```java
public class NetworkSpeed {

    public static void main(String[] args) throws InterruptedException {
        ChromeDriver driver = new ChromeDriver();

        DevTools devTools = driver.getDevTools();
        devTools.createSession();

        devTools.send(Network.enable(Optional.empty(), Optional.empty(), Optional.empty()));
//        devTools.send(Network.emulateNetworkConditions(false, 3000, 20000, 100000, Optional.of(ConnectionType.ETHERNET)));
        devTools.send(Network.emulateNetworkConditions(true, 3000, 20000, 100000, Optional.of(ConnectionType.ETHERNET)));
        devTools.addListener(Network.loadingFailed(), loadingFailed -> {
            System.out.println(loadingFailed.getErrorText());
        });

        driver.get("https://rahulshettyacademy.com/angularAppdemo/");
        driver.findElement(By.cssSelector(".navbar-toggler")).click();
        Thread.sleep(3000);
        driver.findElement(By.linkText("Library")).click();
    }
}
```

## Working with basic authentication using Selenium uriPredicate function

```java
public class BasicAuthentication {

    public static void main(String[] args) {
        ChromeDriver driver = new ChromeDriver();

        Predicate<URI> uriPredicate = uri -> uri.getHost().contains("httpbin.org");
        ((HasAuthentication) driver).register(uriPredicate, UsernameAndPassword.of("foo", "bar"));
        driver.get("https://httpbin.org/basic-auth/foo/bar");
    }
}
```

## How to log JavaScript errors from Selenium script to console for debugging

```java
public class ConsoleLogsCapture {

    public static void main(String[] args) {
        ChromeDriver driver = new ChromeDriver();

        driver.get("https://rahulshettyacademy.com/angularAppdemo/");
        driver.findElement(By.linkText("Browse Products")).click();
        driver.findElement(By.partialLinkText("Selenium")).click();
        driver.findElement(By.cssSelector(".add-to-cart")).click();
        driver.findElement(By.linkText("Cart")).click();
        driver.findElement(By.id("exampleInputEmail1")).clear();
        driver.findElement(By.id("exampleInputEmail1")).sendKeys("2");

        LogEntries entry = driver.manage().logs().get(LogType.BROWSER);
        List<LogEntry> logs = entry.getAll();
        for (LogEntry e : logs) {
            System.out.println(e.getMessage());
        }
    }
}
```

# Database connection to Selenium test cases

## Creating database in MySQL server

```mysql
create database Qadbt;
```

## Creating tables in databases

```mysql
use Qadbt;
create table employeeinfo(name varchar(20), id int, location varchar(20), age int);
```

## Inserting records into table

```mysql
describe employeeinfo;
insert into employeeinfo values('sam', 1, 'newjersey', 21);
```

## Steps to connect database info to Selenium 1

```java
public class DbConnection {

    public static void main(String[] args) throws SQLException {
        Connection con = DriverManager.getConnection("jdbc:mysql://localhost:3306/demo", "root", "toor");
        Statement statement = con.createStatement();
        ResultSet resultSet = statement.executeQuery("select * from credentials where scenario = 'zerobalancecard'");
        while (resultSet.next()) {
            System.out.println(resultSet.getString("username"));
            System.out.println(resultSet.getString("password"));
        }
    }
}
```

# File uploading (AUTO IT) & downloading with Selenium

## Handling window authentication pop ups with Selenium

```
http://username:password@siteURL
```

## Examples on handling pop ups with modified WebDriver URL

```java
public class WindowPopUp {

    public static void main(String[] args) {
        WebDriver driver = new ChromeDriver();

        driver.get("http://admin:admin@the-internet.herokuapp.com/");
        driver.findElement(By.linkText("Basic Auth")).click();
    }
}
```

## What is AutoIT? Installation details

- Shift focus to the file upload window
- Set text/path into file name edit box
- Click open to upload file

## Inspecting the window objects and converting into AutoIT code

```AutoIT
ControlFocus("Abrir", "", "Edit1")
ControlSetText("Abrir", "", "Edit1", "C:\Users\Stephan\Downloads\L3.pdf")
ControlClick("Abrir", "", "Button1")
```

## End to end example on uploading file with AutoIT Selenium

- Au3info - record window component objects
- Build script - scite.exe
- Save it - .au3 extension
- Convert file into .exe by compiling by .au3 file
- Call .exe file with Runtime class in Java into your Selenium tests

```java
Runtime.getRuntime().exec("C:\\Users\\Stephan\\Downloads\\autoit.exe");
```

## Steps to complete the flow to download file from application with Selenium

```java
File f = new File("C:\\Users\\Stephan\\Downloads\\L3.zip");
if (f.exists()) {
    System.out.println("File found");
}
```

## ChromeDriver options to configure download path of browser

```java
String downloadPath = System.getProperty("user.dir");

ChromeOptions options = new ChromeOptions();
HashMap<String, Object> chromePrefs = new HashMap<>();
chromePrefs.put("profile.default_content_settings.popups", 0);
chromePrefs.put("download.default_directory", downloadPath);
options.setExperimentalOption("prefs", chromePrefs);
WebDriver driver = new ChromeDriver(options);
```

```java
File f = new File(downloadPath + "/L3.zip");
if (f.exists()) {
    System.out.println("File found");
    if (f.delete()) {
        System.out.println("File deleted");
    }
}
```

```java
public class FileUpload {

    public static void main(String[] args) throws InterruptedException, IOException {

        String downloadPath = System.getProperty("user.dir");

        ChromeOptions options = new ChromeOptions();
        HashMap<String, Object> chromePrefs = new HashMap<>();
        chromePrefs.put("profile.default_content_settings.popups", 0);
        chromePrefs.put("download.default_directory", downloadPath);
        options.setExperimentalOption("prefs", chromePrefs);
        WebDriver driver = new ChromeDriver(options);

        driver.get("https://altoconvertpdftojpg.com/");
        driver.findElement(By.cssSelector("#browse")).click();
        Thread.sleep(3000);

        Runtime.getRuntime().exec("C:\\Users\\Stephan\\Downloads\\autoit.exe");

        WebDriverWait wait = new WebDriverWait(driver, Duration.ofSeconds(10));
        wait.until(ExpectedConditions.elementToBeClickable(By.cssSelector("#submit_btn")));
        driver.findElement(By.cssSelector("#submit_btn")).click();
        wait.until(ExpectedConditions.visibilityOfElementLocated(By.partialLinkText("Download")));
        driver.findElement(By.partialLinkText("Download")).click();
        Thread.sleep(5000);

        File f = new File(downloadPath + "/L3.zip");
        if (f.exists()) {
            System.out.println("File found");
            if (f.delete()) {
                System.out.println("File deleted");
            }
        }
    }
}
```

# Maven - Build management tool in depth information

## Importance of Surefire plugin in executing tests

```xml
<project>
  [...]
  <build>
    <pluginManagement>
      <plugins>
        <plugin>
          <groupId>org.apache.maven.plugins</groupId>
          <artifactId>maven-surefire-plugin</artifactId>
          <version>3.2.5</version>
        </plugin>
      </plugins>
    </pluginManagement>
  </build>
  [...]
</project>
```

```bash
mvn clean
```

```bash
mvn compile
```

```bash
mvn test
```

## Integration of TestNG with Maven

```xml
<plugins>
    [...]
      <plugin>
        <groupId>org.apache.maven.plugins</groupId>
        <artifactId>maven-surefire-plugin</artifactId>
        <version>3.2.5</version>
        <configuration>
          <suiteXmlFiles>
            <suiteXmlFile>testng.xml</suiteXmlFile>
          </suiteXmlFiles>
        </configuration>
      </plugin>
    [...]
</plugins>
```

```bash
mvn -Dtest=TestCircle test
```

## Switching the tests with Maven profiling

```xml
<profiles>
	<profile>
	<id>Regression</id>
	<build>
	    <pluginManagement>
			<plugins>
			    <plugin>
			        <groupId>org.apache.maven.plugins</groupId>
			        <artifactId>maven-surefire-plugin</artifactId>
			        <version>3.2.5</version>
				    <configuration>
			        <suiteXmlFiles>
			            <suiteXmlFile>testng2.xml</suiteXmlFile>
			        </suiteXmlFiles>
				    </configuration>
		        </plugin>
	      </plugins>
	    </pluginManagement>
	</build>
	</profile>
</profiles>
```

```bash
mvn test -PRegression
```

# Java OOPs basics for Selenium Part 1

## What are abstract classes and how different they are from interfaces

**What is abstraction?**
Abstraction is a process of hiding the implementation details from the user, only the functionality will be provided to the user. In other words, the user will have the information on what the object does instead of how it does it.

**Abstract classes and methods**
Class which is declared with the `abstract` keyword as an abstract class in Java.

It can have abstract (method without the body) and non-abstract methods (method with the body).

Abstraction classes achieve partial abstraction.

Interfaces on the other hand are used for 100% abstraction.

We cannot instantiate object for abstract class. Child classes are forced to implement abstract methods of parent class.

**Differences between abstract classes and interfaces**

**Interface**:
1. Interface contains only abstract methods
2. Access specifiers for methods in interface must be public
3. Variables defined must be public, static, final
4. To implement an interface we use `implements` keyword

**Abstract class**
1. Abstract class can contain abstract methods, concrete methods or both
2. Except private we can have any access specifier for methods in abstract class
3. Except private variables can have any access specifiers
4. To implement an abstract class we use `extends` keyword

```java
public abstract class ParentAirCraft {

    public void engine() {
        System.out.println("Follow engine guidelines");
    }

    public void safetyGuidelines() {
        System.out.println("Follow safety guidelines");
    }

    public abstract void bodyColor();
}
```

```java
public class ChildEmirites extends ParentAirCraft {

    public static void main(String[] args) {
        ChildEmirites c = new ChildEmirites();
        c.engine();
        c.safetyGuidelines();
        c.bodyColor();
    }
    @Override
    public void bodyColor() {
        System.out.println("Red color in the body");
    }
}
```

## Explaining function overloading

```java
public class Overload {

    public void getData(int a) {
        System.out.println(a);
    }

    public void getData(String a) {
        System.out.println(a);
    }

    public void getData(int a, int b) {
        System.out.println(a);
        System.out.println(b);
    }

    public static void main(String[] args) {
        Overload o = new Overload();
        o.getData(2);
        o.getData("hello");
        o.getData(5, 6);
    }
}
```

# Core Java Part 2

## Date class concepts

```java
public class DateDemo {
    public static void main(String[] args) {
        Date d = new Date();
        SimpleDateFormat sdf = new SimpleDateFormat("M/d/yyyy");
        SimpleDateFormat sdf2 = new SimpleDateFormat("M/d/yyyy hh:mm:ss");
        System.out.println(d.toString());
        System.out.println(sdf.format(d));
        System.out.println(sdf2.format(d));
    }
}
```

## Working with calendar objects

```java
public class CalendarDemo {
    public static void main(String[] args) {
        Calendar cal = Calendar.getInstance();
        SimpleDateFormat sdf = new SimpleDateFormat("M/d/yyyy hh:mm:ss");
        System.out.println(sdf.format(cal.getTime()));
        System.out.println(cal.get(Calendar.DAY_OF_MONTH));
        System.out.println(cal.get(Calendar.AM_PM));
        System.out.println(cal.get(Calendar.MINUTE));
    }
}
```

## How constructor play a crucial role

```java
public class ConstructDemo {

    public ConstructDemo() {
        System.out.println("I am in the constructor");
    }

    public void getData() {
        System.out.println("I am the method");
    }

    public static void main(String[] args) {
        ConstructDemo cd = new ConstructDemo();
    }
}
```

## Types of constructors and their usage

```java
public ConstructDemo(int a, int b) {
    System.out.println("I'm in the parameterized constructor");
}

public static void main(String[] args) {
    ConstructDemo cd = new ConstructDemo();
    ConstructDemo cd1 = new ConstructDemo(4, 5);
}
```

## What is super keyword

```java
public class ParentDemo {
    String name = "Stephan";
}
```

```java
public class ChildDemo extends ParentDemo {

    String name = "algo";

    public void getStringData() {
        System.out.println(name);
        System.out.println(super.name);
    }

    public static void main(String[] args) {
        ChildDemo cd = new ChildDemo();
        cd.getStringData();
    }
}
```

## super keyword practical usage

```java
public class ParentDemo {
    String name = "Stephan";

    public ParentDemo() {
        System.out.println("Parent class constructor");
    }

    public void getData() {
        System.out.println("I am parent class");
    }
}
```

```java
public class ChildDemo extends ParentDemo {

    String name = "algo";

    public ChildDemo() {
        super();
        System.out.println("Child class constructor");
    }

    public void getStringData() {
        System.out.println(name);
        System.out.println(super.name);
    }

    public void getData() {
        super.getData();
        System.out.println("I am in child class");
    }

    public static void main(String[] args) {
        ChildDemo cd = new ChildDemo();
        cd.getStringData();
        cd.getData();
    }
}
```

## Importance of this keyword

```java
public class ThisDemo {

    int a = 2;

    public void getData() {
        int a = 3;
        System.out.println(a);
        System.out.println(this.a);
    }

    public static void main(String[] args) {
        ThisDemo td = new ThisDemo();
        td.getData();
    }
}
```

## Static and non static importance in Java

```java
public class StaticVar {

    String name;
    String address;
    static String city;
    static int i;
    
    static {
        city = "Bangalore";
        i = 0;
    }

    StaticVar(String name, String address) {
        this.name = name;
        this.address = address;
        i++;
        System.out.println(i);
    }

    public void getAddress() {
        System.out.println(address + " " + city);
    }

    public static void getCity() {
        System.out.println(city);
    }

    public static void main(String[] args) {
        StaticVar obj = new StaticVar("Bob", "Marthalli");
        StaticVar obj1 = new StaticVar("Ram", "Jayangar");
        obj.getAddress();
        obj1.getAddress();
        
        StaticVar.getCity();
        StaticVar.i = 4;
        obj.address = "XYZ";
    }
}
```

## Final keyword

Class as final you cannot extend that class.
Final method cannot be overriden.

```java
final class FinalDemo {

    final void getData() {
        
    }

    public static void main(String[] args) {
        final int i = 4;
    }
}
```

## Packages and their usage in OOPs

Set of classes, interfaces, etc.
java.lang - default package
java.util

## Types of packages and how they will help in real time

Class A can use the Class B directly by creating object if both Class A and Class B belongs to same package.

## Importance of access modifiers

- Default: access method anywhere only in package
- Public: access across all packages

## Difference between public and private modifiers

- Private: cannot access method or variable outside class
- Protected: access only in subclasses (other packages)

## Different kinds of exceptions

```java
public class ExceptionDemo {

    public static void main(String[] args) {
        int b = 7;
        int c = 0;

        try {
            int k = b / c;
            System.out.println(k);
        } catch (Exception e) {
            System.out.println("I caught the error");
        }
    }
}
```

## Try catch mechanism to handle exceptions

```java
public class ExceptionDemo {

    public static void main(String[] args) {
        int b = 7;
        int c = 0;

        try {
           /* int k = b / c;
            System.out.println(k);*/

            int[] arr = new int[5];
            System.out.println(arr[7]);
        }
        catch (ArithmeticException e) {
            System.out.println("I caught arithmetic exception");
        }
        catch (IndexOutOfBoundsException e) {
            System.out.println("I caught index bound exception");
        }
        catch (Exception e) {
            System.out.println("I caught the exception");
        }
    }
}
```

## Importance of finally block

```java
try {
	int[] arr = new int[5];
    System.out.println(arr[7]);
}
finally {
    System.out.println("Delete cookies");
}
```

# Core Java Part 3 - Collections API

## What are Java collections
The Java Collections framework is a collection of interfaces and classes which help in storing and processing the data efficiently.

### List
A List is an ordered collection (sometimes called a sequence). Lists may contain duplicate elements.

Classes that implement List interface:
- ArrayList
- LinkedList
- Vector

### Set
A Set is a collection that cannot contain duplicate elements. However it makes no guarantees concerning the order of iteration.

Classes that implement Set interface:
- HashSet 
- LinkedHashSet
- TreeSet

### Map
A Map is an object that maps keys to values. A map cannot contain duplicate keys.

Classes that implement Map interface:
- HashMap
- TreeMap
- LinkedHashMap

## Implementation of ArrayList

```java
public class ArrayListExample {

    public static void main(String[] args) {
        ArrayList<String> a = new ArrayList<>();
        a.add("aba");
        a.add("java");
        a.add("java");
        System.out.println(a);
        a.add(0, "student");
        System.out.println(a);

       /* a.remove(1);
        a.remove("java");
        System.out.println(a);*/

        System.out.println(a.get(2));
        System.out.println(a.contains("testing"));

        System.out.println(a.indexOf("aba"));
        System.out.println(a.isEmpty());
        System.out.println(a.size());
    }
}
```

## Implementation of Set interface

```java
public class HashSetExample {

    public static void main(String[] args) {
        HashSet<String> hs = new HashSet<>();
        hs.add("Mexico");
        hs.add("Russia");
        hs.add("Brazil");
        hs.add("Brazil");
        System.out.println(hs);
        hs.remove("Brazil");
        System.out.println(hs);
        System.out.println(hs.isEmpty());
        System.out.println(hs.size());
    }
}
```

## Examples of HashSet using Iterator

```java
public class HashSetExample {

    public static void main(String[] args) {
        HashSet<String> hs = new HashSet<>();
        hs.add("Mexico");
        hs.add("Russia");
        hs.add("Brazil");
        hs.add("Finland");
        hs.add("Estonia");
        System.out.println(hs);
/*        System.out.println(hs);
        System.out.println(hs.isEmpty());
        System.out.println(hs.size());*/

        Iterator<String> iterator = hs.iterator();
        while (iterator.hasNext()) {
            System.out.println(iterator.next());
        }
    }
}
```

## Implementation of Map interface

```java
public class HashMapExample {

    public static void main(String[] args) {
        HashMap<Integer, String> hm = new HashMap<>();
        hm.put(0, "Hello");
        hm.put(1, "goodbye");
        hm.put(42, "morning");
        hm.put(3, "evening");

        System.out.println(hm.get(2));

        hm.remove(42);

        Set es = hm.entrySet();
        Iterator it = es.iterator();
        while (it.hasNext()) {
            Map.Entry mp = (Map.Entry) it.next();
            System.out.println(mp.getKey());
            System.out.println(mp.getValue());
        }
    }
}
```

## Difference between HashMap and HashTable

1. **Synchronization or thread safe**. This is the most important difference between the two. HashMap is not synchronized and not thread safe. On the other hand, HashTable is thread safe and synchronized. When to use HashMap? Answer is if your application does not require any multi-threading task. In other words, HashMap is better for non threading applications. HashTable should be used in multithreading applications.
2. **Null keys and null values**. HashMap allows one null key and any number of null values, while HashTable does not allow null keys and null values in the HashTable object.
3. **Iterating the values**. HashMap object values are iterated by using iterator. HashTable is the only class other than vector which uses enumerator to iterate the values of HashTable object.

## Practice exercise: printing unique number

```java
public class CollectionDemo {

    public static void main(String[] args) {
        int[] array = {4, 5, 5, 5, 4, 6, 6, 9, 4};

        ArrayList<Integer> arrayList = new ArrayList<>();

        for (int i = 0; i < array.length; i++) {
            int k = 0;
            if (!arrayList.contains(array[i])) {
                arrayList.add(array[i]);
                k++;
                for (int j = i + 1; j < array.length; j++) {
                    if (array[i] == array[j]) {
                        k++;
                    }
                }
                /*System.out.println(array[i]);
                System.out.println(k);*/
                if (k == 1) {
                    System.out.println(array[i] + " is unique number");
                }
            }
        }
    }
}
```

## OOPs interview questions

1. What are the core concepts of OOPs?
	1. Abstraction
	2. Encapsulation
	3. Polymorphism
	4. Inheritance
	5. Composition
	6. Association
	7. Aggregation

2. What is abstraction?
Abstraction is an OOPs concept to construct the the structure of the real world objects. During this construction only the general states and behaviors are taken and more specific states and behaviors are left aside for the implementers.

3. What is encapsulation?
Encapsulation is an OOPs concept to create and define the permissions and restrictions of an object and its member variables and methods. A very simple example to explain the concept is to make the member variables of a class private and providing public getter and setter methods. Java provides four types of access of level modifiers: public, protected, no modifier and private.

4. What is the difference between abstraction and encapsulation?
	1. "Program to interfaces, not implementations" is the principle for abstraction and "encapsulate what varies" is the OO principle for encapsulation.
	2. Abstraction provides a general structure of a class and leaves the details for the implementers. Encapsulation is to create and define the permissions and restrictions of an object and its member variables and methods.
	3. Abstraction is implemented in Java using interface and abstract class while encapsulation is implemented using four types of access level modifiers: public, protected, no modifier and private.

5. What is polymorphism?
Polymorphism is the occurrence of something in various forms. Java supports various forms of polymorphism like polymorphic reference variables, polymorphic method, polymorphic return types and polymorphic argument types.

6. What is inheritance?
A subclass can inherit the states and behaviors of its super class is known as inheritance.

7. What is multiple inheritance?
A child class inheriting states and behaviors from multiple parent classes is known as multiple inheritance.

8. What is the diamond problem in inheritance?
In case of multiple inheritance, suppose class A has two subclasses B and C, and a class D has two super classes B and C. If a method present in A is overriden by both B and C but not by D, then from which class D will inherit that method, B or C? This problem is known as diamond problem.

9. Why Java does not support multiple inheritance?
Java was designed to be a simple language and multiple inheritance introduces complexities like diamond problem. Inheriting states or behaviors from two different type of classes is a case which in reality very rare and it can be achieved easily through an object association.

10. What is static binding and dynamic binding?
Static or early binding is resolved at compile time. Method overloading is an example of static binding.
Dynamic or late or virtual binding is resolved at run time. Method overriding is an example of dynamic binding.

11. What is a class?
A class is the specification or template of an object.

12. What is an object?
Object is instance of class.

## Java interview questions

1. What is runtime polymorphism?
Runtime polymorphism or dynamic method dispatch is a process in which a call to an overriden method is resolved at runtime rather than at compile time.
In this process, an overriden method is called through the reference variable of a super class.

2. What is the difference between abstraction and encapsulation?
Abstraction hides the implementation details whereas encapsulation wraps code and data into a single unit.

3. What is abstract class?
A class that is declared as abstract is known as abstract class. It needs to be extended and its methods implemented. It cannot be instantiated.

4. Can there be any abstract method without abstract class?
No, if there is any abstract method in a class, that class must be abstract.

5. Can you use abstract and final both with a method?
No, because abstract method needs to be overriden whereas you can't override a final method.

6. Is it possible to instantiate the abstract class?
No, abstract class can never be instantiated.

7. What is interface?
Interface is a blueprint of a class that have static constants and abstract methods. It can be used to achieve full abstraction and multiple inheritance.

8. Can you declare an interface method static?
No, because methods of an interface is abstract by default, and static and abstract keywords can't be used together.

9. Can an interface be final?
No, because its implementation is provided by another class.

10. What is marker interface?
An interface that have no data member and method is known as marker interface. For example Serializable, Cloneable, etc.

11. What is the difference between abstract class and interface?
**Abstract class**
	1. An abstract class can have method body (non-abstract methods)
	2. An abstract class can have instance variables.
	3. An abstract class can have constructor.
	4. An abstract class can have static methods.
	5. You can extend one abstract class
**Interface**
	1. Interface has only abstract methods.
	2. An interface cannot have instance variables.
	3. Interface cannot have constructor.
	4. Interface cannot have static methods.
	5. You can implement multiple interfaces.

12. Can we define private and protected modifiers for variables in interfaces?
No, they are implicitly plubic.

13. When can an object reference be cast to an interface reference?
An object reference can be cast to an interface reference when the object implements the referenced interface.