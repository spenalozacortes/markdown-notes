# Learn HTML by Building a Cat Photo App

[[Cat Photo App]]

**HTML tags give a webpage its structure. You can use HTML tags to add photos, buttons, and other elements to your webpage.**

The `p` element is used to create a paragraph of text on websites.

The `h1` through `h6` heading elements are used to signify the importance of content below them. The lower the number, the higher the importance, so `h2` elements have less importance than `h1` elements. Only use one h1 element per page and place lower importance headings below higher importance headings.

Commenting allows you to leave messages without affecting the browser display. It also allows you to make code inactive. A comment in HTML starts with `<!--`, contains any number of lines of text, and ends with `-->`.

You can add images to your website by using the `img` element. `img` elements have an opening tag without a closing tag.

HTML attributes are special words used inside the opening tag of an element to control the element's behavior. The `src` attribute in an `img` element specifies the image's URL (where the image is located).

```html
<img src="https://www.example.com/the-image.jpg">
```

The `alt` attribute's text is used for screen readers to improve accessibility and is displayed if the image fails to load. 

 ```html
 <img src="cat.jpg" alt="A cat">
 ```

You can link to another page with the anchor (`a`) element. 

 ```html
 <a href='https://freecodecamp.org'></a>
 ```

A link's text must be placed between the opening and closing tags of an anchor (`a`) element.

 ```html
 <a href="https://www.freecodecamp.org">click here to go to freeCodeCamp.org</a>
 ```

Use list item (`li`) elements to create items in a list. Here is an example of list items in an unordered list:

 ```html
<ul>
  <li>milk</li>
  <li>cheese</li>
</ul>
```

The `figure` element represents self-contained content and will allow you to associate an image with a caption.

A figure caption (`figcaption`) element is used to add a caption to describe the image contained within the figure element. 

The code for an ordered list (`ol`) is similar to an unordered list, but list items in an ordered list are numbered when displayed.

The action attribute indicates where form data should be sent. For example, 

```html
<form action="/submit-url"></form>
```

tells the browser that the form data should be sent to the path /submit-url.

The input element allows you several ways to collect data from a web form. Like img elements, input elements are self-closing and do not need closing tags.

There are many kinds of inputs you can create using the type attribute. You can easily create a password field, reset button, or a control to let users select a file from their computer.

In order for a form's data to be accessed by the location specified in the action attribute, you must give the text field a name attribute and assign it a value to represent the data being submitted. For example, you could use the following syntax for an email address text field: 

```html
<input type="text" name="email">
```

Placeholder text is used to give people a hint about what kind of information to enter into an input.

```html
<input type="text" placeholder="Email address">
```

To prevent a user from submitting your form when required information is missing, you need to add the `required` attribute to an input element. There's no need to set a value to the `required` attribute. Instead, just add the word required to the `input` element, making sure there is space between it and other attributes.

```html
<input type="text" name="catphotourl" placeholder="cat photo URL" required>
```

Use the `button` element to create a clickable button. The default behavior of clicking a form button without any attributes submits the form to the location specified in the form's action attribute. Add the type attribute with the value `submit` to the button to make it clear that it is a submit button.

```html
<button type="submit">Click Here</button>
```

You can use radio buttons for questions where you want only one answer out of multiple options.

```html
<input type="radio"> cat
```

`label` elements are used to help associate the text for an `input` element with the input element itself (especially for assistive technologies like screen readers). 

 ```html
 <label><input type="radio"> cat</label>
 ```

The `id` attribute is used to identify specific HTML elements. Each `id` attribute's value must be unique from all other `id` values for the entire page.

```html
 <label><input type="radio" id="indoor"> Indoor</label>
 ```

To make it so selecting one radio button automatically deselects the other, both buttons must have a `name` attribute with the same value.

 ```html
<label><input id="indoor" type="radio" name="indoor-outdoor"> Indoor</label>
<label><input id="outdoor" type="radio" name="indoor-outdoor"> Outdoor</label>
 ```

If you select the Indoor radio button and submit the form, the form data for the button is based on its `name` and `value` attributes. Since your radio buttons do not have a `value` attribute, the form data will include `indoor-outdoor=on`, which is not useful when you have multiple buttons.

 ```html
 <label><input id="indoor" type="radio" name="indoor-outdoor" value="indoor"> Indoor</label>
 <label><input id="outdoor" type="radio" name="indoor-outdoor" value="outdoor"> Outdoor</label>
 ```

The `fieldset` element is used to group related inputs and labels together in a web form. `fieldset` elements are block-level elements, meaning that they appear on a new line.

 ```html
 <fieldset>
   <label><input id="indoor" type="radio" name="indoor-outdoor" value="indoor"> Indoor</label>
   <label><input id="outdoor" type="radio" name="indoor-outdoor" value="outdoor"> Outdoor</label>
 </fieldset>
 ```

The `legend` element acts as a caption for the content in the `fieldset` element. It gives users context about what they should enter into that part of the form.

  ```html
 <fieldset>
   <legend>Is your cat an indoor or outdoor cat?</legend>
   <label><input id="indoor" type="radio" name="indoor-outdoor" value="indoor"> Indoor</label>
   <label><input id="outdoor" type="radio" name="indoor-outdoor" value="outdoor"> Outdoor</label>
 </fieldset>
 ```

Forms commonly use checkboxes for questions that may have more than one answer. 

 ```html
 <input type="checkbox"> tacos
 ```

There's another way to associate an input element's text with the element itself. You can nest the text within a `label` element and add a `for` attribute with the same value as the input element's `id` attribute.

```html
<input id="loving" type="checkbox"> <label for="loving">Loving</label>
```

Like radio buttons, form data for selected checkboxes are name / value attribute pairs. While the value attribute is optional, it's best practice to include it with any checkboxes or radio buttons on the page.

In order to make a checkbox checked or radio button selected by default, you need to add the `checked` attribute to it. There's no need to set a value to the `checked` attribute. Instead, just add the word checked to the input element, making sure there is space between it and other attributes.

```html
<input id="loving" type="checkbox" name="personality" value="loving" checked> <label for="loving">Loving</label>
```

`footer` element.

```html
<footer>
  <p>No Copyright - freeCodeCamp.org</p>
</footer>
```

Notice that everything you've added to the page so far is inside the `body` element. All page content elements that should be rendered to the page go inside the `body` element. However, other important information goes inside the `head` element.

The `title` element determines what browsers show in the title bar or tab for the page.

```html
<head>
  <title>CatPhotoApp</title>
</head>
```

Notice that the entire contents of the page are nested within an `html` element. All other elements must be descendants of this `html` element.

Add the `lang` attribute with the value en to the opening `html` tag to specify that the language of the page is English.

```html
<html lang="en">
```

All pages should begin with `<!DOCTYPE html>`. This special string is known as a declaration and ensures the browser tries to meet industry-wide specifications.

You can set browser behavior by adding self-closing `meta` elements in the `head`. 

```html
<meta charset="UTF-8">
```

# Learn Basic CSS by Building a Cafe Menu

[[Cafe Menu HTML]]
[[Cafe Menu CSS]]

**CSS tells the browser how to display your webpage. You can use CSS to set the color, font, size, and other aspects of HTML elements.**

You can add style to an element by specifying it in the style element and setting a property for it like this:

```html
<style>
  h1 {
    text-align: center;
  }
</style>
```

You can add the same group of styles to many elements by creating a list of selectors. Each selector is separated with commas like this:

 ```html
<style>
  h1, h2, p {
    text-align: center;
  }
</style>
 ```

You have styled three elements by writing CSS inside the `style` tags. This works, but since there will be many more styles, it's best to put all the styles in a separate file and link to it.

 ```html
 <head>
   <meta charset="utf-8" />
   <title>Cafe Menu</title>
   <link rel="stylesheet" href="styles.css">
 </head>
 ```

For the styling of the page to look similar on mobile as it does on a desktop or laptop, you need to add a `meta` element with a special `content` attribute.

 ```html
<meta name="viewport" content="width=device-width, initial-scale=1.0" />
 ```

The `div` element is used mainly for design layout purposes unlike the other content elements you have used so far. 

Comments in CSS look like this:

```css
/* comment here */
```

Next, you want to center the `div` horizontally. You can do this by setting its `margin-left` and `margin-right` properties to auto. 

```css
div {
  width: 80%;
  background-color: burlywood;
  margin-left: auto;
  margin-right: auto;
}
```

A class selector is defined by a name with a dot directly in front of it, like this:

 ```css
 .menu {
  width: 80%;
  background-color: burlywood;
  margin-left: auto;
  margin-right: auto;
}
 ```
 ```html
 <div class="menu">
 ```
 ```css
 body {
   background-image: url(https://cdn.freecodecamp.org/curriculum/css-cafe/beans.jpg);
 }
 ```

`article` elements commonly contain multiple elements that have related information. 

`p` elements are block-level elements, so they take up the entire width of their parent element.

The `p` elements are nested in an `article` element with the class attribute of item. You can style all the `p` elements nested anywhere in elements with a class named item like this:

```css
.item p {
  display: inline-block;
}
```

`inline-block` elements only take up the width of their content.

Padding.

```css
.menu {
  width: 80%;
  background-color: burlywood;
  margin-left: auto;
  margin-right: auto;
  padding: 20px;
}
```

The current width of the menu will always take up 80% of the `body` element's width. Add a `max-width` property to the menu class with a value of 500px to prevent it from growing too wide.

```css
.menu {
  width: 80%;
  max-width: 500px;
  background-color: burlywood;
  margin-left: auto;
  margin-right: auto;
  padding: 20px;
}
```

You can change the `font-family` of text, to make it look different from the default font of your browser. Each browser has some common fonts available to it.

```css
body {
  background-image: url(https://cdn.freecodecamp.org/curriculum/css-cafe/beans.jpg);
  font-family: sans-serif;
}
```

You can add a fallback value for the `font-family` by adding another font name separated by a comma. Fallbacks are used in instances where the initial is not found/available.

```css
h1, h2 {
  font-family: Impact, serif;
}
```

Make text italicized.

```css
.established {
  font-style: italic;
}
```

Font size.

```css
h1 {
  font-size: 40px;
}
```

You can use an `hr` element to display a divider between sections of different content. Note that `hr` elements are self closing.

```html
<hr>
```

The default properties of an `hr` element will make it appear as a thin light grey line. You can change the height of the line by specifying a value for the `height` property.

```css
hr {
  height: 3px;
}
```

Notice the grey color along the edges of the line. Those edges are known as borders. Each side of an element can have a different color or they can all be the same.

```css
hr {
  height: 3px;
  background-color: brown;
  border-color: brown;
}
```

The default value of a property named `border-width` is 1px for all edges of `hr` elements.

The default color of a link that has not yet been clicked on is typically blue. The default color of a link that has already been visited from a page is typically purple.

```css
a {
  color: black;
}
```

You change properties of a link when the link has actually been visited by using a pseudo-selector that looks like `a:visited { propertyName: propertyValue; }`.

```css
a:visited {
  color: grey;
}
```

You change properties of a link when the mouse hovers over them by using a pseudo-selector that looks like `a:hover { propertyName: propertyValue; }`.

```css
a:hover {
  color: brown;
}
```

You change properties of a link when the link is actually being clicked by using a pseudo-selector that looks like `a:active { propertyName: propertyValue; }`.

```css
a:active {
  color: white;
}
```

`img` elements are "like" inline elements.

```css
img {
  display: block;
  margin-left: auto;
  margin-right: auto;
}
```

The `h2` elements have default top and bottom margin space, so you could change the bottom margin of the `h2` elements to say 0 or another number.
There is an easier way, simply add a negative top margin to the `img` elements to pull them up from their current positions. Negative values are created using a - in front of the value. 

```css
img {
  display: block;
  margin-left: auto;
  margin-right: auto;
  margin-top: -25px;
}
```

# Learn CSS Colors by Building a Set of Colored Markers

[[CSS Color Markers HTML]]
[[CSS Color Markers CSS]]

**Selecting the correct colors for your webpage can greatly improve the aesthetic appeal to your readers.**

To tell browsers how to encode characters on your page, set the `charset` to `utf-8`. `utf-8` is a universal character set that includes almost every character from all human languages.

```html
<meta charset="utf-8">
```

The `margin` shorthand property makes it easy to set multiple margin areas at the same time.

```css
.marker {
  width: 200px;
  height: 25px;
  background-color: red;
  margin: auto;
}
```

When the shorthand `margin` property has two values, it sets `margin-top` and `margin-bottom` to the first value, and `margin-left` and `margin-right` to the second value.

```css
.marker {
  width: 200px;
  height: 25px;
  background-color: red;
  margin: 10px auto;
}
```

Multiple classes can be added to an element by listing them in the `class` attribute and separating them with a space.

```html
<div class="marker one">
</div>
```

There are two main color models: the additive RGB (red, green, blue) model used in electronic devices, and the subtractive CMYK (cyan, magenta, yellow, black) model used in print.
In this project, you'll work with the RGB model. This means that colors begin as black, and change as different levels of red, green, and blue are introduced. An easy way to see this is with the CSS rgb function.

```css
.container {
  background-color: rgb(0, 0, 0);
}
```

A function is a piece of code that can take an input and perform a specific action. The CSS rgb function accepts values, or arguments, for red, green, and blue, and produces a color.
Each red, green, and blue value is a number from 0 to 255. 0 means that there's 0% of that color, and is black. 255 means that there's 100% of that color.

Secondary colors are the colors you get when you combine primary colors.
Tertiary colors are created by combining a primary with a nearby secondary color.

A color wheel is a circle where similar colors, or hues, are near each other, and different ones are further apart.

Two colors that are opposite from each other on the color wheel are called complementary colors. If two complementary colors are combined, they produce gray. But when they are placed side-by-side, these colors produce strong visual contrast and appear brighter.

It's better practice to choose one color as the dominant color, and use its complementary color as an accent to bring attention to certain content on the page.

A very common way to apply color to an element with CSS is with hexadecimal or hex values. Hex color values start with a `#` character and take six characters from 0-9 and A-F. The first pair of characters represent red, the second pair represent green, and the third pair represent blue.

```css
.green {
  background-color: #00FF00;
}
```

With hex colors, 00 is 0% of that color, and FF is 100%. So ```#00FF00``` translates to 0% red, 100% green, and 0% blue, and is the same as rgb(0, 255, 0).

The HSL color model, or hue, saturation, and lightness, is another way to represent colors.
The CSS hsl function accepts 3 values: a number from 0 to 360 for hue, a percentage from 0 to 100 for saturation, and a percentage from 0 to 100 for lightness.
If you imagine a color wheel, the hue red is at 0 degrees, green is at 120 degrees, and blue is at 240 degrees.

Saturation is the intensity of a color from 0%, or gray, to 100% for pure color.

Lightness is how bright a color appears, from 0%, or complete black, to 100%, complete white, with 50% being neutral.

```css
.blue {
  background-color: hsl(240, 100%, 50%);
}
```

A gradient is when one color transitions into another. The CSS `linear-gradient` function lets you control the direction of the transition along a line, and which colors are used.

One thing to remember is that the `linear-gradient` function actually creates an image element, and is usually paired with the background property which can accept an image as a value.

`linear-gradient(gradientDirection, color1, color2, ...);`

`gradientDirection` is the direction of the line used for the transition. `color1` and `color2` are color arguments, which are the colors that will be used in the transition itself. These can be any type of color, including color keywords, hex, rgb, or hsl.

```css
.red {
  background: linear-gradient(90deg, rgb(255, 0, 0), rgb(0, 255, 0));
}
```

Color-stops allow you to fine-tune where colors are placed along the gradient line. They are a length unit like px or percentages that follow a color in the `linear-gradient` function.

```css
.red {
  background: linear-gradient(90deg, rgb(255, 0, 0) 75%, rgb(0, 255, 0), rgb(0, 0, 255));
}
```

If no `gradientDirection` argument is provided to the `linear-gradient` function, it arranges colors from top to bottom, or along a 180 degree line, by default.

Opacity describes how opaque, or non-transparent, something is. With the CSS `opacity` property, you can control how opaque or transparent an element is. With the value 0, or 0%, the element will be completely transparent, and at 1.0, or 100%, the element will be completely opaque like it is by default.

```css
.sleeve {
  width: 110px;
  height: 25px;
  background-color: white;
  opacity: 0.5;
}
```

Another way to set the opacity for an element is with the alpha channel. Similar to the opacity property, the alpha channel controls how transparent or opaque a color is. To add an alpha channel to an rgb color, use the `rgba` function instead.

```css
.sleeve {
  width: 110px;
  height: 25px;
  background-color: rgba(255, 255, 255, 50%);
}
```

This is because the default display property for `div` elements is block. So when two block elements are next to each other, they stack like actual blocks.

All HTML elements have borders, though they're usually set to `none` by default.

```css
.sleeve {
  width: 110px;
  height: 25px;
  background-color: rgba(255, 255, 255, 0.5);
  border-left-width: 10px;
}
```

Borders have several styles to choose from. You can make your border a solid line, but you can also use a dashed or dotted line if you prefer.

```css
.sleeve {
  width: 110px;
  height: 25px;
  background-color: rgba(255, 255, 255, 0.5);
  border-left-width: 10px;
  border-left-style: solid;
}
```

Your border should be visible now. If no color is set, black is used by default. But to make your code more readable, it's better to set the border color explicitly.

```css
.sleeve {
  width: 110px;
  height: 25px;
  background-color: rgba(255, 255, 255, 0.5);
  border-left-width: 10px;
  border-left-style: solid;
  border-left-color: black;
}
```

The `border-left` shorthand property lets you to set the left border's width, style, and color at the same time. Here is the syntax: `border-left: width style color;`

```css
.sleeve {
  width: 110px;
  height: 25px;
  background-color: rgba(255, 255, 255, 0.5);
  border-left: 10px solid black;
}
```

For the `border-left` shorthand property, change the border style value from solid to double.

```css
.sleeve {
  width: 110px;
  height: 25px;
  background-color: rgba(255, 255, 255, 0.5);
  border-left: 10px double black;
}
```

The `box-shadow` property lets you apply one or more shadows around an element. Here is basic syntax: `box-shadow: offsetX offsetY color;`

```css
.red {
  background: linear-gradient(rgb(122, 74, 14), rgb(245, 62, 113), rgb(162, 27, 27));
  box-shadow: 5px 5px red;
}
```

But what if you wanted to position your shadow on the opposite side? You can do that by using negative values for offsetX and offsetY.

```css
.red {
  background: linear-gradient(rgb(122, 74, 14), rgb(245, 62, 113), rgb(162, 27, 27));
  box-shadow: -5px -5px red;
}
```

Notice that the edges of the shadow are sharp. This is because there is an optional `blurRadius` value for the `box-shadow` property: `box-shadow: offsetX offsetY blurRadius color;`

If a `blurRadius` value isn't included, it defaults to 0 and produces sharp edges. The higher the value of `blurRadius`, the greater the blurring effect is.

```css
.green {
  background: linear-gradient(#55680D, #71F53E, #116C31);
  box-shadow: 5px 5px 5px green;
}
```

But what if you wanted to expand the shadow out further? You can do that with the optional `spreadRadius` value: `box-shadow: offsetX offsetY blurRadius spreadRadius color;`

Like `blurRadius`, `spreadRadius` defaults to 0 if it isn't included.

```css
.blue {
  background: linear-gradient(hsl(186, 76%, 16%), hsl(223, 90%, 60%), hsl(240, 56%, 42%));
  box-shadow: 0 0 0 5px blue;
}
```

# Learn HTML Forms by Building a Registration Form

[[Registration Form HTML]]
[[Registration Form CSS]]

**You can use HTML forms to collect information from people who visit your webpage.**

The `vh` unit stands for viewport height, and is relative to 1% of the height of the viewport.

```css
body {
  width: 100%;
  height: 100vh;
}
```

Get rid of the horizontal scroll-bar, by setting the `body` default margin added by some browsers to 0.

```css
body {
  width: 100%;
  height: 100vh;
  margin: 0;
}
```

The `method` attribute specifies how to send form-data to the URL specified in the `action` attribute. The form-data can be sent via a GET request as URL parameters (with `method="get"`) or via a POST request as data in the request body (with `method="post"`).

```html
<form action='https://register-demo.freecodecamp.org' method="post"></form>
```

The `rem` unit stands for root em, and is relative to the font size of the `html` element.

As `label` elements are inline by default, they are all displayed side by side on the same line, making their text hard to read.

```css
label {
  display: block;
  margin: 0.5rem 0;
}
```

Specifying the `type` attribute of a `form` element is important for the browser to know what kind of data it should expect. If the type is not specified, the browser will default to text.

The `email` type only allows emails with a @ and a . in the domain. The `password` type obscures the input, and warns if the site does not use HTTPS.

```html
<fieldset>
    <label for="first-name">Enter Your First Name: <input id="first-name" type="text"/></label>
    <label for="last-name">Enter Your Last Name: <input id="last-name" type="text" /></label>
    <label for="email">Enter Your Email: <input id="email" type="email" /></label>
    <label for="new-password">Create a New Password: <input id="new-password" type="password" /></label>
</fieldset>
```

The first `input` element with a type of `submit` is automatically set to submit its nearest parent `form` element.

```html
<input type="submit" value="Submit">
```

Add custom validation to the `password` input element, by adding a `minlength` attribute.

```html
<label for="new-password">Create a New Password: <input id="new-password" type="password" minlength="8" required/></label>
```

With `type="password"` you can use the `pattern` attribute to define a regular expression that the password must match to be considered valid.

Add a `pattern` attribute to the `password` input element to require the input match: `[a-z0-5]{8,}`

The above is a regular expression which matches eight or more lowercase letters or the digits 0 to 5.

```html
<label for="new-password">Create a New Password: <input id="new-password" type="password" pattern="[a-z0-5]{8,}" required /></label>
```

What if you wanted to allow a user to upload a profile picture? Well, the input type `file` allows just that.

```html
<label>Upload a profile picture: <input type="file" /></label>
```

input with the type of `number`.

```html
<label>Input your age (years): <input type="number" min="13" max="120"></label>
```

Adding a dropdown to the form is easy with the `select` element. The `select` element is a container for a group of option elements, and the option element acts as a label for each dropdown option. Both elements require closing tags.

```html
<label>How did you hear about us?
    <select>
        <option>(select one)</option>
        <option>freeCodeCamp News</option>
        <option>freeCodeCamp YouTube Channel</option>
        <option>freeCodeCamp Forum</option>
        <option>Other</option>
    </select>
</label>
```

Submitting the form with an option selected would not send a useful value to the server. As such, each option needs to be given a `value` attribute. Without which, the text content of the option will be submitted to the server.

```html
<label>How did you hear about us?
    <select>
        <option value="">(select one)</option>
        <option value="1">freeCodeCamp News</option>
        <option value="2">freeCodeCamp YouTube Channel</option>
        <option value="3">freeCodeCamp Forum</option>
        <option value="4">Other</option>
    </select>
</label>
```

The `textarea` element acts like an input element of type text, but comes with the added benefit of being able to receive multi-line text, and an initial number of text rows and columns. Note that the `textarea` requires a closing tag.

```html
<label>Provide a bio: <textarea></textarea></label>
```

To give the `textarea` an initial size, you can add the `rows` and `cols` attributes.

```html
<label for="bio">Provide a bio:
    <textarea id="bio" rows="3" cols="30"></textarea>
</label>
```

The `placeholder` accepts a text value, which is displayed until the user starts typing.

```html
<label for="bio">Provide a bio:
    <textarea id="bio" rows="3" cols="30" placeholder="I like coding on the beach...."></textarea>
</label>
```

With form submissions, it is useful, and good practice, to provide each submittable element with a `name` attribute. This attribute is used to identify the element in the form submission.

You can select the last element of a specific type using the `last-of-type` CSS pseudo-class, like this: `p:last-of-type { }`

```css
fieldset:last-of-type {
  border-bottom: none;
}
```

Select only the .inline elements, and give them width of `unset`. This will remove the earlier rule which set all the input elements to `width: 100%`.

```css
.inline {
  width: unset;
}
```

Set the `vertical-align` property to `middle`.

```css
.inline {
  width: unset;
  margin: 0 0.5em 0 0;
  vertical-align: middle;
}
```

Minimun height.

```css
input, textarea {
  background-color: #0a0a23;
  border: 1px solid #0a0a23;
  color: #ffffff;
  min-height: 2em;
}
```

To style the submit button, you can use an attribute selector, which selects an element based on the given attribute value. Here is an example: `input[name="password"]`

```css
input[type="submit"] {
  display: block;
  width: 60%;
}
```

Most browsers inject their own default CSS properties and values for different elements. If you look closely, you might be able to notice the file input is smaller than the other text input elements. By default, a padding of 1px 2px is given to input elements you can type in.

# Learn the CSS Box Model by Building a Rothko Painting

[[Box Model HTML]]
[[Box Model CSS]]

**Every HTML element is its own box – with its own spacing and a border. This is called the Box Model.**

In the CSS box model, every HTML element is treated as a box with four areas.

The content is surrounded by a space called padding, similar to how bubble wrap separates an item from the box around it.

Think of the border like the cardboard box your item was shipped in.

Margin is the area outside of the box, and can be used to control the space between other boxes or elements.

Replace the `padding` property with `overflow` set to `hidden` - changing the canvas back to its original dimensions.

```css
.canvas {
  width: 500px;
  height: 600px;
  background-color: #4d0f00;
  overflow: hidden;
}
```

You don't always have to use pixels when sizing an element.

```css
.three {
  width: 91%;
}
```

Use the `filter` property to blur the painting by 2px in the .canvas element.

```css
.canvas {
  width: 500px;
  height: 600px;
  background-color: #4d0f00;
  overflow: hidden;
  filter: blur(2px);
}
```

Round each corner of the .one element by 9 pixels, using the `border-radius` property.

```css
.one {
  width: 425px;
  height: 150px;
  background-color: #efb762;
  margin: 20px auto;
  box-shadow: 0 0 3px 3px #efb762;
  border-radius: 9px;
}
```

The `border-radius` property accepts up to four values to round the `top-left`, `top-right`, `bottom-right`, and `bottom-left` corners.

```css
.three {
  width: 91%;
  height: 28%;
  background-color: #b20403;
  margin: auto;
  filter: blur(2px);
  box-shadow: 0 0 5px 5px #b20403;
  border-radius: 30px 25px 60px 12px;
}
```

Use the `transform` property on the .one selector to rotate it counter clockwise by 0.6 degrees.

```css
.one {
  width: 425px;
  height: 150px;
  background-color: #efb762;
  margin: 20px auto;
  box-shadow: 0 0 3px 3px #efb762;
  border-radius: 9px;
  transform: rotate(-0.6deg);
}
```

# Learn CSS Flexbox by Building a Photo Gallery

[[CSS Flexbox Gallery HTML]]
[[CSS Flexbox Gallery CSS]]

**Flexbox helps you design your webpage so that it looks good on any screen size.**

Normalize your box model by creating a `*` selector and setting the `box-sizing` property to `border-box` as the value.

```css
* {
  box-sizing: border-box;
}
```

Make the text uppercase using the `text-transform` property with `uppercase` as the value.

```css
.header {
  text-align: center;
  text-transform: uppercase;
  padding: 32px;
  background-color: #0a0a23;
  color: #fff;
  border-bottom: 4px solid #fdb347;
}
```

Flexbox is a one-dimensional CSS layout that can control the way items are spaced out and aligned within a container.

To use it, give an element a `display` property of `flex`. This will make the element a flex container. Any direct children of a flex container are called flex items.

```css
.gallery {
  display: flex;
}
```

Flexbox has a main and cross axis. The main axis is defined by the flex-direction property, which has four possible values:

- `row` (default): horizontal axis with flex items from left to right
- `row-reverse`: horizontal axis with flex items from right to left
- `column`: vertical axis with flex items from top to bottom
- `column-reverse`: vertical axis with flex items from bottom to top

Note: The axes and directions will be different depending on the text direction. The values shown are for a left-to-right text direction.

```css
.gallery {
  display: flex;
  flex-direction: row;
}
```

The `flex-wrap` property determines how your flex items behave when the flex container is too small. Setting it to wrap will allow the items to wrap to the next row or column. `nowrap` (default) will prevent your items from wrapping and shrink them if needed.

```css
.gallery {
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
}
```

The `justify-content` property determines how the items inside a flex container are positioned along the main axis, affecting their position and the space around them.

```css
.gallery {
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  justify-content: center;
}
```

The `align-items` property positions the flex content along the cross axis. In this case, with your `flex-direction` set to `row`, your cross axis would be vertical.

```css
.gallery {
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  justify-content: center;
  align-items: center;
}
```

Notice how some of your images have become distorted. This is because the images have different aspect ratios. Rather than setting each aspect ratio individually, you can use the `object-fit` property to determine how images should behave.

Give your .gallery img selector the `object-fit` property and set it to `cover`. This will tell the image to fill the img container while maintaining aspect ratio, resulting in cropping to fit.

```css
.gallery img {
  width: 100%;
  max-width: 350px;
  height: 300px;
  object-fit: cover;
}
```

The `gap` CSS shorthand property sets the gaps, also knowns as gutters, between rows and columns. The gap property and its `row-gap` and `column-gap` sub-properties provide this functionality for flex, grid, and multi-column layout. You apply the property to the container element.

```css
.gallery {
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  justify-content: center;
  align-items: center;
  max-width: 1400px;
  margin: 0 auto;
  padding: 20px 10px;
  gap: 16px;
}
```

The `::after` pseudo-element creates an element that is the last child of the selected element. 

```css
.gallery::after {
  content: "";
  width: 350px;
}
```

# Learn Typography by Building a Nutrition Label

[[Nutrition Label HTML]]
[[Nutrition Label CSS]]

**Typography is the art of styling your text to be easily readable and suit its purpose.**

Within your `head` element, add a `link` element with the `rel` attribute set to `stylesheet` and the `href` attribute set to `https://fonts.googleapis.com/css?family=Open+Sans:400,700,800`.

This will import the Open Sans font family, with the font weight values 400, 700, and 800.

```html
<head>
	<meta charset="UTF-8">
    <title>Nutrition Label</title>
    <link rel="stylesheet" href="https://fonts.googleapis.com/css?family=Open+Sans:400,700,800">
    <link rel="stylesheet" href="styles.css">
</head>
```

Remember that fonts with spaces in the name must be wrapped in quotes for CSS.

```css
body {
  font-family: "Open Sans", sans-serif;
}
```

If you inspect your .label element with your browser's developer tools, you may notice that it's actually 288 pixels wide instead of 270. This is because, by default, the browser includes the border and padding when determining an element's size.

To solve this, reset the box model by creating a `*` selector and giving it a `box-sizing` property of `border-box`.

Create an `h1` rule and set the `font-weight` property to 800. This will make your `h1` text bolder.

```css
h1 {
  font-weight: 800;
}
```

The `letter-spacing` property can be used to adjust the space between each character of text in an element.

```css
h1 {
  font-weight: 800;
  text-align: center;
  margin: -4px 0;
  letter-spacing: 0.15px;
}
```

The `float` property is used to place an element on the left or right of its container, allowing other content (such as text) to wrap around it.

```css
.right {
  float: right;
}
```

Give the `.divider` selector a `clear` property set to `right`. This will clear the `float` property, pushing the divider and any following content down below the float text.

```css
.divider {
  border-bottom: 1px solid #888989;
  margin: 2px 0;
  clear: right;
}
```

The `:not` pseudo-selector can be used to select all elements that do not match the given CSS rule.

``` css
div:not(#example) {
  color: red;
}
```

The above selects all `div` elements without an `id` of example.

# Learn Accessibility by Building a Quiz

[[Accessibility Quiz HTML]]
[[Accessibility Quiz CSS]]

**Accessibility is making your webpage easy for all people to use – even people with disabilities.**

Start this accessibility journey by providing a lang attribute to your html element. This will assist screen readers in identifying the language of the page.

The charset attribute specifies the character encoding of the page, and, nowadays, UTF-8 is the only encoding supported by most browsers.

Continuing with the meta elements, a viewport definition tells the browser how to render the page. Including one betters visual accessibility on mobile, and improves SEO (search engine optimization).

Another important meta element for accessibility and SEO is the description definition. The value of the `content` attribute is used by search engines to provide a description of your page.

```html
<meta name="description" content="useful">
```

Lastly in the `head`, the `title` element is useful for screen readers to understand the content of a page. Furthermore, it is an important part of SEO.

Navigation is a core part of accessibility, and screen readers rely on you to provide the structure of your page. This is accomplished with semantic HTML elements.

The `header` element will be used to introduce the page, as well as provide a navigation menu.

The `main` element will contain the core content of your page.

```html
<body>
    <header></header>
    <main></main>
</body>
```

A useful property of an SVG (scalable vector graphics) is that it contains a path attribute which allows the image to be scaled without affecting the resolution of the resultant image.

Use the `aspect-ratio` property to set the desired aspect ratio.

```css
#logo {
  width: max(100px, 18vw);
  background-color: #0a0a23;
  aspect-ratio: 35 / 4;
  padding: 0.4rem;
}
```

Target unordered list elements within `nav` elements, and use Flexbox to evenly space the children.

```css
nav > ul {
  display: flex;
  justify-content: space-evenly;
}
```

You can semantically separate the content within the form using `section` elements.

To increase the page accessibility, the `role` attribute can be used to indicate the purpose behind an element on the page to assistive technologies. The `role` attribute is a part of the Web Accessibility Initiative (WAI), and accepts preset values.

```html
<section role="region"></section>
```

Every region role requires a visible label, which should be referenced by the `aria-labelledby` attribute.

```html
<section role="region" aria-labelledby="student-info"><h2 id="student-info">Student Info</h2></section>
```

Typeface plays an important role in the accessibility of a page. Some fonts are easier to read than others, and this is especially true on low-resolution screens.

To be able to navigate within the page, give each anchor element an `href` corresponding to the `id` of the `h2` elements.

```html
<nav>
    <ul>
        <li><a href="#student-info">INFO</a></li>
        <li><a href="#html-questions">HTML</a></li>
        <li><a href="#css-questions">CSS</a></li>
    </ul>
</nav>
```

Even though you added a placeholder to the first input element in the previous lesson, this is actually not a best-practice for accessibility; too often, users confuse the placeholder text with an actual input value - they think there is already a value in the input.

Arguably, D.O.B. is not descriptive enough. This is especially true for visually impaired users. One way to get around such an issue, without having to add visible text to the label, is to add text only a screen reader can read.

```html
<label for="birth-date">D.O.B.<span class="sr-only">(Date of Birth)</span></label>
```

There is a common pattern to visually hide text for only screen readers to read.

```css
.sr-only {
  position: absolute;
  width: 1px;
  height: 1px;
  padding: 0;
  margin: -1px;
  overflow: hidden;
  clip: rect(0, 0, 0, 0);
  white-space: nowrap;
  border: 0;
}
```

To prevent unnecessary repetition, target the `before` pseudo-element of the `p` element, and give it a content property of "Question #".

```css
p:before {
  content: "Question #";
}
```

The `footer` element is a container for a collection of content that is related to the page, and the address element is a container for contact information for the author of the page.

```html
<footer>
  <address>
	freeCodeCamp<br />
	San Francisco<br />
	California<br />
	USA
  </address>
</footer>
```

On the topic of visual accessibility, contrast between elements is a key factor. For example, the contrast between the text and the background of a heading should be at least 4.5:1.

To make the navigation buttons look more like typical buttons, remove the underline from the anchor tags.

Then, create a new selector targeting the navigation list elements so that when the cursor hovers over them, the background color and text color are switched, and the cursor becomes a pointer.

```css
nav li:hover {
  background-color: #dfdfe2;
  color: #1b1b32;
  cursor: pointer;
}

li > a {
  color: inherit;
  text-decoration: none;
}
```

Tidy up the header, by using Flexbox to put space between the children, and vertically center them. Then, fix the header to the top of the viewport.

```css
header {
  width: 100%;
  height: 50px;
  background-color: #1b1b32;
  display: flex;
  justify-content: space-between;
  align-items: center;
  position: fixed;
  top: 0;
}
```

Clicking on the navigation links should jump the viewport to the relevant section. However, this jumping can be disorienting for some users.

```css
* {
  scroll-behavior: smooth;
}
```

Certain types of motion-based animations can cause discomfort for some users. In particular, people with vestibular disorders have sensitivity to certain motion triggers.

The `@media` at-rule has a media feature called `prefers-reduced-motion` to set CSS based on the user's preferences. It can take one of the following values:

- `reduce`
- `no-preference`

```css
@media (prefers-reduced-motion: no-preference) {
  * {
    scroll-behavior: smooth;
  }
}
```

The navigation accessibility can be improved by providing keyboard shortcuts. The `accesskey` attribute accepts a space-separated list of access keys.

```html
<nav>
    <ul>
        <li><a href="#student-info" accesskey="i">INFO</a></li>
        <li><a href="#html-questions" accesskey="h">HTML</a></li>
        <li><a href="#css-questions" accesskey="c">CSS</a></li>
    </ul>
</nav>
```

# Learn More About CSS Pseudo Selectors By Building a Balance Sheet

[[Balance Sheet HTML]]
[[Balance Sheet CSS]]

**You can use CSS pseudo selectors to change specific HTML elements.**

You want this particular element to be hidden from screen readers, so give it the `aria-hidden` attribute set to `true`.

```html
<div id="years" aria-hidden="true"></div>
```

HTML tables use the `caption` element to describe what the table is about. The `caption` element should always be the first child of a table, but can be positioned with the `caption-side` CSS property.

```html
<table>
    <caption>Assets</caption>
</table>
```

The `thead` and `tbody` elements are used to indicate which portion of your table is the header, and which portion contains the primary data or content.

```html
<table>
    <caption>Assets</caption>
    <thead></thead>
    <tbody></tbody>
</table>
```

The `tr` element is used to indicate a table row. The `td` element indicates a data cell, while the `th` element indicates a header cell.

```html
<thead>
    <tr>
        <td></td>
        <th></th>
        <th></th>
        <th></th>
    </tr>
</thead>
```

Leave the `td` element empty. This element exists only to ensure your table has a four-column layout and associate the headers with the correct columns.

The `span [class~="sr-only"]` selector will select any `span` element whose class includes `sr-only`.

```css
span[class~="sr-only"] {
  border: 0;
}
```

The CSS `clip` property is used to define the visible portions of an element. The `clip-path` property determines the shape the `clip` property should take. 

```css
span[class~="sr-only"] {
  border: 0;
  clip: rect(1px, 1px, 1px, 1px);
  clip-path: inset(50%);
  -webkit-clip-path: inset(50%);
}
```

The `flex-direction` property to `column-reverse` will display the nested elements from bottom to top. 

```css
h1 .flex {
  display: flex;
  flex-direction: column-reverse;
  gap: 1rem;
}
```

The `:first-of-type` pseudo-selector is used to target the first element that matches the selector. 

```css
h1 .flex span:first-of-type {
  font-size: 0.7em;
}
```

Justify the content to the end of the flex direction, and make the element sticky. Fix it to the top of its container with `top: 0`.

```css
#years {
  display: flex;
  justify-content: flex-end;
  position: sticky;
  top: 0;
}
```

The `calc()` function is a CSS function that allows you to calculate a value based on other values.

Ensure your years do not get hidden by setting a `z-index` of 999.

```css
#years {
  display: flex;
  justify-content: flex-end;
  position: sticky;
  top: 0;
  background: #0a0a23;
  color: #fff;
  z-index: 999;
  margin: 0 -2px;
  padding: 0.5rem calc(1.25rem + 2px) 0.5rem 0;
}
```

The `span[class]` syntax will target any span element that has a class attribute set, regardless of the attribute's value.

```css
#years span[class] {
  width: 4.5rem;
  font-weight: bold;
  text-align: right;
}
```

Rather than having to constantly double-check you are not overwriting your earlier properties, you can use the `!important` keyword to ensure these properties are always applied, regardless of order or specificity.

```css
span[class~="sr-only"] {
  border: 0 !important;
  clip: rect(1px, 1px, 1px, 1px) !important;
  clip-path: inset(50%) !important;
  -webkit-clip-path: inset(50%) !important;
  height: 1px !important;
  width: 1px !important;
  position: absolute !important;
  overflow: hidden !important;
  white-space: nowrap !important;
  padding: 0 !important;
  margin: -1px !important;
}
```

Set the `border-collapse` property to `collapse`, which will allow cell borders to collapse into a single border, instead of a border around each cell. 

```css
table {
  border-collapse: collapse;
  border: 0;
}
```

The key difference between `tr[class="total"]` and `tr.total` is that the first will select `tr` elements where the only class is total. The second will select `tr` elements where the class includes total.

The `:nth-of-type()` pseudo-selector is used to target specific elements based on their order among siblings of the same type. 

```css
tr.total td:nth-of-type(3) {
  padding: 0.5rem;
}
```

# Learn Intermediate CSS by Building a Picasso Painting

[[Picasso Painting HTML]]
[[Picasso Painting CSS]]

FontAwesome is a library of SVG-powered icons, many of which are freely available to use.

```html
<link rel="stylesheet" href="https://use.fontawesome.com/releases/v5.8.2/css/all.css">
```

Typically, HTML is rendered in a top-down manner. Elements at the top of the code are positioned at the top of the page. However, many times you may want to move the elements to different positions. You can do this with the position property. An absolute position takes the element out of that top-down document flow and allows you to adjust it relative to its container. When an element is manually positioned, you can shift its layout with top, left, right, and bottom. 

```css
#back-wall {
  background-color: #8B4513;
  width: 100%;
  height: 60%;
  position: absolute;
  top: 0;
  left: 0;
}
```

The `z-index` property is used to create "layers" for your HTML elements. If you are familiar with image editing tools, you may have worked with layers before. This is a similar concept.

Elements with a higher `z-index` value will appear to be layered on top of elements with a lower `z-index` value. 

```css
#back-wall {
  background-color: #8B4513;
  width: 100%;
  height: 60%;
  position: absolute;
  top: 0;
  left: 0;
  z-index: -1;
}
```

The `i` element is used for idiomatic text, or text that is separate from the "normal" text content. This could be for italic text, such as scientific terms, or for icons like those provided by FontAwesome.

This special class is how FontAwesome determines which icon to load. `fas` indicates the category of icons (FontAwesome Solid, here), while `fa-music` selects the specific icon.

```html
<i class="fas fa-music"></i>
<i class="fas fa-bars"></i>
```

FontAwesome icons come with their own styling to define the icon. However, you can still set the styling yourself as well, to change things like the color and size. 

# Learn Responsive Web Design by Building a Piano

[[Piano HTML]]
[[Piano CSS]]

**Responsive Design tells your webpage how it should look on different-sized screens.**

Now that you have reset the html box model, you need to pass that on to the elements within as well. To do this, you can set the `box-sizing` property to `inherit`, which will tell the targeted elements to use the same value as the parent element.

You will also need to target the pseudo-elements, which are special keywords that follow a selector. The two pseudo-elements you will be using are the `::before` and `::after` pseudo-elements.

```css
*, ::before, ::after {
 box-sizing: inherit; 
}
```

To create the black keys, add a new `.key.black--key::after` selector. This will target the elements with the class key black--key, and select the pseudo-element after these elements in the HTML.

The `content` property is used to set or override the content of the element. By default, the pseudo-elements created by the `::before` and `::after` pseudo-selectors are empty, and the elements will not be rendered to the page. Setting the `content` property to an empty string `""` will ensure the element is rendered to the page while still being empty.

```css
.key.black--key::after {
  background-color: #1d1e22;
  content: "";
}
```

The `img` element needs its parent to have a position set as a point of reference.

The `@media` at-rule, also known as a media query, is used to conditionally apply CSS. Media queries are commonly used to apply CSS based on the viewport width using the `max-width` and `min-width` properties.

```css
@media (max-width: 768px) {
  #piano {
    width: 358px;
  }
}
```

Set `overflow` to `hidden` in the first `.keys` selector, to take care of this issue. This property will hide any element that is pushed outside the set width value of `.keys`.

Logical operators can be used to construct more complex media queries. The `and` logical operator is used to query two media conditions.

```css
@media (min-width: 769px) and (max-width: 1199px) {
  
}
```

# Learn CSS Variables by Building a City Skyline

**CSS variables help you organize your styles and reuse them.**

[[City Skyline HTML]]
[[City Skyline CSS]]

In CSS, you can target everything with an asterisk.

```css
* {
  border: 1px solid black;
}
```

You can see the `body` (it's the inner-most box on your page); the box around it is the `html` element. Make your `body` fill the whole viewport by giving it a `height` of `100vh`. Remove the default margin from the body by setting the margin to 0. Finally, set the `overflow` property to `hidden` to hide any scroll bars that appear when something extends past the viewport.

```css
body {
  height: 100vh;
  margin: 0;
  overflow: hidden;
}
```

Variable declarations begin with two dashes (`-`) and are given a name and a value like this: `--variable-name: value;`

```css
.bb1 {
  width: 10%;
  height: 70%;
  display: flex;
  flex-direction: column;
  align-items: center;
  --building-color1: #999;
}
```

To use a variable, put the variable name in parentheses with `var` in front of them like this: `var(--variable-name)`. Whatever value you gave the variable will be applied to whatever property you use it on.

```css
.bb1a {
  width: 70%;
  height: 10%;
  background-color: var(--building-color1);
}
```

This is the main advantage of using variables, being able to quickly change many values in your stylesheet by just changing the value of a variable.

Use the `align-items` and `justify-content` properties to evenly space the buildings across the bottom of the element.

```css
.background-buildings {
  width: 100%;
  height: 100%;
  display: flex;
  justify-content: space-evenly;
  align-items: flex-end;
}
```

You should add a fallback value to a variable by putting it as the second value of where you use the variable like this: `var(--variable-name, fallback-value)`. The property will use the fallback value when there's a problem with the variable.

```css
.bb2 {
  width: 10%;
  height: 50%;
  background-color: var(--building-color2, green);
}
```

That didn't work, because the variables you declared in `.bb1` do not cascade to the `.bb2` and `.bb3` sibling elements. That's just how CSS works. Because of this, variables are often declared in the `:root` selector. This is the highest level selector in CSS; putting your variables there will make them usable everywhere.

```css
:root {
  --building-color1: #aa80ff;
  --building-color2: #66cc99;
  --building-color3: #cc6699;
}
```

Give it a width and height of 100%, set the position to absolute, and the top to 0. This will make it the same size as the body and move the start of it to the top left corner.

```css
.foreground-buildings {
  width: 100%;
  height: 100%;
  position: absolute;
  top: 0;
}
```

Move the position of `.fb4` relative to where it is now by adding a position of `relative` and `left` of 10% to it. 

```css
.fb4 {
  width: 8%;
  height: 45%;
  background-color: var(--building-color1);
  position: relative;
  left: 10%;
}
```

Gradients in CSS are a way to transition between colors across the distance of an element. They are applied to the background property and the syntax looks like this:

```css
gradient-type(
  color1,
  color2
);
```

In the example, color1 is solid at the top, color2 is solid at the bottom, and in between it transitions evenly from one to the next.

```css
.bb1a {
  width: 70%;
  height: 10%;
  background-color: var(--building-color1);
  background: linear-gradient(
      var(--building-color1),
      var(--window-color1)
    );
}
```

Gradients can use as many colors as you want like this:

```css
gradient-type(
  color1,
  color2,
  color3
);
```

```css
.bb1d {
  width: 100%;
  height: 70%;
  background-color: var(--building-color1);
  background: linear-gradient(
    orange,
    var(--building-color1),
    var(--window-color1)
  );
}
```

You can specify where you want a gradient transition to complete by adding it to the color like this:

```css
gradient-type(
  color1,
  color2 20%,
  color3
);
```

Here, it will transition from color1 to color2 between 0% and 20% of the element and then transition to color3 for the rest. 

```css
.bb1d {
  width: 100%;
  height: 70%;
  background: linear-gradient(
      orange,
      var(--building-color1) 80%,
      var(--window-color1)
    );
}
```

Gradient transitions often gradually change from one color to another. You can make the change a solid line like this:

```css
linear-gradient(
  var(--first-color) 0%,
  var(--first-color) 40%,
  var(--second-color) 40%,
  var(--second-color) 80%
);
```

```css
.bb2b {
  width: 100%;
  height: 100%;
  background: linear-gradient(
    var(--building-color2) 0%,
    var(--building-color2) 6%,
    var(--window-color2) 6%,
    var(--window-color2) 9%
  );
}
```

Change the gradient type from `linear-gradient` to `repeating-linear-gradient` for this section. This will make the four colors of your gradient repeat until it gets to the bottom of the element; giving you some stripes, and saving you from having to add a bunch of elements to create them.

```css
.bb2b {
  width: 100%;
  height: 100%;
  background: repeating-linear-gradient(
      var(--building-color2),
      var(--building-color2) 6%,
      var(--window-color2) 6%,
      var(--window-color2) 9%
    );
}
```

After you add these, you can see how a thick border on an element gives you some angles where two sides meet.

```css
.bb2a {
  margin: auto;
  width: 5vw;
  height: 5vw;
  border-top: 1vw solid #000;
  border-bottom: 1vw solid #000;
  border-left: 1vw solid #999;
  border-right: 1vw solid #999;
}
```

Remove the width and height from `.bb2a`, and change the `border-left` and `border-right` to use `5vw` instead of `1vw`. The element will now have zero size and the borders will come together in the middle.

```css
.bb2a {
  margin: auto;
  border-top: 1vw solid #000;
  border-bottom: 1vw solid #000;
  border-left: 5vw solid #999;
  border-right: 5vw solid #999;
}
```

Remove the `margin` and `border-top` properties and values from `.bb2a` to turn it into a triangle for the top of the building.

```css
.bb2a {
  border-bottom: 1vw solid #000;
  border-left: 5vw solid transparent;
  border-right: 5vw solid transparent;
}
```

Finally, on the `border-bottom` property of `.bb2a`, change the `1vw` to `5vh` and change the `#000` color to your `--building-color2` variable. 

```css
.bb2a {
  border-bottom: 5vh solid var(--building-color2);
  border-left: 5vw solid transparent;
  border-right: 5vw solid transparent;
}
```

So far, all the gradients you created have gone from top to bottom, that's the default direction. You can specify another direction by adding it before your colors like this:

```css
gradient-type(
  direction,
  color1,
  color2
);
```

Fill in `.bb3` with a `repeating-linear-gradient`. Use `90deg` for the direction, your `building-color3` for the first two colors, and `window-color3` at 15% for the third. When you don't specify a distance for a color, it will use the values that makes sense. In this case, the first two colors will default to 0% and 7.5% because it starts at 0%, and 7.5% is half of the 15%.

```css
.bb3 {
  width: 10%;
  height: 55%;
  background-color: var(--building-color3);
  background: repeating-linear-gradient(
    90deg,
    var(--building-color3),
    var(--building-color3),
    var(--window-color3) 15%
  );
}
```

You can add multiple gradients to an element by separating them with a comma (,) like this:

```css
gradient1(
  colors
),
gradient2(
  colors
);
```

```css
.fb1c {
  width: 100%;
  height: 80%;
  background: repeating-linear-gradient(
      90deg,
      var(--building-color4),
      var(--building-color4) 10%,
      transparent 10%,
      transparent 15%
    ),
    repeating-linear-gradient(
      var(--building-color4),
      var(--building-color4) 10%,
      var(--window-color4) 10%,
      var(--window-color4) 90%
    );
}
```

Give the sky class a `radial-gradient`. Use `#ffcf33` from 0% to 20%, `#ffff66` at 21%, and `#bbeeff` at 100%. This will add circular gradient to the background that will be your sun.

```css
.sky {
  background: radial-gradient(
    #ffcf33,
    #ffcf33 20%,
    #ffff66 21%,
    #bbeeff 100%
  );
}
```

At the top of the sky gradient color list, where you would put a direction for the gradient; add circle `closest-corner` at 15% 15%,. This will move the start of the gradient to 15% from the top and left. It will make it end at the `closest-corner` and it will maintain a circle shape. These are some keywords built into gradients to describe how it behaves.

```css
.sky {
  background: radial-gradient(
	    circle closest-corner at 15% 15%,
      #ffcf33,
      #ffcf33 20%,
      #ffff66 21%,
      #bbeeff 100%
    );
}
```

# Learn CSS Grid by Building a Magazine

**CSS Grid gives you control over the rows and columns of your webpage design.**

[[Magazine HTML]]
[[Magazine CSS]]

The loading attribute on an img element can be set to lazy to tell the browser not to fetch the image resource until it is needed (as in, when the user scrolls the image into view). As an additional benefit, lazy loaded elements will not load until the non-lazy elements are loaded - this means users with slow internet connections can view the content of your page without having to wait for the images to load.

```html
<img src="https://cdn.freecodecamp.org/platform/universal/fcc_meta_1920X1080-indigo.png" alt="freecodecamp logo" class="hero-img" loading="lazy">
```

The Referer HTTP header contains information about the address or URL of a page that a user might be visiting from. This information can be used in analytics to track how many users from your page visit freecodecamp.org, for example. Setting the rel attribute to noreferrer omits this information from the HTTP request. 

```html
<a href="https://freecodecamp.org" target="_blank" rel="noreferrer">freeCodeCamp</a>
```

Create an html selector and give it a font-size property set to 62.5%. This will set the default font size for your web page to 10px (the browser default is 16px).
This will make it easier for you to work with rem units later, as 2rem would be 20px.

```css
html {
  font-size: 62.5%;
  box-sizing: border-box;
}
```

CSS Grid offers a two-dimensional grid-based layout, allowing you to center items horizontally and vertically while still retaining control to do things like overlap elements.

```css
main {
  display: grid;
}
```

Set the content to have a three-column layout by adding a grid-template-columns property with a value of 1fr 94rem 1fr. This will create three columns where the middle column is 94rem wide, and the first and last columns are both 1 fraction of the remaining space in the grid container.

```css
main {
  display: grid;
  grid-template-columns: 1fr 94rem 1fr;
}
```

Use the `minmax` function to make your columns responsive on any device. The `minmax` function takes two arguments, the first being the minimum value and the second being the maximum. These values could be a length, percentage, fr, or even a keyword like max-content.

```css
main {
  display: grid;
  grid-template-columns: minmax(2rem, 1fr) minmax(min-content, 94rem) minmax(2rem, 1fr);
}
```

To add space between rows in the grid layout, you can use the `row-gap` property. 

```css
main {
  display: grid;
  grid-template-columns: minmax(2rem, 1fr) minmax(min-content, 94rem) minmax(2rem, 1fr);
  row-gap: 3rem;
}
```

One option is the `grid-column` property, which is shorthand for `grid-column-start` and `grid-column-end`. The `grid-column` property tells the grid item which grid line to start and end at.

```css
.heading {
  grid-column: 2 / 3;
}
```

For additional control over the layout of your content, you can have a CSS Grid within a CSS Grid.

```css
.heading {
  display: grid;
  grid-column: 2 / 3;
}
```

The CSS `repeat()` function is used to repeat a value, rather than writing it out manually, and is helpful for grid layouts. For example, setting the `grid-template-columns` property to `repeat(20, 200px)` would create 20 columns each 200px wide.

```css
.heading {
  grid-column: 2 / 3;
  display: grid;
  grid-template-columns: repeat(2, 1fr);
}
```

There may be times where you are unsure of how many columns your grid will have, but you want an element to stop at the last column. To do this, you can use -1 for the end column.
Create a `.hero` selector and give it a `grid-column` property set to 1 / -1. This will tell the element to span the full width of the grid.

```css
.hero {
  grid-column: 1 / -1;
}
```

The `object-fit` property tells the browser how to position the element within its container. In this case, cover will set the image to fill the container, cropping as needed to avoid changing the aspect ratio.

```css
img {
  width: 100%;
  object-fit: cover;
}
```

The default settings for CSS Grid will create additional rows as needed, unlike Flexbox. 

If you wanted to add more social icons, but keep them on the same row, you would need to update grid-template-columns to create additional columns. As an alternative, you can use the `grid-auto-flow` property.

This property takes either row or column as the first value, with an optional second value of dense. `grid-auto-flow` uses an auto-placement algorithm to adjust the grid layout. Setting it to column will tell the algorithm to create new columns for content as needed. The dense value allows the algorithm to backtrack and fill holes in the grid with smaller items, which can result in items appearing out of order.

```css
.social-icons {
  display: grid;
  font-size: 3rem;
  grid-template-columns: repeat(5, 1fr);
  grid-auto-flow: column;
}
```

Now the auto-placement algorithm will kick in when you add a new icon element. However, the algorithm defaults the new column width to be auto, which will not match your current columns.

You can override this with the `grid-auto-columns` property. 

```css
.social-icons {
  display: grid;
  font-size: 3rem;
  grid-template-columns: repeat(5, 1fr);
  grid-auto-flow: column;
  grid-auto-columns: 1fr;
}
```

Much like Flexbox, with CSS Grid you can align the content of grid items with `align-items` and `justify-items`. `align-items` will align child elements along the column axis, and `justify-items` will align child elements along the row axis.

```css
.social-icons {
  display: grid;
  font-size: 3rem;
  grid-template-columns: repeat(5, 1fr);
  grid-auto-flow: column;
  grid-auto-columns: 1fr;
  align-items: center;
}
```

Your `.text` element is not a CSS Grid, but you can create columns within an element without using Grid by using the `column-width` property.

```css
.text {
  grid-column: 2 / 3;
  font-size: 1.8rem;
  letter-spacing: 0.6px;
  column-width: 25rem;
}
```

Magazines often use justified text in their printed content to structure their layout and control the flow of their content. While this works in printed form, justified text on websites can be an accessibility concern, for example presenting challenges for folks with dyslexia.

To make your project look like a printed magazine, give the .text selector a text-align property set to justify.

```css
.text {
  grid-column: 2 / 3;
  font-size: 1.8rem;
  letter-spacing: 0.6px;
  column-width: 25rem;
  text-align: justify;
}
```

The `::first-letter` pseudo-selector allows you to target the first letter in the text content of an element.

```css
.first-paragraph::first-letter {
  font-size: 6rem;
  color: orangered;
}
```

Set the `list-style-type` property to none. This will get rid of the bullet points on the list items.

```css
.lists {
  list-style-type: none;
}
```

Give the .image-wrapper selector a grid-template-columns property set to 2fr 1fr and a grid-template-rows property set to repeat(3, min-content). This will give our grid rows that adjust in height based on the content, but columns that remain a fixed width based on the container.

```css
.image-wrapper {
  display: grid;
  grid-template-columns: 2fr 1fr;
  grid-template-rows: repeat(3, min-content);
}
```

The `gap` property is a shorthand way to set the value of `column-gap` and `row-gap` at the same time. If given one value, it sets the `column-gap` and `row-gap` both to that value. If given two values, it sets the `row-gap` to the first value and the `column-gap` to the second.

```css
.image-wrapper {
  display: grid;
  grid-template-columns: 2fr 1fr;
  grid-template-rows: repeat(3, min-content);
  gap: 2rem;
}
```

The `place-items` property can be used to set the `align-items` and `justify-items` values at the same time. The `place-items` property takes one or two values. If one value is provided, it is used for both the `align-items` and `justify-items` properties. If two values are provided, the first value is used for the `align-items` property and the second value is used for the `justify-items` property.

```css
.image-wrapper {
  display: grid;
  grid-template-columns: 2fr 1fr;
  grid-template-rows: repeat(3, min-content);
  gap: 2rem;
  place-items: center;
}
```

# Learn CSS Animation by Building a Ferris Wheel

[[Ferris Wheel HTML]]
[[Ferris Wheel CSS]]

The `transform-origin` property is used to set the point around which a CSS transformation is applied.

Give the `.line` selector a `transform-origin` property of `0% 0%`. This will offset the origin point by 0% from the left and 0% from the top, setting it to the top left corner of the element.

```css
.line {
  background-color: black;
  width: 50%;
  height: 2px;
  position: absolute;
  top: 50%;
  left: 50%;
  transform-origin: 0% 0%;
}
```

The `@keyframes` at-rule is used to define the flow of a CSS animation. Within the `@keyframes` rule, you can create selectors for specific points in the animation sequence, such as 0% or 25%, or use from and to to define the start and end of the sequence.

`@keyframes` rules require a name to be assigned to them, which you use in other rules to reference. 

```css
@keyframes wheel {}
```

You now need to define how your animation should start. To do this, create a 0% rule within your `@keyframes` wheel rule. The properties you set in this nested selector will apply at the beginning of your animation.

```css
@keyframes wheel {
  0% {
    transform: rotate(0deg);
  }
}
```

The `animation-name` property is used to link a `@keyframes` rule to a CSS selector. The value of this property should match the name of the `@keyframes` rule.

The `animation-duration` property is used to set how long the animation should sequence to complete. The time should be specified in either seconds (s) or milliseconds (ms).

```css
.wheel {
  border: 2px solid black;
  border-radius: 50%;
  margin-left: 50px;
  position: absolute;
  height: 55vw;
  width: 55vw;
  max-width: 500px;
  max-height: 500px;
  animation-name: wheel;
  animation-duration: 10s;
}
```

The `animation-iteration-count` property sets how many times your animation should repeat. This can be set to a number, or to infinite to indefinitely repeat the animation. 

The `animation-timing-function` property sets how the animation should progress over time. There are a few different values for this property, but you want the Ferris wheel animation to run at the same rate from start to finish. Set the `animation-timing-function` to `linear` in your `.wheel` selector.

```css
.wheel {
  border: 2px solid black;
  border-radius: 50%;
  margin-left: 50px;
  position: absolute;
  height: 55vw;
  width: 55vw;
  max-width: 500px;
  max-height: 500px;
  animation-name: wheel;
  animation-duration: 10s;
  animation-iteration-count: infinite;
  animation-timing-function: linear;
}
```

Set the `animation` property of the `.cabin` rule to `cabins 10s linear infinite`. This will set the `animation-name`, `animation-duration`, `animation-timing-function`, and `animation-iteration-count` properties in that order.

```css
.cabin {
  background-color: red;
  width: 20%;
  height: 20%;
  position: absolute;
  border: 2px solid;
  transform-origin: 50% 0%;
  animation: cabins 10s linear infinite;
}
```

You can use the `ease-in-out` timing function. This setting will tell the animation to start and end at a slower pace, but move more quickly in the middle of the cycle.

```css
.cabin {
  background-color: red;
  width: 20%;
  height: 20%;
  position: absolute;
  border: 2px solid;
  transform-origin: 50% 0%;
  animation: cabins 10s ease-in-out infinite;
}
```

You can use `@keyframes` rules to control more than just the transformation of an element. 

```css
@keyframes cabins {
  0% {
    transform: rotate(0deg);
    background-color: yellow;
  }
  100% {
    transform: rotate(-360deg);
  }
}
```

# Learn CSS Transforms by Building a Penguin

To make the mountain look more like a mountain, you can use the `skew` transform function, which takes two arguments. The first being an angle to shear the x-axis by, and the second being an angle to shear the y-axis by.

```css
.left-mountain {
  width: 300px;
  height: 300px;
  background: linear-gradient(rgb(203, 241, 228), rgb(80, 183, 255));
  position: absolute;
  transform: skew(0deg, 44deg);
}
```

Target the `.penguin` element when it is active, and increase its size by 50% in both dimensions.

```css
.penguin:active {
  transform: scale(1.5);
}
```

When you activate the `.penguin` element, it might look as though you can drag it around. This is not true.

Indicate this to users, by giving the active element a `cursor` property of `not-allowed`.

```css
.penguin:active {
  transform: scale(1.5);
  cursor: not-allowed;
}
```









