# Introduction to Maven and JUnit

## XML and JSON Overview

### JSON basics

#### What is JSON?

- JavaScript is a programming language
- JSON was originally created to hold structured data to be used in JavaScript

#### Basic Data Types

- Strings: text enclosed in double quotation marks
- Numbers: integer or decimal, positive or negative
- Booleans: true or false, no quotation marks
- Null: means "nothing", no quotation marks

#### Arrays

- Arrays are lists
- In square brackets
- Comma-separated
- Can mix data types

```
[65, "toast", true, 21, null, 100, 23.1]
```

#### Objects

- Objects are JSON's dictionaries
- They are enclosed in curly brackets
- Keys and values are separated by a colon
- Pairs are separated by commas
- Keys and values can be any data type

```
{"red": 205, "green": 123, "blue": 53}
```

#### Nesting

- Nesting involves putting arrays and objects inside each other

### JSON examples

#### White Space and Formatting

- White space doesn't matter, unless it's inside quotation marks
- Good JSON formatting:
	- In general, add an indent for every new level of brackets
	- End lines with commas or end brackets
	- Lots of exceptions to these rules!

```json
[
	{
		"header": "File",
		"items": [
			{"id": "Open", "label": "Open"},
			{"id": "New", "label": "New"},
			{"id": "Close", "label": "Close"}
		]
	},
	{
		"header": "View",
		"items": [
			{"id": "ZoomIn", "label": "Zoom In"},
			{"id": "ZoomOut", "label": "Zoom Out"},
			{"id": "OriginalView", "label": "Original View"}
		]
	}
]
```

### XML basics

### XML attributes and examples


## Getting Started with Apache Maven

## Project Object Model (POM)

## Maven Plugins

## Creating an Project with Maven

## Testing with Maven

## JUnit Basics

## Getting Started with JUnit

## JUnit Options