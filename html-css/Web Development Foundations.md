# Fundamentals of HTML

## Elements
A tag and the content between it is called an HTML element. 

One of the key HTML elements we use to build a webpage is the body element. Only content inside the opening and closing body tags can be displayed to the screen. 

```html
<body>
 
</body>
```

When an element is contained inside another element, it is considered the child of that element. The child element is said to be nested inside of the parent element.

The relationship between elements and their ancestor and descendent elements is known as hierarchy.

Understanding HTML hierarchy is important because child elements can inherit behavior and styling from their parent element. 

In HTML, there are six different headings, or heading elements.

One of the most popular elements in HTML is the \<div> element. \<div> is short for “division” or a container that divides the page into sections. These sections are very useful for grouping elements in your HTML together.

```html
<body>
  <div>
    <h1>Why use divs?</h1>
    <p>Great for grouping elements!</p>
  </div>
</body>
```

\<div>s don’t inherently have a visual representation, but they are very useful when we want to apply custom styles to our HTML elements. \<div>s allow us to group HTML elements to apply the same styles for all HTML elements inside. We can also style the \<div> element as a whole.

\<div>s can contain any text or other HTML elements, such as links, images, or videos.

Attributes are content added to the opening tag of an element and can be used in several different ways, from providing information to changing styling. Attributes are made up of the following two parts:

- The name of the attribute
- The value of the attribute

```html
<div id="intro">
  <h1>Introduction</h1>
</div>
```

If you want to display text in HTML, you can use a paragraph or span:

- Paragraphs (\<p>)contain a block of plain text.
- \<span> contains short pieces of text or other HTML. They are used to separate small pieces of content that are on the same line as other content.

```html
<div>
  <h1>Technology</h1>
</div>
<div>
  <p><span>Self-driving cars</span> are anticipated to replace up to 2 million jobs over the next two decades.</p>
</div>
```

It’s best to use a \<span> element when you want to target a specific piece of content that is inline, or on the same line as other text. If you want to divide your content into blocks, it’s better to use a \<div>.

You can also style text using HTML tags. The \<em> tag emphasizes text, while the \<strong> tag highlights important text.

Browsers have built-in style sheets that will generally style these tags in the following ways:

- The \<em> tag will generally render as italic emphasis.
- The \<strong> will generally render as bold emphasis.

```html
<p><strong>The Nile River</strong> is the <em>longest</em> river in the world, measuring over 6,850 kilometers long (approximately 4,260 miles).</p>
```

The spacing between code in an HTML file doesn’t affect the positioning of elements in the browser. If you are interested in modifying the spacing in the browser, you can use HTML’s line break element: \<br>

```html
<p>The Nile River is the longest river <br> in the world, measuring over 6,850 <br> kilometers long (approximately 4,260 <br> miles).</p>
```

In HTML, you can use an unordered list tag (\<ul>) to create a list of items in no particular order. An unordered list outlines individual list items with a bullet point.

Individual list items must be added to the unordered list using the \<li> tag.

```html
<ul>
  <li>Limes</li>
  <li>Tortillas</li>
  <li>Chicken</li>
</ul>
```

Ordered lists (\<ol>) are like unordered lists, except that each list item is numbered. 

```html
<ol>
  <li>Preheat the oven to 350 degrees.</li>
  <li>Mix whole wheat flour, baking soda, and salt.</li>
  <li>Cream the butter, sugar in separate bowl.</li>
  <li>Add eggs and vanilla extract to bowl.</li>
</ol>
```

The <img> tag allows you to add an image to a web page. Most elements require both opening and closing tags, but the \<img> tag is a self-closing tag. Note that the end of the \<img> tag has a forward slash /. Self-closing tags may include or omit the final slash — both will render properly.

```html
<img src="image-location.jpg" />
```

The src attribute must be set to the image’s source, or the location of the image. In this case, the value of src must be the uniform resource locator (URL) of the image. A URL is the web address or local address where a file is stored.

The alt attribute, which means alternative text, brings meaning to the images on our sites. The alt attribute can be added to the image tag just like the src attribute. The value of alt should be a description of the image.

```html
<img src="#" alt="A field of yellow sunflowers" />
```

The alt attribute also serves the following purposes:

- If an image fails to load on a web page, a user can mouse over the area originally intended for the image and read a brief description of the image. This is made possible by the description you provide in the alt attribute.
- Visually impaired users often browse the web with the aid of screen reading software. When you include the alt attribute, the screen reading software can read the image’s description out loud to the visually impaired user.
- The alt attribute also plays a role in Search Engine Optimization (SEO), because search engines cannot “see” the images on websites as they crawl the internet. Having descriptive alt attributes can improve the ranking of your site.

If the image on the web page is not one that conveys any meaningful information to a user (visually impaired or otherwise), the alt attribute should be left empty.

In addition to images, HTML also supports displaying videos. Like the <img> element, the \<video> element requires a src attribute with a link to the video source. Unlike the \<img> element however, the \<video> element requires an opening and a closing tag.

```html
<video src="myVideo.mp4" width="320" height="240" controls>
  Video not supported
</video>
```

After the src attribute, the width and height attributes are used to set the size of the video displayed in the browser. The controls attribute instructs the browser to include basic video controls such as pausing and playing.

The text, Video not supported, between the opening and closing video tags will only be displayed if the browser is unable to load the video.

### Review
1. HTML stands for HyperText Markup Language and is used to create the structure and content of a webpage.
2. Most HTML elements contain opening and closing tags with raw text or other HTML tags between them.
3. HTML elements can be nested inside other elements. The enclosed element is the child of the enclosing parent element.
4. Any visible content should be placed within the opening and closing \<body> tags.
5. Headings and sub-headings, \<h1> to \<h6> tags, are used to provide titles for sections of content.
6. \<p>, \<span> and \<div> tags specify text or blocks.
7. The \<em> and \<strong> tags are used to emphasize text.
8. Line breaks are created with the \<br> tag.
9. Ordered lists (\<ol>) are numbered and unordered lists (\<ul>) are bulleted.
10. Images (\<img>) and videos (\<video>) can be added by linking to an existing source.

## Structure
HTML files require certain elements to set up the document properly. We can let web browsers know that we are using HTML by starting our document with a document type declaration.

```html
<!DOCTYPE html>
```

This declaration is an instruction, and it must be the first line of code in your HTML document. It tells the browser what type of document to expect, along with what version of HTML is being used in the document. For now, the browser will correctly assume that the html in <!DOCTYPE html> is referring to HTML5, as it is the current standard.

HTML code is always saved in a file with an .html extension.

To create HTML structure and content, we must add opening and closing \<html> tags after declaring <!DOCTYPE html>

```html
<!DOCTYPE html>
<html>
 
</html>
```

The \<head> element contains the metadata for a web page. Metadata is information about the page that isn’t displayed directly on the web page.

```html
<head>
</head>
```

A browser’s tab displays the title specified in the \<title> tag. The \<title> tag is always inside of the \<head>.

```html
<!DOCTYPE html>
<html>
  <head>
    <title>My Coding Journal</title>
  </head>
</html>
```

You can add links to a web page by adding an anchor element \<a> and including the text of the link in between the opening and closing tags.

```html
<a href="https://www.wikipedia.org/">This Is A Link To Wikipedia</a>
```

The target attribute specifies how a link should open. For a link to open in a new window, the target attribute requires a value of _blank. 

When making multi-page static websites, web developers often store HTML files in the root directory, or a main folder where all the files for the project are stored. 

Because the files are stored in the same folder, we can link web pages together using a relative path.

```html
<a href="./contact.html">Contact</a>
```

A relative path is a filename that shows the path to a local file (a file on the same website, such as ./index.html) versus an absolute path (a full URL, like https://www.codecademy.com/learn/learn-html which is stored in a different folder). The ./ in ./index.html tells the browser to look for the file in the current folder.

HTML allows you to turn nearly any element into a link by wrapping that element with an anchor element.

```html
<a href="https://en.wikipedia.org/wiki/Opuntia" target="_blank"><img src="https://www.Prickly_Pear_Closeup.jpg" alt="A red prickly pear fruit"/></a>
```

In order to link to a target on the same page, we must give the target an id. An id can be added to most elements on a webpage. The target link is a string containing the # character and the target element’s id.

```html
<p id="top">This is the top of the page!</p>
<h1 id="bottom">This is the bottom! </h1>

<ol>
  <li><a href="#top">Top</a></li>
  <li><a href="#bottom">Bottom</a></li>
</ol>
```

Programmers use two tools to visualize the relationship between elements: whitespace and indentation.

The browser ignores whitespace in HTML files when it renders a web page, so it can be used as a tool to make code easier to read and follow.

The World Wide Web Consortium, or W3C, is responsible for maintaining the style standards of HTML. At the time of writing, the W3C recommends 2 spaces of indentation when writing HTML code. 

Indentation is used to easily visualize which elements are nested within other elements.

Comments begin with \<!-- and end with -->. Any characters in between will be ignored by your browser.

```html
<!-- This is a comment that the browser will not display. -->
```

Including comments in your code is helpful for many reasons:
- They help you (and others) understand your code if you decide to come back and review it at a much later date.
- They allow you to experiment with new code, without having to delete old code.

### Review
1. The <!DOCTYPE html> declaration should always be the first line of code in your HTML files. This lets the browser know what version of HTML to expect.
2. The \<html> element will contain all of your HTML code.
3. Information about the web page, like the title, belongs within the \<head> of the page.
4. You can add a title to your web page by using the \<title> element, inside of the head.
5. A webpage’s title appears in a browser’s tab.
6. Anchor tags (\<a>) are used to link to internal pages, external pages or content on the same page.
7. You can create sections on a webpage and jump to them using \<a> tags and adding ids to the elements you wish to jump to.
8. Whitespace between HTML elements helps make code easier to read while not changing how elements appear in the browser.
9. Indentation also helps make code easier to read. It makes parent-child relationships visible.
10. Comments are written in HTML using the following syntax: <!-- comment -->.

## Tables
Before displaying data, we must first create the table that will contain the data by using the \<table> element.

```html
<table>
 
</table>
```

The first step in entering data into the table is to add rows using the table row element: \<tr>.

```html
<table>
  <tr>
  </tr>
  <tr>
  </tr>
</table>
```

Rows aren’t sufficient to add data to a table. Each cell element must also be defined. In HTML, you can add data using the table data element: \<td>.

```html
<table>
  <tr>
    <td>73</td>
    <td>81</td>
  </tr>
</table>
```

To add titles to rows and columns, you can use the table heading element: \<th>. Just like table data, a table heading must be placed within a table row.
The blank heading creates the extra table cell necessary to align the table headings correctly over the data they correspond to.

```html
<table>
  <tr>
    <th></th>
    <th scope="col">Saturday</th>
    <th scope="col">Sunday</th>
  </tr>
  <tr>
    <th scope="row">Temperature</th>
    <td>73</td>
    <td>81</td>
  </tr>
</table>
```

Note, also, the use of the scope attribute, which can take one of two values:

- row - this value makes it clear that the heading is for a row.
- col - this value makes it clear that the heading is for a column.

In older versions of HTML, a border could be added to a table using the border attribute and setting it equal to an integer. This integer would represent the thickness of the border.

```html
<table border="1">
  <tr>
    <td>73</td>
    <td>81</td>
  </tr>
</table>
```

The code in the example above is deprecated, so please don’t use it. It’s meant to illustrate older conventions you may come across when reading other developers’ code.
You can achieve the same table border effect using CSS.

```css
table, td {
  border: 1px solid black;
}
```

Data can span columns using the colspan attribute. The attribute accepts an integer (greater than or equal to 1) to denote the number of columns it spans across.

```html
<table>
  <tr>
    <th>Monday</th>
    <th>Tuesday</th>
    <th>Wednesday</th>
  </tr>
  <tr>
    <td colspan="2">Out of Town</td>
    <td>Back in Town</td>
  </tr>
</table>
```

Data can also span multiple rows using the rowspan attribute. It accepts an integer (greater than or equal to 1) to denote the number of rows it spans across.

```html
<table>
  <tr> <!-- Row 1 -->
    <th></th>
    <th>Saturday</th>
    <th>Sunday</th>
  </tr>
  <tr> <!-- Row 2 -->
    <th>Morning</th>
    <td rowspan="2">Work</td>
    <td rowspan="3">Relax</td>
  </tr>
  <tr> <!-- Row 3 -->
    <th>Afternoon</th>
  </tr>
  <tr> <!-- Row 4 -->
    <th>Evening</th>
    <td>Dinner</td>
  </tr>
</table>
```

Over time, a table can grow to contain a lot of data and become very long. When this happens, the table can be sectioned off so that it is easier to manage.
Long tables can be sectioned off using the table body element: \<tbody>.
The \<tbody> element should contain all of the table’s data, excluding the table headings.

```html
<table>
  <tbody>
    <tr>
      <th></th>
      <th>Saturday</th>
      <th>Sunday</th>
    </tr>
    <tr>
      <th>Morning</th>
      <td rowspan="2">Work</td>
      <td rowspan="3">Relax</td>
    </tr>
    <tr>
     <th>Afternoon</th>
    </tr>
    <tr>
      <th>Evening</th>
      <td>Dinner</td>
    </tr>
  </tbody>
</table>
```

When a table’s body is sectioned off, however, it also makes sense to section off the table’s column headings using the \<thead> element.

```html
<table>
  <thead>
    <tr>
      <th></th>
      <th scope="col">Saturday</th>
      <th scope="col">Sunday</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th scope="row">Morning</th>
      <td rowspan="2">Work</td>
      <td rowspan="3">Relax</td>
    </tr>
    <tr>
     <th scope="row">Afternoon</th>
    </tr>
    <tr>
      <th scope="row">Evening</th>
      <td>Dinner</td>
    </tr>
  </tbody>
</table>
```

Only the column headings go under the \<thead> element.

The bottom part of a long table can also be sectioned off using the \<tfoot> element.

```html
<table>
  <thead>
    <tr>
      <th>Quarter</th>
      <th>Revenue</th>
      <th>Costs</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Q1</th>
      <td>$10M</td>
      <td>$7.5M</td>
    </tr>
    <tr>
      <th>Q2</th>
      <td>$12M</td>
      <td>$5M</td>
    </tr>
  </tbody>
  <tfoot>
    <tr>
      <th>Total</th>
      <td>$22M</td>
      <td>$12.5M</td>
    </tr>
  </tfoot>
</table>
```

Footers are often used to contain sums, differences, and other data results.

CSS, or Cascading Style Sheets, is a language that web developers use to style the HTML content on a web page. You can use CSS to style tables.

```css
table, th, td {
  border: 1px solid black;
  font-family: Arial, sans-serif;
  text-align: center;
}
```

### Review
- The \<table> element creates a table.
- The \<tr> element adds rows to a table.
- To add data to a row, you can use the \<td> element.
- Table headings clarify the meaning of data. Headings are added with the \<th> element.
- Table data can span columns using the colspan attribute.
- Table data can span rows using the rowspan attribute.
- Tables can be split into three main sections: a head, a body, and a footer.
- A table’s head is created with the \<thead> element.
- A table’s body is created with the \<tbody> element.
- A table’s footer is created with the \<tfoot> element

## Semantic HTML
A ```<header>``` is a container usually for either navigational links or introductory content containing ```<h1>``` to ```<h6>``` headings.

 ```html
 <header>
  <h1>
     Everything you need to know about pizza!
  </h1>
</header>
 ```

A ```<nav>``` is used to define a block of navigation links such as menus and tables of contents. It is important to note that ```<nav>``` can be used inside of the ```<header>``` element but can also be used on its own.

 ```html
 <header> 
  <nav>
    <ul>
      <li><a href="#home">Home</a></li>
      <li><a href="#about">About</a></li>      
    </ul>
  </nav>
</header>
 ```

Two more structural elements are ```<main>``` and ```<footer>```. These elements along with ```<nav>``` and ```<header>``` help describe where an element is located based on conventional web development standards.

The element ```<main>``` is used to encapsulate the dominant content within a webpage. This tag is separate from the ```<footer>``` and the ```<nav>``` of a web page since these elements don’t contain the principal content. 

```html
<main>
  <header>
    <h1>Types of Sports</h1>
  </header>
  <article>
    <h3>Baseball</h3>
    <p>
      The first game of baseball was played in Cooperstown, New York in the summer of 1839.
    </p>
  </article>
</main>
```

The content at the bottom of the subject information is known as the footer, indicated by the ```<footer>``` element. The footer contains information such as:

- Contact information
- Copyright information
- Terms of use
- Site Map
- Reference to top of page links

```html
<footer>
  <p>Email me at Codey@Codecademy.com</p>
</footer>
```

The ```<footer>``` tag is separate from the ```<main>``` element and typically located at the bottom of the content.

```<section>``` defines elements in a document, such as chapters, headings, or any other area of the document with the same theme.

```html
<section>
  <h2>Fun Facts About Cricket</h2> 
</section>
```

The ```<article>``` element holds content that makes sense on its own. ```<article>``` can hold content such as articles, blogs, comments, magazines, etc. An ```<article>``` tag would help someone using a screen reader understand where the article content (that might contain a combination of text, images, audio, etc.) begins and ends.

```html
<section>
  <h2>Fun Facts About Cricket</h2>
  <article>
    <p>A single match of cricket can last up to 5 days.</p>
  </article>
</section>
```

It is important to note that a ```<section>``` element could also be placed in an ```<article>``` element depending on the context.

The ```<aside>``` element is used to mark additional information that can enhance another element but isn’t required in order to understand the main content. This element can be used alongside other elements such as ```<article>``` or ```<section>```. Some common uses of the ```<aside>``` element are for:

- Bibliographies
- Endnotes
- Comments
- Pull quotes
- Editorial sidebars
- Additional information

```html
<article>
  <p>The first World Series was played between Pittsburgh and Boston in 1903 and was a nine-game series.</p>
</article>
<aside>
  <p>
   Babe Ruth once stated, “Heroes get remembered, but legends never die.” 
  </p>
</aside>
```

```<figure>``` is an element used to encapsulate media such as an image, illustration, diagram, code snippet, etc, which is referenced in the main flow of the document.

```html
<figure>
  <img src="overwatch.jpg">
</figure>
```

```<figcaption>``` is an element used to describe the media in the ```<figure>``` tag. Usually, ```<figcaption>``` will go inside ```<figure>```.

```html
<figure>
  <img src="overwatch.jpg">
  <figcaption>This picture shows characters from Overwatch.</figcaption>
</figure>
```

The ```<audio>``` element is used to embed audio content into a document. Like ```<video>```, ```<audio>``` uses src to link the audio source.

```html
<audio>
  <source src="iAmAnAudioFile.mp3" type="audio/mp3">
</audio>
```

Although not always necessary, it’s recommended that we state the type of audio as it helps the browser identify it more easily and determine if that type of audio file is supported by the browser.

There are many attributes for ```<audio>``` but today we’re going to be focusing on controls and src:
- controls: automatically displays the audio controls into the browser such as play and mute.
- src: specifies the URL of the audio file.

```html
<audio autoplay controls>
```

Some attributes that can alter a video playback include:
- controls: When added in, a play/pause button will be added onto the video along with volume control and a fullscreen option.
- autoplay: The attribute which results in a video automatically playing as soon as the page is loaded.
- loop: This attribute results in the video continuously playing on repeat.

```html
<video src="coding.mp4" controls>Video not supported</video>
```

Another tag that can be used to incorporate media content into a page is the ```<embed>``` tag, which can embed any media content including videos, audio files, and gifs from an external source. This means that websites that have an embed button have some form of media content that can be added to other websites. The ```<embed>``` tag is a self-closing tag, unlike the ```<video>``` element. Note that ```<embed>``` is a deprecated tag and other alternatives, such as ```<video>```, ```<audio>``` and ```<img>```, should be used in its place.

```html
<embed src="download.gif"/>
```

Embed can be used to add local files as well as media content straight from some other websites.

### Review
- Semantic HTML introduces meaning to a page through specific elements that provide context as to what is in between the tags.
- Semantic HTML is a modern standard and makes a website accessible for people who use screen readers to translate the webpage and improves your website’s SEO.
- ```<header>```, ```<nav>``` , ```<main>``` and ```<footer>``` create the basic structure of the webpage.
- ```<section>``` defines elements in a document, such as chapters, headings, or any other area of the document with the same theme.
- ```<article>``` holds content that makes sense on its own such as articles, blogs, comments, etc.
- ```<aside>``` contains information that is related to the main content, but not required in order to understand the dominant information.
- ```<figure>``` encapsulates all types of media.
- ```<figcaption>``` is used to describe the media in ```<figure>```.
- ```<video>```, ```<embed>```, and ```<audio>``` elements are used for media files.

# Fundamentals of CSS

## Selectors and Visual Rules

### Setup and syntax

While HTML is the fundamental structure of every web page, it can be visually unappealing on its own. Cascading Style Sheets or CSS is a language web developers use to style the HTML content on a web page. If you’re interested in modifying colors, font types, font sizes, images, element positioning, and more, CSS is the tool for the job!

Two different methods, or syntaxes, for writing CSS code. The first syntax shows CSS applies as a ruleset, while the second shows it written as an inline style. 

Both syntaxes contain a declaration. Declarations are the core of CSS. They apply a style to the selected element. 

Ruleset Terms:
- Selector—The beginning of the ruleset used to target the element that will be styled.
- Declaration Block—The code in-between (and including) the curly braces ({ }) that contains the CSS declaration(s).
- Declaration—The group name for a property and value pair that applies a style to the selected element.
- Property—The first part of the declaration that signifies what visual characteristic of the element is to be modified.
- Value—The second part of the declaration that signifies the value of the property.

Inline Style Terms:
- Opening Tag—The start of an HTML element. This is the element that will be styled.
- Attribute—The style attribute is used to add CSS inline styles to an HTML element.
- Declaration—The group name for a property and value pair that applies a style to the selected element.
- Property—The first part of the declaration that signifies what visual characteristic of the element is to be modified.
- Value—The second part of the declaration that signifies the value of the property.

Although CSS is a different language than HTML, it’s possible to write CSS code directly within HTML code using inline styles.
To style an HTML element, you can add the style attribute directly to the opening tag. After you add the attribute, you can set it equal to the CSS style(s) you’d like applied to that element.

```html
<p style='color: red;'>I'm learning to code!</p>
```

If you’d like to add more than one style with inline styles, simply keep adding to the style attribute. Make sure to end the styles with a semicolon (;).

```html
<p style='color: red; font-size: 20px;'>I'm learning to code!</p>
```

It’s important to know that inline styles are a quick way of directly styling an HTML element, but are rarely used when creating websites.

HTML allows you to write CSS code in its own dedicated section with a \<style> element nested inside of the \<head> element. The CSS code inside the \<style> element is often referred to as an internal stylesheet.
An internal stylesheet has certain benefits and use cases over inlines styles, but once again, it’s not best practice.

```html
<head>
  <style>
    p {
      color: red;
      font-size: 20px;
    }
  </style>
</head>
```

Developers avoid mixing code by storing HTML and CSS code in separate files (HTML files contain only HTML code, and CSS files contain only CSS code).
You can create an external stylesheet by using the .css file name extension, like so: style.css

When HTML and CSS codes are in separate files, the files must be linked. 
You can use the \<link> element to link HTML and CSS files together. The \<link> element must be placed within the head of the HTML file. It is a self-closing tag and requires the following attributes:
- href — like the anchor element, the value of this attribute must be the address, or path, to the CSS file.
- rel — this attribute describes the relationship between the HTML file and the CSS file. Because you are linking to a stylesheet, the value should be set to stylesheet.

```html
<link href='https://www.codecademy.com/stylesheets/style.css' rel='stylesheet'>
```

If the CSS file is stored in the same directory as your HTML file, then you can specify a relative path instead of a URL.

```html
<link href='./style.css' rel='stylesheet'>
```

#### Review
- The basic anatomy of CSS syntax written for both inline styles and stylesheets.
- Some commonly used CSS terms, such as ruleset, selector, and declaration.
- CSS inline styles can be written inside the opening HTML tag using the style attribute.
- Inline styles can be used to style HTML, but it is not the best practice.
- An internal stylesheet is written using the \<style> element inside the \<head> element of an HTML file.
- Internal stylesheets can be used to style HTML but are also not best practice.
- An external stylesheet separates CSS code from HTML, by using the .css file extension.
- External stylesheets are the best approach when it comes to using HTML and CSS.
- External stylesheets are linked to HTML using the \<link> element.

### Selectors

A selector is used to target the specific HTML element(s) to be styled by the declaration. 

Since element types are often referred to by their opening tag name, the type selector is sometimes referred to as the tag name or element selector.

The universal selector selects all elements of any type. The universal selector uses the * character in the same place where you specified the type selector in a ruleset.

```css
* { 
  font-family: Verdana;
}
```

When working with HTML and CSS a class attribute is one of the most common ways to select an element.

```html
<p class='brand'>Sole Shoe Company</p>
```

To select an HTML element by its class using CSS, a period (.) must be prepended to the class’s name.

```css
.brand {
 
}
```
 
 It’s possible to add more than one class name to an HTML element’s class attribute.
 
 ```css
 .green {
  color: green;
}
 
.bold {
  font-weight: bold;
}
 ```

 We can add multiple classes to an HTML element’s class attribute by separating them with a space.
 
 ```html
 <h1 class='green bold'> ... </h1>
 ```
 
 If an HTML element needs to be styled uniquely, we can give it an ID using the id attribute.
 
 ```html
 <h1 id='large-title'> ... </h1>
 ```

 In contrast to class which accepts multiple values, and can be used broadly throughout an HTML document, an element’s id can only have a single value, and only be used once per page.

To select an element’s ID with CSS, we prepend the id name with a number sign (#).

```css
#large-title {
 
}
```

The attribute selector can be used to target HTML elements that already contain attributes. Elements of the same type can be targeted differently by their attribute or attribute value.

```css
[href]{
   color: magenta;
}
```

It can get more granular from there by adding type and/or attribute values. One way is by using type\[attribute*=value]. In short, this code selects an element where the attribute contains any instance of the specified value. 

```html
<img src='/images/seasons/cold/winter.jpg'>
<img src='/images/seasons/warm/summer.jpg'>
```
```css
img[src*='winter'] {
  height: 50px;
}
 
img[src*='summer'] {
  height: 100px;
}
```

The attribute selector is used to target each image individually.
- The first ruleset looks for an img element with an attribute of src that contains the string 'winter', and sets the height to 50px.
- The second ruleset looks for an img element with an attribute of src that contains the string 'summer', and sets the height to 100px.

:focus, :visited, :disabled, and :active are all pseudo-classes. Factors such as user interaction, site navigation, and position in the document tree can all give elements a different state with pseudo-class.

A pseudo-class can be attached to any selector. It is always written as a colon : followed by a name.

```css
p:hover {
  background-color: lime;
}
```

CSS classes are meant to be reused over many elements. By writing CSS classes, you can style elements in a variety of ways by mixing classes.

While classes are meant to be used many times, an ID is meant to style only one element. IDs override the styles of types and classes. Since IDs override these styles, they should be used sparingly and only on elements that need to always appear the same.

Specificity is the order by which the browser decides which CSS styles will be displayed. A best practice in CSS is to style elements while using the lowest degree of specificity so that if an element needs a new style, it is easy to override.

IDs are the most specific selector in CSS, followed by classes, and finally, type.

When writing CSS rules, it’s possible to require an HTML element to have two or more CSS selectors at the same time.
This is done by combining multiple selectors, which we will refer to as chaining. 

```css
h1.special {
 
}
```

The code above would select only the \<h1> elements with a class of special.

CSS also supports selecting elements that are nested within other HTML elements, also known as descendants. 

```html
<ul class='main-list'>
  <li> ... </li>
  <li> ... </li>
  <li> ... </li>
</ul>
```

The nested \<li> elements are descendants of the \<ul> element and can be selected with the descendant combinator.

```css
.main-list li {
 
}
```

Instead of writing font-family: Georgia twice for two selectors, we can separate the selectors by a comma to apply the same style to both.

```css
h1, 
.menu {
  font-family: Georgia;
}
```

#### Review
- CSS can select HTML elements by type, class, ID, and attribute.
- All elements can be selected using the universal selector.
- An element can have different states using the pseudo-class selector.
- Multiple CSS classes can be applied to one HTML element.
- Classes can be reusable, while IDs can only be used once.
- IDs are more specific than classes, and classes are more specific than type. That means IDs will override any styles from a class, and classes will override any styles from a type selector.
- Multiple selectors can be chained together to select an element. This raises the specificity but can be necessary.
- Nested elements can be selected by separating selectors with a space.
- Multiple unrelated selectors can receive the same styles by separating the selector names with commas.

### Visual Rules

Font refers to the technical term typeface, or font family.
To change the typeface of text on your web page, you can use the font-family property.

```css
h1 {
  font-family: Garamond;
}
```

When setting typefaces on a web page, keep the following points in mind:
- The font specified must be installed on the user’s computer or downloaded with the site.
- Web safe fonts are a group of fonts supported across most browsers and operating systems.
- Unless you are using web safe fonts, the font you choose may not appear the same between all browsers and operating systems.
- When the name of a typeface consists of more than one word, it’s a best practice to enclose the typeface’s name in quotes.

```css
h1 {
  font-family: 'Courier New';
}
```

To change the size of text on your web page, you can use the font-size property.

```css
p {
  font-size: 18px;
}
```

In CSS, the font-weight property controls how bold or thin text appears.

```css
p {
  font-weight: bold;
}
```

The font-weight property has another value: normal.

To align text we can use the text-align property. The text-align property will align text to the element that holds it, otherwise known as its parent.

```css
h1 {
  text-align: right;
}
```

The text-align property can be set to one of the following commonly used values:
- left — aligns text to the left side of its parent element, which in this case is the browser.
- center — centers text inside of its parent element.
- right — aligns text to the right side of its parent element.
- justify— spaces out text in order to align with the right and left side of the parent element.

In CSS, these two design aspects can be styled with the following two properties:
- color: this property styles an element’s foreground color
- background-color: this property styles an element’s background color

```css
h1 {
  color: red;
  background-color: blue;
}
```

Opacity is the measure of how transparent an element is. It’s measured from 0 to 1, with 1 representing 100%, or fully visible and opaque, and 0 representing 0%, or fully invisible.

```css
.overlay {
  opacity: 0.5;
}
```
 
 One option is to make the background of an element an image. This is done through the CSS property background-image.
 
 ```css
 .main-banner {
  background-image: url('https://www.example.com/image.jpg');
}
 ```
 
 The url can be a file within your project, or it can be a link to an external site. To link to an image inside an existing project, you must provide a relative file path. If there was an image folder in the project, with an image named mountains.jpg, the relative file path would look like below:
 
 ```css
 .main-banner {
  background-image: url('images/mountains.jpg');
}
 ```

 !important can be applied to specific declarations, instead of full rules. It will override any style no matter how specific it is. As a result, it should almost never be used. Once !important is used, it is very hard to override.
 
 ```css
 p {
  color: blue !important;
}
 
.main p {
  color: red;
}
```

#### Review
- The font-family property defines the typeface of an element.
- font-size controls the size of text displayed.
- font-weight defines how thin or thick text is displayed.
- The text-align property places text in the left, right, or center of its parent container.
- Text can have two different color attributes: color and background-color. color defines the color of the text, while background-color defines the color behind the text.
- CSS can make an element transparent with the opacity property.
- CSS can also set the background of an element to an image with the background-image property.
- The !important flag will override any style, however it should almost never be used, as it is extremely difficult to override.
#corregir
## The Box Model

### The Box Model

Browsers load HTML elements with default position values. 

All elements on a web page are interpreted by the browser as “living” inside of a box.

The properties include:
1. width and height: The width and height of the content area.
2. padding: The amount of space between the content area and the border.
3. border: The thickness and style of the border surrounding the content area and padding.
4. margin: The amount of space between the border and the outside edge of the element.

An element’s content has two dimensions: a height and a width. By default, the dimensions of an HTML box are set to hold the raw contents of the box.
The CSS height and width properties can be used to modify these default dimensions.
```css
p {
  height: 80px;
  width: 240px;
}
```
Pixels allow you to set the exact size of an element’s box (width and height). When the width and height of an element are set in pixels, it will be the same size on all devices — an element that fills a laptop screen will overflow a mobile screen.

A border is a line that surrounds an element, like a frame around a painting. Borders can be set with a specific width, style, and color:
- width—The thickness of the border. A border’s thickness can be set in pixels or with one of the following keywords: thin, medium, or thick.
- style—The design of the border. Web browsers can render any of 10 different styles. Some of these styles include: none, dotted, and solid.
- color—The color of the border. Web browsers can render colors using a few different formats, including 140 built-in color keywords.
```css
p {
  border: 3px solid coral;
}
```
The default border is medium none color, where color is the current color of the element. If width, style, or color are not set in the CSS file, the web browser assigns the default value for that property.

You can modify the corners of an element’s border box with the border-radius property.
```css
div.container {
  border: 3px solid blue;
  border-radius: 5px;
}
```
The space between the contents of a box and the borders of a box is known as padding. Padding is like the space between a picture and the frame surrounding it. In CSS, you can modify this space with the padding property.
```css
p.content-header {
  border: 3px solid coral;
  padding: 10px;
}
```
If you want to be more specific about the amount of padding on each side of a box’s content, you can use the following properties:
- padding-top
- padding-right
- padding-bottom
- padding-left
```css
p.content-header {
  border: 3px solid fuchsia;
  padding-bottom: 10px;
}
```
A declaration that uses multiple properties as values is known as a shorthand property.
You can specify these properties in a few different ways:
4 Values
```css
p.content-header {
  padding: 6px 11px 4px 9px;
}
```
In the example above, the four values 6px 11px 4px 9px correspond to the amount of padding on each side, in a clockwise rotation. In order, it specifies the padding-top value (6px), the padding-right value (11px), the padding-bottom value (4px), and the padding-left value (9px) of the content.

3 Values
```css
p.content-header {
  padding: 5px 10px 20px;
}
```
The first value sets the padding-top value (5px), the second value sets the padding-left and padding-right values (10px), and the third value sets the padding-bottom value (20px).

2 Values
```css
p.content-header {
  padding: 5px 10px;
}
```
The first value sets the padding-top and padding-bottom values (5px), and the second value sets the padding-left and padding-right values (10px).

Margin refers to the space directly outside of the box. The margin property is used to specify the size of this space.
```css
p {
  border: 1px solid aquamarine;
  margin: 20px;
}
```
This means that other HTML elements on the page cannot come within 20 pixels of the paragraph’s border.

If you want to be even more specific about the amount of margin on each side of a box, you can use the following properties:
- margin-top
- margin-right
- margin-bottom
- margin-left
```css
p {
  border: 3px solid DarkSlateGrey;
  margin-right: 15px;
}
```
Margin can be written as a shorthand property as well.

The margin property also lets you center content.
```css
div.headline {
  width: 400px;
  margin: 0 auto;
}
```
The 0 sets the top and bottom margins to 0 pixels. The auto value instructs the browser to adjust the left and right margins until the element is centered within its containing element.

In order to center an element, a width must be set for that element. Otherwise, the width of the div will be automatically set to the full width of its containing element, like the \<body>, for example. It’s not possible to center an element that takes up the full width of the page, since the width of the page can change due to display and/or browser window size.

One additional difference is that top and bottom margins, also called vertical margins, collapse, while top and bottom padding does not.

Horizontal margins (left and right), like padding, are always displayed and added together.

#### Minimum and Maximum Height and Width
Because a web page can be viewed through displays of differing screen size, the content on the web page can suffer from those changes in size. To avoid this problem, CSS offers two properties that can limit how narrow or how wide an element’s box can be sized to:
- min-width—this property ensures a minimum width of an element’s box.
- max-width—this property ensures a maximum width of an element’s box.
```css
p {
  min-width: 300px;
  max-width: 600px;
}
```
You can also limit the minimum and maximum height of an element:
- min-height — this property ensures a minimum height for an element’s box.
- max-height — this property ensures a maximum height of an element’s box.
```css
p {
  min-height: 150px;
  max-height: 300px;
}
```
#### Overflow
The overflow property controls what happens to content that spills, or overflows, outside its box. The most commonly used values are:

- hidden—when set to this value, any content that overflows will be hidden from view.
- scroll—when set to this value, a scrollbar will be added to the element’s box so that the rest of the content can be viewed by scrolling.
- visible—when set to this value, the overflow content will be displayed outside of the containing element. Note, this is the default value.
```css
p {
  overflow: scroll; 
}
```
The overflow property is set on a parent element to instruct a web browser on how to render child elements.

#### Resetting Defaults
All major web browsers have a default stylesheet they use in the absence of an external stylesheet. These default stylesheets are known as user agent stylesheets. In this case, the term user agent is a technical term for the browser.

User agent stylesheets often have default CSS rules that set default values for padding and margin. This affects how the browser displays HTML elements, which can make it difficult for a developer to design or style a web page.

Many developers choose to reset these default values so that they can truly work with a clean slate.
```css
* {
  margin: 0;
  padding: 0;
}
```
#### Visibility
Elements can be hidden from view with the visibility property.

The visibility property can be set to one of the following values:
- hidden — hides an element.
- visible — displays an element.
- collapse — collapses an element.
```css
.future {
  visibility: hidden;
}
```
Keep in mind, however, that users can still view the contents of the list item (e.g., Donate) by viewing the source code in their browser. Furthermore, the web page will only hide the contents of the element. It will still leave an empty space where the element is intended to display.

**Note**: What’s the difference between display: none and visibility: hidden? An element with display: none will be completely removed from the web page. An element with visibility: hidden, however, will not be visible on the web page, but the space reserved for it will.

#### Review
- The box model comprises a set of properties used to create space around and between HTML elements.
- The height and width of a content area can be set in pixels or percentages.
- Borders surround the content area and padding of an element. The color, style, and thickness of a border can be set with CSS properties.
- Padding is the space between the content area and the border. It can be set in pixels or percent.
- Margin is the amount of spacing outside of an element’s border.
- Horizontal margins add, so the total space between the borders of adjacent elements is equal to the sum of the right margin of one element and the left margin of the adjacent element.
- Vertical margins collapse, so the space between vertically adjacent elements is equal to the larger margin.
- margin: 0 auto horizontally centers an element inside of its parent content area, if it has a width.
- The overflow property can be set to display, hide, or scroll, and dictates how HTML will render content that overflows its parent’s content area.
- The visibility property can hide or show elements.

### Changing the Box Model

#### Box Model: Content-Box
In CSS, the box-sizing property controls the type of box model the browser should use when interpreting a web page.

The default value of this property is content-box. This is the same box model that is affected by border thickness and padding.

![[Pasted image 20230103172141.png]]

#### Box Model: Border-Box
Fortunately, we can reset the entire box model and specify a new one: border-box.
```css
* {
  box-sizing: border-box;
}
```
This new box model avoids the dimensional issues that exist in the former box model you learned about.

In this box model, the height and width of the box will remain fixed. The border thickness and padding will be included inside of the box, which means the overall dimensions of the box do not change.

![[Pasted image 20230103172429.png]]

#### Review
- In the default box model, box dimensions are affected by border thickness and padding.
- The box-sizing property controls the box model used by the browser.
- The default value of the box-sizing property is content-box.
- The value for the new box model is border-box.
- The border-box model is not affected by border thickness or padding.

## Display and Positioning

### Flow of HTML
A browser will render the elements of an HTML document that has no CSS from left to right, top to bottom, in the same order as they exist in the document. This is called the flow of elements in HTML.

In addition to the properties that it provides to style HTML elements, CSS includes properties that change how a browser positions elements. These properties specify where an element is located on a page, if the element can share lines with other elements, and other related attributes.

### Position
![[Pasted image 20230104162257.png]]
Block-level elements like these boxes create a block the full width of their parent elements, and they prevent other elements from appearing in the same horizontal space.

You can see block-level elements also consistently appear on the left side of the browser. This is the default position for block-level elements.

The default position of an element can be changed by setting its position property. The position property can take one of five values:
- static - the default value (it does not need to be specified)
- relative
- absolute
- fixed
- sticky

### Position: Relative
This value allows you to position an element relative to its default static position on the web page.
```css
.green-box {
  background-color: green;
  position: relative;
}
```
Although the code in the example above instructs the browser to expect a relative positioning of the .green-box element, it does not specify where the .green-box element should be positioned on the page. This is done by accompanying the position declaration with one or more of the following offset properties that will move the element away from its default static position:
- top - moves the element down from the top.
- bottom - moves the element up from the bottom.
- left - moves the element away from the left side (to the right).
- right - moves the element away from the right side (to the left).

You can specify values in pixels, ems, or percentages, among others, to dial in exactly how far you need the element to move. It’s also important to note that offset properties will not work if the element’s position property is the default static.
```css
.green-box {
  background-color: green;
  position: relative;
  top: 50px;
  left: 120px;
}
```
![[Pasted image 20230104162819.png]]
Offsetting the relative element will not affect the positioning of other elements.

### Position: Absolute
When an element’s position is set to absolute, all other elements on the page will ignore the element and act like it is not present on the page. The element will be positioned relative to its closest positioned parent element, while offset properties can be used to determine the final position from there. 
![[Pasted image 20230104163212.png]]
The “This website is in progress. Please come back later!” text is displaced from its static position at the top left corner of its parent container. It has offset property declarations of top: 300px; and right: 0px;, positioning it 300 pixels down, and 0 pixels from the right side of the page.

### Position: Fixed
When an element’s position is set to absolute, as in the last exercise, the element will scroll with the rest of the document when a user scrolls.

We can fix an element to a specific position on the page (regardless of user scrolling) by setting its position to fixed, and accompanying it with the familiar offset properties top, bottom, left, and right.
```css
.title {
  position: fixed;
  top: 0px;
  left: 0px;
}
```
![[Pasted image 20230104163702.png]]
This technique is often used for navigation bars on a web page.

### Position: Sticky
Since static and relative positioned elements stay in the normal flow of the document, when a user scrolls the page (or parent element) these elements will scroll too. And since fixed and absolute positioned elements are removed from the document flow, when a user scrolls, these elements will stay at their specified offset position.

The sticky value is another position value that keeps an element in the document flow as the user scrolls, but sticks to a specified position as the page is scrolled further.
```css 
.box-bottom {
  background-color: darkgreen;
  position: sticky;
  top: 240px;
}
```
In the example above, the .box-bottom ```<div>``` will remain in its relative position, and scroll as usual. When it reaches 240 pixels from the top, it will stick to that position until it reaches the bottom of its parent container where it will “unstick” and rejoin the flow of the document.

### Z-index
When boxes on a web page have a combination of different positions, the boxes (and therefore, their content) can overlap with each other, making the content difficult to read or consume.

The z-index property controls how far back or how far forward an element should appear on the web page when elements overlap. This can be thought of as the depth of elements, with deeper elements appearing behind shallower elements.

The z-index property accepts integer values. Depending on their values, the integers instruct the browser on the order in which elements should be layered on the web page.
```css
.blue-box {
  background-color: blue;
  position: relative;
  z-index: 1;
}
 
.green-box {
  background-color: green;
  position: relative;
  top: -170px;
  left: 170px;
}
```
We changed position to relative, because the z-index property does not work on static elements.

The z-index of 1 moves the .blue-box element forward, because the z-index value has not been explicitly specified for the .green-box element, which means it has a default z-index value of 0.
![[Pasted image 20230104164652.png]]
### Inline Display
Every HTML element has a default display value that dictates if it can share horizontal space with other elements. Some elements fill the entire browser from left to right regardless of the size of their content. Other elements only take up as much horizontal space as their content requires and can be directly next to other elements.

The default display for some elements, such as ```<em>```, ```<strong>```, and ```<a>```, is called inline. Inline elements have a box that wraps tightly around their content, only taking up the amount of space necessary to display their content and not requiring a new line after each element. The height and width of these elements cannot be specified in the CSS document. For example, the text of an anchor tag (```<a>```) will, by default, be displayed on the same line as the surrounding text, and it will only be as wide as necessary to contain its content. inline elements cannot be altered in size with the height or width CSS properties.

The CSS display property provides the ability to make any element an inline element. This includes elements that are not inline by default such as paragraphs, divs, and headings.
```css
h1 {
  display: inline;
}
```
The browser will render ```<h1>``` elements on the same line as other inline elements immediately before or after them (if there are any).

### Display: Block
Some elements are not displayed in the same line as the content around them. These are called block-level elements. These elements fill the entire width of the page by default, but their width property can also be set. Unless otherwise specified, they are the height necessary to accommodate their content.

Elements that are block-level by default include all levels of heading elements (```<h1>``` through ```<h6>```), ```<p>```, ```<div>``` and ```<footer>```. 
```css
strong {
  display: block;
}
```
### Display: Inline-Block
Inline-block display combines features of both inline and block elements. Inline-block elements can appear next to each other and we can specify their dimensions using the width and height properties. Images are the best example of default inline-block elements.

![[Pasted image 20230104170902.png]]
```html
<div class="rectangle">
  <p>I’m a rectangle!</p>
</div>
<div class="rectangle">
  <p>So am I!</p>
</div>
<div class="rectangle">
  <p>Me three!</p>
</div>
```
```css
.rectangle {
  display: inline-block;
  width: 200px;
  height: 300px;
}
```
The .rectangle ```<div>```s will all appear inline (provided there is enough space from left to right) with a width of 200 pixels and height of 300 pixels, even though the text inside of them may not require 200 pixels by 300 pixels of space.

### Float
If you’re simply interested in moving an element as far left or as far right as possible in the container, you can use the float property.

The float property is commonly used for wrapping text around an image. Note, however, that moving elements left or right for layout purposes is better suited for tools like CSS grid and flexbox.

The float property is often set using one of the values below:
- left - moves, or floats, elements as far left as possible.
- right - moves elements as far right as possible.
```css
.green-section {
  width: 50%;
  height: 150px;
}
 
.orange-section {
  background-color: orange;
  width: 50%;
  float: right;
}
```
This works for static and relative positioned elements.
![[Pasted image 20230104171518.png]]
Floated elements must have a width specified. Otherwise, the element will assume the full width of its containing element, and changing the float value will not yield any visible results.

### Clear
The float property can also be used to float multiple elements at once. However, when multiple floated elements have different heights, it can affect their layout on the page. Specifically, elements can “bump” into each other and not allow other elements to properly move to the left or right.

The clear property specifies how elements should behave when they bump into each other on the page. It can take on one of the following values:
- left—the left side of the element will not touch any other element within the same containing element.
- right—the right side of the element will not touch any other element within the same containing element.
- both—neither side of the element will touch any other element within the same containing element.
- none—the element can touch either side.
```css
div {
  width: 200px;
  float: left;
}
 
div.special {
  clear: left;
}
```
In the example above, all ```<div>```s on the page are floated to the left side. The element with class special did not move all the way to the left because a taller ```<div>``` blocked its positioning. By setting its clear property to left, the special ```<div>``` will be moved all the way to the left side of the page.

### Review
- The position property allows you to specify the position of an element.
- When set to relative, an element’s position is relative to its default position on the page.
- When set to absolute, an element’s position is relative to its closest positioned parent element. It can be pinned to any part of the web page, but the element will still move with the rest of the document when the page is scrolled.
- When set to fixed, an element’s position can be pinned to any part of the web page. The element will remain in view no matter what.
- When set to sticky, an element can stick to a defined offset position when the user scrolls its parent container.
- The z-index of an element specifies how far back or how far forward an element appears on the page when it overlaps other elements.
- The display property allows you to control how an element flows vertically and horizontally in a document.
- inline elements take up as little space as possible, and they cannot have manually adjusted width or height.
- block elements take up the width of their container and can have manually adjusted heights.
- inline-block elements can have set width and height, but they can also appear next to each other and do not take up their entire container width.
- The float property can move elements as far left or as far right as possible on a web page.
- You can clear an element’s left or right side (or both) using the clear property.

# Deploying Websites

## Command Line for Building Websites

### Introduction
The **command line** is a text interface for your computer. It’s a program that takes in commands and passes them on to the computer’s operating system to run.

### Filesystem
A filesystem organizes a computer’s files and directories into a tree structure.

### ls
A command is a directive to the computer to perform a specific task. When you type ls, the command line looks at the directory you are in, and then “lists” all the files and directories inside of it.

### pwd
The next command we’re going to look at is pwd, which stands for “print working directory.” It outputs the name of the directory you are currently in, called the working directory.

### cd I
Our next command is cd, which stands for “change directory.” Just as you would click on a folder in Windows Explorer or Finder, cd switches you into the directory you specify. In other words, cd changes the working directory.
```bash
cd 2015
```
When a file, directory, or program is passed into a command, it is called an argument. Here the 2015/ directory is an argument for the cd command.

The cd command takes a directory name as an argument and switches into that directory.

It is also important to move up one directory. For this, we use:
```bash
cd ..
```
The argument .. stands for the directory above the current working directory. 

### cd II
To move across multiple directories with a single command, we can provide cd a relative path to the memory/ directory as an argument. From the blog/ directory use:
```bash
cd 2015/jan/memory
```
We can also move up multiple directories using the .. argument. To go from memory up 2 directories to 2015, we use ../..
```bash
cd ../..
```

Lastly, we can move to an adjacent directory using .. and then a directory name.
```bash
cd ../2014
```
### mkdir
Now that we can traverse the existing filesystem, let’s try editing it by making directories (folders) through the command line. The command for that is mkdir.
```bash
mkdir media
```
The mkdir command stands for “make directory”. It takes in a directory name as an argument and then creates a new directory in the current working directory.

### touch
Now we know how to create directories through the command line, but how do we create new files?

We can do this using the command touch:
```bash
touch keyboard.txt
```
The touch command creates a new file inside the working directory. It takes in a filename as an argument and then creates an empty file with that name in the current working directory.

### Review
- The command line is a text interface for the computer’s operating system. To access the command line, we use the terminal.
- A filesystem organizes a computer’s files and directories into a tree structure. It starts with the root directory. Each parent directory can contain more child directories and files.
- From the command line, you can navigate through files and folders on your computer:
	- pwd outputs the name of the current working directory.
	- ls lists all files and directories in the working directory.
	- cd switches you into the directory you specify.
	- mkdir creates a new directory in the working directory.
	- touch creates a new file inside the working directory.

# Improved Styling with CSS

## Colors

### Introduction to Color
Colors in CSS can be described in three different ways:
- Named colors — English words that describe colors, also called keyword colors
- RGB — numeric values that describe a mix of red, green, and blue
- HSL — numeric values that describe a mix of hue, saturation, and lightness

### Foreground vs Background
Color can affect the following design aspects:
- The foreground color
- The background color

Foreground color is the color that an element appears in. For example, when a heading is styled to appear green, the foreground color of the heading has been styled.

Conversely, when a heading is styled so that its background appears yellow, the background color of the heading has been styled

In CSS, these two design aspects can be styled with the following two properties:
- color - this property styles an element’s foreground color.
- background-color - this property styles an element’s background color.
```css
h1 {
  color: red;
  background-color: blue;
}
```
### Hexadecimal
One syntax that we can use to specify colors is called hexadecimal. Colors specified using this system are called hex colors. A hex color begins with a hash character (#) which is followed by three or six characters. The characters represent values for red, blue and green.
```
darkseagreen: #8FBC8F
sienna:       #A0522D
saddlebrown:  #8B4513
brown:        #A52A2A
black:        #000000 or #000
white:        #FFFFFF or #FFF
aqua:         #00FFFF or #0FF
```
Notice that black, white, and aqua are all represented with both three characters and six characters. This can be done with hex colors whose number pairs are the same characters.

You can include hex colors just as you would include named colors: background-color: ```#9932cc;```, and the letters can be uppercase or lowercase.

### RGB Colors
There is another syntax for representing RGB values, commonly referred to as “RGB value” or just “RGB”, that uses decimal numbers rather than hexadecimal numbers.
```css
h1 {
  color: rgb(23, 45, 23);
}
```
Each of the three values represents a color component, and each can have a decimal number value from 0 to 255. The first number represents the amount of red, the second is green, and the third is blue.

In general, hex and RGB color representations are equivalent. Which you choose is a matter of personal taste. That said, it’s good to choose one and be consistent throughout your CSS, because it’s easier to compare hex to hex and RGB to RGB.

### Hue, Saturation, and Lightness
The first number represents the degree of the hue, and can be between 0 and 360. The second and third numbers are percentages representing saturation and lightness respectively.
```css
color: hsl(120, 60%, 70%);
```
Hue is the first number. It refers to an angle on a color wheel. Red is 0 degrees, Green is 120 degrees, Blue is 240 degrees, and then back to Red at 360. 

![[Pasted image 20230111154419.png]]

Saturation refers to the intensity or purity of the color. The saturation increases towards 100% as the color becomes richer. The saturation decreases towards 0% as the color becomes grayer.

Lightness refers to how light or dark the color is. Halfway, or 50%, is normal lightness. Imagine a sliding dimmer on a light switch that starts halfway. Sliding the dimmer up towards 100% makes the color lighter, closer to white. Sliding the dimmer down towards 0% makes the color darker, closer to black.

### Opacity and Alpha
All of the colors we’ve seen so far have been opaque, or non-transparent. When we overlap two opaque elements, nothing from the bottom element shows through the top element. In this exercise, we’ll change the opacity, or the amount of transparency, of some colors so that some or all of the bottom elements are visible through a covering element.

To use opacity in the HSL color scheme, use hsla instead of hsl, and four values instead of three.
```css
color: hsla(34, 100%, 50%, 0.1);
```
The first three values work the same as hsl. The fourth value is the alpha. This last value is sometimes called opacity.

Alpha is a decimal number from zero to one. If alpha is zero, the color will be completely transparent. If alpha is one, the color will be opaque. The value for half-transparent would be 0.5.

The RGB color scheme has a similar syntax for opacity, rgba. Again, the first three values work the same as rgb and the last value is the alpha. 
```css
color: rgba(234, 45, 98, 0.33);
```
A little unconventional, but still worth mentioning is how hex colors can also have an alpha value. By adding a two-digit hexadecimal value to the end of the six-digit representation (#52BC8280), or a one-digit hexadecimal value to the end of the three-digit representation (#F003), you can change the opacity of a hexadecimal color. Hex opacity ranges from 00 (transparent) to FF (opaque).

Alpha can only be used with HSL, RGB, and hex colors; we cannot add the alpha value to name colors like green.

There is, however, a named color keyword for zero opacity, transparent. It’s equivalent to rgba(0, 0, 0, 0), and it’s used like any other color keyword:
```css
color: transparent;
```
### Review
There are four ways to represent color in CSS:
- Named colors—there are more than 140 named colors, which you can review here on MDN.
- Hexadecimal or hex colors
	- Hexadecimal is a number system that has sixteen digits, 0 to 9 followed by “A” to “F”.
	- Hex values always begin with # and specify values of red, blue, and green using hexadecimal numbers such as ```#23F41A```.
	- Six-digit hex values with duplicate values for each RGB value can be shorted to three digits.
- RGB
	- RGB colors use the rgb() syntax with one value for red, one value for blue and one value for green.
	- RGB values range from 0 to 255 and look like this: rgb(7, 210, 50).
- HSL
	- HSL stands for hue (the color itself), saturation (the intensity of the color), and lightness (how light or dark a color is).
	- Hue ranges from 0 to 360 and saturation and lightness are both represented as percentages like this: hsl(200, 20%, 50%).
- You can add opacity to color in RGB and HSL by adding a fourth value, a, which is represented as a percentage.

## Typography

Typography, the art of arranging text on a page.

### Font Family

#### Multi-Word Values
When specifying a typeface with multiple words, like Times New Roman, it is recommended to use quotation marks (' ') to group the words together, like so:
```css
h1 {
  font-family: 'Times New Roman';
}
```
#### Web Safe Fonts
There is a selection of fonts that will appear the same across all browsers and operating systems. These fonts are referred to as web safe fonts. 

#### Fallback Fonts and Font Stacks
Web safe fonts are good fallback fonts that can be used if your preferred font is not available.
```css
h1 {
  font-family: Caslon, Georgia, 'Times New Roman';
}
```
In the example above, Georgia and Times New Roman are fallback fonts to Caslon. When you specify a group of fonts, you have what is known as a font stack. A font stack usually contains a list of similar-looking fonts. Here, the browser will first try to use the Caslon font. If that’s not available, it will try to use a similar font, Georgia. And if Georgia is not available, it will try to use Times New Roman.

#### Serif and Sans-Serif
The fonts Caslon, Georgia, and Times New Roman are Serif fonts. Serif fonts have extra details on the ends of each letter, as opposed to Sans-Serif fonts, which do not have the extra details.

![[Pasted image 20230111163443.png]]

serif and sans-serif are also keyword values that can be added as a final fallback font if nothing else in the font stack is available.
```css
h1 {
  font-family: Caslon, Georgia, 'Times New Roman', serif;
}
```
In this final example, the font stack has 4 fonts. If the first 3 fonts aren’t available, the browser will use whatever serif font is available on the system.

### Font Weight
In CSS, the font-weight property controls how bold or thin text appears. It can be specified with keywords or numerical values.

#### Keyword Values
The font-weight property can take any one of these keyword values:
- bold: Bold font weight.
- normal: Normal font weight. This is the default value.
- lighter: One font weight lighter than the element’s parent value.
- bolder: One font weight bolder than the element’s parent value

#### Numerical Values
Numerical values can range from 1 (lightest) to 1000 (boldest), but it is common practice to use increments of 100. A font weight of 400 is equal to the keyword value normal, and a font weight of 700 is equal to bold.
```css
.left-section {
  font-weight: 700;
}
 
.right-section {
  font-weight: bold; 
}
```
It’s important to note that not all fonts can be assigned a numeric font weight, and not all numeric font weights are available to all fonts. It’s a good practice to look up the font you are using to see which font-weight values are available.

### Font Style
You can also italicize text with the font-style property.
```css
h3 {
  font-style: italic;
}
```
The italic value causes text to appear in italics. The font-style property also has a normal value which is the default.

### Text Transformation
Text can also be styled to appear in either all uppercase or lowercase with the text-transform property.
```css
h1 {
  text-transform: uppercase;
}
```
The code in the example above formats all ```<h1>``` elements to appear in uppercase, regardless of the case used for the heading within the HTML code. Alternatively, the lowercase value could be used to format text in all lowercase.

### Text Layout

#### Letter Spacing
The letter-spacing property is used to set the horizontal spacing between the individual characters in an element. It’s not common to set the spacing between letters, but it can sometimes help the readability of certain fonts or styles. The letter-spacing property takes length values in units, such as 2px or 0.5em.
```css
p {
  letter-spacing: 2px;
}
```
In the example above, each character in the paragraph element will be separated by 2 pixels.

#### Word Spacing
You can set the space between words with the word-spacing property. It’s also not common to increase the spacing between words, but it may help enhance the readability of bolded or enlarged text. The word-spacing property also takes length values in units, such as 3px or 0.2em.
```css
h1 {
  word-spacing: 0.3em;
}
```
In the example above, the word spacing is set to 0.3em. For word spacing, using em values are recommended because the spacing can be set based on the size of the font.

#### Line Height
![[Pasted image 20230111164548.png]]
We can use the line-height property to set how tall we want each line containing our text to be. Line height values can be a unitless number, such as 1.2, or a length value, such as 12px, 5% or 2em.
```css
p {
  line-height: 1.4;
}
```
In the example above, the height between lines is set to 1.4. Generally, the unitless value is preferred since it is responsive based on the current font size. In other words, if the line-height is specified by a unitless number, changing the font size will automatically readjust the line height.

#### Text Alignment
The text-align property aligns text to its parent element.
```css
h1 {
  text-align: right;
}
```
In the example above, the ```<h1>``` element is aligned to the right side, instead of the default left.

### Web Fonts
The fonts you can use for your website are limitless.

Free font services, like Google Fonts and Adobe Fonts, host fonts that you can link to from your HTML document with a provided ```<link>``` element.

You can also use fonts from paid font distributors like fonts.com by downloading and hosting them with the rest of your site’s files. You can create a @font-face ruleset in your CSS stylesheet to link to the relative path of the font file.

### Web Fonts Using ```<link>```
```html
<head>
  <!-- Add the link element for Google Fonts along with other metadata -->
  <link href="https://fonts.googleapis.com/css2?family=Roboto:wght@100&display=swap" rel="stylesheet">
</head>
```
The generated ```<link>``` element needs to be added to the ```<head>``` element in your HTML document for it to be ready to be used in your CSS.

### Web Fonts Using @font-face
Fonts can also be added using a @font-face ruleset in your CSS stylesheet instead of using a ```<link>``` element in your HTML document. As mentioned earlier, fonts can be downloaded just like any other file on the web. They come in a few different file formats, such as:
- OTF (OpenType Font)
- TTF (TrueType Font)
- WOFF (Web Open Font Format)
- WOFF2 (Web Open Font Format 2)

The different formats are a progression of standards for how fonts will work with different browsers, with WOFF2 being the most progressive. It’s a good idea to include TTF, WOFF, and WOFF2 formats with your @font-face rule to ensure compatibility on all browsers.

Within the “Selected Families” section, you can use the “Download” button to download the font files to your computer. The files will be downloaded as a single format, in this case, TTF. You can use a tool such as Google Web Fonts Helper to generate additional file types for WOFF and WOFF2.

When you have the files you need, move them to a folder inside your website’s working directory, and you’re ready to use them in a @font-face ruleset.
```css
@font-face {
  font-family: 'MyParagraphFont';
  src: url('fonts/Roboto.woff2') format('woff2'),
       url('fonts/Roboto.woff') format('woff'),
       url('fonts/Roboto.ttf') format('truetype');
}
```
It’s recommended to define the @font-face ruleset at the top of your CSS stylesheet.

Inside the declaration block, the font-family property is used to set a custom name for the downloaded font. The name can be anything you choose, but it must be surrounded by quotation marks.

Note that the ordering for the different formats is important because our browser will start from the top of the list and search until it finds a font format that it supports.

### Review
- Typography is the art of arranging text on a page.
- Text can appear bold or thin with the font-weight property.
- Text can appear in italics with the font-style property.
- The vertical spacing between lines of text can be modified with the line-height property.
- Serif fonts have extra details on the ends of each letter. Sans-Serif fonts do not.
- Fallback fonts are used when a certain font is not installed on a user’s computer.
- The word-spacing property changes how far apart individual words are.
- The letter-spacing property changes how far apart individual letters are.
- The text-align property changes the horizontal alignment of text.
- Google Fonts provides free fonts that can be used in an HTML file with the ```<link>``` tag or the @font-face property.
- Local fonts can be added to a document with the @font-face property and the path to the font’s source.

## Links and Buttons

### Link Styling
Link styles should not be replicated in other page text. Link color should sufficiently contrast the text colors in the rest of the design. For example, if links are underlined, other text should not be.

Anchor text, the text itself of a link, should be descriptive of the linked resource. Although this is not strictly a design problem, it is important for usability, accessibility, and SEO. 

### Tooltips and Titles

Additional context can be provided as text using the HTML title attribute. Although the title attribute can be provided to any HTML element, it is often extremely useful as additional context or advisory text for clickable elements.

Most browsers will display the text of a title attribute as a tooltip, meaning when a user hovers their cursor over an element, the text will appear in a small box near the cursor.
```html
<p>
  <a href="https://www.codecademy.com" title="Codecademy is an online learning platform">Codecademy</a> is the best place to learn to code!
</p>
```
**NOTE**: The title attribute is HTML’s built-in way of creating tooltips, but is known to cause a variety of accessibility issues. Developers have come up with a number of ways to create tooltips that are more accessible, but this generally requires using CSS and JavaScript.

### Hover States and Cursors
The CSS pseudo-class :hover can be used to style elements on mouse hover.
```css
a {
  color: blue;
}
 
a:hover {
  color: orange;
}
```
In addition to any text style changes when hovering over a link, the user’s cursor should change from the default appearance to a pointing hand. The CSS cursor property is used to control this behavior.
```css
a {
  cursor: pointer;
}
```
Luckily, this behavior is generally included in browser user agent stylesheets, and it also exists in the HTML5 default styles.

Hover state styling should never be used as the sole indication that something is a link. Users should not be forced to move their mouse over an entire document to tell what might be clickable. Additionally, hover states are not accessible in mobile browsers. Mobile devices do not generally have on-screen cursors, and users must actually touch the device (and possibly trigger a click event) to interact.

Add a declaration to also change the cursor to pointer. Even though this behavior is seen when the mouse is hovered over, you should add it to the rule for all ```<a>``` tags, as the browser will only change cursor styles on hover by default. Putting the rule on an a:hover rule can cause unwanted behavior in some cases.

### Link States
Links have four main states: normal (not clicked), hover, active (clicked), and visited. These four states have associated CSS pseudo-classes: :link, :hover, :active, and :visited. 

Each state should still make it clear that the element in question is a link, meaning it should not make text identical to non-link text or alter the link’s appearance so much that users could perceive its behavior differently.

The ordering of link state pseudo-class rules is important to reveal the proper information. When a user hovers and then clicks a link, those styles should always override the static styling surrounding a user’s history with the link (unvisited :link and :visited). The proper order of these rules is:
- :link
- :visited
- :hover
- :active

### Skeuomorphism and Flat Design
The concept of UI elements that replicate or imitate real-life counterparts is known as skeuomorphism.

Flat design is an alternative approach to skeuomorphism which embraces the fact that computer interfaces do not necessarily need to model real-life interfaces. As users grow more familiar with digital displays and interfaces, designers have felt less need to model physical interactions and instead rely on other signifiers to indicate interactive elements. To generalize, flat design uses simplicity and lack of clutter for its UI elements.

### Buttons: Skeuomorphic styling
Skeuomorphic button design aims to imitate the appearance and interactivity of a real-life button, often including a ‘raised’ appearance while the button is unpressed and a ‘pressed’ appearance when clicked.

Skeuomorphic button design can be implemented using image files, CSS rules, or a combination of both. CSS styles should be preferred over image files if possible, since they are faster to load, have smaller file sizes, and allow for a more consistent scaling and appearance across different screen sizes and resolutions. Modern CSS3 has support for many 2-D and 3-D effects and animations and can create many skeuomorphic button designs on its own.

If using CSS rules, the use of hover and/or active states is important in order to model interaction with a real button. For example, to implement a bare minimum 3-D button design, the following CSS ruleset could be used:
```css
button {
  padding: 5px;
  border: 1px solid black;
  border-radius: 5px;
  text-decoration: none;
  box-shadow: 0px 5px;
}
 
button:hover {
  cursor: pointer;
}
 
button:active {
  margin-top: 5px;
  color: black;
  box-shadow: 0px 0px;
}
```
### Buttons: Flat Design
Flat design is so-called because of its 2-D appearance. Elements appear flat on the screen, and designers must rely on other styling and signifiers to indicate clickability.

Flat design buttons commonly appear as rectangles, rounded rectangles, or circles. These shapes are used ubiquitously for button elements, so users often perceive them as buttons and expect them to be clickable.

Since there are fewer obvious signifiers surrounding buttons in a flat design, they should be visually distinct from other page elements.

In flat designs in particular, button text is very important for clarity—the possibility of user confusion is reduced by pairing buttons with specific, descriptive labels. A button with ‘Click here’ leaves many more open questions than a button that reads ‘Submit form’.

### Buttons: Hover States
Just as with links, buttons should make use of hover states and the cursor: pointer declaration. All the caveats about the shortcomings of hover states on mobile devices apply to buttons, but their use is still encouraged.

Users expect buttons to be clickable. Since buttons can consist of any number of total elements (rectangular/circular body, text, image(s)), all elements should be clickable, should display their clickability, and should result in the same behavior.

## Secondary Navigation
The primary navigation system typically contains the most important links and buttons that need to be displayed on every single page of the site.

Secondary navigation, or breadcrumb navigation, usually consists of a clickable list of pages or attributes that led to the current page. It can help users understand the extent of the site and also where they are currently.

### Simple Example of Breadcrumbs
Breadcrumbs are usually displayed as a horizontal list of pages and take up minimal space. Users expect to find them in the header, left-aligned, and below any primary navigation. Typically they are separated with a “>” or a “/“ symbol.
```css
.breadcrumb > li {
  display: inline;
}

.breadcrumb li+li::before {
	padding: 10px;
  content: ">";
}

.breadcrumb a {
  text-decoration: none;
}

.breadcrumb a:hover {
  color: red;
}
```
### Breadcrumb Types
There are three major types of breadcrumbs:
- Location
- Attribute
- Path

Location based breadcrumbs are based on where you are with respect to the navigation structure of the website.

Attribute based breadcrumbs are based on the attributes of the page or product that you are browsing.

Finally, breadcrumbs can be based on a user’s unique path through the site. For example, if they landed on the home page, browsed to the about page and finally the registration page, their breadcrumb trail may look like:

Home > About > Register

Note that this breadcrumb trail will be different for each user and each visit. For even mildly complex sites, the number of steps will become large. To simplify the display, the beginning of the trail is often abbreviated:

... > About > Register

### Breadcrumb Pitfalls
Path based breadcrumbs are unique to a user’s journey and are not commonly implemented. Only use this type of breadcrumbs if there is a compelling reason for it.

While breadcrumbs are common, it is not the primary way users will navigate a site. Don’t make the breadcrumbs the only navigation structure.

In general, the rule of not adding anything extraneous to the design applies here. If the site only contains a few pages or if the pages in the breadcrumbs are already available through primary navigation, there is little reason to include breadcrumbs in the design.

### Summary
- Use breadcrumbs to indicate where a user is and the extent of the site
- Breadcrumbs are implemented using unordered lists in HTML with custom CSS styling
- Three types of breadcrumbs exist:
	- location - based on hierarchical structure of site
	- attribute - based on attributes of current page or item
	- path - unique to a user’s journey on the site
- Path-based breadcrumbs can be confusing, only use if needed
- Ensure breadcrumbs will add value before adding to a site

# Making a Website Responsive

## Grids and Spacing

### Grid Anatomy
When designing a website, the grid comprises three major components: columns, gutters, and margins.

Columns are defined as the vertical sections that span the width of a page. In web design, it’s common to see layouts consisting of 12 or 16 columns, while other may only feature three columns. Defining the number of columns depends on what’s appropriate for your design, device, and or screen viewing size.

Next, a gutter is the negative space between each column. Gutters help in ensuring the columns don’t run together, which would negate the purpose of using a column-based grid.

Margins appear on the left and right sides of the column-based grid. These ensure the content of your designs doesn’t match up to the edges of the browser window.

It’s important to note, margins may vary depending on the width of the grid, browser window, or device. For larger displays, margins may be very noticeable while on smaller screens, they may have the same width as a gutter.

### Grid Columns
Columns are the vertical containers that span the width of the page. They can be dependent on each other, meaning they are used to organize related content such as a continuation of a paragraph. They can also be independent of each other, meaning they are used for organizing the layout of unrelated content such as a sidebar. This allows for the flexibility of organizing information. 

Within a grid, content can span multiple columns. What this means is that a website does not need to maintain the same column layout throughout. For example, a section of a website with a 12 column grid can have content that spans 4 columns, three times. 

Columns can also be used to push, or offset content. Say you want to only display content on the right 4 columns of a page while using a 12 column grid. To do this, you can easily offset the content by 8 columns so the content is pushed to those right 4 columns.

### Grid Rows
Rows are the horizontal lines on a grid. Think of rows as invisible boxes that group content together by height. Rows are commonly used in web designs to group content together and re-order other content to allow for more whitespace.

For example, let’s say you have a set of items that all span the same amount of columns and you want them to align across the page without being disrupted by other elements. One way to achieve this outcome is to wrap the content in a row component. This will force any content, not inside of the row, to be pushed away.

Again, remember that a row can be used to force content away from an area that has remaining columns not used. What does this mean? Great question.

Let’s say our design uses a 12 column grid and we want one element to span seven columns. That means we still have five unfilled columns to either the left or the right side. Naturally, any new content added to our document will try and fill this unused space. However, by placing a row element around our component that spans 7 columns we can force any new content to start beneath our component and leave the remaining 5 columns empty.

### Grid Gutters
Gutters make up the negative space between columns. This design element helps to provide a natural break between elements aligned horizontally, while also helping to break rows of content vertically.

Note, there will always be one less gutter than the total number of columns. For example, if you are designing on a 12 column grid, then you will only have 11 gutters, one for every gap that separates each column.

While there is no set standard for a gutter width, it’s best practice to select a size that visually separates horizontal columns but is significantly thinner than the width of a column. The same can be said for vertical gutters. 

Moreover, vertical and horizontal gutters do not need to match in size for a given grid layout. This is because you as a designer may want more vertical spacing than horizontal spacing when separating elements on a page. 

Remember, if the gutter space is too tight, it can be hard to visually tell where one element ends and another starts. On the other hand, if the gutter space is too large, the design can be hard to follow.

### Responsive Grid
When designing web content, a designer needs to take into account the different screen-sizes a user might encounter and how that will affect a website’s layout. Many websites utilize responsive design, a set of techniques that allow a website’s content to shift based on the device or screen size. Because of these changes, responsive design requires a different number of total columns based on screen size, in order to accommodate content and keep it from being squished. 

Consider your mobile, tablet and desktop devices. Now, think about their viewable areas. All are substantially different in size. Thus, it’s common practice in web design to create responsive grid sizes. On a large or desktop device you may start with a 12 column grid, but on a small or mobile device, you adjust the 12 column grid to a 4 column grid.

### Whitespace
Whitespace, or negative space, refers to the emptiness between elements, whether that’s in the gutter of the columns, or additional padding around a block of text. As a designer, don’t be afraid of using space to enhance the usability of your site and prioritize the content.

### Passive Whitespace
The first type of whitespace we will discuss is called passive whitespace or micro whitespace. Used to improve the aesthetics of the layout without guiding the user through a specific reading, flow, or content order; passive whitespace is sometimes referred to as the unconsidered space. The most frequent use of passive whitespace comes within text elements.

Different font families have varying amounts of passive whitespace and you can control aspects of them within your design by altering CSS properties such as line-height or margin when setting type.

### Active Whitespace
Unlike passive whitespace, which occurs more naturally, active whitespace is intentional. Also called macro whitespace, active whitespace refers to enhancing the overall page structure through space to emphasize content or guide users from one point to the next.

## Layout with Flexbox

### What is Flexbox?
Flexible Box Layout or flexbox, a tool that greatly simplifies how to position elements. 

There are two important components to a flexbox layout: *flex containers* and *flex items*. A flex container is an element on a page that contains flex items. All direct child elements of a flex container are flex items. 

To designate an element as a flex container, set the element’s display property to flex or inline-flex. Once an item is a flex container, there are several properties we can use to specify how its children behave.

### display: flex
Any element can be a flex container. Flex containers are helpful tools for creating websites that respond to changes in screen sizes. Child elements of flex containers will change size and location in response to the size and position of their parent container.

For an element to become a flex container, its display property must be set to flex.
```css
div.container {
  display: flex;
}
```
In the example above, all divs with the class container are flex containers. If they have children, the children are flex items. A div with the declaration display: flex; will remain block level — no other elements will appear on the same line as it.

However, it will change the behavior of its child elements. Child elements will not begin on new lines.

### inline-flex
If we didn’t want div elements to be block-level elements, we would use display: inline. Flexbox, however, provides the inline-flex value for the display property, which allows us to create flex containers that are also inline elements.
```html
<div class='container'>
  <p>I’m inside of a flex container!</p>
  <p>A flex container’s children are flex items!</p>
</div>
<div class='container'>
  <p>I’m also a flex item!</p>
  <p>Me too!</p>
</div>
```
```css
.container {
  width: 200px;
  height: 200px;
  display: inline-flex;
}
```
In the example above, there are two container divs. Without a width, each div would stretch the entire width of the page. The paragraphs within each div would also display on top of each other because paragraphs are block-level elements.

When we change the value of the display property to inline-flex, the divs will display inline with each other if the page is wide enough.

Notice that in the example above, the size of the flex container is set. Currently, the size of the parent container will override the size of its child elements. If the parent element is too small, the flex items will shrink to accommodate the parent container’s size. 

### justify-content
In previous exercises, when we changed the display value of parent containers to flex or inline-flex, all of the child elements (flex items) moved toward the upper left corner of the parent container. This is the default behavior of flex containers and their children. We can specify how flex items spread out from left to right, along the main axis. 

To position the items from left to right, we use a property called justify-content.
```css
.container {
  display: flex;
  justify-content: flex-end;
}
```
This will cause all of the flex items to shift to the right side of the flex container.

Below are five commonly used values for the justify-content property:

- flex-start — all items will be positioned in order, starting from the left of the parent container, with no extra space between or before them.
- flex-end — all items will be positioned in order, with the last item starting on the right side of the parent container, with no extra space between or after them.
- center — all items will be positioned in order, in the center of the parent container with no extra space before, between, or after them.
- space-around — items will be positioned with equal space before and after each item, resulting in double the space between elements.
- space-between — items will be positioned with equal space between them, but no extra space before the first or after the last elements.

In the definitions above, “no extra space” means that margins and borders will be respected, but no more space (than is specified in the style rule for the particular element) will be added between elements. The size of each individual flex item is not changed by this property.

### align-items
It is also possible to align flex items vertically within the container. The align-items property makes it possible to space flex items vertically.
```css
.container {
  align-items: baseline;
}
```
In the example above, the align-items property is set to baseline. This means that the baseline of the content of each item will be aligned.

Below are five commonly used values for the align-items property:

- flex-start — all elements will be positioned at the top of the parent container.
- flex-end — all elements will be positioned at the bottom of the parent container.
- center — the center of all elements will be positioned halfway between the top and bottom of the parent container.
- baseline — the bottom of the content of all items will be aligned with each other.
- stretch — if possible, the items will stretch from top to bottom of the container (this is the default value; elements with a specified height will not stretch; elements with a minimum height or no height specified will stretch).

These five values tell the elements how to behave along the cross axis of the parent container. In these examples, the cross axis stretches from top to bottom of the container. 

min-height, max-height, min-width, and max-width are properties that ensure an element is at least a certain size or at most a certain size. 

### flex-grow
We learned that all flex items shrink proportionally when the flex container is too small. However, if the parent container is larger than necessary then the flex items will not stretch by default. The flex-grow property allows us to specify if items should grow to fill a container and also which items should grow proportionally more or less than others.
```html
<div class='container'>
  <div class='side'>
    <h1>I’m on the side of the flex container!</h1>
  </div>
  <div class='center'>
    <h1>I'm in the center of the flex container!</h1>
  </div>
  <div class='side'>
    <h1>I'm on the other side of the flex container!</h1>
  </div>
</div>
```
```css
.container {
  display: flex;
}
 
.side {
  width: 100px;
  flex-grow: 1;
}
 
.center {
  width: 100px;
  flex-grow: 2;
}
```
The .center div will stretch twice as much as the .side divs. For example, if there were 60 additional pixels of space, the center div would absorb 30 pixels and the side divs would absorb 15 pixels each. 

If a max-width is set for an element, it will not grow larger than that even if there is more space for it to absorb.

All of the previous properties we have learned are declared on flex containers, or the parent elements. This property — flex-grow — is the first we have learned that is declared on flex items. 

### flex-shrink
Just as the flex-grow property proportionally stretches flex items, the flex-shrink property can be used to specify which elements will shrink and in what proportions. 

You may have noticed in earlier exercises that flex items shrank when the flex container was too small, even though we had not declared the property. This is because the default value of flex-shrink is 1. However, flex items do not grow unless the flex-grow property is declared because the default value of flex-grow is 0. 
```html
<div class='container'>
  <div class='side'>
    <h1>I'm on the side of the flex container!</h1>
  </div>
  <div class='center'>
    <h1>I'm in the center of the flex container!</h1>
  </div>
  <div class='side'>
    <h1>I'm on the other side of the flex container!</h1>
  </div>
</div>
```
```css
.container {
  display: flex;
}
 
.side {
  width: 100px;
  flex-shrink: 1;
}
 
.center {
  width: 100px;
  flex-shrink: 2;
}
```
In the example above, the .center div will shrink twice as much as the .side divs if the .container div is too small to fit the elements within it. If the content is 60 pixels too large for the flex container that surrounds it, the .center div will shrink by 30 pixels and the outer divs will shrink by 15 pixels each. Margins are unaffected by flex-grow and flex-shrink.

Keep in mind, minimum and maximum widths will take precedence over flex-grow and flex-shrink. As with flex-grow, flex-shrink will only be employed if the parent container is too small or the browser is adjusted. 

### flex-basis
In the previous two exercises, the dimensions of the divs were determined by heights and widths set with CSS. Another way of specifying the width of a flex item is with the flex-basis property. flex-basis allows us to specify the width of an item before it stretches or shrinks.
```html
<div class='container'>
  <div class='side'>
    <h1>Left side!</h1>
  </div>
  <div class='center'>
    <h1>Center!</h1>
  </div>
  <div class='side'>
    <h1>Right side!</h1>
  </div>
</div>
```
```css
.container {
  display: flex;
}
 
.side {
  flex-grow: 1;
  flex-basis: 100px;
}
 
.center {
  flex-grow: 2;
  flex-basis: 150px;
}
```
In the example above, the .side divs will be 100 pixels wide and the .center div will be 150 pixels wide if the .container div has just the right amount of space (350 pixels, plus a little extra for margins and borders). If the .container div is larger, the .center div will absorb twice as much space as the .side divs.

### flex
The shorthand flex property provides a convenient way for specifying how elements stretch and shrink, while simplifying the CSS required. The flex property allows you to declare flex-grow, flex-shrink, and flex-basis all in one line.
```css
.big {
  flex-grow: 2;
  flex-shrink: 1;
  flex-basis: 150px;
}
 
.small {
  flex-grow: 1;
  flex-shrink: 2;
  flex-basis: 100px;
}
```
Keep in mind, this doesn’t mean big items will be twice as big as small items, they’ll just take up more of the extra space. 

The CSS below declares these three properties in one line.
```css
.big {
  flex: 2 1 150px;
}
 
.small {
  flex: 1 2 100px;
}
```
We use the flex property to declare flex-grow and flex-basis. Note that there is no way to set only flex-shrink and flex-basis using 2 values.
```css
.small {
  flex: 1 20px;
}
```
### flex-wrap
Sometimes, we don’t want our content to shrink to fit its container. Instead, we might want flex items to move to the next line when necessary. This can be declared with the flex-wrap property. The flex-wrap property can accept three values:

- wrap — child elements of a flex container that don’t fit into a row will move down to the next line
- wrap-reverse — the same functionality as wrap, but the order of rows within a flex container is reversed (for example, in a 2-row flexbox, the first row from a wrap container will become the second in wrap-reverse and the second row from the wrap container will become the first in wrap-reverse)
- nowrap — prevents items from wrapping; this is the default value and is only necessary to override a wrap value set by a different CSS rule.
```html
<div class='container'>
  <div class='item'>
    <h1>We're going to wrap!</h1>
  </div>
  <div class='item'>
    <h1>We're going to wrap!</h1>
  </div>
  <div class='item'>
    <h1>We're going to wrap!</h1>
  </div>
</div>
```
```css
.container {
  display: inline-flex;
  flex-wrap: wrap;
  width: 250px;
}
 
.item {
  width: 100px;
  height: 100px;
}
```
The flex container is only 250 pixels wide so the three 100 pixel wide flex items cannot fit inline. The flex-wrap: wrap; setting causes the third, overflowing item to appear on a new line, below the other two items. 

**Note**: The flex-wrap property is declared on flex containers.

### align-content
align-items is for aligning elements within a single row. If a flex container has multiple rows of content, we can use align-content to space the rows from top to bottom.

Below are some of the more commonly used align-content values:
- flex-start — all rows of elements will be positioned at the top of the parent container with no extra space between.
- flex-end — all rows of elements will be positioned at the bottom of the parent container with no extra space between.
- center — all rows of elements will be positioned at the center of the parent element with no extra space between.
- space-between — all rows of elements will be spaced evenly from the top to the bottom of the container with no space above the first or below the last.
- space-around — all rows of elements will be spaced evenly from the top to the bottom of the container with the same amount of space at the top and bottom and between each element.
- stretch — if a minimum height or no height is specified, the rows of elements will stretch to fill the parent container from top to bottom (default value).
```html
<div class='container'>
  <div class='child'>
    <h1>1</h1>
  </div>
  <div class='child'>
    <h1>2</h1>
  </div>
  <div class='child'>
    <h1>3</h1>
  </div>
  <div class='child'>
    <h1>4</h1>
  </div>
</div>
```
```css
.container {
  display: flex;
  width: 400px;
  height: 400px;
  flex-wrap: wrap;
  align-content: space-around;
}
 
.child {
  width: 150px;
  height: 150px;
}
```
In the example above, there are four flex items inside of a flex container. The flex items are set to be 150 pixels wide each, but the parent container is only 400 pixels wide. This means that no more than two elements can be displayed inline. The other two elements will wrap to the next line and there will be two rows of divs inside of the flex container. The align-content property is set to the value of space-around, which means the two rows of divs will be evenly spaced from top to bottom of the parent container with equal space before the first row and after the second, with double space between the rows.

**Note**: The align-content property is declared on flex containers.

### flex-direction
By default, the main axis is horizontal and the cross axis is vertical.

The main axis is used to position flex items with the following properties:
- justify-content
- flex-wrap
- flex-grow
- flex-shrink

The cross axis is used to position flex items with the following properties:
- align-items
- align-content

The main axis and cross axis are interchangeable. We can switch them using the flex-direction property. If we add the flex-direction property and give it a value of column, the flex items will be ordered vertically, not horizontally. 
```html
<div class='container'>
  <div class='item'>
    <h1>1</h1>
  </div>
  <div class='item'>
    <h1>2</h1>
  </div>
  <div class='item'>
    <h1>3</h1>
  </div>
  <div class='item'>
    <h1>4</h1>
  </div>
  <div class="item">
    <h1>5</h1>
  </div>
</div>
```
```css
.container {
  display: flex;
  flex-direction: column;
  width: 1000px;
}
.item {
  height: 100px;
  width: 100px;
}
```
In the example above, the five divs will be positioned in a vertical column.

The flex-direction property can accept four values:
- row — elements will be positioned from left to right across the parent element starting from the top left corner (default).
- row-reverse — elements will be positioned from right to left across the parent element starting from the top right corner.
- column — elements will be positioned from top to bottom of the parent element starting from the top left corner.
- column-reverse — elements will be positioned from the bottom to the top of the parent element starting from the bottom left corner.

**Note**: The flex-direction property is declared on flex containers.

### flex-flow
Like the shorthand flex property, the shorthand flex-flow property is used to declare both the flex-wrap and flex-direction properties in one line.
```css
.container {
  display: flex;
  flex-wrap: wrap;
  flex-direction: column;
}
```
In the example above, we take two lines to accomplish what can be done with one.
```css
.container {
  display: flex;
  flex-flow: column wrap;
}
```
**Note**: The flex-flow property is declared on flex containers.

### Nested Flexboxes
So far, we’ve had multiple flex containers on the same page to explore flex item positioning. It is also possible to position flex containers inside of one another.
```html
<div class='container'>
  <div class='left'>
    <img class='small' src='#'/>
    <img class='small' src='#'/>
    <img class='small' src='#' />
  </div>
  <div class='right'>
    <img class='large' src='#' />
  </div>
</div>
```
```css
.container {
  display: flex;
  justify-content: center;
  align-items: center;
}
 
.left {
  display: inline-flex;
  flex: 2 1 200px;
  flex-direction: column;
}
 
.right {
  display: inline-flex;
  flex: 1 2 400px;
  align-items: center;
}
 
.small {
  height: 200px;
  width: auto;
}
 
.large {
  height: 600px; 
  width: auto;
}
```
In the example above, a div with three smaller images will display from top to bottom on the left of the page (.left). There is also a div with one large image that will display on the right side of the page (.right). The left div has a smaller flex-basis but stretches to fill more extra space; the right div has a larger flex-basis but stretches to fill less extra space. Both divs are flex items and flex containers.

### Review

- display: flex changes an element to a block-level container with flex items inside of it.
- display: inline-flex allows multiple flex containers to appear inline with each other.
- justify-content is used to space items along the main axis.
- align-items is used to space items along the cross axis.
- flex-grow is used to specify how much space (and in what proportions) flex items absorb along the main axis.
- flex-shrink is used to specify how much flex items shrink and in what proportions along the main axis.
- flex-basis is used to specify the initial size of an element styled with flex-grow and/or flex-shrink.
- flex is used to specify flex-grow, flex-shrink, and flex-basis in one declaration.
- flex-wrap specifies that elements should shift along the cross axis if the flex container is not large enough.
- align-content is used to space rows along the cross axis.
- flex-direction is used to specify the main and cross axes.
- flex-flow is used to specify flex-wrap and flex-direction in one declaration.
- Flex containers can be nested inside of each other by declaring display: flex or display: inline-flex for children of flex containers.




