# The box model

## Block-level Elements
- Elements are formatted visually as blocks
- Elements occupy 100% of parent element's width, no matter the content
- Elements are stacked vertically by default, one after another
- **Default elements:** `body, main, header, footer, section, nav, aside, div, h1-h6, p, ul, ol, li, etc.`
- **With CSS:** `display: block`

<br>

## Inline Elements
- Occupies only the space necessary for its conent
- Causes **no line-breaks** after or before the element
- Box model applies in a different way: ***heights and widths do not apply***
- ***Paddings and margins*** are applied **only horizontally** (left and right)
- **Default elements:** `a, img, strong, em, button, etc.`
- **With CSS:** `display: inline`

<br>

## What is the CSS box model?
- Apply to block boxes
- Define how the different parts of a box — ***margin, border, padding, and content*** — work together to create a box that you can see on a page.
- Inline boxes use just some of the behavior defined in the box model.

![box model](https://developer.mozilla.org/en-US/docs/Learn/CSS/Building_blocks/The_box_model/box-model.png)

- **Content**: The area where your content is displayed - Text, images, etc.
- **Padding**: Sit around the content as white space
- **Border**: Wrap the content and any padding
- **Margin**: The outermost layer, wrapping the content, padding, and border as whitespace between this box and other elements

<br>

## The standard CSS box model

```css
    .box {
        width: 350px;
        height: 150px;
        margin: 10px;
        padding: 25px;
        border: 5px solid black;
    }
```

> **total width** = left border + left padding + width + right padding + right border

> **total height** = top border + top padding + height + bottom padding + bottom border

The actual space taken up by the box will be 410px wide (350 + 25 + 25 + 5 + 5) and 210px high (150 + 25 + 25 + 5 + 5).

![content-box](https://developer.mozilla.org/en-US/docs/Learn/CSS/Building_blocks/The_box_model/standard-box-model.png)

<br>

## The alternative CSS box model

```css
    .box {
        box-sizing: border-box;
     }

    .box {
        width: 350px;
        height: 150px;
        margin: 10px;
        padding: 25px;
        border: 5px solid black;
    }
```

> **total width** = specified width

> **total height** = specified height

![border-box](https://developer.mozilla.org/en-US/docs/Learn/CSS/Building_blocks/The_box_model/alternate-box-model.png)

<br>

To use the alternative box model for all of your elements, set the box-sizing property on the `<html>` element and set all other elements to inherit that value:

```css
    html {
      box-sizing: border-box;
    }

    *,
    *::before,
    *::after {
      box-sizing: inherit;
    }
```

<br>

## Using display: inline-block
- `display: inline-block` A special value of display, which provides a middle ground between inline and block
- The **width and height** properties are respected
- **Padding, margin, and border** will cause other elements to be pushed away from the box.
- Does not break onto a new line, and will only become larger than its content if you explicitly add width and height properties.
