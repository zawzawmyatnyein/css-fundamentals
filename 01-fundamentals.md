# CSS Fundamentals

## What is CSS?

- Cascading Style Sheets
- CSS describe the ***visual style and presentation*** of the ***content written in HTML***
- CSS consist of many ***properties*** (font, text, spacing, layout, etc.) that can be used to format the content

<br>
<br>

## Anatomy of CSS ruleset
```css
    p {
        color: red;
    }
```

![css ruleset](https://developer.mozilla.org/en-US/docs/Learn/Getting_started_with_the_web/CSS_basics/css-declaration-small.png)

<br>
<br>

## How does CSS work?

- Load and Parse HTML
- Convert HTML into a ***DOM (Document Object Model)***
- Fetch resources linked to HTML document (css, js, images, videos, etc.)
- Load and Parse CSS
- Resolve conflicting CSS rules (cascade) and process final CSS values
- Attach styles to DOM nodes (Render tree)
- Display the page (Painting)

![css process](https://developer.mozilla.org/en-US/docs/Learn/CSS/First_steps/How_CSS_works/rendering.svg)

---
<br>

## Applying CSS to HTML

- External Style Sheet
```html
    <link rel="stylesheet" href="style.css">
```
```css
    /* style.css */

    h1 {
      color: blue;
      background-color: yellow;
      border: 1px solid black;
    }

    p {
      color: red;
    }
```

<br>

- Internal Style Sheet
```html
    <!DOCTYPE html>
    <html lang="en-GB">
      <head>
        <meta charset="utf-8" />
        <title>My CSS experiment</title>
        <style>
          h1 {
            color: blue;
            background-color: yellow;
            border: 1px solid black;
          }

          p {
            color: red;
          }
        </style>
      </head>
      <body>
        <h1>Hello World!</h1>
        <p>This is my first CSS example</p>
      </body>
    </html>
```

<br>

- Inline Styles
```html
    <!DOCTYPE html>
    <html lang="en-GB">
      <head>
        <meta charset="utf-8" />
        <title>My CSS experiment</title>
      </head>
      <body>
        <h1 style="color: blue; background-color: yellow; border: 1px solid black;">
          Hello World!
        </h1>
        <p style="color: red;">This is my first CSS example</p>
      </body>
    </html>
```
