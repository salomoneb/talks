# It’s Hip to Be Square: A Re-introduction to Web Layout 

## But Why
* Layout is not cool - there are a million other things that we could talk about. 
* Fundamentals often get dismissed in pursuit of the shiny thing (knowing the fundamentals can help you understand the shiny thing).
* Programmers are often quick to dismiss layout - and CSS in general - as secondary or irrelevant to their work. 
* As web developers, we make things **for the web**. If you can know what things like “dependency injection” and “memoization” mean, but are overwhelmed at the prospect of styling a login page, then you are missing key skills. 

## Goals
* Familiarize ourselves with the fundamentals of web layout. 
* Understand the different ways that we can apply these technologies when building web pages.

## Let's Review
* The box model
* The `display` property
* Flow, floats, and positioning

These are the primary concepts governing layout in the [visual formatting model](https://www.w3.org/TR/CSS21/visuren.html#visual-model-intro). 

## The Box Model
In order to understand page layout, we first need to understand how individual elements are formed and occupy space.

> The CSS box model describes the rectangular boxes that are generated for elements in the document tree and laid out according to the visual formatting model. 

Source: [W3](https://www.w3.org/TR/CSS2/box.html)

### Content, Padding, Border, and Margin
* **Content area** - contains the “real” element content (text, image, etc). Defined with width and height properties (including min-width, min-height, etc). 
* **Padding area** - extends the content area. Can be set with the padding property. Pushes against the content. 
* **Border** - the border around the padding and the content. 0 by default. 
* **Margin** - the space surrounding a CSS box. Pushes against other CSS boxes in the layout.

[Chrome Devtools]

### Margin Collapse

>Margins have a specific behavior called margin collapsing. When two boxes touch against one another, the distance between them is the value of the largest of the two touching margins, and not their sum.

Source: [MDN](https://developer.mozilla.org/en-US/docs/Learn/CSS/Introduction_to_CSS/Box_model)

#### :bulb: [DEMO 1](https://codepen.io/soluhmin/pen/ReGqdw)

### Box-sizing
* The `box-sizing` CSS property defines how the user agent should calculate the total width and height of an element. 
* Accepts two values: `content-box` (default) and `border-box`.
* By default, the width and height you assign to an element is **only applied to its content box.** This means that when you set a height and width, you have to adjust the values to account for border and padding (margin is excluded). 
* By setting `box-sizing: border-box;`, the user agent factors in the padding and border values when calculating the total element size. 

#### :bulb: [DEMO 2](https://codepen.io/soluhmin/pen/wYzQgB)

### :warning: Using border to troubleshoot layout
* We often need to calculate the sizing of things on web pages. Sometimes we want to know how two boxes are laid out next to each other.
* Generally, it's not a good idea to use border for this.
* Border occupies space, which affects layout. Use `outline` instead (ex. `outline: 1px solid red;`).
* Outline doesn’t take up space and is not part of the box model. It also doesn’t have to be rectangular. 

To see all boxes on a page:
```
* {
    outline: 1px solid red;
}
```
