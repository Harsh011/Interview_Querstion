<details>
<summary>
<h3>1. Difference between Div and Span</h3>
</summary>

`<div>` and `<span>` are two fundamental HTML elements used for grouping and styling content, but they serve different purposes and have different characteristics.

**`<div>` Element**

- **Type**: Block-level element
- **Usage**: Used for grouping larger sections of content or layout purposes.
- **Behavior**: Occupies the full width available (by default), creating a block of content.
- **Common Uses**: Structuring sections of a web page, creating layouts, wrapping multiple elements.
  **Example:**

```js
<div>
  <h1>Title</h1>
  <p>This is a paragraph inside a div.</p>
</div>
```

**`<span>` Element**

- **Type**: Inline-level element
- **Usage**: Used for styling or grouping smaller pieces of text or inline content.
- **Behavior**: Does not start on a new line and only takes up as much width as necessary.
- **Common Uses**: Styling parts of text, wrapping small pieces of content without affecting the flow of the document.
  Example:

```js
<p>
  This is a <span style="color: red;">red</span> word in a paragraph.
</p>
```

**Visual Representation**

`<div>` Example:

```js
<div style="border: 1px solid black;">
  <h1>Header</h1>
  <p>Paragraph inside a div.</p>
</div>
<div style="border: 1px solid black;">
  Another div.
</div>

```

This will render as two separate blocks, each starting on a new line and occupying the full width.

`<span> `Example:

```js
<p>This is a <span style="color: red;">red</span> word in a paragraph.</p>
<p>Another paragraph with a <span style="font-weight: bold;">bold</span> word.</p>

```

This will render the words "`red`" and "`bold`" with their respective styles, without affecting the flow of the text.

**When to Use**

Use `<div>` when you need to create distinct sections or blocks of content on your web page.
Use `<span>` when you need to apply styles or classes to specific parts of inline content without disrupting the flow of text.
Understanding the differences between `<div> `and `<span> `helps in structuring HTML documents appropriately and applying styles effectively.

</details>

<details>
<summary>
<h3></h3>
</summary>
</details>
