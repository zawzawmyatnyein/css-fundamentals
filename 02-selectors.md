# CSS Selectors

## What is a selector?

- First part of a CSS Rule
- Tell the browser which HTML elements should be selected to apply the CSS property values inside the Rule

![css selector](https://developer.mozilla.org/en-US/docs/Learn/CSS/Building_blocks/Selectors/selector.png)

<br>
<br>

## Types of selectors

- Type selector
```css
    h1 {
    }
```
- Class selector
```css
    .box {
    }
```
- ID selector
```css
    #unique {
    }
```
- Attribute selector
```css
    a[title] {
    }

    a[href="https://example.com"] {
    }
```
- Pseudo-class selector
```css
    a:hover {
    }
```
- Pseudo-element selector
```css
    p::first-line {
    }
```
- Universal selector
```css
    /* Selects all elements */
    * {
      color: green;
    }
```
