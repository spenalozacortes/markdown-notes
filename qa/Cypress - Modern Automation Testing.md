# Introduction to Cypress and its advantages in automation world

## What is Cypress? And why it is future of automation

**What is Cypress?**
Cypress is a next generation front end automation testing tool built for the modern web applications.

**How Cypress is unique from other automation tools?**
Cypress automatically waits for commands and assertions before moving on. No more async hell.

Ability to test edge test cases by mocking the server response.

Cypress takes snapshots as your tests run. We can hover over each command in the command log to see exactly what happened at each step.

Because of its architectural design, Cypress delivers fast, consistent and reliable test execution compared to other automation tools.

View videos of your entire tests execution when run from the Cypress Dashboard.

Cypress built on Node.js and comes packaged as an npm module.

As it is built on Node.js, it uses JavaScript for writing tests. But 90% of coding can be done using Cypress inbuilt commands which are easy to understand.

Cypress also bundles with jQuery and inherits many of jQuery methods for UI components identification.

## Understand Cypress architecture and its benefits

**Cypress architecture**
Most testing tools (like Selenium) operate by running outside of the browser and executing remote commands across the network. But Cypress engine directly operates inside the browser. In other words, it is the browser that is executing your test code.

This enables Cypress to listen and modify the browser behavior at run time by manipulating DOM and altering network requests and responses on the fly.

Cypress open doors to new kind of testing with having ultimate control over your application (front and back).

**Cypress browser support**

- Chrome
- Electron
- Firefox & IE

**Cypress components**

- Test Runner
- Dashboard Service

# Step by step instructions for Cypress installation and project setup

## Install Node.js, VS Code & Cypress for Windows and Mac

**What is Node.js?**
Node.js in an open-source, cross-platform, back-end JavaScript runtime environment that runs on the V8 engine and executes JavaScript code outside a web browser.

**Create a new project with package.json**
A package.json is a JSON file that exists at the root of a JavaScript/Node project. It holds metadata relevant to the project and it is used for managing the project's dependencies.

**Install Cypress**

```shell
npm -i init
```

```shell
npm install cypress --save-dev
```

```shell
npm install
```

# Introduction to Cypress Test Runner and command line features

## What is Cypress TestRunner

```shell
node_modules/.bin/cypress open
```

```js
// cypress.config.js
module.exports = defineConfig({
  e2e: {
    setupNodeEvents(on, config) {
      // implement node event listeners here
    },
    specPattern: 'cypress/integration/examples/*.js'
  },
});
```

## Build Cypress basic test and run from TestRunner

- `visit()`: Visit the given url

```js
describe('My first test suite', function() {
    it('My first test case', function() {
        cy.visit("https://rahulshettyacademy.com/seleniumPractise/#/");
    });
});
```

## Running Cypress tests in supported browsers

Through command line Cypress runs in headless.

```shell
./node_modules/.bin/cypress run
```

```shell
./node_modules/.bin/cypress run --headed
```

```shell
./node_modules/.bin/cypress run --browser chrome
```

## Exploring the Cypress project framework structure

- fixtures: data
- plugins: listeners
- support: utilities

Settings -> Project Settings

# Getting started with Cypress test automation

## Cypress locator strategies and how to construct them

Supports only CSS selectors.

tagname#idname
tagname.classname
tagname\[attribute='value']
parent child

## Cypress inbuilt plugin in TestRunner to generate locators

- `get()`: Get one or more DOM elements by selector. The querying behavior of this command matches exactly how $(…) works in jQuery.

```js
/// <reference types="Cypress" />

describe('My first test suite', function() {
    it('My first test case', function() {
        cy.visit("https://rahulshettyacademy.com/seleniumPractise/#/");
        cy.get('.search-keyword').type('ca');
    });
});
```

## Basic assertion in writing the tests with Cypress

- `wait()`: Wait for a number of milliseconds
- `should('have.length', n)`: Asserts that the target's `length` property is equal to the given number `n`.

```js
cy.wait(2000);
cy.get('.product').should('have.length', 4);
```

## Handling invisible elements with Cypress by understanding logs

```js
cy.get('.product:visible').should('have.length', 4);
```

# Deep diving into Cypress commands and its asynchronous nature

## Understanding get and find commands with Cypress

- `find()`: Finds the descendent DOM elements with the given selector.
- `eq()`: Get A DOM element at a specific index in an array of elements.
- `contains()`: Get the DOM element containing the text. DOM elements can contain more than the desired text and still match. Additionally, Cypress prefers some DOM elements over the deepest element found.
- `click()`: Click a DOM element.

```js
cy.get('.products').find('.product').should('have.length', 4);
cy.get('.products').find('.product').eq(2).contains('ADD TO CART').click();
```

## Grabbing text for validations using Cypress text command

- `each()`: Iterate through an array like structure (arrays or objects with a length property).
- `text()`: Get the combined text contents of each element in the set of matched elements, including their descendants.
- `wrap()`: Yield the element passed into `.wrap()`.

```js
cy.get('.products').find('.product').each(($el, index, $list) => {
    const textVeg = $el.find('h4.product-name').text();
	if(textVeg.includes('Cashews')) {
        cy.wrap($el).find('button').click();
    }
});
```

## Understanding the difference between jQuery methods and Cypress commands

Non Cypress commands cannot resolve promise by themselves. We need to manually resolve it by `then()`.

- `then()`: Enables you to work with the subject yielded from the previous command / promise.
- `log()`: Print a message to the Cypress Command Log.

```js
cy.get('.brand').then(function(logo) {
    cy.log(logo.text());
});
```

## Handling async promises with Cypress

- `as()`: Assign an alias for later use. Reference the alias later within a [cy.get()](vscode-file://vscode-app/usr/share/code/resources/app/out/vs/code/electron-sandbox/workbench/workbench.html "https://on.cypress.io/get") or [cy.wait()](vscode-file://vscode-app/usr/share/code/resources/app/out/vs/code/electron-sandbox/workbench/workbench.html "https://on.cypress.io/wait") command with a `@` prefix. You can alias DOM elements, routes, stubs and spies.
- `should('have.text', text)`: Assert that the text of the first element of the selection is equal to the given text, using `.text()`.

```js
cy.get('.products').as('productsLocator');
cy.get('@productsLocator').find('.product').should('have.length', 4);
cy.get('@productsLocator').find('.product').eq(2).contains('ADD TO CART').click().then(function() {
    console.log("hello");
});

cy.get('.brand').should('have.text', 'GREENKART');
```

## Code

```js
// test1.js
/// <reference types="Cypress" />

describe('My first test suite', function() {
    it('My first test case', function() {
        cy.visit("https://rahulshettyacademy.com/seleniumPractise/#/");
        cy.get('.search-keyword').type('ca');
        cy.wait(2000);
        cy.get('.product:visible').should('have.length', 4);
        cy.get('.products').as('productsLocator');
        cy.get('@productsLocator').find('.product').should('have.length', 4);
        cy.get('@productsLocator').find('.product').eq(2).contains('ADD TO CART').click().then(function() {
            console.log("hello");
        });
        cy.get('@productsLocator').find('.product').each(($el, index, $list) => {
            const textVeg = $el.find('h4.product-name').text();
            if(textVeg.includes('Cashews')) {
                cy.wrap($el).find('button').click();
            }
        });
        cy.get('.brand').should('have.text', 'GREENKART');
        cy.get('.brand').then(function(logo) {
            cy.log(logo.text());
        });
    });
});
```

```js
// test2.js
/// <reference types="Cypress" />

describe('My second test suite', function() {
    it('My second test case', function() {
        cy.visit("https://rahulshettyacademy.com/seleniumPractise/#/");
        cy.get('.search-keyword').type('ca');
        cy.wait(2000);
        cy.get('.products').as('productsLocator');
        cy.get('@productsLocator').find('.product').each(($el, index, $list) => {
            const textVeg = $el.find('h4.product-name').text();
            if(textVeg.includes('Cashews')) {
                cy.wrap($el).find('button').click();
            }
        });
        cy.get('.cart-icon > img').click();
        cy.contains('PROCEED TO CHECKOUT').click();
        cy.contains('Place Order').click();
    });
});
```

# Handling web controls UI using Cypress

## How to verify and automate check boxes with Cypress

- `check()`: Check checkbox(es) or radio(s). This element must be an `<input>` with type `checkbox` or `radio`.
- `should('be.checked')`: Check checkbox(es) or radio(s). This element must be an `<input>` with type `checkbox` or `radio`.
- `and('have.value', 'value')`: Assert that the first element of the selection has the given value, using `.val()`.
- `uncheck()`: Uncheck checkbox(es).
- `should('not.be.checked')`: Assert that at least one element of the selection is not checked, using `.is(':checked')`.

```js
cy.get('#checkBoxOption1').check().should('be.checked').and('have.value', 'option1');
cy.get('#checkBoxOption1').uncheck().should('not.be.checked');
cy.get('input[type="checkbox"]').check(['option2', 'option3']);
```

## Handling static dropdowns using select command with Cypress

- `select()`: Select an `<option>` with specific text, value, or index within a `<select>`.

```js
cy.get('select').select('option2').should('have.value', 'option2');
```

## Handling dynamic dropdowns with each command iteration

```js
cy.get('#autocomplete').type('ind');
cy.get('.ui-menu-item div').each(($el, index, $list) => {
    if ($el.text() === 'India') {
        $el.click();
    }
});
cy.get('#autocomplete').should('have.value', 'India');
```

## Handling visible and invisible elements using assertions in Cypress

- `should('be.visible')`: Assert that at least one element of the selection is visible, using `.is(':visible')`.

```js
cy.get('#displayed-text').should('be.visible');
cy.get('#hide-textbox').click();
cy.get('#displayed-text').should('not.be.visible');
cy.get('#show-textbox').click();
cy.get('#displayed-text').should('be.visible');

cy.get('[value="radio2"').check().should('be.checked');
```

## Code

```js
/// <reference types="Cypress" />

describe('Controls UI', function() {
    it('Controls UI 1', function() {
        cy.visit('https://rahulshettyacademy.com/AutomationPractice/');
        cy.get('#checkBoxOption1').check().should('be.checked').and('have.value', 'option1');
        cy.get('#checkBoxOption1').uncheck().should('not.be.checked');
        cy.get('input[type="checkbox"]').check(['option2', 'option3']);

        cy.get('select').select('option2').should('have.value', 'option2');

        cy.get('#autocomplete').type('ind');
        cy.get('.ui-menu-item div').each(($el, index, $list) => {
            if ($el.text() === 'India') {
                $el.click();
            }
        });
        cy.get('#autocomplete').should('have.value', 'India');

        cy.get('#displayed-text').should('be.visible');
        cy.get('#hide-textbox').click();
        cy.get('#displayed-text').should('not.be.visible');
        cy.get('#show-textbox').click();
        cy.get('#displayed-text').should('be.visible');

        cy.get('[value="radio2"').check().should('be.checked');
    });
});
```

# Advance automation to handling alerts, popups, child windows using Cypress - jQuery

## How Cypress auto handles alerts in web apps

Cypress auto accepts alerts and pop ups.
Cypress has capability to listen to browser events.

```js
cy.get('#alertbtn').click();
cy.get("[value='Confirm']").click();

cy.on('window:alert', str => {
    expect(str).to.equal('Hello , share this practice page and share your knowledge');
});

cy.on('window:confirm', str => {
    expect(str).to.equal('Hello , Are you sure you want to confirm?');
});
```

## Handling child tab with combination of Cypress & jQuery commands

- `invoke()`: Invoke a function on the previously yielded subject.
- `origin()`: Enables running Cypress commands in a secondary origin.

```js
cy.get("#opentab").invoke('removeAttr', 'target').click();

cy.origin("https://www.qaclickacademy.com/", () => {
    cy.get("#navbarSupportedContent a[href*='about']").click();
    cy.get(".mt-50 h2").should('contain', 'QAClick Academy');
});
```

## Handling web tables with Cypress using each command

- `next()`: Get the immediately following sibling of each DOM element within a set of DOM elements.

```js
cy.get("tr td:nth-child(2)").each(($el, index, $list) => {
    const text = $el.text();
    if (text.includes("Python")) {
        cy.get("tr td:nth-child(2)").eq(index).next().then(function(price) {
            const priceText = price.text();
            expect(priceText).to.equal('25');
        });
    }
});
```

## Handling mouse hover popups using Cypress

- `url()`: Get the current URL of the page that is currently active.
- `should('include', value)`: When the target is a string, `.include` asserts that the given string `val` is a substring of the target.

`show()` method should be applied on immediate parent of hidden element.

```js
// cy.get(".mouse-hover-content").invoke("show");
cy.contains("Top").click({ force: true });
```

## Code

```js
// test4.js
/// <reference types="Cypress" />

describe('', function() {
    it('', function() {
        cy.visit('https://rahulshettyacademy.com/AutomationPractice/');
        cy.get('#alertbtn').click();
        cy.get("[value='Confirm']").click();

        cy.on('window:alert', str => {
            expect(str).to.equal('Hello , share this practice page and share your knowledge');
        });

        cy.on('window:confirm', str => {
            expect(str).to.equal('Hello , Are you sure you want to confirm?');
        });
    });
});
```

```js
// test5.js
/// <reference types="Cypress" />

describe('Handling child windows', () => {
    it('Should handle child window', () => {
        cy.visit('https://rahulshettyacademy.com/AutomationPractice/');
        cy.get("#opentab").invoke('removeAttr', 'target').click();

        cy.origin("https://www.qaclickacademy.com/", () => {
            cy.get("#navbarSupportedContent a[href*='about']").click();
            cy.get(".mt-50 h2").should('contain', 'QAClick Academy');
        });
    });
});
```

```js
// test6.js
/// <reference types="Cypress" />

describe("", () => {
    it("", () => {
        cy.visit("https://rahulshettyacademy.com/AutomationPractice/");
        cy.get("tr td:nth-child(2)").each(($el, index, $list) => {
            const text = $el.text();
            if (text.includes("Python")) {
                cy.get("tr td:nth-child(2)").eq(index).next().then(function(price) {
                    const priceText = price.text();
                    expect(priceText).to.equal('25');
                });
            }
        });
    });
});
```

```js
// test7.js
/// <reference types="Cypress" />

describe("", () => {
    it("", () => {
        cy.visit("https://rahulshettyacademy.com/AutomationPractice/");
        // cy.get(".mouse-hover-content").invoke("show");
        cy.contains("Top").click({ force: true });
        cy.url().should("include", "top");
    });
});
```

# Understand how to automate frames & child windows & calendars in Cypress

## Handling frames with Cypress 

```shell
npm install -D cypress-iframe
```

```js
/// <reference types="cypress-iframe" />
import 'cypress-iframe';

cy.frameLoaded('#courses-iframe');
cy.iframe().find('a[href*="mentorship"]').eq(0).click();
```

## Strategy of automating calendars using Cypress

```js
/// <reference types="Cypress" />

describe('Calendar test', () => {
    it('Verify date selection', () => {
        const monthNumber = "6";
        const date = "15";
        const year = "2027";
        const expectedList = [monthNumber, date, year];

        cy.visit('https://rahulshettyacademy.com/seleniumPractise/#/offers');
        cy.get('.react-date-picker__inputGroup').click();
        cy.get('.react-calendar__navigation__label').click();
        cy.get('.react-calendar__navigation__label').click();
        cy.contains("button", year).click();
        cy.get('.react-calendar__year-view__months__month').eq(Number(monthNumber) - 1).click();
        cy.contains("abbr", date).click();
        cy.get('.react-date-picker__inputGroup__input').each(($el, index) => {
            cy.wrap($el).invoke('val').should('eq', expectedList[index]);
        });
    });
});
```

## Code

```js
// test8.js
/// <reference types="Cypress" />
/// <reference types="cypress-iframe" />
import 'cypress-iframe';

describe("Frames tests", () => {
    it("", () => {
        cy.visit("https://rahulshettyacademy.com/AutomationPractice/");
        cy.frameLoaded('#courses-iframe');
        cy.iframe().find('a[href*="mentorship"]').eq(0).click();
        cy.iframe().find("h1[class*='pricing-title']").should('have.length', 2);
    })
});
```

# Cypress framework Part 1 - Understanding fixtures and custom commands

## Understand how fixtures work in driving data

- `fixture()`: Load a fixed set of data located in a file.

```json
{
  "name": "Bob",
  "gender": "Male"
}
```

```js
describe("Framework tests", function() {
    before(function() {
        cy.fixture("example").then(function(data) {
            this.data = data;
        });
    });

    it("First test", function() {
        cy.visit("https://rahulshettyacademy.com/angularpractice/");

        cy.get("input[name='name']:nth-child(2)").type(this.data.name);
        cy.get("select").select(this.data.gender);
    });
});
```
#aqui
## Validating attribute properties and their behavior with Cypress assertions

- `should("have.attr", attribute, value)`: Assert that the first element of the selection has the given attribute, using `.attr()`. Optionally, assert a particular value as well. The return value is available for chaining.
- `should("be.disabled")`: Assert that at least one element of the selection is disabled, using `.is(':disabled')`.

```js
cy.get("input.ng-valid").should("have.value", this.data.name);
cy.get("input[name='name']:nth-child(2)").should("have.attr", "minlength", "2");
cy.get("#inlineRadio3").should("be.disabled");
```

## Building customized Cypress commands for reusing the code

```js
// commands.js
Cypress.Commands.add('selectProduct', (productName) => { 
    cy.get("h4.card-title").each(($el, index, $list) => {
        if ($el.text().includes(productName)) {
            cy.get("button.btn.btn-info").eq(index).click();
        }
    });
});
```

```js
// test10.js
cy.selectProduct("Blackberry");
```

## Code

```js
// test10.js
/// <reference types="Cypress" />

describe("Framework tests", function() {
    before(function() {
        cy.fixture("example").then(function(data) {
            this.data = data;
        });
    });

    it("First test", function() {
        cy.visit("https://rahulshettyacademy.com/angularpractice/");

        cy.get("input[name='name']:nth-child(2)").type(this.data.name);
        cy.get("select").select(this.data.gender);
        cy.get("input.ng-valid").should("have.value", this.data.name);
        cy.get("input[name='name']:nth-child(2)").should("have.attr", "minlength", "2");
        cy.get("#inlineRadio3").should("be.disabled");

        cy.get("a[href*=shop]").click();
        cy.selectProduct("Blackberry");     
    });
});
```

# Cypress framework part 2 - Page object design & test parameterization

## Parameterizing the test data from JSON files using each command

```json
{
  "name": "Bob",
  "gender": "Male",
  "productName": ["Blackberry", "Nokia Edge"]
}
```

```js
this.data.productName.forEach(function(element) {
    cy.selectProduct(element);
});  
```

## Test debugging and pause with Cypress

- `pause()`: Stop cy commands from running and allow interaction with the application under test. You can then "resume" running all commands or choose to step through the "next" commands from the Command Log. This does not set a `debugger` in your code, unlike `.debug()`

```js
cy.pause();
```

## Implementing page object design pattern into Cypress

```js
// HomePage.js
class HomePage {

    getEditBox() {
        return cy.get("input[name='name']:nth-child(2)");
    }

    getTwoWayDataBinding() {
        return cy.get("input.ng-valid");
    }

    getGender() {
        return cy.get("select");
    }

    getEntrepreneur() {
        return cy.get("#inlineRadio3");
    }

    getShopTab() {
        return cy.get("a[href*=shop]");
    }
}

export default HomePage;
```

```js
// test10.js
import HomePage from "../pageObjects/HomePage";

const homePage = new HomePage();
```

## Modifying existing tests into page object pattern as per Cypress standards
