# HTML/CSS Workshop: Create your own Portfolio

Hi everyone! We'll be using HTML and CSS to make a portfolio for R2-D2! You can see all the different versions of our code on [GitHub](https://github.com/hackatbrown/html-css-workshop-2016).

But first of all, we need some background on what HTML and CSS actually *are*.
These are the standard languages used to make all web pages, so you've already seen
their result on every website you've been to. HTML stands for HyperText Markup Language.
HyperText is just a fancy word for text that links to other stuff, like images and other web pages.
HTML is a markup language because it describes ("marks up") the structure of the content. Instead of just
being a pile of words, it has structure - paragraphs and lists and headings and containers and so on. CSS defines
the appearance of the page - how all those parts should actually look. It's why websites aren't all black Times New
Roman text on a white background.

As an analogy, think of a web page as a building. HTML is the walls, the doors, the foundation - all the parts you
need for the building to work. CSS is like the paint, doorknobs, furniture, and lava lamps - you don't have to have
them, but they make the building a lot prettier and nicer to use.

## Checkpoint 0: Setup

First, create a folder on your desktop called "Workshops". Open up your favorite text editor and create a new file called
`index.html`, this is your HTML file.

We'll play around with the HTML file first before conquering the CSS part.

## Checkpoint 1: Structuring

Time to write some HTML! Open up `index.html` again and write `<!DOCTYPE html>`
This lets the browser know that everything in the file from this point onwards will be in HTML.

HTML is made up of different tags that are used to structure different parts of the page so that the browser knows
what they are and so that we can style and adjust them later. We ALWAYS start with an html tag, so
on the second line, type `<html>` and on the third line type `</html>`. HTML tags
come in pairs, so the first on line two is an opening tag, and the second
on line three is a closing tag, which is why we added that forward slash in the
beginning.

Inside the `<html>` tags, type in the opening and closing for the `<head>` and
`<body>` tags. You got this! Everything between the head tags is information for the
browser to understand your page and everything between the body tags is content
that you want people to see (like your text and images).

Inside the `<body>` element, type `Hello, World!` so that your page has some content to display. You should now
have something like [this](https://github.com/hackatbrown/html-css-workshop-2016/blob/2c3625bff329624e7460dd811443d06bdb8c413d/index.html)
(but without the comments).

Open `index.html` in your browser, and it should say "Hello, World!". Congrats, you made your first web page!

## Checkpoint 2: Headings and Titles

Remember when we said the `<head>` element holds info for the browser to use? That includes things like the page
title that shows up in your tab bar, which is what we'll add next! Inside the `<head>`, add a `<title>` tag
like this:

```html
<head>
	<title>Hack@Brown Workshop</title>
</head>
```

Likewise, we'll add a `<h1>` tag in the `<body>`. HTML has 6 levels of heading, from `<h1>` (the biggest) to
`<h6>` (the smallest). It's like how, when writing a paper, you have a heading for the whole paper, and then
sections within the paper that can have their own headings, and maybe even sections inside those sections.

```html
<body>
	<h1>Hello, World!</h1>
	<h4>Welcome to our workshop!</h4>
</body>
```

Now, `index.html` should look like [this](https://github.com/hackatbrown/html-css-workshop-2016/blob/a98bed5b08afb9e3a8149ee649834695ec40f5de/index.html). Refresh your
browser to see the new headings!

## Checkpoint 3: Paragraphs, Lists, Links, and Other Fun Stuff

It's time to start making our portfolio a portfolio!

First, change the `<title>` content from "Hack@Brown Workshop" to "R2-D2". Next, replace the content of the `<body>`
element with this:

```html
<h1>R2-D2</h1>

<p>Hi! I'm R2-D2, an astromech droid from Star Wars.</p>
```

We've seen `<h1>` before, but what's a `<p>`? It's short for "paragraph", since `<p>` is the HTML tag used to create
separate paragraphs like this one.

After the `</p>`, add this starting on a new line:

```html
<p>I've met a lot of people over 7 movies:</p>
<ul>
	<li>Padmé Amidala</li>
	<li>Obi-Wan Kenobi</li>
	<li>Leia Organa</li>
	<li>Luke Skywalker</li>
	<li>Han Solo</li>
</ul>
```

There are two new HTMl tags here: `<ul>` and `<li>`. `<ul>` is an *unordered list*, like a bulleted list on a PowerPoint.
It contains `<li>`, or *list item* elements, one for each thing in the list. This is one of many examples of HTML tags
that are designed to go together. Another example is the tags to create tables.

A portfolio wouldn't be complete without a couple of plugs to follow our intrepid droid friend online. Let's add that next!

```html
<p>Follow me online!</p>
<ol>
	<li><a href="https://www.facebook.com/hackatbrown">Facebook</a></li>
	<li><a href="https://twitter.com/hackatbrown">Twitter</a></li>
</ol>
```

This looks a lot like our first list, but there are a couple of new things here. First, instead of a `<ul>`, we're using `<ol>`. It's just a different kind of list, ordered instead of unordered. It's important to remember that HTML defines the *semantics*, or meaning, of the content. With CSS, you could easily make an unordered list use numbers or an ordered list use bullet points. The difference between `<ul>` and `<ol>` is that one is for a list of things that's inherently unordered and one is for a list that's inherently ordered, even if you display them the same way.

The other new thing is a funny-looking `<a>` tag. `<a>` is short for *anchor*, which is what links to other pages are called in HTML.
All that stuff inside the opening `<a>` tag (`href=...`) is an
*attribute* of the element. Attributes are extra information about the element, like `<head>` is extra information about the page. It might not get rendered, but it's still important! In this case, the `href` attribute specifies the URL of the page to link to. This list will have two links, one to Facebook and one to Twitter.

`index.html` should now be something like [this](https://github.com/hackatbrown/html-css-workshop-2016/blob/f9d148bfe8e2973ea930591b4931f58edb0c4e92/index.html). If you reload your browser, you'll see that the content for R2-D2's portfolio is almost complete. There's only one thing missing before we can begin to style it: a profile picture!

## Checkpoint 4: Images!

After the `<h1>` element, add the following HTML:

```html
 <img src="https://upload.wikimedia.org/wikipedia/en/3/39/R2-D2_Droid.png" alt="R2-D2" title="R2-D2" />
 ```

 This tag has even more attributes! The first, and most straighforward, is `src`. This is just the URL of the image to display. It's not quite the same as `href`, because that's a URL to link to as a separate page, but `src` is a URL for something to include as part of this particular element.

 The next, `alt`, is text to display if the image can't be displayed, such as if something goes wrong downloading it or if the page is being viewed on a screen reader. The `title` attribute is text that'll be displayed when someone hovers over the image, almost like a caption. You don't *have* to have either attribute, but it's a good idea to do so if you can.

 At this point, your `index.html` should be like [this](https://github.com/hackatbrown/html-css-workshop-2016/blob/169d65bd8d61de4e71a9adf6c649c6b04395ee54/index.html), and we're ready to add CSS!

## Checkpoint 5: CSS

CSS stands for Cascading Style Sheets. CSS saves us a lot of work and can change multiple things on your webpage in just one line, definitely saves us a lot of typing! In your folder, create a new file and call it `index.css`. You can confirm that your file is saved correctly by checking the type of the file all the way to the right when you open up your folder.

Before we get started, we first need to create a link to our CSS file so that the two files can communicate with each other. Inside the `<head>` tag, type out ``<link rel="stylesheet"href="index.css">``

In CSS, we use the names of the tags from our HTML  file to indicate what we want to apply our CSS styling to. In your CSS file, type `body {}`. Inside the curly brackets, we'll have a list of properties and what values we want them to have. We END each pair with a semi-colon.

In our example, we style the font. Choose your favorite font from [Google Fonts](http://fonts.google.com) or [CSS Font Stack](http://www.cssfontstack.com/), or any font you have on your computer.

Now let's add a background color to our image and add a bit of padding. We can do this by creating an *id* in our html file. Id's are basically unique names we assign to tags to be more specific. So, in our `<img>` tag, add an id called "profile". The syntax for this would be something like `<img id="profile" ...`

In our CSS file, we will style our "profile" similarly to body but we will add a `#` right before profile to denote that we are referring to an ID name.

```css
#profile {
	padding: 20px;
	background-color: rgb(58, 195, 216);
}
```

In between those two curly braces, we add CSS for padding and background color. Definitely play around with those numbers!
There are a couple ways to specify colors in CSS. Here, we use an RGB value, which lists how red, how green, and how blue the color should be.

We can also change our description to look a lot nicer by making the text bold and changing the font color! Similarly to how we added an id for our profile picture, add a *class* in the first `<p>` tag in your html file. The syntax would be something like `<p class="intro">...`

To style this in CSS, instead of using a `#` which referred to an id, we will use a `.` to refer to a class. In between the curly braces, we change the color and background color of the text.
(Classes keep our code clean - instead of creating ids for everything we would like to style, we can just add the same class that we call in our CSS file to style our HTML)

```css
.intro {
	font-size: 18px;
	color: gray;
}
```

The last thing we'll do is style the list of R2-D2's friends.
This won't require any HTML changes, just a new CSS selector.

In `index.css`, add this at the end:

```css
ul > li {
	font-weight: bold;
	color: #292348;
}
```

The `ul > li` selector will match `<li>` elements inside a `<ul>`. We need to be more specific here because we also have `<li>` elements inside our `<ol>`. `font-weight` is just another CSS property that specifies how bold the text should be.

## Wrapping Up

Congratulations! You’ve just created your own portfolio! How awesome! But it doesn’t have to end here, if you want to learn more, here are a few more resources you should totally check out:

* [Mozilla Developer Network](https://developer.mozilla.org/en-US/) - Mozilla's documentation has a complete list of every HTML tag and CSS property you could ever want
* [Dash by General Assembly](https://dash.generalassemb.ly/)
* [W3Schools](http://www.w3schools.com/)
* [CSS-Tricks](https://css-tricks.com/)
* [HTML5 Rocks](http://www.html5rocks.com/en/)

Happy, Happy Coding and feel free to email us with any questions at [workshops@hackatbrown.org](mailto:workshops@hackatbrown.org)!
