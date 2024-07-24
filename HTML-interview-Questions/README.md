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
<h3>2. In HTML why use DOCTYPE</h3>
</summary>

The <!DOCTYPE> declaration in HTML specifies the document type and version of HTML being used. It is an important part of the HTML document because it helps the browser understand how to render the content.

</details>
<details>
<summary>
<h3>3. Why do you use Semantic tags</h3>
</summary>

Semantic tags in HTML are elements that provide meaningful structure to the content of a webpage. These tags not only describe how the content looks but also define its meaning and role within the document. This enhances the understanding of the content for both browsers and developers, and it provides several key benefits:

1. **Improved Accessibility**

Semantic tags make it easier for assistive technologies, such as screen readers, to interpret and present the content to users with disabilities. For example, using `<nav>` to define navigation sections or`<header>`for header content helps screen readers navigate the page more effectively.

2. **Better SEO (Search Engine Optimization)**

Search engines use the structure and tags within an HTML document to understand the content and its relevance. Semantic tags help search engines better index and rank pages by clearly defining the content structure and importance of various parts. For example, `<article>`, `<section>`, and `<aside> `help indicate the primary content and side information.

3. **Improved Code Readability and Maintainability**

Semantic tags provide meaningful names that convey the purpose of the content, making the code easier to read and understand. This is especially useful in collaborative projects or when returning to a project after some time. For example, `<footer>` clearly indicates the footer section of a page, as opposed to a non-semantic tag like `<div>`.

4. **Enhanced Styling and Consistency**

By using semantic tags, you can apply consistent styling across different sections of your site. For example, if all articles are enclosed within `<article>` tags, you can style them uniformly using CSS, enhancing both the visual and functional consistency of the website.

5. **Future-Proofing**

Using semantic tags helps ensure that your web content remains relevant and accessible as web technologies evolve. Since these tags are standardized and widely supported, they are less likely to become obsolete compared to non-semantic tags or custom structures.

Examples of Semantic Tags

`<header>`: Represents a header section, usually containing introductory content or navigational links.

`<nav>`: Defines a set of navigation links.

`<article>`: Specifies independent, self-contained content that could be distributed independently (like a blog post or news article).

`<section>`: Represents a standalone section, typically with a heading.

`<aside>`: Contains content that is tangentially related to the main content (like sidebars or call-out boxes).

`<footer>`: Represents a footer section, usually containing information about the author, copyright information, or links to related documents.

`<main>`: Specifies the main content of a document, excluding header, footer, and navigation sections.

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Example Page</title>
  </head>
  <body>
    <header>
      <h1>Website Title</h1>
      <nav>
        <ul>
          <li><a href="#home">Home</a></li>
          <li><a href="#about">About</a></li>
          <li><a href="#contact">Contact</a></li>
        </ul>
      </nav>
    </header>
    <main>
      <article>
        <h2>Article Title</h2>
        <p>This is the main content of the article.</p>
      </article>
      <aside>
        <h3>Related Links</h3>
        <ul>
          <li><a href="#link1">Link 1</a></li>
          <li><a href="#link2">Link 2</a></li>
        </ul>
      </aside>
    </main>
    <footer>
      <p>&copy; 2024 Example Website</p>
    </footer>
  </body>
</html>
```

</details>
<details>
<summary>
<h3>4. What are attribute</h3>
</summary>

Attributes in HTML are additional information provided within an HTML tag that helps define the properties and behaviors of an element. Attributes are always specified in the opening tag and are written as name-value pairs. They provide details about an element that are not considered content, such as its identity, appearance, or functionality.

**Key Points about Attributes**

1.  Structure:

    - An attribute consists of a name and a value, separated by an equals sign (=). The value is enclosed in double quotes (") or single quotes ('), though double quotes are more commonly used.
    - Example:` <img src="image.jpg" alt="Description">`
    - Here, src and alt are attribute names, and "image.jpg" and "Description" are their respective values.

1.  Common Attributes:

        - id: Specifies a unique identifier for an element. Example: `<div id="header">`.
        - class: Defines one or more class names for an element, which can be used to style the element with CSS. Example: `<p class="intro">`.
        - style: Contains inline CSS styles for the element.    - Example: `<h1 style="color: blue;">`.
        - src: Specifies the source file for media elements like images, videos, and audio. Example: `<img src="image.jpg">`.
        - href: Provides the URL for a link in an <a> tag. Example: `<a href="https://example.com">`Visit Example</a>.
        - alt: Provides alternative text for images, used by screen readers and when the image cannot be displayed. Example:` <img src="image.jpg" alt="A description of the image">.`
        - title: Provides additional information about an element, often shown as a tooltip when the mouse hovers over the    - element. Example: `<p title="Tooltip text">Hover over me!</p>.`

    data- attributes\*: Used to store custom data private to the page or application. They are prefixed with data- and can hold any information. Example: `<div data-user-id="12345">.`

1.  Boolean Attributes:

    - Some attributes do not require a value and are considered "boolean attributes." These attributes are either present or absent, and their presence typically represents a true value.
    - Example: `<input type="checkbox" checked>` (The checked attribute is a boolean attribute indicating that the checkbox should be initially checked).

1.  Global Attributes:

    - These attributes can be used on any HTML element. Examples include class, id, style, title, and lang.

1.  Specificity and Overriding:

    - Attributes can override other settings. For instance, an inline style attribute (using the style attribute) will override styles defined in external or internal CSS.

Example

Here's an example demonstrating the use of various attributes:

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Attribute Example</title>
  </head>
  <body>
    <header id="main-header" class="header">
      <h1>Welcome to My Website</h1>
      <nav>
        <ul>
          <li><a href="#home" title="Go to Home">Home</a></li>
          <li><a href="#about" title="Learn more about us">About</a></li>
          <li><a href="#contact" title="Contact us">Contact</a></li>
        </ul>
      </nav>
    </header>
    <main>
      <section>
        <h2>About Us</h2>
        <p>We are a company that values excellence...</p>
        <img src="company-logo.png" alt="Company Logo" width="200" />
      </section>
    </main>
    <footer>
      <p>&copy; 2024 My Website</p>
    </footer>
  </body>
</html>
```

In this example:

- The `id` attribute is used for the header (`id="main-header"`), making it uniquely identifiable.
- The `class` attribute is used for styling purposes (`class="header"`).
- The `src` attribute specifies the source of the image (`src="company-logo.png"`).
- The `alt` attribute provides alternative text for the image (`alt="Company Logo"`).
- The `href` and `title` attributes in the `<a> `tags specify the destination URL and additional information shown as tooltips, respectively.

</details>
<details>
<summary>
<h3></h3>
</summary>
</details>
<details>
<summary>
<h3></h3>
</summary>
</details>
