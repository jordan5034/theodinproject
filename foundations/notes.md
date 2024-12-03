# The Odin Project - Foundation

## HTML Foundations

### [Introduction to HTML and CSS](https://www.theodinproject.com/lessons/foundations-introduction-to-html-and-css)

* HTML is the structure
* CSS is the design and style
* JavaScript adds functionality

### [Elements and Tags](https://www.theodinproject.com/lessons/foundations-elements-and-tags)

* Structure is ```<tag start>Element content</tag end>```
* void tags don't have an end tag, such as ```<br>```

### [HTML Boilerplate](https://www.theodinproject.com/lessons/foundations-html-boilerplate)

* Home page file will always be named *index.html*
* Basic structure
  
    ```HTML
    <!DOCTYPE html>
    <html lang="en">
    <head>
        <meta charset="UTF-8">
        <title>My First Webpage</title>
    </head>

    <body>
        <h1>Hello World!</h1>
    </body>
    </html>
    ```

There are different boilerplates of course, but this is the one provided by the Odin Project

### [Working with Text](https://www.theodinproject.com/lessons/foundations-working-with-text)

* Paragraphs
  
    ```HTML
    <p>This is a paragraph.</p>
    <p>Here's another paragraph.</p>
    ```

* Headings (up to ```<h6>```)
  
    ```HTML
    <h1>Main Heading</h1>
    <h2>Subheading</h2>
    <h3>Smaller Subheading</h3>
    ```

### [Lists](https://www.theodinproject.com/lessons/foundations-lists)

* Unordered Lists - order doesn't matter

    ```HTML
    <ul>
        <li>Item 1</li>
        <li>Item 2</li>
        <li>Item 3</li> 
    </ul>
    ```

* Ordered Lists - order matters

    ```HTML
    <ol>
        <li>Item 1</li>
        <li>Item 2</li>
        <li>Item 3</li> 
    </ol>
    ```

### [Links and Images](https://www.theodinproject.com/lessons/foundations-links-and-images)

* Anchor Elements

  * Creating Links

      ```HTML
      <a href="https://example.com">Visit Example</a>
      ```

  * Opening Links in New Tabs

      ```HTML
      <a href="https://example.com" target="_blank" rel="noopener noreferrer">Open in New Tab</a>
      ```

  * Link Types  

      Absolute Links : Full URL, e.g., ```https://example.com```

      Relative Links : Based on directory structure, e.g., ```./about.html```

  * Images

      Adding an Image

      ```HTML
      <img src="https://example.com/image.jpg" alt="Example Image">
      ```

      Using Local Files

      ```HTML
      <img src="./images/example_310x310.png" alt="Example Image" height="310" width="310">
      ```

      Parent Directory Access

      ```HTML
      <img src="../images/example_310x310.png" alt="Parent Directory Image">
      ```

      "src" and "alt" are required  

      width and height can be customized

### [Commit Messages](https://www.theodinproject.com/lessons/foundations-commit-messages)

Good commits are crucial!  

A good commit message describes what problem your changes solve and how it solves them.  

They consist of...

```a subject``` a brief summary of the change you made to the project  
```a body``` a concise yet clear description of what you did

Some bad examples  

    fix a bug

<br>

    fix stuff

Good examples

    Add missing link and alt text to the company's logo
    
    Screen readers won't read the images to users with disabilities without this information

<br>

    feat: Add user authentication with JWT
    
    Implemented JWT-based authentication for users, allowing secure login and session management.
    This includes:
    - Backend changes to handle JWT generation and validation.
    - Updated user model to store JWT tokens.
    - New authentication middleware to protect routes.

You should commit every time you have a meaningful change in code. Basically, whenever your code functions how you want to. These will be your "snapshots".  

## CSS Foundations

### [Intro to CSS](https://www.theodinproject.com/lessons/foundations-intro-to-css)

Basic Syntax

<!-- Maybe adjust the dimensions -->
![css-basic-syntax](notes-images/css-basic-syntax.jpg)

#### Selectors

Refer to the HTML elements to which CSS rules apply

Universal Selector

* selects elements of any type
* an * is used to select all

```css
* {
    color: purple;
}
```

Type selectors

* selects all elements of the given type
* syntax is just the name of the element

```html
<!-- index.html -->

<div>Hello, World!</div>
<div>Hello again!</div>
<p>Hi...</p>
<div>Okay, bye.</div>
```

```css
/* styles.css */

div {
    color: white;
}
```

* only the ```<div>``` elements will be affected

Class Selectors

* selects all elements with the given class
* you can add multiple class to an element using whitespace to separate them

```html
<!-- index.html -->

<div class="alert-text">Please agree</div>
```

```css
/* styles.css */
.alert-text {
    color: red;
}
```

ID selectors

* similar to class, but use given ID
* elements can only have **one** ID
* IDs should be used sparingly

```html
<!-- index.html -->

<div id="title">My Title</div>
```

```css
/* styles.css */

#title {
    background-color: red;
}
```

The grouping selector 

* used to group elements that share some of the same style declarations
* cuts down on repetition and makes it easier to edit multiple classes at once

```css
/* BEFORE */

.read {
  color: white;
  background-color: black;
  /* several unique declarations */
}

.unread {
  color: white;
  background-color: black;
  /* several unique declarations */
}
```

```css
/* AFTER */

.read,
.unread {
    color: white;
    background-color: black;
}

.read {
    /* several unique declarations */
}

.unread {
    /* several unique declarations */
}
```

Chaining selectors

* chains (connects) together class selectors
* can chain anything except type selectors (because an element can't be more than one type)
* can chain different selectors using certain symbols

```html
<div>
  <div class="subsection header">Latest Posts</div>
  <p class="subsection preview">This is where a preview for a post might go.</p>
</div>
```

```css
.subsection.header {
  color: red;
}

```

an example of ```chaining a class and an ID```


```html
<div>
  <div class="subsection header">Latest Posts</div>
  <p class="subsection" id="preview">
    This is where a preview for a post might go.
  </p>
</div>

```

```css
.subsection.header {
  color: red;
}
/* notice how a # was used to chain the ID */
.subsection#preview {
  color: blue;
}
```

Descendant combinator

* combinators allow us to combine multiple selectors differently than group or chaining them
* relationship based
* 4 types
  * descendant combinator (space)
  * child combinator (>)
  * next sibling combinator (+)
  * subsequent-sibling combinator (~)
* combinator symbol/character goes in between selectors
  
```html
<!-- index.html -->

<div class="ancestor">
  <!-- A -->
  <div class="contents">
    <!-- B -->
    <div class="contents"><!-- C --></div>
  </div>
</div>

<div class="contents"><!-- D --></div>
```

```css
/* styles.css */
/* example of descendant combinator, this will select B and C, but not D */

.ancestor .contents {
  /* some declarations */
}
```

#### Properties to get started with

* there are many properties, but there are some basic ones
  
```Color and background-color```  

* **color** : sets an element's text color
* **background-color** : sets an element's background color
* both accept keywords such as *red* (colors), *transparent*, *rbg*, *hsl*, and [more](https://www.w3schools.com/cssref/css_colors_legal.php).
  
```Typography basics and text-align```

* **font-family** : single or comma-separated list of values determining element font
  * uses first family name, and moves to the next if not found
  * ex. *font-family: "Times New Roman", serif;*
* **font-size** : sets font size (*ex. font-size: 22px*)
* **font-weight** : sets boldness of text, if supported (*ex. font-weight: 700*)
* **text-align** : aligns text horizontally within an element (*ex. text-align: center*)

```Image height and width```

* images and other elements can have their height and width adjusted
* best to include these, even if you aren't changing the dimensions (for rendering purposes)

```css
img {
  height: auto;
  width: 500px;
}
```

#### Adding CSS to HTML

External CSS

* most common
* using separate css file and linking inside of HTML file

```html
<!-- index.html -->

<head>
  <link rel="stylesheet" href="styles.css">
</head>
```

```css
/* styles.css */

div {
  color: white;
  background-color: black;
}

p {
  color: red;
}
```

Internal CSS

* adds CSS to the HTML file *directly*

```html
<head>
  <style>
    div {
      color: white;
      background-color: black;
    }

    p {
      color: red;
    }
  </style>
</head>
<body>
  ...
</body>
```

Inline CSS

* adds styles directly to HTML elements
* should be used rarely

```html
<body>
  <div style="color: white; background-color: black;">...</div>
</body>
```

#### Assignment

"Go to our [CSS exercises repository](https://github.com/TheOdinProject/css-exercises) and read the README file.
Then, once you know how to use the exercises, [navigate to the CSS exercises repository’s **foundations/intro-to-css** directory](https://github.com/TheOdinProject/css-exercises/tree/main/foundations/intro-to-css). Review each README file prior to completing the following exercises in order:

01-css-methods  
02-class-id-selectors  
03-group-selectors  
04-chain-selectors  
05-descendant-combinator  
Note: Solutions for these exercises can be found in the solution folder of each exercise."  
