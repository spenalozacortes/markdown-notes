# L1
## Introduction

![[Pasted image 20231013081329.png]]
## Version Control System (git)

### Why do we need VCS?
Version control systems/version control software allows multiple developers and team members to work together on the same project. A version control system is critical to ensure everyone has access to the latest code and modifications are tracked.

### Commits and branches
Commits are the main building blocks of a git project. Commits can be thought of as snapshots or milestones along the timeline of a git project. Commits are created with the `git commit` command to capture the state of a project at that point in time. Git snapshots are always committed to the local repository.

Each commit consists of following parts:

- snapshot of changes (the files you modified/added/removed)
- message (written by you, should have some info regarding the changes you've introduced)
- name and email of author (so that we could easily track who made the change)

Commits are also linked to each other, so we can tell which one comes first and if there's anything coming after it.

One of the most important features of VCS (git) is branching.

Branch is a specific pointer to one of the commits - saying that this is the branch and all of the linked commits as well. Once you make a new commit to the same branch - this pointer moves forward automatically. That means that every branch in git - not a set of commits, it's not static - it's a moveable pointer which points to the last commit in branch. If you address to the branch (i.e. checkout branch) then you'll receive all of the changes stored in last (and all previous linked to it) commits.

### gitignore
When you build a project it usually generates lots of different files which are used to run it - sometimes it will be a .exe file, sometimes it will be a .json specification. They are specific to your device and won't be needed if someone else wants to run the project. Any IDE you're using automatically generates these files anew each time you build a project.

As you can see, there's no need to store them in your repository - anyone who clones it and builds a project will get their own version of these.

To make sure that these files won't get to your repository you can use gitignore file. It's a specific file which mentions files and folders that are not supposed to end up in your repository.

### Pull requests
Pull request is a tool that can be used to review changes in branches before merging them together.

## Testing Library

### Glossary

**Unit testing**
A type of software testing where individual units or components of a software are tested. The purpose is to validate that each unit of the software code performs as expected. Unit Testing is done during the development (coding phase) of an application by the developers. Unit Tests isolate a section of code and verify its correctness. A unit may be an individual function, method, procedure, module, or object.

**Testing**
A method to check whether the actual software product matches expected requirements and to ensure that software product is defect free. It involves execution of software/system components using manual or automated tools to evaluate one or more properties of interest. The purpose of software testing is to identify errors, gaps or missing requirements in contrast to actual requirements.

**Test case**
A singular set of actions or instructions for a tester to perform that validates a specific aspect of a product or application functionality. If the test fails, the result might be a software defect that the organization can triage.

**Defect**
A variation or deviation of the software application from end user's requirements or original business requirements. A software defect is an error in coding which causes incorrect or unexpected results from a software program which does not meet actual requirements. Testers might come across such defects while executing the test cases.

**Automated testing**
Approach to verifying code that makes use of special software tools that execute tests automatically and then compare actual test results with expected results.

### Testing libraries: best practices

#### Autotest structure

**Test body**
- Method that describes (calls other methods) all steps and validations by test scenario
- Test method must include steps and validations number equal to steps and validations number in test case (test scenario)

![[Pasted image 20231013124405.png]]

- Test validations are implemented by **asserts**

![[Pasted image 20231013124704.png]]

- Asserts must include **messages**

![[Pasted image 20231013124909.png]]

![[Pasted image 20231013125109.png]]
![[Pasted image 20231013125137.png]]

- Pre & post conditions must be implemented by built-in mechanisms

![[Pasted image 20231013125311.png]]

- Pre & post conditions mustn't be implemented in test method body

![[Pasted image 20231013132252.png]]
![[Pasted image 20231013132320.png]]

![[Pasted image 20231013132413.png]]
![[Pasted image 20231013132439.png]]

#### Parametrisation
- The way to run autotest on different sets of test data

### Testing libraries: documentation

Java: [TestNg](https://testng.org/doc/documentation-main.html)
C#: [NUnit](https://docs.nunit.org/articles/nunit/intro.html)
JS: [Mocha](https://mochajs.org/), [Chai](https://www.chaijs.com/)

## Selenium WebDriver

### Locators. xPath

**What's the locator?**
Locator - a string, that identifies a UI element (exactly the one we need)

Locator should be:

1. Stable (won't break due to a small change on web page)
2. Precise (points exactly to the needed UI element)

#### Types of locators
There are multiple types of locators that could be used:

- XPath locator (`//div[@id='userName']`)
- CSS selector (`div.username`)
- Selenium built-in subtypes (By.id, By.name, By.class, etc)

#### Absolute and relative path
When writing an xpath locator you can use two types of path:

1. **Absolute path**. Uses single slash as a separator (`/div/span/classname`). Not reliable as any page change could cause that part of this path could change and we won't be able to find element.
2. **Relative path**. Uses double slash (`//div//span//classname`). Doesn't rely on page structure which is more reliable and stable.

#### Indexes
Let's imagine we have written a locator, but instead of 1 element it shows 5. What do we do? You can add index to a written locator (`//div//span[5]`) which will allow you to reach 5th element on the page by this locator.

#### Tools (methods)
Sometimes it's hard to create a locator using unique ID or name, but we could use its part. How?

- Contains - allows you to find element using a part of its tag/text/name/id/etc.
- And/or - allows you to combine multiple parts of the locator (like `contains(@id,'name') AND contains(@id,'profile')`)

#### XPath axes
Sometimes you can find dynamic IDs on page or a very bad page structure. In that case it'd be better to link locator to parent/child/sibling element, and then using axes, get back to needed element.

- Following
- Following-sibling
- Preceding
- Parent
- etc.

#### Decent locator

- Stable
- Precise
- Easy to read
- Doesn't have redundant parts

#### Practice

![[Pasted image 20231013193201.png]]

`a[contains(@class,'apphub_sectionTab']//span[text()='Broadcasts']`

#### Overview

- Use relative path
- Use indexes if there's nothing unique to use
- Use axes and logical operators to make locator more stable
- Try to keep locator readable

### SWD: best practices

#### Selenium WebDriver benefits

- Open source
- Multi-browser support
- Multi-language support
- Ease of implementation

#### Benefits of using WebDriver Manager

- No need in downloading driver.exe
- Easy to control installed version
- Versatility of solution

#### General rules of working with browser

- Initiate/close driver instance before and after each test
- Set up driver even before we start working with it
- We should work with only one instance at a time

#### SWD classes

- WebDriver (`.get(...)`; `.findElement(...)`; `.findElements(...)`)
- WebElement (`.click()`; `sendKeys(...)`; `isDisplayed()`; `getText()`)
- By (`id(...)`; `xpath(...)`; `className(...)`; `cssSelector(...)`)

```java
WebDriverManager.chromedriver().setup();
WebDriver driver = new ChromeDriver();
WebElement loginField = driver.findElement(By.id("login"));
loginField.sendKeys("User Login");
```

#### Waits in Selenium

- Implicit - set up only once for whole project
- Explicit - used in case if needed for separate element

```java
// Implicit wait
driver.manage().timeouts().implicitlyWait(10, TimeUnit.SECONDS);

// Explicit wait
WebDriverWait wait = new WebDriverWait(driver, 30);
wait.until(ExpectedConditions.visibilityOfElementLocated(By.ID("id")));
```

#### Assertions

- Should be made by using test libraries instruments
- Should be performed by using "assert" methods

```java
driver.get("https://www.amazon.com");
String actualTitle = driver.getTitle();
String expectedTitle = "Welcome to Amazon";
Assert.assertEquals(actualTitle, expectedTitle, "Title is not correct");
```

#### How to check we're on a needed page?

- Unique element of the page
- Any element of your choice (preferably if it can be found only on this page)
 
## Project Structure

### Patterns

#### Why is it important to build the project with good structure?

- Readability of the project - quick search for the necessary classes and methods
- Easily maintained by other developers
- Avoid code duplication

#### Pattern PageObject

- Separation of test code and page descriptions
- Consolidation of all actions for working with a web page in one place
- Avoid code duplication

```c#
public class UserinterfaceTests 
{
	private IWebDriver driver;
	private const string url = "URL";

	[SetUp]
	public void Setup() 
	{
		ChromeOptions options = new ChromeOptions();
		driver = new ChromeDriver(options);
		driver.Navigate().GoToUrl(url);
	}

	[Test]
	public void AuthorizationTest() 
	{
		var loginButton = driver.FindElement(By.Id("LoginButton"));
		Assert.IsTrue(loginButton.Displayed, "Login Page is not opened");

		var loginField = driver.FindElement(By.Id("username"));
		var passwordField = driver.FindElement(By.Id("password"));

		loginField.SendKeys("login");
		passwordField.SendKeys("password");

		loginButton.Click();
	}
}
```

```c#
namespace Userinterface.PageObjects
{
	public class LoginPage
	{
		private static IWebDriver driver;
		private IWebElement loginButton = driver.FindElement(By.Id("LoginButton"));
		private IWebElement loginField = driver.FindElement(By.Id("username"));
		private IWebElement passwordField = driver.FindElement(By.Id("password"));

		public LoginPage(IWebDriver webDriver)
		{
			driver = webDriver;
		}

		public void SetLogin(string login)
		{
			loginField.SendKeys(login);
		}

		public void SetPassword(string password)
		{
			passwordField.SendKeys(password);
		}

		public bool IsLoginPageOpened()
		{
			return loginButton.Displayed;
		}

		public void ClickLoginButton()
		{
			loginButton.Click();
		}
	}
}
```

```c#
namespace Userinterface.Tests
{
	public class UserinterfaceTests
	{
		private IWebDriver driver;
		private const string url = "URL";

		[SetUp]
		public void Setup()
		{
			ChromeOptions options = new ChromeOptions();
			driver = new ChromeDriver(options);
			driver.Navigate.GoToUrl(url);
		}

		[Test]
		public void AuthorizationTest()
		{
			var loginPage = new LoginPage(driver);

			Assert.IsTrue(loginPage.IsLoginPageOpened(), "Login Page is not opened");

			loginPage.SetLogin("login");
			loginPage.SetPassword("password");

			loginPage.ClickLoginButton();
		}
	}
}
```

#### Singleton
Singleton is a design pattern that restricts the instantiation of a class to one "single" instance.

Main advantages:

- A global access to driver
- Single instance

```c#
public static class Singleton
{
	private static IWebDriver driver;

	public static IWebDriver Driver()
	{
		if (driver == null)
		{
			driver = new ChromeDriver();
		}
		return driver;
	}
}
```

```c#
public class LoginPage
{
	private IWebElement loginButton = Singleton.Driver().FindElement(By.Id("LoginButton"));
	private IWebElement loginField = Singleton.Driver().FindElement(By.Id("username"));
	private IWebElement passwordField = Singleton.Driver().FindElement(By.Id("password"));

	public LoginPage()
	{
	}

	public void SetLogin(string login)
	{
		loginField.SendKeys(login);
	}

	public void SetPassword(string password)
	{
		passwordField.SendKeys(password);
	}

	public bool IsLoginPageOpened()
	{
		return loginButton.Displayed;
	}
}
```

```c#
namespace Userinterface.Tests
{
	public class UserinterfaceTests
	{
		private const string url = "URL";

		[SetUp]
		public void Setup()
		{
			Singleton.Driver().Navigate().GoToUrl(url);
		}

		[Test]
		public void AuthorizationTest()
		{
			var loginPage = new LoginPage();

			Assert.IsTrue(loginPage.IsLoginPageOpened(), "Login Page is not opened");

			loginPage.SetLogin("login");
			loginPage.SetPassword("password");

			loginPage.ClickLoginButton();
		}
	}
}
```

#### Browser Factory
The two important ideas of browser factory:

- Hide the logic of initializing an object inside the factory.
- Refer to the object using a common interface instead of the concrete class.

### Utility classes

#### Why do we need them?
Sometimes we need additional functionality, which doesn't fit in any of existing classes. For example, for the test we need to generate a random number, where should we put this method? It doesn't fit into Page Object classes (as this logic isn't part of page itself) and it would be wrong to put in test method (we want to be able to reuse this logic without copying lines of code each time). In this case, we can create RandomUtils class and put this method (let's say we name it GetRandomNumber) in it.

#### How to use?
Since these classes are utility ones, so they are helping functionality and not the ones we're testing, we don't want to create any instances of them. In order to achieve it, we can declare methods in these utility classes as static - this way we'll be able to address methods without creating an instance (object) of the class itself. For example from above, it'll be `RandomUtils.GetRandomNumber()`.

#### How many should be in there?
Number of these classes depends solely on how many of them you need. If you have functionality which doesn't belong to page or test and you can reuse it, put it in Utility class. Name of such class should reflect what's inside, so that it'd be easy to find needed methods. Please avoid names like `CommonUtils` or `BasicUtils`, these names are bad examples. Try something more specific - `ParseUtils`, `RandomUtils`, `FileUtils`, etc.

### Singleton|Object pool implementation
Implementation of Singleton in Java/C#/JS + DriverUtils with method navigateTo.

```java
// Singleton|Object pool class
public class Browser {
	private static WebDriver driver;

	public static WebDriver getDriver() {
		if (driver == null) {
			driver = new ChromeDriver();
		}
		return driver;
	}

	public static void quitDriver() {
		driver.quit();
		driver = null;
	}
}
```

```java
// DiverUtils class
public class DriverUtils {
	public static void navigate(String url) {
		Browser.getDriver().navigate().to(url);
	}
}
```

### BaseElement and Page Object implementation
Regular WebElement (class provided by Selenium) is the class that we'll be using only in some specific cases. For interactions with elements and as a way to declare and store them, use provided BaseElement.

This class is a wrap around locator, and all of the logic of working with WebElement is encapsulated into BaseElement class itself.

This class represents basic element, any of them, so it may have some other methods. In the provided class you'll find methods:

-  `getElement` - internal method which allows us to search for the element (and avoid code duplication)
- `click` - public method which can be used in page classes to interact with the element

If you see that test case requires a new type of interaction with element (getting/sending text, checking if element is displayed/hidden, etc.), feel free to expand the provided class, just make sure to follow the same logic.

Also on this page you may find an example of page class (ExamplePage) which shows how to use these elements in code.

```java
// BaseElement
public class BaseElement {
	private By locator;

	public BaseElement(By locator) {
		this.locator = locator;
	}

	public void click() {
		getElement().click();
	}

	public String getText() {
		return getElement().getText();
	}

	protected WebElement getElement() {
		return Browser.getDriver().findElement(locator);
	}
}
```

```java
// ExamplePage
public class ExamplePage {
	private BaseElement loginButton = new BaseElement(By.xpath("//div[@auto-id='abc']"));
	private BaseElement userNameForm = new BaseElement(By.id("userNameWelcomeForm"));

	public void clickLoginButton() {
		loginButton.click();
	}

	public String getUserName() {
		return userNameForm.getText();
	}
}
```

> We must work with elements only inside page object classes. So it's better to make element fields private. It is not allowed to return WebElements or find them outside of the page object class. Because we must store and use elemetns in one place.You can only return some state of the element like isDisplayed or some info about the element for example text

> 1 method in page object should work with 1 element. When you manipulate with a lot of elements in one method – you don’t have possibility to use only one part of it. For example if you have Register() method that works with login, password, name fields and you need to use only login in the next test – you have to split the logic.Make 1 method for 1 element and if you want to combine some actions – create step method. Steps can be a separate class or a private method in your test class

> I know this practice to return page object instance. But actually it's better not to use it, it have a lot of disadvantages
## Elements

### Different types of elements
In previous task you were working with only one type of element - BaseElement

Probably you've noticed that elements on pages behave in a different way, so we should follow this pattern. If we have a button for login on page, a regular user would be able to click on it (and that's what they would do in most of the cases), so we are not supposed to send text to this element, as this may break the scenario we're following.

Another thing is that if we could declare type of element explicitly, it would be much easier to navigate through page object classes, understanding which element we can use in what way.

Creating a new type of element is easy - create a new class, inherit it from BaseElement and use instances of it in page classes.

Since we'll already have specific implementation, BaseElement for us will be some sort of pattern, a blueprint to use. Make sure to mark BaseElement as abstract to prevent creating any instances of it.

```java
// Button class
public class Button extends BaseElement {
	public Button(By locator) {
		super(locator);
	}
}
```

### Data types: config data, test data, constants
For any project or framework, it's important to be able to configure the way it works, without amending code, so for this reason we're using two configs: one for config data and one for test data.

#### Config data
Type of data that can be used to change the behavior of the driver or test solution in general.

For example, using config data we can change the browser we're working with, set a new value for timeout, define the main URL, set some capabilities, etc. Mostly these settings will be related to driver.

#### Test data
Type of data that affects only tests. For example, the test case you're working on says that you should type the name of the game to a search field and click search. Name of the game in this case is not related to the logic of test case, scenario would work the same if you type 'Dota' / 'Dota 2' / 'Dota 3', as you'll need to perform same actions.

#### Constants
Some values that we're using in code can be configured, but they are not updated regularly or they are not supposed to change at all. These types of data we can save as constants in code.

For example, you need to generate a random string. You'll need to have an alphabet to do so, so you use it in method, but you can see that it can be reused so you save it as a const value in the same class. There's no need to put this alphabet into config or test data, but it's still important to separate it from the specific method that uses it.


> Switching tabs shouldn't be in the page object.  
That's utility logic and should be in separate Util class. To understand what is util think about:

1. Are there too many lines of code or nested loops
2. Will this logic be reused
3. Is the current class/method responsible for this logic or is it logically possible to take it out  
    Also try to have the method do one thing and be relatively small. If you have too many strings that work with different variables, multiple if constructs or loops - create additional methods for that logic.

> '2023' is test data because one of these reasons:

1. test-case (task documentation) has the exact text to check
2. Changing this value will affect the logic of the test  
    Test data must be in a separate file, for example testData.json  
    We must do it to be able to quickly find this value and change it without going into the code.

## Forms

### Better approach to Page Object
Page Object pattern is a way to describe pages we work with.

It's pretty easy to use once you get used to it, but it has a flaw: page may contain hundreds of elements and it's hard to keep track of each of them. Page classes may grow significantly and reach thousands of lines of code.

Updating and refactoring page classes in these conditions may take significant amount of time.

Let's reimagine the way we see the page. Instead of interpreting it as a single monolith, let's try to separate it into smaller parts.

For example, Steam main page has:

- Top navigation bar
- Middle navigation bar
- Footer
- Left menu and so on

Each of these parts can be put into classes, but we need to follow some rules in this case:

- Each of these classes will be called a form (i.e. TopNavigationForm, MiddleNavigationForm, etc.)
- Forms can't be used by themselves, but only as part of another page (for example, you won't be able to address to its method as  `TopNavigationForm.clickStoreButton()` from your test, it should be a part of page  `StorePage.topNavigationForm.clickStoreButton()`)

### BaseForm implementation
For all of the forms and pages there is a common functionality that we use: checking whether page is open or not.

This action is done via checking if unique element (the one we've chosen) is present on page or not, so this method would return true or false.

This logic is common as there won't be any changes regardless of what type of page we're working with, only the unique element will differ, meaning that we can create a base class, which will contain this logic, so we won't have to implement same method every time we create a new page object class.

```java
public class BaseForm {
	private final BaseElement uniqueElement;

	public BaseForm(BaseElement uniqueElement) {
		this.uniqueElement = uniqueElement;
	}

	public boolean isPageOpen() {
		return uniqueElement.isExist();
	}
}
```

### Forms quiz
**Which methods should be in BaseForm class?**
isPageOpen

BaseForm is responsible for common behavior of all pages and forms, the only shared logic between them is how we validate if page is open (using unique element).

Navigation/refresh etc. are not related to Page Object, it's a functionality of driver and should be put to DriverUtils class.

**What's the difference between form and page?**
Forms can't be used by itself, only as part of a page

Form is basically just a part of a page, that we can see on multiple pages, so we can reuse it (include as a part of a page to all of the classes of pages that use it).

**What's the correct way of addressing to a form in a test method?**

```java
MainPage mainPage = new MainPage();
mainpage.navigationForm.clickForward();
```

Forms are part of the page, they cannot be instantiated or used by themselves, only as a part of another page.
 
> 0 and 1 are magic numbers here, move to test data  
That’s magic number. Magic numbers are hard-coded numeric values that are used throughout code without any explanation or context. It's bad to use magic numbers in code for the following reasons:

1. Code readability: Magic numbers make code harder to read and understand, especially for other developers who are not familiar with the codebase. It's difficult to know what a number represents without any explanation or context.
2. Code maintainability: If a magic number is used in multiple places throughout the codebase, it can be difficult to update or change the value without introducing bugs or unintended consequences.
3. Code reuse: Magic numbers cannot be reused in other parts of the code or in other projects, which can lead to redundancy and inefficiency.
4. Debugging: When a bug occurs, it can be difficult to trace the root cause if magic numbers are used without any explanation or context.  
    To avoid these issues, it's important to use named constants or variables instead of magic numbers in code. This makes the code more readable, maintainable, reusable, and easier to debug.

# L2

## REST API (GET/POST)

> in non-static approach we can maintain state in a instance of the class if neccessary.
> if we decide to run tests in parallel, then non-static methods will have better level of isolation, because each instance will have its state, and the risk of interference between threads will be less. so, this approach will be more thread safe

