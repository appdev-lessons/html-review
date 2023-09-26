# Raghu's HTML review

Before we get into the HTML review, let's talk about the elements in this interactive lesson.

<div class="bg-blue-100 py-1 px-5" markdown="1">

[Here is a brief video demonstration](https://share.descript.com/view/vlV7S3cEM0F). You should not rely entirely on the video to complete this lesson, but I wanted to give you a quick, visual overview of the process. As you watch the video, pause it frequently and **READ** the relevant lesson sections as you are going through the steps. There is much more detail in the text than in the video.

 **You will not get full credit for the lesson if you do not "Run" every code block.**
</div>

### Quiz questions

The basic quiz question types are:

* **Choose the best option:** For these questions, you can only select one response. Select the best one to get full credit.
* **Choose all correct options:** For these questions, you can select multiple responses. Select all that apply. You get partial credit for each correct response you select. If any of the responses you've selected are incorrect, then you get zero credit.
* **Free text**: For these questions, you can type text into the box to get credit.

### Interactive code blocks

We will have lots of examples of code in the readings. These are called "code blocks", and you'll see them all over the internet. For example:

```html
<span>I'm some HTML</span>
```

That code block is not interactive — you can only read it. 

However, some of our code blocks, are _runnable_ — you can run the code within and see the output. Just running them once is enough to get full credit. **You must run each of them to get credit**. Try clicking the "Run" button below this block:

```html
Welcome to the lesson!
```
{: .repl #first_runnable_code title="First runnable code" points="1"}

It will take a moment, but then the output of the program in the pane on the left (called the **editor**) will be displayed in the pane on the right (called the **terminal**) 🎉 

Most importantly, you can _change_ the code and re-run it to see how the output changes. You should always be:

- Thinking, "What if I changed it like _this_? What would it do then?"  
- Predict what you _think_ will happen.
- Try it, run it, compare the actual behavior to the behavior you predicted, and learn!

You can press "Reset" to get the editor back to its original state.

Okay, let's get on with it!

### Just text

The web is, mostly, a bunch of text.

```html
You can learn about the world at Wikipedia.
```
{: .repl #one title="It's all text" points="1"}

Most of the incredible value of the internet is based in making it easy to distribute and access information, instantaneously and across any distance.

### Not just text — _hyper_ text

```html
You can learn about the world at <a href="https://www.wikipedia.org/" target="_blank">Wikipedia</a>.
```
{: .repl #two title="Hyper-text!" points="1"}

With hyperlinks, we can make it easy for our users to **navigate** from URL to URL. This is what makes plain ol' text into **hyper text** (the H and the T in HTML).

Hypertext documents linked to one another is what makes the Web a web! All web sites and web apps are based on this fundamental idea.

<aside markdown="1">
"Hyperlinks" are also known as "links", a.k.a. "anchors", a.k.a. `<a>` tags.
</aside>

### Anatomy of an HTML element

In the below example, the entire **syntax** (or "grammar") of the HTML language can be seen:

```html
<a href="https://www.wikipedia.org/" target="_blank">Wikipedia</a>
```

- `<a>` is called the **opening tag**.
- `</a>` is called the **closing tag**.
- Everything between the opening tag and closing tag is called the **content**.
	- In this case, `Wikipedia`.
- Within the opening tag (but never the closing tag), there might be **attributes**.
	- In this case, there are two attributes:
		- `href="https://www.wikipedia.org/"`
		- `target="_blank"`.
	- Each attribute is comprised of a **name**, then a `=`, then a **value**.
		- In this case, `href` and `target` are the names of the two attributes.
		- `"https://www.wikipedia.org/"` and `"_blank"` are their values, respectively.
		- Values should always be within a pair of quotes (`" "`).
		- We typically don't included spaces around the `=` that connects an attribute's name and value.
	-  Within an opening tag, we typically use one space to separate attributes.

Collectively, all of that is called one **element**.

There are more elements that we need to learn about — mainly, `<span>`, `<img>`, and `<form>`. We'll get to those, and a few others, soon.

But all elements have the same structure as the above example — opening tag, closing tag, content, attributes. That's it for the syntax of HTML!

Consider this HTML:

```html
<a href="https://www.google.com/">Link</a>
```

- Within that example, the `href` and the `"https://www.google.com/"` are known, respectively, as... 
- an element.
  - Not quite. Re-read above.
- an opening tag and a closing tag, and collectively an element.
  - Not quite. Re-read above.
- a name and a value, and collectively an attribute.
  - Yes!
- an attribute and the content.
  - Not quite. Re-read above.
{: .choose_best #html_structure title="HTML structure" points="1" answer="3" }

### A very special attribute: `style`

There's a very special attribute we can use to change how an element looks — `style`:

```html
You can learn about the world at <a style="color: red" href="https://www.wikipedia.org/" target="_blank">Wikipedia</a>.
```
{: .repl #style_1 title="The style attribute" points="1"}

By adding the attribute `style="color: red"`, we have changed the color of the link.

Within the value of the `style` attribute, we can write **CSS** (Cascading Style Sheets) — a whole different language with its own syntax, designed specifically for visual styling.

In this CSS:

```
color: red
```

- `color` is called the **property**.
	- CSS offers over 100 properties that you can modify to customize the look and feel of elements. We'll focus on just a handful.
- `red` is the **value**.
	- For a given property, there is usually a set list of valid values that you're allowed to choose from. In this case, we're allowed to use the word `red`. There are also many other ways to specify a color, which we'll look at soon.
- The property must be separated from the value by a colon (`:`).
- Together, this is one **declaration**.

You can have multiple declarations within the same `style` attribute, but you must separate them with a semicolon (`;`):

```html
You can learn about the world at <a style="color: red; font-size: 50px" href="https://www.wikipedia.org/" target="_blank">Wikipedia</a>.
```
{: .repl #style_2 title="Multiple declarations" points="1"}

As you can see, the `font-size` property is how we can change how big text is. In this example, we're using the `px` unit to indicate that we want the text to be 50 pixels tall. There are many other units to specify dimensions, which we'll look at soon.

- What is each property and value pair called in CSS?
- declaration
  - That's right!
- any
  - Not quite.
{: .free_text #declaration title="CSS property: value" points="1" answer="1" }

### Adding structure with `<span>`

What if we want to change the look of some of the text that's _not_ within an `<a>` tag? What would we add the `style` attribute to? For example, what if we wanted the text "learn about the world" to be italic?

In order to give ourselves a hook to hang CSS on, we can wrap the content in a `<span>` element:

```html
You can <span>learn about the world</span> at <a style="color: red; font-size: 50px" href="https://www.wikipedia.org/" target="_blank">Wikipedia</a>.
```
{: .repl #span_1 title="The span element" points="1"}

At first, it looks like nothing changed. And it didn't. But now that we have an element, we can add a `style` attribute to it:

```html
You can <span style="font-style: italic">learn about the world</span> at <a style="color: red; font-size: 50px" href="https://www.wikipedia.org/" target="_blank">Wikipedia</a>.
```
{: .repl #span_2 title="Styled span" points="1"}

As you can see, the `font-style` property is how we choose between normal and italic text.

Unlike the special `<a>` element, which is purpose built for navigation, `<span>` elements are not clickable. You can try adding an `href=""` attribute to it, but try all you might, it won't take you anywhere when you click on it. 

Instead, `<span>` is used to add _structure_ to our content so that we can then style and position bits of it as needed.

- `span` and `a` are both... 
- HTML attributes.
  - Not quite. Re-read above.
- CSS declarations.
  - Not quite. Re-read above.
- HTML values.
  - Not quite. Re-read above.
- HTML elements.
  - Yes!
{: .choose_best #span_and_a title="<span> and <a>" points="1" answer="4" }

### The `<img>` element

There's a very special element that allows us to embed images right into our documents: `<img>`.

First, the image we want to embed needs to already be on the internet, and have its own URL. We'll talk about how to do that soon, but for now we can use this image that's hosted by Wikipedia at the following URL:

[https://upload.wikimedia.org/wikipedia/en/thumb/8/80/Wikipedia-logo-v2.svg/263px-Wikipedia-logo-v2.svg.png](https://upload.wikimedia.org/wikipedia/en/thumb/8/80/Wikipedia-logo-v2.svg/263px-Wikipedia-logo-v2.svg.png)

Next, given a URL like this, we can use it as the value for the `src` attribute of an `<img>` element to embed it in our page:

```html
You can <span>learn about the world</span> at <a style="color: red; font-size: 50px" href="https://www.wikipedia.org/" target="_blank">Wikipedia</a>.

<img src="https://upload.wikimedia.org/wikipedia/en/thumb/8/80/Wikipedia-logo-v2.svg/263px-Wikipedia-logo-v2.svg.png">
```
{: .repl #first_image title="First image" points="1"}

### The HTML family tree

Elements can contain other elements:

```html
<span style="color: red">This is the parent element, and <a style="font-weight: bold">this is the child element.</a> Over here I'm back in the parent element.</span>
```
{: .repl #parent_child title="Family tree" points="1"}

- The outer element is known as the "parent element". The inner element is known as the "child element".
- One parent element can have multiple children.
	- If so, the other children of your parent are called your sibling elements (as in a human family tree).
- Your children and all of their children, and children's children, etc, are called your "descendant elements".
- Your parent, parent's parent, etc, are called your "ancestor elements".

---

- In HTML speak, "descendants" are...
- Inner HTML elements.
  - Yes!
- All of the HTML elements on a page.
  - Not quite. Re-read above.
- The outermost HTML element.
  - Not quite. Re-read above.
{: .choose_best #descendants_are title="Descendants are..." points="1" answer="1" }

### All whitespace collapses to a single space

```html
You        can

      learn                               about the

world at

<a href="https://www.wikipedia.org/" target="_blank">Wikipedia</a>.
```
{: .repl #whitespace title="HTML whitespace" points="1"}

Notice that, despite all the spaces and new lines I added to the code, the code is **interpreted** and rendered by the browser the same as the previous examples — the whole sentence is on the same line.

This means that we can't use whitespace and new lines to position content around the page where we want it, the way that we might in a word processor like Microsoft Word.

<aside>
Tools where the input you create and the output the tool renders are supposed to be the same are called What You See Is What You Get, or WYSIWYG, pronounced "wizeewig". Word processors and Photoshop are examples of WYSIWYG tools.
</aside>

So, then: how can we position content around the page, rather than all on the same line? For example, what if I wanted the two spans below to be on their own lines?

```html
<span>You can learn about the world at Wikipedia.</span>

<span>Another good place to learn is Khan Academy.</span>
```
{: .repl #wall_of_text title="Wall of text" points="1"}

Right now, they run into each other and form a wall of text. What's the solution?

### Layout systems

To position content wherever we wish, we need to choose and use one of the many layout systems that HTML provides:

- Flow
- Flexbox
- Positioned, Grid, and a few others; but we're going to focus on the above two for now.

### In the beginning, there was Flow

The very first layout system offered by HTML was called **flow layout**. For a long time, it was the _only_ layout system.

In flow layout, the browser lays out elements as if it was typesetting a paper book or a magazine.

<aside>
It makes sense that flow was the first and only layout for a long time, since the earliest use of the web was for scientists to share research papers.
</aside>

Words, images, and other **inline** items are placed side by side horizontally.

Paragraphs, headings, and other **blocks** are placed above and below one another vertically.

![](https://res.cloudinary.com/dmxgp9oq2/image/upload/v1687373236/typesetting_hfhnil.gif)

So: in flow layout, if we don't want all of our content to be on the same line, we need to create some elements that act as **block** elements. By default, `<span>`, `<a>`, and `<img>` elements all act as **inline** elements.

How can we make an element act as a block instead of inline? With the `display: block` CSS declaration:

```html
<span style="display: block">You can learn about the world at Wikipedia.</span>

<span style="display: block">Another good place to learn is Khan Academy.</span>
```
{: .repl #display_block title="display: block" points="1"}

Voila! The two spans are now blocks, so they are stacked vertically on top of one another.

### The `<div>` element

We're going to need a _lot_ of block level elements. It would be a pain to have to add `style="display: block"` to `<span>`s over and over and over every time we wanted a block element; so, HTML provides a shortcut — the `<div>` element:

```html
<div>You can learn about the world at Wikipedia.</div>

<div>Another good place to learn is Khan Academy.</div>
```
{: .repl #first_div title="First div" points="1"}

A `<div>` is just a `<span>` with `display: block` already set. We'll end up using `<div>`s even more than `<span>`s to add structure to our HTML documents, because in the modern web apps we need a _lot_ of blocks.

Phew, that's going to save us a lot of typing!

- Select all that are true:
- Flow is an HTML element.
  - Not quite.
- Flow is a layout system.
  - Yes!
- Inline elements are placed side by side horizontally, blocks are placed side by side vertically.
  - Yes!
- Inline elements are placed side by side vertically, blocks are placed side by side horizontally.
  - Not quite.
- By default, "span" acts as a block element
  - Not quite.
- A `div` is essentially just a `span` with the attribute `style="display: block"`
  - Yes!
{: .choose_all #flow_quiz title="Flow quiz" points="3" answer="[2,3,6]" }

### Drawing borders around elements

A very handy set of CSS properties lets us draw borders around elements. Borders are essential for almost every design, but they're also really nice when learning & debugging, because it makes it easier to see where each element is and how much space it is taking up.

First, `border-style`:

```html
<div style="border-style: dotted;">You can learn about the world at Wikipedia.</div>

<div style="border-style: dotted;">Another good place to learn is Khan Academy.</div>
```
{: .repl #border_style title="border-style" points="1"}

You can also try the values `solid`, `dashed`, or `double`. (The default value of `border-style` for an element is `none`.)

The default color for borders is black. We can customize that with the `border-color` property:

```html
<div style="border-style: dotted; border-color: blue;">You can learn about the world at Wikipedia.</div>

<div style="border-style: dotted; border-color: blue;">Another good place to learn is Khan Academy.</div>
```
{: .repl #border_color title="border-color" points="1"}

The default width of a border is 1px. We can customize that with the `border-width` property:

```html
<div style="border-style: dotted; border-color: blue; border-width: 10px">You can learn about the world at Wikipedia.</div>

<div style="border-style: dotted; border-color: blue; border-width: 10px">Another good place to learn is Khan Academy.</div>
```
{: .repl #border_width title="border-width" points="1"}

There's a handy shortcut for specifying style, color, and width all at once — the `border` property:

```html
<div style="border: dotted blue 10px">You can learn about the world at Wikipedia.</div>

<div style="border: dotted blue 10px">Another good place to learn is Khan Academy.</div>
```
{: .repl #border_shortcut title="border shortcut" points="1"}

### The box model

For elements that are `display: block`, we can set a few useful properties:

- width: how much space we want the content to take up
- padding: how much space we want outside the content of the element, but inside the border
- border: we already discussed this
- margin: how much space we want outside the border of the element, between it and its neighbors

![](https://res.cloudinary.com/dmxgp9oq2/image/upload/v1687385113/Screen_Shot_2023-06-21_at_5.05.02_PM_frg6ku.png)

For example:

```html
<div style="width: 200px; padding: 20px; border: solid red 5px; margin: 30px">You can learn about the world at Wikipedia.</div>

<div style="width: 200px; padding: 20px; border: solid red 5px; margin: 30px">Another good place to learn is Khan Academy.</div>
```
{: .repl #box_model title="Box model" points="1"}

You can also individually set `padding-top`, `padding-bottom`, `padding-left`, `padding-right`, `margin-top`, `margin-bottom`, `margin-left`, and `margin-right`.

- In the box model, the "margin" is the... 
- space the content takes up.
  - Not quite. Re-read above.
- space outside the border.
  - Yes!
- space outside the content but inside the border.
  - Not quite. Re-read above.
{: .choose_best #margin_is title="margin is..." points="1" answer="2" }

### CSS style rules

We're often going to want to apply the same set of styles to multiple elements in our HTML document; sometimes to _hundreds_ of elements. It's a big pain to have to repeat the same, long `style="..."` attribute on lots of elements.

CSS provides a better way: **style rules**. First, we need a `<style>` element in our document. Then, within that element, we can write style rules. For example:

```html
<style>
  div {
    width: 200px;
    padding: 20px;
    border: solid red 5px;
    margin: 30px;
  }	
</style>

<div>You can learn about the world at Wikipedia.</div>

<div>Another good place to learn is Khan Academy.</div>

<span style="display: block">I'm a span, unlike the above two blocks, which are divs.</span>
```
{: .repl #style_element title="style element" points="1"}

In the style rule:

```css
div {
  width: 200px;
  padding: 20px;
  border: solid red 5px;
  margin: 30px;
}	
```

- `div` is called the **selector**.
	- This particular selector is saying to target all of the `<div>` elements in the document. This is why the border is not being applied to the third block in the document; it's a `<span>`, not a `<div>`.
- After the selector is a set of curly brackets (`{ }`).
- Within the curly brackets, we can have a set of declarations, separated by semicolons; just as we could within a `style=""` attribute.
- Everything within the `{ }` is called the **declaration block**.
- The whole thing all together is called a **style rule**.

Nice! Now we can apply a set of declarations to hundreds or thousands of elements easily! But, we now have to learn how to target just the elements we want, using **CSS selectors**.

- What is the `div` within the `style` called? 
- selector
  - That's right!
- declaration
  - Not quite.
- style rule
  - Not quite.
{: .choose_best #css_selector title="div within style" points="1" answer="1" }

- And what does that `div` style rule do? 
- It selects the first `div` element it finds in the rest of the HTML.
  - Not quite. Re-read above.
- It selects all non-`div` elements it finds in the rest of the HTML.
  - Not quite. Re-read above.
- It selects all `div` elements it finds in the rest of the HTML.
  - Is there a better answer here?
- It selects all `div` elements it finds in the rest of the HTML and it applies the specified declarations.
  - Yes!
{: .choose_best #div_selector_does title="The div does..." points="1" answer="4" }

### CSS selectors

The two main types of selectors we're going to focus on for now are **tag-type** selectors and **class-level** selectors.

In the same example, what if we wanted to make text in the second `div` red, but leave the first `div` alone?

```html
<style>
	div {
		width: 200px;
		padding: 20px;
		border: solid red 5px;
		margin: 30px;
	}	
</style>

<div>You can learn about the world at Wikipedia.</div>

<div>Another good place to learn is Khan Academy.</div>

<span style="display: block">I'm a span, unlike the above two blocks, which are divs.</span>
```

Since `div` is a tag-type selector, if we add `color: red` to the declaration block, it will apply to _all_ `<div>` elements in the document:

```html
<style>
  div {
    width: 200px;
    padding: 20px;
    border: solid red 5px;
    margin: 30px;

    color: red;
  }	
</style>

<div>You can learn about the world at Wikipedia.</div>

<div>Another good place to learn is Khan Academy.</div>

<span style="display: block">I'm a span, unlike the above two blocks, which are divs.</span>
```
{: .repl #tag_selector_too_broad title="Tag selector too broad" points="1"}

We could achieve the more precise targeting we want by dropping back down to an inline `style=""` attribute:

```html
<style>
  div {
    width: 200px;
    padding: 20px;
    border: solid red 5px;
    margin: 30px;
  }	
</style>

<div>You can learn about the world at Wikipedia.</div>

<div style="color: red">Another good place to learn is Khan Academy.</div>

<span style="display: block">I'm a span, unlike the above two blocks, which are divs.</span>
```
{: .repl #inline_style title="Add inline style" points="1"}

This does what we want, but we've lost the nice ability to affect hundreds or thousands of elements at once with a style rule. 

What's the solution? A **class-level selector**:

```html
<style>
  div {
    width: 200px;
    padding: 20px;
    border: solid red 5px;
    margin: 30px;
  }
	
  .danger {
    color: red
  }
</style>

<div>You can learn about the world at Wikipedia.</div>

<div class="danger">Another good place to learn is Khan Academy.</div>

<span class="danger" style="display: block">I'm a span, unlike the above two blocks, which are divs.</span>
```
{: .repl #class_selector title="Class selector" points="1"}

In the above example:

- `.danger` is a class-level selector because we started it with a `.` 
- To any element we want to apply the style rule to, we must add a `class="danger"` attribute.
	- Notice there's no `.` when _applying_ a class, only when writing the selector.
- We can now specifically target individual `<div>`s rather than styling them all at once. We can also use the class for other types of elements, like the `<span>` at the bottom.

For 99% of our CSS work, we will be defining class-level style rules and then applying them to our HTML elements using the `class=""` attribute; rather than using inline `style=""` attributes, or tag-type selectors.

- Select all that are true:
- A single tag selector could apply to all `span` elements.
  - Yes!
- We define classes by writing `style=""` inside an HTML element opening tag.
  - Not quite. We use `class=""`.
- A class selector allows us to target any elements where the `class=""` attribute matches.
  - Yes!
- This is the correct way to add a class to an HTML element: `class=".danger"`
  - Not quite. The `.` only goes in the CSS selector, not in the HTML attribute.
- The same class selector cannot apply to different types of HTML elements.
  - Not quite. Look at the example above.
{: .choose_all #selector_quiz title="Selector quiz" points="2" answer="[1,3]" }

### Flexbox layout

As the web matured, people started using it for more than just sharing research papers. It became a platform for stores, photo albums, games, and a million other things — _apps_.

The typesetting-like flow layout system struggled to support all these varied use cases. For example, putting two columns of text side by side horizontally was not easy in flow mode, which is very much optimized for "inline words, block paragraphs".

So, eventually CSS added a few other layout systems. The one we'll use most while building our apps is called **flexbox**.

As discussed above, the default system that an element uses to position its children is flow. Examine this example:

```html
<style>
  .parent {
    border: dotted blue 1px;
  }

  .child {
    width: 50px;
    padding: 20px;
    border: solid red 5px;
  }
</style>

<div class="parent">
  <div class="child">A</div>

  <div class="child">B</div>

  <div class="child">C</div>
</div>
```
{: .repl #flexbox_1 title="Flexbox, 1" points="1"}

The three inner `div`s have the class `child`, so they have a border, etc. They are still vertically stacked on top of each other even though they are narrow, because they are blocks and the parent element uses flow to lay them out.

If we want to change the parent's layout mode to flexbox, we use the `display: flex` property:

```html
<style>
  .parent {
    border: dotted blue 1px;

    display: flex;
  }

  .child {
    width: 50px;
    padding: 20px;
    border: solid red 5px;
  }
</style>

<div class="parent">
  <div class="child">A</div>

  <div class="child">B</div>

  <div class="child">C</div>
</div>
```
{: .repl #flexbox_2 title="Flexbox, 2" points="1"}

Boom! All of a sudden, we're in a wild new world. Within an element that is `display: flex`, "block" and "inline" don't really mean anything anymore. Those terms are relevant for typesetting, but flexbox is for more dynamic, responsive, app-type layouts.

Instead, we can now set the `flex-direction` property:

```html
<style>
  .parent {
    border: dotted blue 1px;
    display: flex;

    flex-direction: column;
  }

  .child {
    width: 50px;
    padding: 20px;
    border: solid red 5px;
  }
</style>

<div class="parent">
  <div class="child">A</div>

  <div class="child">B</div>

  <div class="child">C</div>
</div>
```
{: .repl #flexbox_3 title="Flexbox, 3" points="1"}

`flex-direction` defaults to `row`, which positions children horizontally within the flex container. This makes putting elements side by side (which was hard in flow layout) a breeze!

We can switch `flex-direction` to `column` if we want to lay things out vertically (sort of similar to blocks in flow layout).

[Read more about flex-direction here.](https://developer.mozilla.org/en-US/docs/Web/CSS/flex-direction)

### Flexbox froggy

To get more familiar with flexbox, which we'll be using for the majority of our layouts, play through this interactive game:

[Flexbox Froggy](https://flexboxfroggy.com/)

Ask lots of questions!

- What level did you reach in Flexbox Froggy?
{: .free_text_number #flexbox_froggy_level title="Flexbox Froggy Level" points="1" answer="any" }

### That's all, for now

This concludes my ultra-minimal review of HTML & CSS. I hope it helped fill in a few gaps. Next, we'll learn more HTML elements and CSS properties by building some useful websites!
