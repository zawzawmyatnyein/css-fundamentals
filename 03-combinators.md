# CSS Combinators

<br>

## Adjacent sibling combinator `(+)`
- Separate two selectors
- ***Match the second element*** only if it immediately ***follows the first element***, and both are ***children of the same parent element***

```html
    <ul>
        <li>One</li>
        <li>Two!</li>
        <li>Three</li>
    </ul>
```

```css
    li:first-of-type + li {
        color: red;
    }
```

<br>

## General sibling combinator `(~)`
- Separate two selectors
- ***Match all iterations of the second element***, that are ***following the first element*** (though not necessarily immediately), and are children of the same parent element

```html
    <span>This is not red.</span>
    <p>Here is a paragraph.</p>
    <code>Here is some code.</code>
    <span>And here is a red span!</span>
    <span>And this is a red span!</span>
    <code>More code…</code>
    <div>How are you?</div>
    <p>Whatever it may be, keep smiling.</p>
    <h1>Dream big</h1>
    <span>And yet again this is a red span!</span>
```

```css
    p ~ span {
        color: red;
    }
```

<br>

## Child combinator `(>)`
- Place between two CSS selectors
- Match only those ***elements matched by the second selector*** that are the ***direct children of elements matched by the first***

```html
    <div>
        <span>Span #1, in the div.
            <span>Span #2, in the span that's in the div.</span>
        </span>
    </div>
    <span>Span #3, not in the div at all.</span>
```

```css
    span {
        background-color: aqua;
    }

    div > span {
        background-color: yellow;
    }
```

<br>

## Descendant combinator `( )`
- Represent by a single space (" ") character
- Combine two selectors such that ***elements matched by the second selector are selected*** if they have ***an ancestor element matching the first selector***

```html
    <ul>
        <li>
            <div>Item 1</div>
            <ul>
                <li>Subitem A</li>
                <li>Subitem B</li>
            </ul>
        </li>
        <li>
            <div>Item 2</div>
            <ul>
                <li>Subitem A</li>
                <li>Subitem B</li>
            </ul>
        </li>
    </ul>
```

```css
    li {
        list-style-type: disc;
    }

    li li {
        list-style-type: circle;
    }
```

<br>

## Selector list `(,)`
- A comma-separated list of selectors
- Select all the matching nodes.
- ***Multiple selectors share the same declarations*** can be grouped together into a comma-separated list
-  Can ***pass as parameters*** to some ***functional CSS pseudo-classes***

Following three declarations are equivalent:
```css
    /* first declaration */
    span {
        border: red 2px solid;
    }
    div {
        border: red 2px solid;
    }

    /* second declaration */
    span,
    div {
        border: red 2px solid;
    }

    /* third declaration */
    :is(span, div) {
        border: red 2px solid;
    }
```

Single line grouping
```css
    h1, h2, h3, h4, h5, h6 {
        font-family: helvetica;
    }
```

Multi line grouping
```css
    #main,
    .content,
    article,
    h1 + p {
        font-size: 1.1em;
    }
```
