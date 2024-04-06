# What is Cypress?
Cypress is an end-to-end testing framework for web applications. It is an open-source JavaScript-based tool that enables developers to write and run automated tests on their web applications in a fast and efficient manner. Cypress provides a simple and intuitive API, real-time reloading, built-in debugging, and an automatic wait-time feature that helps avoid flaky tests.

Cypress runs directly in the browser and can interact with the application in the same way that users do, allowing for fast and accurate testing. It also provides features such as time-travel debugging and automatic screenshots that help developers identify and fix issues quickly.

Overall, Cypress is a powerful and user-friendly testing tool that helps developers and QA engineers ensure that their web applications are working as expected.

_**For more information, please follow this link:**_ [https://docs.cypress.io/guides/overview/why-cypress](https://docs.cypress.io/guides/overview/why-cypress)
## The pros and cons of Cypress compared to webdrivers
In addition to Cypress, webdrivers are quite popular in JavaScript and other languages. Let's look at the pros and cons of Cypress compared to webdrivers.

**The benefits of Cypress:**

1. **Faster Test Execution** - Cypress is much faster than WebdriverIO due to its architecture that runs tests directly in the browser without the need for Selenium or any other third-party tool.
2. **Easy Setup** - Cypress has a simple setup process compared to WebdriverIO, which requires additional setup for Selenium or other third-party tools.
3. **Built-in Test Runner** - Cypress comes with a built-in test runner, which allows developers to run tests and debug them easily.
4. **Automatic Waiting and Retries** - Cypress automatically waits for DOM elements to become available, which eliminates the need for explicit waiting and retrying that is required in WebdriverIO.
5. **Real-time Reloads** - Cypress automatically reloads the browser in real-time when code changes are made, which makes it easier to develop and test code
6. **Automatic Screenshots and Videos** - Cypress automatically captures screenshots and videos of test runs, making it easier to diagnose issues and share test results with stakeholders.
7. **Rich API** - Cypress provides a rich set of APIs for interacting with the DOM and browser, making it easier to write tests. Although the Cypress API may seem rather awkward at first, because it's very different from the webdrivers many people are used to.

Overall, Cypress is a more modern and developer-friendly testing framework compared to WebdriverIO, with faster test execution, easier setup, and a more integrated approach to testing.

**The disadvantages of cypress:**

1. **Limited Browser Support** - Cypress only supports Chrome, Firefox, and Electron browsers, whereas WebdriverIO supports multiple browsers like Chrome, Firefox, Safari, Edge, and Internet Explorer.
2. **Limited Cross-Browser Testing** - Due to the limited browser support, it is difficult to perform cross-browser testing with Cypress.
3. **No Parallel Execution** - Currently, Cypress does not have native support for parallel test execution, while WebdriverIO allows for parallel execution, which can be useful for large test suites.
4. **Limited Third-Party Integrations** - Cypress has limited support for third-party integrations, while WebdriverIO has integrations with popular tools like Selenium Grid, Sauce Labs, and BrowserStack.
5. **Lack of Flexibility** - Cypress provides a highly opinionated approach to testing, which may not suit all testing needs. WebdriverIO, on the other hand, provides more flexibility to customize tests to specific needs.
6. **Reliance on JavaScript** - Cypress is a JavaScript-only testing framework, which may not be suitable for teams that prefer other programming languages for testing.

Overall, while Cypress offers many benefits, its limited browser support and lack of flexibility may make it less suitable for some testing scenarios compared to WebdriverIO.

**_You can also read about the key differences between Cypress and Webdrivers at this link: [https://docs.cypress.io/guides/overview/key-differences](https://docs.cypress.io/guides/overview/key-differences)_**

# Cypress installation

1. Install Node.js and IDE.  
    
    [Download last version Node.js](https://nodejs.org/en/download) 
    
    [Download Visual Studio Code](https://code.visualstudio.com/)
    
2. Open IDE and your project folder **File → Open Folder...** and select desirable folder.
3. Open terminal in VSCode **Terminal → New Terminal.** New terminal is open.
4. Run the Cypress installation command **_npm install cypress_**. 
5. Run Cypress for the first time to set it up using **_npx cypress open_**. Cypress window is open.
6. Next, you need to select the type of testing. (For automated tests in the absolute majority of cases we choose E2E Testing)
7. Cypress then offers us the standard file structure and we agree to it by clicking **_Continue_**.
8. Select a browser for testing. (Electron is a built-in browser provided by Cypress)
9. In the browser window that opens, select **_"Scaffold example specs"_** to automatically generate test examples.
10. You can see which test files will be generated by Cypress and click **_"Ok"_**

# Project overview

## Cypress config overview
Let's take a little closer look at what options may be in the Cypress configuration file. Below we'll take a look at the most frequently used options.

1. **baseUrl**: Sets the base URL for all relative Cypress commands.
    
    `"baseUrl": "[https://www.example.com](https://www.example.com/)"`
    
2. **defaultCommandTimeout**: Specifies the timeout duration in milliseconds for **cy** commands.
    
    `"defaultCommandTimeout": 5000`
    
3. **pageLoadTimeout**: Sets the maximum time allowed for a page to load before considering it a failure.
    
    `"pageLoadTimeout": 10000`
    
4. **viewportWidth** and **viewportHeight**: Defines the width and height of the browser's viewport.
    
    `"viewportWidth": 1280,`
    
    `"viewportHeight": 720`
5. **screenshotsFolder**: Specifies the folder path where screenshots are saved.
    
    `"screenshotsFolder": "cypress/screenshots"`
    
6. **supportFile**: Points to a JavaScript file that Cypress loads before running tests, allowing you to define custom commands and utilities.
    
    `"supportFile": "cypress/support/index.js"`
    
7. **reporter**: Determines the reporter used for test result output, allowing you to choose different reporting options.
    
    `"reporter": "mochawesome"`
    
8. **ignoreTestFiles**: Specifies an array of file patterns to ignore during test runs.
    
    `"ignoreTestFiles": ["**/skip-*.spec.js"]`
    
9. **requestTimeout**: Sets the maximum time allowed for a network request to complete.
    
    `"requestTimeout": 10000`
    
10. **env**: Allows you to define environment variables that can be accessed in your tests.
    
    `"env": { "API_URL": "[https://api.example.com](https://api.example.com/)" }`
    
11. **watchForFileChanges**: Enables or disables watching for file changes and rerunning tests automatically.
    
    `"watchForFileChanges": false`
    

**_Useful link: [https://docs.cypress.io/guides/references/configuration](https://docs.cypress.io/guides/references/configuration)_**

## Cypress browser actions
All Cypress methods can be divided into methods that work with elements and with the browser.

1. _**`visit()`**_ method in Cypress is used to navigate to a specific URL within the browser. It simulates a user visiting a webpage and triggers the page load process.

_**`cy.visit(url, options)`**_

- `url` (string): The URL to visit, either an absolute or relative path.
- `options` (object, optional): Additional options for the visit.

```js
cy.visit('https://www.example.com', {
	timeout: 10000,
	headers: {
		'X-MyHeader': 'my-value'
	},
	auth: {
		username: 'my-username',
		password: 'my-password'
	}
});
```

- `timeout` (number): Sets the maximum time allowed for the page to load.
- `headers` (object): Specifies custom headers to be sent with the request.
- `auth` (object): Provides authentication credentials for the visit.

2. _**`refresh()`**_ method in Cypress is used to refresh the current page in the browser. It simulates the action of manually refreshing the page by clicking the browser's refresh button.
3. _**`url()`**_ method in Cypress is used to retrieve the current URL of the page.
4. **_`title()`_** method in Cypress is used to retrieve the title of the current page.
5. _**`go()`**_ method in Cypress is used to navigate backward or forward in the browser's history. It allows you to simulate user navigation actions like clicking the browser's back or forward buttons.  
    _`**cy.go(direction)**,`_ **'direction'** can be one of the following values        a. -1 or 'back': navigates back in the browser's history.   
            b. `0` or `'reload'`: reloads the current page.

```js
cy.go('back');
cy.go('forward');
cy.go(1);
cy.go(-1);
```

6. Commands for dealing with browser cache and cookies.

	1. _**`cy.clearCookies()`**_: Clears all browser cookies.
	2. _**`cy.clearLocalStorage()`**_: Clears all items from local storage.
	3. _**`cy.clearSessionStorage()`**_: Clears all items from session storage.
	4. _**`cy.setCookie(name, value)`**_: Sets a cookie with the specified name and value.
	5. _**`cy.getCookies()`**_: Retrieves all browser cookies.
	6. **_`cy.getCookie(name)`_**: Retrieves a specific browser cookie by its name.
	7. _**`cy.clearCookie(name)`**_: Clears a specific browser cookie by its name.

```js
cy.setCookie('my-cookie', 'value of my cookie');
cy.getCookie('my-cookie');
cy.clearCookie('my-cookie');
```

Of course, these are not all methods of interaction with the browser, but the most used. You can find a complete list of methods by clicking on the link below. 

**_Useful link: [https://docs.cypress.io/api/table-of-contents](https://docs.cypress.io/api/table-of-contents#Other-Commands)_**

## Cypress examples overview
And now we can go back to the IDE to understand a little bit more about what kind of files were generated by Cypress.

The first thing I suggest is to understand the structure of the tests.  Since Cypress uses the Mocha library internally, the structure of the tests is handled by the familiar _**"it"**_ and **_"describe"_** functions, as well as the new _**"context"**_ function. Since you are already familiar with it and describe, let's understand what context is all about.

**_"describe" -_** is used to define a test suite, which is a collection of related tests that share a common context or functionality. It is typically used to group tests for a specific feature, component, or functionality. It provides a way to organize and structure your tests hierarchically. You can have nested describe blocks to further organize your tests. Each describe block can contain one or more it blocks (test cases) or other nested describe blocks.

**_"context"_** - also known as an alias for describe, serves a similar purpose as describe. It is primarily used to provide additional context or clarification within a test suite. It helps in improving the readability and maintainability of your tests by providing more descriptive labels or explanations. In Cypress, context is an alias for describe and can be used interchangeably. You can use it to add more context to your test suite, highlight specific scenarios, or group related tests together based on a specific context.

A description of the test structure is usually followed by navigation to the test environment. The commands for navigating can be found in the block above.

Next, the interaction with the application under test begins. And first of all we need to find the elements with which we will interact. There are quite a few commands to find items in Cypress and here are the main ones:

1. _**get() -**_ command in Cypress is used to locate and retrieve DOM elements from the web page using css-selectors. This example will allow you to find all elements with the action-email class.

```js
cy.get('.action-email');
```

But the result of this method is not usual WebElement, but a special Cypress object that contains a WebElement inside of it. And if you need to access a found WebElement directly, you can use the then() method.

```js
cy.get('.action-email').then(webElement => {
	// some actions with webElement here
});
```

2. **_find()_** - is used to search for child elements within a parent element or a previously selected element. It allows you to narrow down your selection and perform actions or assertions on specific child elements. This example will allow you to find the last tr element in tbody, which is inside an element with the assertion-table class.

```js
cy.get('.assertion-table').find('tbody tr:last');
```

3. **_contains()_** - is used to find an element that contains a specific text or substring. It allows you to search for elements based on their visible text content. This example will allow you to find all tr elements with text contains "Data Entry Sheet".

```js
cy.contains('tr', 'Data Entry Sheet');
```

These are the 3 most used methods for finding items in Cypress. But element searches can be used:

- **_`filter()`_**: Filters elements based on a specific selector or predicate function.

```js
cy.get('li').filter('.active');
```

- **_`first()`_**: Retrieves the first element from a set of matched elements.

```js
cy.get('li').first();
```

- **_`last()`_**: Retrieves the last element from a set of matched elements.

```js
cy.get('li').last();
```

- **_`eq()`_**: Retrieves an element at a specific index within a set of matched elements.

```js
cy.get('li').eq(2);
```

- **_`next()`_**: Retrieves the next sibling element of the current subject.

```js
cy.get('.current').next();
```

- _**`prev()`**_: Retrieves the previous sibling element of the current subject

```js
cy.get('.current').prev();
```

- **_`siblings()`_**: Retrieves all sibling elements of the current subject.

```js
cy.get('.current').siblings();
```

You can read more about them in the Cypress documentation **_[https://docs.cypress.io/api/table-of-contents](https://docs.cypress.io/api/table-of-contents) in Queries tab_** and sample tests.

Once an element is found, we can interact with it. The methods from **_[https://docs.cypress.io/api/table-of-contents](https://docs.cypress.io/api/table-of-contents)_ _Actions tab_** are used for interaction. They are quite clear, simple and very similar to Selenium or WebdriverIO methods. More examples you can find in **_[actions.cy](http://actions.cy/).js_** file in your project.

And at the end, when we have done something with the elements, we want to check the expected result. For this purpose there are only 2 commands in Cypress: **_"should"_** and **_"and"_**. These methods allow us to check the content of an item, its state, the presence of attributes, the number of items found and much more.

```js
cy.get('.my-element').should('be.visible');
cy.get('.my-element').should('have.text', 'Hello, World!');
cy.get('input[name="username"]').should('have.value', 'john.doe');
cy.get('.my-element').should('have.class', 'active');
cy.get('li').should('have.length', 5);
cy.get('button').should('be.disabled');
cy.get('input').should('have.attr', 'type', 'email');
cy.get('.my-element')
	.should('be.visible')
	.and('have.class', 'active')
	.and('have.text', 'Hello, World!');
cy.url().should('eq', 'https://example.com');
cy.get('.my-element').should('exist');
```

We have looked at quite a few Cypress methods. And as you have noticed they are either called on the cy object or on the result of another Cypress method.

But what if we just want to compare 2 numbers?  
That's where the **_"wrap"_** method comes in. This method allows us to wrap any value into a Cypress object. And it allows you to apply Cypress methods to any object.

```js
2.should('eq', 2); // error
cy.wrap(2).should('eq', 2); // correct usage
```

Alternatively, if you don't want to compare Cypress objects, but numbers, strings, objects, you can use the methods of the chai library, which is built into Cypress.

```js
expect(2).eq(2);
expect('testString123').include('123');
expect({a: 1, b: 2}).deep.eq.({a: 1, b: 2});
```

# Test data
Almost any test has its test data and of course Cypress provides the ability to store and work with test data.   
Cypress recommends storing test data in the fixtures folder.  
Json files with test data can be imported into our test file and used as a normal object. And we can also use `cy.fixture(<test data file name>).then(data => {<work with test data here>})` method.

```js
import profile from '../fixtures/profile.json';

describe('template spec', () => {
	it('my test', () => {
		cy.log(profile.email);
		cy.log(profile.id);
		cy.log(profile.name);
		cy.fixture("profile.json").then(profile => {
			cy.log(profile.id);
			cy.log(profile.email);
			cy.log(profile.name);
		});
	});
});
```

Also the fixture method provides quite interesting possibilities to work with any files (images, audio, video), about which we can read at the link **_[https://docs.cypress.io/api/commands/fixture](https://docs.cypress.io/api/commands/fixture)_**

# Cypress commands
In the previous task, you have already encountered a situation where you have to do the same actions in several tests, but with different parameters. For example, entering your email, password and their confirmation from cases 3 and 4. Usually we put repetitive actions into class methods, but Cypress provides its own way to get rid of duplicate application testing logic - creating your own Cypress commands.

Cypress recommends storing all commands in the **support** folder. The **commands.js** and **e2e.js** files are already located there. You can create your commands in the **commands.js** file, or create your own file in this folder and add your commands to it. But it is worth considering that for Cypress to see your commands file, you must import your file into **e2e.js**.  
Creating a Cypress command is pretty simple - you need to call the method to create a Cypress.Commands.add() command and pass in a command name and a function that will describe the steps of your command.

```js
// support -> my_commands.js
Cypress.Commands.add('myCustomCommand', (firstParam, secondParam) => {
	cy.get('input.class').type(firstParam);
	cy.get('div').contains(secondParam);
});
```

Also, don't forget that the command files you create must be imported into **e2e.js**.

Your team is now ready to be used in a test via cy.

```js
it('my test', () => {
	cy.myCustomCommand('testParam1', 'testParam2');
});
```

Let's now look at an example of a command that returns a value.  
Cypress works with chains of commands, so when working with Cypress we only access static values from a command when calling then. So if we want to return the text of an element, we must return the chain of Promise, and then call the then() method and inside it we will get access to the text of the element.

```js
// my_commands.js
Cypress.Commands.add('myCustomCommand', () => {
	return cy.get('h4#type').invoke('text');
});
```

```js
// test.cy.js
describe('template spec', () => {
	beforeEach(() => {
		cy.visit('https://example.cypress.io/commands/actions');
	});
	
	it('my test', () => {
		cy.myCustomCommand().then((text => cy.log(text));
		cy.log(cy.myCustomCommand());
	});
});
```

![[Pasted image 20240405133147.png]]

As you can see cy.log() called in then() output the text of our ".type()" element - line 3.  
And the next cy.log() outputs the result of our command - the object responsible for the chain of Promise - line 6.

# Screenshots and video
Quite often we can miss the point at which the test crashed, and we would not want to run it again to see what the problem was.   
That's why you should get acquainted with the possibility to make a video recording of your test, as well as screenshots. Making a screenshot or video recording is quite easy.

**Video:**

You can run tests with the _**"cypress run"**_ command, or you can open cypress with _**"npx cypress open"**_ and manually select tests to run. So let's look at video recording for both options.  
When running with cypress run, you don't need to do anything, because in this mode your tests will be recorded automatically and the video files will be saved in _**"cypress/videos"**_.

The situation is slightly different when using **_"npx cypress open"_**. Since in this mode you see the execution of your tests on your screen, video recording is disabled by default.   
To enable video recording, you must go to the cypress configuration file and add the **_"video: true"_** option to it. After that, run your tests, go make yourself some tea, and when you return, look for the recording of your test run in **_"cypress/videos"_**. 

Sometimes you may encounter the problem that the video recording of your tests is of insufficient quality or, on the contrary, of very high quality, but the recording of all your tests takes up all the memory of your PC. In this case you should use the **_"videoCompression"_** option in the cypress configuration file.  
This option can take values from 0 to 51. 0 is maximum video quality and therefore takes up as much memory as possible, 51 is minimum video quality, but also takes up the minimum amount of memory. The default value of this option is 32.

```js
const { defineConfig } = require("cypress");

module.exports = defineConfig({
	e2e: {
		setupNodeEvents(on, config) {
			// implement node event listeners here
		},
		video: true,
		videoCompression: 1,
	}
},

```

**Screenshoots:**

The situation with the screenshots is quite similar to the video. If you use **"cypress run"** to run tests, Cypress will automatically make a screenshot when the test crashes and you can find it in the **"cypress/screenshots"** folder.   
But what to do if we want to see screenshots not only in case of a crash, but also of some important moments in the test? In this case, the **"_cy.screenshot()"_** method will help us. You just need to add this method to your test and look for your screenshot in the **"cypress/screenshots"** folder. 

If you run tests with **"npx cypress open"** you can also take a screenshot of any test step simply by adding **_"cy.screenshot()"_** to your test. But what if we want to get a screenshot of a test crash?  
In that case, the same **_"cy.screenshot()"_** method will help us. Only we have to put it not in the test, but in the **"afterEach" hook**. And for the screenshot to be executed only when the test crashes, we have to check the status of our test, like in the screenshot below.

```js
afterEach(() => {
	if (this.currentTest.state == 'failed') {
		cy.screenshot();
	}
});
```

_**Useful link: [https://docs.cypress.io/guides/guides/screenshots-and-videos](https://docs.cypress.io/guides/guides/screenshots-and-videos)**_

# Plugins and extensions
Cypress, like any other tool, has its advantages and disadvantages. And a large number of plugins have been developed to cover the disadvantages of Cypress. They will allow you to do some specific tasks much easier, simplify integration with some other tools.

The most used and popular plugins:

1. **Cypress-Cucumber-Preprocessor:** If you prefer writing tests using the Gherkin syntax (Given-When-Then), this plugin enables you to use Cucumber with Cypress. It allows you to write feature files with scenarios, which are then executed as Cypress tests. Must have plugin for BDD-testing. **_More info at the link: [https://github.com/badeball/cypress-cucumber-preprocessor](https://github.com/badeball/cypress-cucumber-preprocessor)_**
    
2. **Cypress-Eslint-Preprocessor:** is a preprocessor for integrating ESLint with the Cypress testing framework. It allows running ESLint checks directly during test execution with Cypress. _**More info at the link: [https://github.com/chinchiheather/cypress-eslint-preprocessor](https://github.com/chinchiheather/cypress-eslint-preprocessor)**_
    
3. **Cypress-Docker-Images:** is a collection of Docker images specifically designed for running Cypress tests in a containerized environment. These images provide a preconfigured and optimized setup for running Cypress tests, making it easier to integrate Cypress into a Dockerized CI/CD pipeline. You may not need this plugin at the beginning of your career. But it is a must have plugin for more experienced engineers when setting up the CI/CD process. **_More info at the link: [https://github.com/cypress-io/cypress-docker-images](https://github.com/cypress-io/cypress-docker-images)_**
4. **Cypress-Xpath:** as you know xpath and css selectors have their advantages and disadvantages, and sometimes it is necessary to use both css and xpath locators. And since cypress doesn't support xpath out of the box, this plugin can help you. _**More info at the link: [https://www.npmjs.com/package/cypress-xpath](https://www.npmjs.com/package/cypress-xpath)**_
5. **Cypress-Plugin-API:** is a utility library for Cypress that provides additional methods and functionalities to enhance your test automation workflows. It extends the capabilities of Cypress by introducing new commands and hooks that can be used within your test scripts. A very popular API testing plugin, which is one of the reasons why Cypress is increasingly being chosen for API testing. _**More info at the link:**_ _**[https://github.com/filiphric/cypress-plugin-api](https://github.com/filiphric/cypress-plugin-api)**_

As you can see Cypress plugins are very versatile and will help you solve 90% of your issues. But beware, since some plugins are developed by the community and not by Cypress developers, you might encounter some bugs.   
**_A more complete list of plugins and their detailed descriptions can be found at this link: [https://docs.cypress.io/plugins](https://docs.cypress.io/plugins)_**

