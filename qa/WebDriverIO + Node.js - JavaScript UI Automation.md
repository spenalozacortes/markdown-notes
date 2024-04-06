ess# Introduction

## Introduction to WebDriverIO

**What is WebDriverIO?**
WebDriver IO allows you to automate any application written with modern web frameworks such as React, Angular, Polymeror, Vue.js as well as native mobile applications for Android and iOS.

WebDriver built on Node.js engine and used JavaScript to code the automation. WebDriverIO uses Selenium under hood. All the great things about Selenium are available in WebDriverIO with additional advantage of exclusive assertions for test validations.

## Getting started with Node.js and npm installation

**Step by step instructions to run first test with WebDriverIO**

1. Install Node.js
2. Set Node Home path in system variables
3. Create new npm project
4. Download and import project into Visual Studio Code
5. Understand the importance of package.json in Node projects
6. Install WebDriverIO CLI dependencies
7. Generate configuration file to store WebDriverIO settings
8. Create Mocha spec/test file to write first automation program
9. Run the test with WebDriver Test Runner

```shell
npm init wdio .
```

# Setting up WebDriverIO automation 

## Generate WebDriverIO spec file template and adjust VS Code settings

Autocompletion:

```json
{
    "compilerOptions": {
        "types": [
            "node",
            "@wdio/globals/types",
            "@wdio/mocha-framework"
        ]
    },
    "include": [
        "test/specs/*.js",
        "**/*.json",
        "node_modules/@wdio/sync",
        "node_modules/@wdio/mocha-framework"
    ]
}
```

```js
describe("Ecommerce Application", () => {
    it("Login fail page", () => {
        browser.url("https://rahulshettyacademy.com/loginpagePractise/");
        console.log(browser.getTitle());
    });
});
```

## Understand JavaScript async mode / promises and how to use async awaits

```js
describe("Ecommerce Application", async () => {
    it("Login fail page", async () => {
        await browser.url("https://rahulshettyacademy.com/loginpagePractise/");
        console.log(await browser.getTitle());
    });
});
```

```js
// wdio.conf.js
specs: [
        //'./test/specs/**/*.js'
        './test/specs/firstTest.js'
]
```

```shell
npx wdio run wdio.conf.js
```

# Locators to identify objects with assertions in WebDriverIO

## Introduction to WebDriverIO inbuild expect statements for assertion

- toHaveTitle: Checks if website has a specific title.
- toHaveTitleContaining: Checks if website has a specific title that contains a value.

```js
await expect(browser).toHaveTitleContaining("Rahul Shetty Academy");
await $("#username").setValue("fanjo");
await browser.pause(3000);
```

## Different locator techniques available in WebDriverIO to automate

```js
const password = $("//input[@type='password']");
await password.setValue("learningdfsdf");
await $("#signInBtn").click();
await browser.pause(3000);
console.log(await $(".alert-danger").getText());
```

## Different wait mechanisms available in WebDriverIO framework

- waitUntil: This wait command is your universal weapon if you want to wait on something. It expects a condition and waits until that condition is fulfilled with a truthy value to be returned. 

```
browser.waitUntil(condition, { timeout, timeoutMsg, interval })
```

```js
await browser.waitUntil(async () => await $("#signInBtn").getAttribute('value') === 'Sign In', 
        {
            timeout: 5000,
            timeoutMsg: "Error message not showing up"
        });
```

## Understanding assertions of validating texts on browser with WebDriverIO

- toHaveTextContaining: Checks if element contains a specific text. Can also be called with an array as parameter in the case where the element can have different texts.

```js
await expect($("p")).toHaveTextContaining("username is rahulshettyacademy");
```

# Automate checkboxes, dropdowns, pop ups with WebDriverIO

## Build happy path to sign into page with WebDriverIO

- toHaveUrlContaining: Checks if browser is on a page URL that contains a value.

```js
await $(".btn-primary").waitForExist();
await expect(browser).toHaveUrlContaining("shop");
await expect(browser).toHaveTitle("ProtoCommerce");
```

```js
xit("Login fail page", async () => {
```

## Radiobuttons handling with JavaScript array logic in WebDriverIO

```js
const radioButtons = await $$(".customradio");
const userRadioButton = radioButtons[1];
await userRadioButton.$("span").click();
```

## Handling web pop ups with WebDriverIO framework

- toBeDisplayed: Calls [`isDisplayed`](https://webdriver.io/docs/api/element/isDisplayed/) on given element.

```js
const modal = await $(".modal-body");
await modal.waitForDisplayed();

console.log(await $$(".customradio")[0].$("span").isSelected());

await expect(modal).not.toBeDisplayed();
```

## How to handle static dropdowns using WebDriverIO

```js
const dropdown = await $("select.form-control");
await dropdown.selectByAttribute('value', 'teach');
await dropdown.selectByVisibleText("Consultant");
await dropdown.selectByIndex(0);
console.log(await dropdown.getValue());
```

## Chai assertion on selected radiobuttons, dropdown options with WebDriverIO

```shell
npm install chai
```

```js
import { expect as expectchai } from 'chai';

expectchai(await dropdown.getValue()).to.equal("stud");
```

## Code

```js
// firstTest.js
describe("Ecommerce Application", async () => {
    xit("Login fail page", async () => {
        await browser.url("https://rahulshettyacademy.com/loginpagePractise/");

        await expect(browser).toHaveTitleContaining("Rahul Shetty Academy");

        await $("#username").setValue("fanjo");
        await browser.pause(3000);
        const password = $("//input[@type='password']");
        await password.setValue("learningdfsdf");
        await $("#signInBtn").click();
        
        await browser.waitUntil(async () => await $("#signInBtn").getAttribute('value') === 'Sign In', 
        {
            timeout: 5000,
            timeoutMsg: "Error message not showing up"
        });
        console.log(await $(".alert-danger").getText());

        await expect($("p")).toHaveTextContaining("username is rahulshettyacademy");
    });

    it("Login success page title", async () => {
        await browser.url("https://rahulshettyacademy.com/loginpagePractise/");
        await $("#username").setValue("rahulshettyacademy");
        const password = $("//input[@type='password']");
        await password.setValue("learning");
        await $("#signInBtn").click();
        await $(".btn-primary").waitForExist();
        await expect(browser).toHaveUrlContaining("shop");
        await expect(browser).toHaveTitle("ProtoCommerce");
    });
});
```

```js
// uiControls.js
import { expect as expectchai } from 'chai';

describe("UI Controls Test Suite", async () => {
    it("UI Controls", async () => {
        await browser.url("https://rahulshettyacademy.com/loginpagePractise/");
        await $("#username").setValue("rahulshettyacademy");
        const password = $("//input[@type='password']");
        await password.setValue("learning");
        const radioButtons = await $$(".customradio");
        const userRadioButton = radioButtons[1];
        await userRadioButton.$("span").click();

        const modal = await $(".modal-body");
        await modal.waitForDisplayed();
        await $("#cancelBtn").click();
        console.log(await $$(".customradio")[0].$("span").isSelected());
        await userRadioButton.$("span").click();
        await modal.waitForDisplayed();
        await $("#okayBtn").click();
        await $$(".customradio")[0].$("span").click();
        await expect(modal).not.toBeDisplayed();

        const dropdown = await $("select.form-control");
        await dropdown.selectByAttribute('value', 'teach');
        await dropdown.selectByVisibleText("Consultant");
        await dropdown.selectByIndex(0);
        console.log(await dropdown.getValue());

        expectchai(await dropdown.getValue()).to.equal("stud");
    });
});
```
 
# Functional real time validations with WebDriverIO automation

## Understand how to automate dropdowns with WebDriverIO

```js
let items = await $$("[class='ui-menu-item'] div");
for (let i = 0; i < await items.length; i++) {
    if (await items[i].getText() === "India") {
        await items[i].click();
    }
}
```

## Handling checkboxes with WebDriverIO and save screenshots of the page

```js
const elements = await $$("input[type='checkbox']");
await elements[1].click();
console.log(await elements[1].isSelected());
console.log(await elements[2].isSelected());
await browser.saveScreenshot("screenshot.png");
```

## Scrolling to invisible object with view mode using WebDriverIO

```js
await $("#mousehover").scrollIntoView();
await $("#mousehover").moveTo();
await $("=Top").click();
```

## Handling JavaScript related alerts with WebDriverIO

```js
await $("button").doubleClick();
expectchai(await browser.isAlertOpen()).to.be.true;
expectchai(await browser.getAlertText()).to.equal("You double clicked me.. Thank You..");
await browser.acceptAlert();
```

## How to apply sort the web tables using WebDriverIO

```js
await $("tr th:nth-child(1)").click();
const veggiesLocators = await $$("tr td:nth-child(1)");
const originalVeggies = await veggiesLocators.map(async veggie => await veggie.getText());
const veggies = originalVeggies.slice();
veggies.sort();
expectchai(originalVeggies).to.eql(veggies);
```

## Debugging WebDriverIO code with Visual Studio editor

JavaScript Debugger 
.vscode -> launch.json -> Add configuration

```json
{
    "configurations": [
        {
            "name": "WebDriverIO Test",
            "type": "node",
            "request": "launch",
            "args": ["wdio.conf.js"],
            "cwd": "${workspaceFolder}",
            "autoAttachChildProcesses": true,
            "program": "${workspaceRoot}/node_modules/@wdio/cli/bin/wdio.js",
            "console": "integratedTerminal",
            "skipFiles": [
                "${workspaceFolder}/node_modules/**/*.js",
                "${workspaceFolder}/lib/**/*.js",
                "<node_internals>/**/*.js"
            ]
        },
    ]
}
```

## Automate search table functionality with JavaScript stream methods

```js
await expect(veggiesLocators).toBeElementsArrayOfSize({ eq: 1 });
await expect(veggiesLocators[0]).toHaveText("Tomato");
```

## Code

```js
// uiControls.js
    xit("Dynamic dropdown controls", async () => {
        await browser.url("https://rahulshettyacademy.com/AutomationPractice/");
        await $("#autocomplete").setValue("ind");
        await browser.pause(3000);
        let items = await $$("[class='ui-menu-item'] div");
        for (let i = 0; i < await items.length; i++) {
            if (await items[i].getText() === "India") {
                await items[i].click();
            }
        }
    });

    it ("Checkboxes identification", async () => {
        await browser.url("https://rahulshettyacademy.com/AutomationPractice/");
        const elements = await $$("input[type='checkbox']");
        await elements[1].click();
        console.log(await elements[1].isSelected());
        console.log(await elements[2].isSelected());
        await browser.saveScreenshot("screenshot.png");
    });
```

```js
// functionalScenarios.js
import { expect as expectchai } from 'chai';

describe ("Functional testing on application", async () => {
    xit ("Scrolling and mouse hover", async () => {
        await browser.url("https://rahulshettyacademy.com/AutomationPractice/");
        await $("#mousehover").scrollIntoView();
        await $("#mousehover").moveTo();
        await $("=Top").click();
    });

    xit("Alerts", async () => {
        await browser.url("https://only-testing-blog.blogspot.com/2014/09/selectable.html");
        await $("button").doubleClick();
        expectchai(await browser.isAlertOpen()).to.be.true;
        expectchai(await browser.getAlertText()).to.equal("You double clicked me.. Thank You..");
        await browser.acceptAlert();
    });

    xit ("Web tables sort validation", async () => {
        await browser.url("https://rahulshettyacademy.com/seleniumPractise/#/offers");
        await $("tr th:nth-child(1)").click();
        const veggiesLocators = await $$("tr td:nth-child(1)");
        const originalVeggies = await veggiesLocators.map(async veggie => await veggie.getText());
        const veggies = originalVeggies.slice();
        veggies.sort();
        expectchai(originalVeggies).to.eql(veggies);
    });

    it("Web tables filter validation", async() => {
        await browser.url("https://rahulshettyacademy.com/seleniumPractise/#/offers");
        await $("input[type='search']").setValue("tomato");
        const veggiesLocators = await $$("tr td:nth-child(1)");
        await expect(veggiesLocators).toBeElementsArrayOfSize({ eq: 1 });
        await expect(veggiesLocators[0]).toHaveText("Tomato");
    });
});
```

# Handling child windows and frames with WebDriverIO

## How to handle multiple windows with WebDriverIO

```js
const handles = await browser.getWindowHandles();
await browser.switchToWindow(handles[1]);

await browser.closeWindow();
```

## Understanding difference between SwitchWindow and NewWindow methods

```js
await browser.newWindow("https://google.com");

await browser.switchWindow("https://rahulshettyacademy.com/loginpagePractise/");
```

## How to automate frames using WebDriverIO

```js
await browser.switchToFrame(await $("#courses-iframe"));
console.log(await $("=Courses").getTagName());
 
await browser.switchToFrame(null);
```

## Code

```js
// windowFrames.js
describe("Windows and frames miscellanous", async() => {
    xit("Parent and child windows switch", async() => {
        await browser.url("https://rahulshettyacademy.com/loginpagePractise/");
        await $(".blinkingText").click();
        const handles = await browser.getWindowHandles();
        await browser.switchToWindow(handles[1]);
        console.log(await $("h1").getText());
        console.log(await browser.getTitle());
        await browser.closeWindow();
        await browser.switchToWindow(handles[0]);
        console.log(await browser.getTitle());

        await browser.newWindow("https://google.com");
        console.log(await browser.getTitle());
        await browser.switchWindow("https://rahulshettyacademy.com/loginpagePractise/");
        await $("#username").setValue("helloiswitchedback");
    });

    it("Frames switch", async() => {
        await browser.url("https://rahulshettyacademy.com/AutomationPractice/");
        await $("#mousehover").scrollIntoView();
        console.log(await $$("a").length);
        await browser.switchToFrame(await $("#courses-iframe"));
        console.log(await $("=Courses").getTagName());
        console.log(await $$("a").length);
        await browser.switchToFrame(null);
        console.log(await $$("a").length);
    });
});
```

# Automation of end to end flow in ecommerce app using WebDriverIO

```js
// ecommerceE2E.js
import { expect as expectchai } from 'chai';

describe("Ecommerce application", async () => {
    it("End to end test", async() => {
        const products = ['iphone X', 'Blackberry'];

        await browser.url("https://rahulshettyacademy.com/loginpagePractise/");

        await $("#username").setValue("rahulshettyacademy");
        const password = $("//input[@type='password']");
        await password.setValue("learning");
        await $("#signInBtn").click();

        const link = await $(".btn-primary");
        await link.waitForExist();
        const cards = await $$("div[class='card h-100']");
        for (let i = 0; i < cards.length; i++) {
            const card = await cards[i].$("div h4 a");
            if (products.includes(await card.getText())) {
                await cards[i].$(".card-footer button").click();
            }
        }
        await link.click();
        const productPrices = await $$("//tr/td[4]/strong");
        const sumOfProducts = (await Promise.all(await productPrices.map(async price => parseInt((await price.getText()).split(".")[1].trim()))))
            .reduce((acc, price) => acc + price, 0);
        const totalValue = await $("h3 strong").getText();
        const totalIntValue = parseInt(totalValue.split(".")[1].trim());
        expectchai(sumOfProducts).to.equal(totalIntValue);

        await $(".btn-success").click();
        await $("#country").setValue("ind");
        await $(".lds-ellipsis").waitForExist({ reverse: true });
        await $("=India").click();
        await $("input[type='submit']").click();
        expect(await $(".alert-success")).toHaveTextContaining("Success");
    });
});
```

# WebDriverIO + JS framework development from scratch - Part 1

## Implementing page object design patterns for tests

```js
// pageobjects/loginPage.js
class LoginPage {
    get username() {
        return $("input[name='username']");
    }

    get password() {
        return $("//input[@type='password']");
    }

    get alert() {
        return $(".alert-danger");
    }

    get signIn() {
        return $("#signInBtn");
    }

    get textInfo() {
        return $("p");
    }

    async login(username, password) {
        await this.username.setValue(username);
        await this.password.setValue(password);
        await this.signIn.click();
    }
}

export default new LoginPage();
```

```js
// specs/poTest.js
import loginPage from '../pageobjects/loginPage.js';

describe("Ecommerce Application", async () => {
    it("Login fail page", async () => {
        await browser.url("https://rahulshettyacademy.com/loginpagePractise/");
        await loginPage.login("badusername", "badpassword");
        await browser.waitUntil(async () => await loginPage.signIn.getAttribute('value') === 'Sign In', 
        {
            timeout: 5000,
            timeoutMsg: "Error message not showing up"
        });
        console.log(await loginPage.alert.getText());
        await expect(loginPage.textInfo).toHaveTextContaining("username is rahulshettyacademy");
    });
});
```
 
## Updating end to end test with page object pattern mechanism

```js
// shopPage.js
class ShopPage {
    get checkout() {
        return $(".btn-primary");
    }

    get cards() {
        return $$("div[class='card h-100']");
    }

    async addProductsToCart(products) {
        for (let i = 0; i < await this.cards.length; i++) {
            const card = await this.cards[i].$("div h4 a");
            if (products.includes(await card.getText())) {
                await this.cards[i].$(".card-footer button").click();
            }
        }
    }
}

export default new ShopPage();
```

```js
// reviewPage.js
class ReviewPage {
    
    get productPrices() {
        return $$("//tr/td[4]/strong");
    } 

    get totalPrice() {
        return $("h3 strong");
    }

    get checkout() {
        return $(".btn-success");
    }

    async sumOfProducts() {
        return (await Promise.all(await this.productPrices.map(async price => parseInt((await price.getText()).split(".")[1].trim()))))
        .reduce((acc, price)=> acc+price, 0);
    }

    async totalFormattedPrice() {
        const totalValue = await this.totalPrice.getText();
        return parseInt(totalValue.split(".")[1].trim());
    }
}

export default new ReviewPage();
```

```js
// deliveryPage.js
class DeliveryPage {

    get country() {
        return $("#country");
    }

    get ellipsis() {
        return $(".lds-ellipsis");
    }

    get link() {
        return $("=India");
    }

    get purchase() {
        return $("input[type='submit']");
    }

    get message() {
        return $(".alert-success");
    }
}

export default new DeliveryPage();
```

```js
// poTest.js
import loginPage from '../pageobjects/loginPage.js';
import shopPage from '../pageobjects/shopPage.js';
import reviewPage from '../pageobjects/reviewPage.js';
import deliveryPage from '../pageobjects/deliveryPage.js'

import { expect as expectchai } from 'chai';

describe("Ecommerce Application", async () => {

    it("End to end test", async() => {
        const products = ['iphone X', 'Blackberry'];

        await browser.url("https://rahulshettyacademy.com/loginpagePractise/");

        await loginPage.login("rahulshettyacademy", "learning");

        await shopPage.checkout.waitForExist();
        await shopPage.addProductsToCart(products);
        await shopPage.checkout.click();
        
        const sumOfProducts = await reviewPage.sumOfProducts();        
        const totalIntValue = await reviewPage.totalFormattedPrice();
        expectchai(sumOfProducts).to.equal(totalIntValue);
        await reviewPage.checkout.click();

        await deliveryPage.country.setValue("ind");
        await deliveryPage.ellipsis.waitForExist({ reverse: true });
        await deliveryPage.link.click();
        await deliveryPage.purchase.click();
        expect(await deliveryPage.message).toHaveTextContaining("Success");
    });
});
```

## Parameterize the test cases using Mocha framework and JSON files

```json
[
    {
        "username": "rahulshettyacademy",
        "password": "learning123"
    },
    {
        "username": "rahulshettyacademy",
        "password": "LEARNING"
    }
]
```

```json
[
    {
        "products": ["iphone X", "Blackberry"]
    },
    {
        "products": ["Blackberry", "Nokia Edge"]
    }
]
```

```js
import loginPage from '../pageobjects/loginPage.js';
import shopPage from '../pageobjects/shopPage.js';
import reviewPage from '../pageobjects/reviewPage.js';
import deliveryPage from '../pageobjects/deliveryPage.js'

import { expect as expectchai } from 'chai';

import fs from 'fs';
let credentials = JSON.parse(fs.readFileSync('test/testData/loginTest.json'));
let e2eData = JSON.parse(fs.readFileSync('test/testData/e2eTest.json'));

describe("Ecommerce Application", async () => {
    credentials.forEach(({ username, password }) => {
        xit("Login fail page", async () => {
            await browser.url("https://rahulshettyacademy.com/loginpagePractise/");
            await loginPage.login(username, password);
            await browser.waitUntil(async () => await loginPage.signIn.getAttribute('value') === 'Sign In', 
            {
                timeout: 5000,
                timeoutMsg: "Error message not showing up"
            });
            console.log(await loginPage.alert.getText());
            await expect(loginPage.textInfo).toHaveTextContaining("username is rahulshettyacademy");
        });
    });

    e2eData.forEach(({ products }) => {
        it("End to end test", async() => {
            await browser.url("https://rahulshettyacademy.com/loginpagePractise/");
    
            await loginPage.login("rahulshettyacademy", "learning");
    
            await shopPage.checkout.waitForExist();
            await shopPage.addProductsToCart(products);
            await shopPage.checkout.click();
            
            const sumOfProducts = await reviewPage.sumOfProducts();        
            const totalIntValue = await reviewPage.totalFormattedPrice();
            expectchai(sumOfProducts).to.equal(totalIntValue);
            await reviewPage.checkout.click();
    
            await deliveryPage.country.setValue("ind");
            await deliveryPage.ellipsis.waitForExist({ reverse: true });
            await deliveryPage.link.click();
            await deliveryPage.purchase.click();
            expect(await deliveryPage.message).toHaveTextContaining("Success");
        });
    });
});

```

# WebDriverIo + JS framework development from scratch - Part 2

## Running tests in parallel mode with utilization of capabilities mode

```js
// wdio.conf.js

specs: [
        './test/specs/**/*.js'
    ],
    maxInstances: 6,
    capabilities: [{
	    maxInstances: 5,
        browserName: 'chrome',
        acceptInsecureCerts: true,
        'goog:chromeOptions': {
            args: ['--headless', '--disable-gpu'],
        }
    }],
```

## Running selected tests using Mocha grep options in framework

```js
it ("Web tables sort validation - Smoke", async () => {
```

```shell
npx wdio run wdio.conf.js --mochaOpts.grep Smoke
```

## Importance of bail and base URL options in configuration file

```js
// wdio.conf.js
bail: 1,
```

```js
// wdio.conf.js
baseUrl: 'https://rahulshettyacademy.com',
```

```js
// firstTest.js
await browser.url("/loginpagePractise/");
```

## Controlling the execution of tests through command line parameters

```js
// wdio.conf.js
    suites: {
        debitCard: ['test/specs/uiControls.js', 'test/specs/windowFrames.js'],
        creditCar: ['test/specs/ecommerceE2E.js']
    },
```

```shell
npx wdio run wdio.conf.js --suite debitCard
```

## Running individual tests and in the group with Mocha options runtime

```shell
npx wdio run wdio.conf.js --spec test/specs/ecommerceE2E.js 
```

```js
// wdio.conf.js
    specs: [
        './test/specs/**/*.js'
        // './test/specs/poTest.js'
    ],
    // Patterns to exclude.
    exclude: [
        'test/specs/ecommerceE2E.js'
    ],
```

## How to build customized configuration files for test execution in WebDriverIO

```js
const merge = require('deepmerge');
const wdioConf = require('./wdio.conf.js')

exports.config = merge(wdioConf.config, {
    baseUrl: "http://rahulshettyacademyUAT.com",
    waitforTimeout: 5000,
    mochaOpts: {
        ui: 'bdd',
        timeout: 60000,
        grep: "sanity"
    }
});
```

# WebDriverIO + JS framework development from scratch - Part 3

## How to apply retry mechanism for flaky tests with WebDriverIO conf

```js
// firstTest.js
it("Login fail page-Smoke", async function() {
        this.retries(2);
```

## Generating scripts through Node.js from package.json file for consolidation

```json
  "scripts": {
    "wdio": "wdio run ./wdio.conf.js",
    "debitcard": "npx wdio run wdio.conf.js --suite debitCard"
  },
```

```shell
npm run debitcard
```

## Generating HTML reports through Allure package from WebDriverIO

1. Download Allure dependencies

```shell
npm install @wdio/allure-reporter --save-dev
```

2. Prepare configuration to create report directory

```js
// wdio.conf.js
reporters: [['allure', {
        outputDir: 'allure-results',
        disableWebdriverScreenshotsReporting: false,
    }]],
```

3. Add screenshot method in afterTest hook

```js
// wdio.conf.js
    afterTest: async function(test, context, { error, result, duration, passed, retries }) {
        if (error) {
            await browser.takeScreenshot();
        }
    },
```

4. Remove specs reporter

```js
// wdio.conf.js
// reporters: ['spec']
```

## Converting Allure XML files to official consolidated HTML report with commands

```shell
npm install -g allure-commandline --save-dev
```

```shell
allure generate allure-results && allure open
```

```shell
allure generate allure-results --clean && allure open
```

## Creating new Jenkins job for WebDriverIO framework execution

Execute Windows batch command

```
npm run "%Script%"
```

## Integrating Allure reports to Jenkins WebDriverIO framework jobs for post results

Install Allure Jenkins plugin

Tools -> Allure Commandline installations
Name: allure
-> Add installer
Extract \*.zip/\*.tar.gz
https://github.com/allure-framework/allure2/releases
https://github.com/allure-framework/allure2/archive/refs/tags/2.27.0.zip

Post-build Actions -> Allure Report

