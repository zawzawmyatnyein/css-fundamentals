# Normal Flow and Positioning

## Normal Flow
- Normal flow is how the browser lays out HTML pages by default when you do nothing to control page layout

```html
    <h1>Basic document flow</h1>

    <p>
      I am a basic block level element. My adjacent block level elements sit on new
      lines below me.
    </p>

    <p>
      By default we span 100% of the width of our parent element, and we are as tall
      as our child content. Our total width and height is our content + padding +
      border width/height.
    </p>

    <p>
      We are separated by our margins. Because of margin collapsing, we are
      separated by the width of one of our margins, not both.
    </p>

    <p>
      Inline elements <span>like this one</span> and <span>this one</span> sit on
      the same line along with adjacent text nodes, if there is space on the same
      line. Overflowing inline elements will
      <span>wrap onto a new line if possible (like this one containing text)</span>,
      or just go on to a new line if not, much like this image will do:
      <img src="https://yari-demos.prod.mdn.mozit.cloud/en-US/docs/Learn/CSS/CSS_layout/Normal_Flow/long.jpg" alt="snippet of cloth" />
    </p>
```

```css
    body {
      width: 500px;
      margin: 0 auto;
    }

    p {
      background: rgba(255, 84, 104, 0.3);
      border: 2px solid rgb(255, 84, 104);
      padding: 10px;
      margin: 10px;
    }

    span {
      background: white;
      border: 1px solid black;
    }
```

<br>

## Positioning
- Positioning allows you to take elements out of normal document flow and make them behave differently

<br>

### Static Positioning
- Static positioning is the default that every element gets
- It just means "put the element into its normal position in the document flow

```html
    <h1>Static positioning</h1>

    <p>I am a basic block level element. My adjacent block level elements sit on new lines below me.</p>

    <p class="positioned">By default we span 100% of the width of our parent element, and our are as tall as our child content. Our total width and height is our content + padding + border width/height.</p>

    <p>We are separated by our margins. Because of margin collapsing, we are separated by the width of one of our margins, not both.</p>

    <p>inline elements <span>like this one</span> and <span>this one</span> sit on the same line as one another, and adjacent text nodes, if there is space on the same line. Overflowing inline elements <span>wrap onto a new line if possible — like this one containing text</span>, or just go on to a new line if not, much like this image will do: <img src="long.jpg" alt="a wide but short section of a photo of several fabrics"></p>
```

```css
    body {
        width: 500px;
        margin: 0 auto;
    }

    p {
        background: aqua;
        border: 3px solid blue;
        padding: 10px;
        margin: 10px;
    }

    span {
        background: red;
        border: 1px solid black;
    }

    .positioned {
        position: static;
        background: yellow;
    }
```

<br>

### Relative Positioning
- Very similar to static positioning, except that once the positioned element has taken its place in the normal flow, you can then modify its final position, including making it overlap other elements on the page

```css
    .positioned {
        position: relative;
        background: yellow;
        top: 30px;
        left: 30px;
    }
```

<br>

### Absolute Positioning
- Element is removed from the normal flow: ***out of flow***
- No impact on surrounding elements, might overlap them
- Use `top`, `bottom`, `left`, or `right` to offset the element from its relatively positioned container

```css
    body {
        width: 500px;
        margin: 0 auto;
        position: relative;
    }

    .positioned {
        position: absolute;
        background: yellow;
        top: 30px;
        left: 30px;
    }
```

### Introducing `z-index`

```css
    p:nth-of-type(1) {
        position: absolute;
        background: lime;
        top: 10px;
        right: 30px;
        /* z-index: 1; */
    }
```

<br>

### Fixed Positioning
- Works in exactly the same way as absolute positioning, with one key difference
- Absolute positioning fixes an element in place relative to its nearest positioned ancestor
- Fixed positioning usually fixes an element in place relative to the visible portion of the viewport

> **Note:** remove `p:nth-of-type(1)` and `.positioned `rules from your CSS.

```css
    body {
        width: 500px;
        height: 1400px;
        margin: 0 auto;
    }

    h1 {
        position: fixed;
        top: 0;
        width: 500px;
        margin-top: 0;
        background: white;
        padding: 10px;
    }

    p:nth-of-type(1) {
        margin-top: 60px;
    }
```

<br>

### Sticky Positioning
- A hybrid between relative and fixed position
- Allow a positioned element to act like it's relatively positioned until it's scrolled to a certain threshold (e.g., 10px from the top of the viewport), after which it becomes fixed.

```html
    <h1>Sticky positioning</h1>

    <dl>
        <dt>A</dt>
        <dd>Apple</dd>
        <dd>Ant</dd>
        <dd>Altimeter</dd>
        <dd>Airplane</dd>
        <dt>B</dt>
        <dd>Bird</dd>
        <dd>Buzzard</dd>
        <dd>Bee</dd>
        <dd>Banana</dd>
        <dd>Beanstalk</dd>
        <dt>C</dt>
        <dd>Calculator</dd>
        <dd>Cane</dd>
        <dd>Camera</dd>
        <dd>Camel</dd>
        <dt>D</dt>
        <dd>Duck</dd>
        <dd>Dime</dd>
        <dd>Dipstick</dd>
        <dd>Drone</dd>
        <dt>E</dt>
        <dd>Egg</dd>
        <dd>Elephant</dd>
        <dd>Egret</dd>
    </dl>
```

```css
    body {
        width: 500px;
        height: 1400px;
        margin: 0 auto;
    }

    dt {
        background-color: black;
        color: white;
        padding: 10px;
        position: sticky;
        top: 0;
        left: 0;
        margin: 1em 0;
    }
```
