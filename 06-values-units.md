# CSS values and units

### Absolute length units

Unit |	Name	               | Equivalent to
---- | ---------------------- | -------------------
cm   |  Centimeters	       | 1cm = 37.8px = 25.2/64in
mm   |  Millimeters	       | 1mm = 1/10th of 1cm
Q	 |  Quarter-millimeters   | 1Q = 1/40th of 1cm
in   |  Inches	               | 1in = 2.54cm = 96px
pc   |  Picas	               | 1pc = 1/6th of 1in
pt   |  Points	               | 1pt = 1/72nd of 1in
px   |  Pixels	               | 1px = 1/96th of 1in

<br>

### Relative length units

Unit      | Relative to
--------- | -----------
em        | Font size of the parent, in the case of typographical properties like `font-size`, and font size of the element itself, in the case of other properties like `width`.
ex        | x-height of the element's font.
ch        | The advance measure (width) of the glyph "0" of the element's font.
rem       | Font size of the root element.
lh        | Line height of the element.
rlh       | Line height of the root element. When used on the `font-size` or `line-height` properties of the root element, it refers to the properties' initial value.
vw        | 1% of the viewport's width.
vh        | 1% of the viewport's height.
vmin      | 1% of the viewport's smaller dimension.
vmax      | 1% of the viewport's larger dimension.
vb        | 1% of the size of the initial containing block in the direction of the root element's block axis.
vi        | 1% of the size of the initial containing block in the direction of the root element's inline axis.
svw, svh  | 1% of the small viewport's width and height, respectively.
lvw, lvh  | 1% of the large viewport's width and height, respectively.
dvw, dvh  | 1% of the dynamic viewport's width and height, respectively.

<br>

An example

```html
    <div class="wrapper">
        <div class="box px">I am 200px wide</div>
        <div class="box vw">I am 10vw wide</div>
        <div class="box em">I am 10em wide</div>
    </div>
```

```css
    .wrapper {
        font-size: 1em;
    }

    .px {
        width: 200px;
    }

    .vw {
        width: 10vw;
    }

    .em {
        width: 10em;
    }
```

<br>

### ems and rems
- `em` unit means "my parent element's font-size" in the case of typography.
- The `<li>` elements inside the `<ul>` with a class of ems take their sizing from their parent.
- So each successive level of nesting gets progressively larger, as each has its font size set to 1.3em — 1.3 times its parent's font size.
- `rem` unit means "The root element's font-size" (rem stands for "root em").
- The `<li>` elements inside the `<ul>` with a class of rems take their sizing from the root element (`<html>`). This means that each successive level of nesting does not keep getting larger.
- However, if you change the `<html>` element's font-size in the CSS you will see that everything else changes relative to it — both rem- and em-sized text.
```html
    <ul class="ems">
        <li>One</li>
        <li>Two</li>
        <li>Three
            <ul>
                <li>Three A</li>
                <li>Three B
                    <ul>
                        <li>Three B 2</li>
                    </ul>
                </li>
            </ul>
        </li>
    </ul>

    <ul class="rems">
        <li>One</li>
        <li>Two</li>
        <li>Three
            <ul>
                <li>Three A</li>
                <li>Three B
                    <ul>
                        <li>Three B 2</li>
                    </ul>
                </li>
            </ul>
        </li>
    </ul>
```

```css
    html {
        font-size: 16px;
    }

    .ems li {
        font-size: 1.3em;
    }

    .rems li {
        font-size: 1.3rem;
    }
```

<br>

### Percentages
- They are always set relative to some other value.
- For example, if you set an element's font-size as a percentage, it will be a percentage of the font-size of the element's parent.
- If you use a percentage for a width value, it will be a percentage of the width of the parent.

```html
    <div class="box px">I am 200px wide</div>
    <div class="box percent">I am 40% wide</div>
    <div class="wrapper">
        <div class="box px">I am 200px wide</div>
        <div class="box percent">I am 40% wide</div>
    </div>
```

```css
    .wrapper {
        width: 400px;
        border: 5px solid rebeccapurple;
    }

    .px {
        width: 200px;
    }

    .percent {
        width: 40%;
    }
```

<br>

### Numbers

```html
    <div class="wrapper">
        <div class="box">I am a box with opacity</div>
    </div>
```

```css
    .box {
        opacity: 0.6;
    }
```

<br>

### Color
- Color keywords: `background-color: antiquewhite`
- Hexadecimal RGB values: `background-color: #02798b`
- RGB values: `background-color: rgb(2, 121, 139)`
- RGBA values: `background-color: rgba(2, 121, 139, .3)`
- HSL values: `background-color: hsl(188, 97%, 28%)`
- HSLA values: `background-color: hsl(188, 97%, 28%)`

<br>

### Functions
- `calc()` function gives you the ability to do simple calculations inside your CSS.
- Below we are using `calc()` to make the box `20% + 100px` wide.
- The 20% is calculated from the width of the parent container `.wrapper` and so will change if that width changes.

```html
    <div class="wrapper">
        <div class="box">My width is calculated.</div>
    </div>
```
```css
    .wrapper {
      width: 400px;
    }

    .box {
      width: calc(20% + 100px);
    }
```
