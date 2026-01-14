# Web Dev

```html
element formatting: <[tag name]>[content]</[tag name]>

	<!-- HTML tags & attributes: -->
<p>
<head> <!-- contains the metadata of an html prgm; precedes everything else -->
<section> <!-- groups elements into sections  -->
<body> <!-- holds everything else within it -->
<header> 
<h1> ... <h6> <!-- headings, decrementing in size -->
<main> <!-- only one each-->
<nav>
<ul> <!-- unordered list -->
<li> <!-- each item in list -->
<ol> <!-- ordered list-->
<a> <!-- used for links -->
<img src = “[img file name/path]” alt = “[alt text]”> <!-- this is a self-closing tag -->
```

> [CSS Tutorial](https://www.w3schools.com/css/default.asp)
> 

```css
body {
	background-color: blue;
}
/*
- body (aka a rule set) specifies which part of your site specifically it should assign colors to
- background-color is a specific attribute (check website for mre details)
- blue can be replaced w/ a hex code, assigns it a color
*/

p {
	font-family: "Roboto", sans-serif;
	text-align: left | right | center | justify;
	font-size: size in px | cm | em | small/medium/large
}
/*
it will try the first font (family name), and if it doesn't work then go to the font family (generic)
*/

img { 
	width: num;
	height: num;
	/*alternatively, write in %*/
	border-radius: num in px | %;
}
```

> Box Model
> 

![image.png](image.png)

- Field guidelines
    
    ```css
    /* Padding */
    *{
    	padding
    	padding-top
    	padding-bottom
    	padding-left
    	padding-right
    }
    
    /* Border */
    *{
    	border-style
    	border-width
    	border-color
    }
    
    /* Margin */
    *{
    	margin
    	margin-top
    	margin-bottom
    	margin-left
    	margin-right
    }
    ```
    

```css
/*default all elements to have a margin/padding value of 0*/
*{
	margin: 0px;
	padding: 0px;
}
```

> Classes and IDs
> 

both are more or less a variable

- classes can be used more than once
- ID’s are only used once in the page
- example
    
    ```html
    <p class class = "class"> "this is some funny little text </p>
    <img id = "id" src = "assets/sillyimage.png" alt = "its just a silly little image!"> 
    ```
    
    ```css
    .class {
    	color: bruh;
    }
    
    #id {
    	color: bruh;
    }
    ```
    

- format copy + paste
    
    /* */
    *{
    	
    }