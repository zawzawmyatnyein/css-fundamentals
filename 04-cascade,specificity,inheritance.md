# Cascade, specificity, and inheritance

## Cascade (Conflicting rules)
- Process of combining different stylesheets and resolving conflicts between different CSS rules, when more than one rule applies to a certain element

<br>

### Source Order
- More than one rule ***(exactly the same weight)***, then ***the one that comes last*** in the CSS will win
- Only matter when the specificity weight of the rules is the same
```html
    <h1>This is my heading.</h1>
```

```css
    h1 {
        color: red;
    }

    h1 {
        color: blue;
    }
```

<br>

### Specificity
- Algorithm that the browser uses to decide which property value is applied to an element
- Decide the property value that gets applied to the element if multiple style blocks have different selectors that configure the same property with different values and target the same element
-  A measure of how specific a selector's selection will be

<br>

> **Note:** The universal selector `(*)`, combinators `(+, >, ~, ' ')`, and specificity adjustment selector `:where()` along with its parameters, have no effect on specificity.

> **Note:** The negation `:not()`, relational selector `:has()`, and the matches-any `:is()` pseudo-classes themselves don't have effect on specificity, but their parameters do.

<br>

| Selector | ID | Class, pseudo-class, attribute | Element, pseudo-element | Total specificity |
| -------- | -- | ------------------------------- | ---------------------- | ----------------- |
| `h1`     | 0	|              0	              |            1	       |      0-0-1        |
| `h1 + p::first-letter` | 0 |         0	      |            3	       |      0-0-3        |
| `li > a[href*="en-US"] > .inline-warning` | 0 | 2 |          2	       |      0-2-2        |
| `#btn`   | 1	|              0	              |            0	       |      1-0-0        |
| `button:not(#mainBtn, .cta)` | 1 |      0	      |            1	       |      1-0-1        |

<br>

An example in action
```html
    <div id="outer" class="container">
        <div id="inner" class="container">
            <ul>
                <li class="nav"><a href="#">One</a></li>
                <li class="nav"><a href="#">Two</a></li>
            </ul>
        </div>
    </div>
```

```css
    /* 1. specificity: 1-0-1 */
    #outer a {
        background-color: red;
    }

    /* 2. specificity: 2-0-1 */
    #outer #inner a {
        background-color: blue;
    }

    /* 3. specificity: 1-0-4 */
    #outer div ul li a {
        color: yellow;
    }

    /* 4. specificity: 1-1-3 */
    #outer div ul .nav a {
        color: white;
    }

    /* 5. specificity: 0-2-4 */
    div div li:nth-child(2) a:hover {
        border: 10px solid black;
    }

    /* 6. specificity: 0-2-3 */
    div li:nth-child(2) a:hover {
        border: 10px dashed black;
    }

    /* 7. specificity: 0-3-3 */
    div div .nav:nth-child(2) a:hover {
        border: 10px double black;
    }

    a {
        display: inline-block;
        line-height: 40px;
        font-size: 20px;
        text-decoration: none;
        text-align: center;
        width: 200px;
        margin-bottom: 10px;
    }

    ul {
        padding: 0;
    }

    li {
        list-style-type: none;
    }
```

> **Note**: *Inline styles* take precedence over all normal styles, no matter the specificity. Such declarations don't have selectors, but their specificity can be construed as `1-0-0-0`; always more than any other specificity weight no matter how many IDs are in the selectors.

<br>

### Importance `!important`
- Special piece of CSS that can overrule all of the above calculations, even inline styles - the `!important` flag
- Should be very careful while using it
- Use to make an individual property and value pair the most specific rule
- Override the normal rules of the cascade, including normal inline styles

```html
    <p class="better">This is a paragraph.</p>
    <p class="better" id="winning">One selector to rule them all!</p>
```

```css
    #winning {
        background-color: red;
        border: 1px solid black;
    }

    .better {
        background-color: gray;
        border: none !important;
    }

    p {
        background-color: blue;
        color: white;
        padding: 5px;
    }
```

<br>

General Conclusion
- CSS declarations marked with `!important` have the highest priority
- Only use `!important` as a last resource. It's better to use correct specificities - **more maintainable code!**
- Inline styles will always have priority over styles in external stylesheets
- A selector that contains **1** ID is more specific than one with **1000** classes
- A selector that contains **1** class is more specific than one with **1000** elements
- The universal selector `*` has no specificity value (0, 0, 0)
- Rely more on **specificity** than on the **order** of selectors
- But, rely on order when using 3rd-party stylesheets - always put your author stylesheet last

---
<br>

## Inheritance

- The `color` property is an inherited property. So, the color property value is applied to the direct children and also to the indirect children
- Every CSS property page lists whether or not the property is inherited

```html
    <ul class="main">
        <li>Item One</li>
        <li>Item Two
            <ul>
                <li>2.1</li>
                <li>2.2</li>
            </ul>
        </li>
        <li>Item Three
            <ul class="special">
                <li>3.1
                    <ul>
                        <li>3.1.1</li>
                        <li>3.1.2</li>
                    </ul>
                </li>
                <li>3.2</li>
            </ul>
        </li>
    </ul>
```

```css
    .main {
        color: rebeccapurple;
        border: 2px solid #ccc;
        padding: 1em;
    }

    .special {
        color: black;
        font-weight: bold;
    }
```

<br>

### Controlling inheritance

- `inherit`: Sets the property value applied to a selected element to be the same as that of its parent element. Effectively, this "turns on inheritance".
- `initial`: Sets the property value applied to a selected element to the initial value of that property.
- `revert`: Resets the property value applied to a selected element to the browser's default styling rather than the defaults applied to that property. This value acts like unset in many cases.
- `unset`: Resets the property to its natural value, which means that if the property is naturally inherited it acts like inherit, otherwise it acts like initial.

```html
    <ul>
        <li>Default <a href="#">link</a> color</li>
        <li class="my-class-1">Inherit the <a href="#">link</a> color</li>
        <li class="my-class-2">Reset the <a href="#">link</a> color</li>
        <li class="my-class-3">Unset the <a href="#">link</a> color</li>
    </ul>
```

```css
    body {
        color: green;
    }

    .my-class-1 a {
        color: inherit;
    }

    .my-class-2 a {
        color: initial;
    }

    .my-class-3 a {
        color: unset;
    }
```
