# HTML NOTES

# **Chapter 1: Hello World**

### **Introduction to HTML**

- **HTML (HyperText Markup Language)** is a **markup language**, _not a programming language_.
- It defines the **structure and meaning (semantics)** of content on a webpage, not how it looks.

  - The **appearance** is controlled by **CSS (Cascading Style Sheets)**.

- Older styling tags (like `<font>`) are **obsolete** and should not be used.

### **HTML Elements and Tags**

- **Elements** describe content and provide meaning to the browser and search engines.
- An element usually has:

  ```html
  <element_name>...content...</element_name>
  ```

- **Tags** are the parts inside the angle brackets (`<>`), e.g. `<p>` or `</p>`.
- **Difference:**

  - **Elements:** video, audio, table, footer
  - **Tags:** `<video>`, `<audio>`, `<table>`, `</footer>`

### **Void Elements**

- Some elements don’t have closing tags or content.
- Examples: `<img>`, `<meta>`, `<link>`, `<input>`.

### **Example: The `<p>` Element**

- The `<p>` tag defines a **paragraph**.
- Syntax:

  ```html
  <p>This is a simple paragraph.</p>
  ```

- The **opening tag** is `<p>` and the **closing tag** is `</p>`.

### **Creating a Simple HTML Page**

#### Example:

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <title>Hello!</title>
  </head>
  <body>
    <h1>Hello World!</h1>
    <p>This is a simple paragraph.</p>
  </body>
</html>
```

#### File Info:

- Save with `.html` or `.htm` extension.
- Open in any web browser to view.

### **Page Breakdown**

| **Tag**                  | **Meaning / Function**                                                |
| ------------------------ | --------------------------------------------------------------------- |
| `<!DOCTYPE>`             | Declares the document type and HTML version (HTML5 here).             |
| `<html lang="en">`       | Wraps the entire HTML page; `lang` defines language (English = `en`). |
| `<head>`                 | Contains **metadata** and external links (not visible on page).       |
| `<meta charset="UTF-8">` | Defines character encoding (UTF-8 recommended).                       |
| `<title>`                | Defines the **page title** (appears on browser tab).                  |
| `<body>`                 | Contains all **visible content** shown to users.                      |
| `<h1>`                   | Heading level 1 – typically the main title of the page.               |
| `<p>`                    | Defines a paragraph of text.                                          |

---

# **Chapter 2: Doctypes**

### **What is a Doctype?**

- **Doctype** = short for **“Document Type Declaration.”**
- It tells the **browser which version of HTML** the document uses.
- Helps browsers **interpret and render** the page correctly.
- **Not** an HTML tag - it must appear **before** the `<html>` tag, at the **very top** of the document.

### **Section 2.1: Adding the Doctype**

- Always include a **doctype declaration** at the start of your HTML file.
- Example:

  ```html
  <!DOCTYPE html>
  ```

- Placed **before** `<html>`.
- This declaration informs the browser that the page follows **HTML5 standards**.

### **Section 2.2: HTML5 Doctype**

- **HTML5** is **not based on SGML (Standard Generalized Markup Language)**.

  - Therefore, **no DTD (Document Type Definition)** reference is required.

- The **simplified HTML5 Doctype**:

  ```html
  <!DOCTYPE html>
  ```

- This version works across all modern browsers and is **backward compatible**.

### **Case Insensitivity**

- The HTML5 doctype is **case-insensitive**, meaning different letter cases still work.
- All the following are **valid**:

  ```html
  <!DOCTYPE html>
  <!DOCTYPE html>
  <!DOCTYPE html>
  <!DOCTYPE html>
  ```

- However, the **recommended and standard** form is:

  ```html
  <!DOCTYPE html>
  ```

---

# **Chapter 3: Headings**

### **Introduction**

- HTML provides **six heading tags** to define titles and subtitles of different importance.
- These are **`<h1>` to `<h6>`**, where:

  - `<h1>` = **largest / most important heading**
  - `<h6>` = **smallest / least important heading**

- Headings help structure content and improve readability and SEO (search engine optimization).

### **Section 3.1: Using Headings**

- Headings are defined using tags:

  ```html
  <h1>Heading 1</h1>
  <h2>Heading 2</h2>
  <h3>Heading 3</h3>
  <h4>Heading 4</h4>
  <h5>Heading 5</h5>
  <h6>Heading 6</h6>
  ```

- All heading tags support **global attributes** (like `id`, `class`, `style`, etc.).

### **Importance of Correct Structure**

- Headings are **semantic elements** - they describe document hierarchy and structure.
- Search engines and assistive technologies (like screen readers) use headings to:

  - Understand page organization
  - Build **tables of contents**
  - Improve **SEO** and accessibility

### **Proper Heading Hierarchy**

- Use headings in **logical order**, not just for visual size.
- **General rule:**

  - Each page or article should have **only one `<h1>`** (main title).
  - Use **`<h2>`** for main sections, and **`<h3>`** (and beyond) for subsections.
  - Don’t skip heading levels or use `<h1>` for subtopics.

#### **Example of Proper Structure:**

```html
<h1>Main title</h1>
<p>Introduction</p>

<h2>Reasons</h2>

<h3>Reason 1</h3>
<p>Paragraph</p>

<h3>Reason 2</h3>
<p>Paragraph</p>

<h2>In conclusion</h2>
<p>Paragraph</p>
```

**Hierarchy explanation:**

- `<h1>` → Page title
- `<h2>` → Major sections
- `<h3>` → Subsections within `<h2>`

---

# **Chapter 4: Paragraphs**

### **Introduction**

- Paragraphs are among the **most basic and commonly used elements** in HTML.
- They define blocks of text content and are automatically separated by **blank lines (margins)** in browsers.
- Related tags:

  | Tag     | Description                                                      |
  | ------- | ---------------------------------------------------------------- |
  | `<p>`   | Defines a paragraph                                              |
  | `<br>`  | Inserts a **single line break**                                  |
  | `<pre>` | Defines **preformatted text** (preserves spaces and line breaks) |

### **Section 4.1: HTML Paragraphs**

- A paragraph is created using the `<p>` tag.

  ```html
  <p>This is a paragraph.</p>
  <p>This is another paragraph.</p>
  ```

- Each `<p>` tag creates a **new block of text**, separated from others automatically.

### **Display Behavior**

- HTML is **not whitespace-sensitive**.

  - Multiple spaces, tabs, or line breaks in the code are **collapsed into a single space** by the browser.

- The **display result** depends on screen size, browser, and window resizing HTML automatically adjusts.

**Example:**

```html
<p>This is another paragraph, extra spaces will be removed by browsers</p>
```

✅ **Displayed as:**

> This is another paragraph, extra spaces will be removed by browsers

---

# **Chapter 5: Text Formatting**

### **Introduction**

- HTML provides **inline formatting tags** to style specific portions of text.
- These tags help highlight, emphasize, or annotate text **semantically** (meaningfully) not just visually.
- Common formatting includes: **highlighting**, **bold**, **italic**, **underline**, **abbreviations**, **insertions/deletions**, **subscript**, and **superscript**.

## **Section 5.1: Highlighting**

- The `<mark>` element (introduced in **HTML5**) highlights text that is relevant or important in another context.
- Common use case: **search result highlighting**.

**Example:**

```html
<p>
  Here is some content that contains the <mark>searched query</mark> we are
  looking for.
</p>
```

**Default Output:**

> Black text on a **yellow background** (can be styled using CSS).

**Use Case:**
Highlighting search terms, key words, or relevant references.

## **Section 5.2: Bold, Italic, and Underline**

### **Bold Text**

Use either:

```html
<strong>Bold Text Here</strong>
```

or

```html
<b>Bold Text Here</b>
```

**Difference:**

- `<strong>` → Indicates **semantic importance** (content meaningfully important).
- `<b>` → Purely **visual bolding**, no semantic value.

  _Example of difference:_

- `<strong>`: Screen readers emphasize tone for importance.
- `<b>`: Only visual styling change.

### **Italic Text**

Use either:

```html
<em>Italicized Text Here</em>
```

or

```html
<i>Italicized Text Here</i>
```

**Difference:**

- `<em>` → Adds **emphasis** or stress to words (semantic meaning).
- `<i>` → Used for **stylistic differentiation**, like book titles or foreign words.

**Examples:**

```html
<em>Would you just submit the edit already?</em>
<!-- Emphasized action -->
<i>I was forced to read Romeo and Juliet in high school.</i>
<!-- Title -->
```

### **Underlined Text**

```html
<p>This paragraph contains some <u>mispelled</u> text.</p>
```

- `<u>` was **deprecated in HTML4** but **reintroduced in HTML5** with new meaning:
  → Used for **non-textual annotations** (e.g., misspellings or proper name marks).
- Should not be used for stylistic underlines (CSS preferred instead).

## **Section 5.3: Abbreviation**

- The `<abbr>` tag defines an **abbreviation or acronym**.
- The `title` attribute provides the **full form** of the abbreviation when hovered.

**Example:**

```html
<p>I like to write <abbr title="Hypertext Markup Language">HTML</abbr>!</p>
```

_Output Tip:_ Hovering over “HTML” shows the full text “Hypertext Markup Language.”

## **Section 5.4: Inserted, Deleted, or Stricken Text**

| **Purpose**   | **Tag** | **Example**                       |
| ------------- | ------- | --------------------------------- |
| Inserted Text | `<ins>` | `<ins>New Text</ins>`             |
| Deleted Text  | `<del>` | `<del>Deleted Text</del>`         |
| Strikethrough | `<s>`   | `<s>Struck-through text here</s>` |

**Usage:**

- `<ins>` and `<del>` indicate document edits or revisions.
- `<s>` is for content that is **no longer accurate or relevant** (stylistic, not semantic).

## **Section 5.5: Superscript and Subscript**

- Used to display text slightly **above** or **below** the normal line.

**Superscript (`<sup>`) Example:**

```html
<p>10<sup>2</sup> = 100</p>
```

**Output:** 10² = 100

**Subscript (`<sub>`) Example:**

```html
<p>H<sub>2</sub>O</p>
```

**Output:** H₂O

_Use Cases:_

- `<sup>` → exponents, ordinal indicators (e.g., 1st → 1<sup>st</sup>)
- `<sub>` → chemical formulas, footnotes, etc.

---

# **Chapter 6: Anchors and Hyperlinks**

### **Introduction**

- The **`<a>` tag (anchor element)** creates **hyperlinks** that connect one resource to another.
- Links can:

  - Open other web pages
  - Jump to a section within the same page
  - Launch apps (e.g., email, phone)
  - Trigger scripts or downloads

### **Common `<a>` Tag Attributes**

| **Attribute** | **Description / Usage**                                                                                                                                              |
| ------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `href`        | Specifies the **destination** (URL, path, or anchor ID). Can be: <br>→ **Absolute URL**: `http://example.com/` <br>→ **Relative URL**: `/about-us/` (same site path) |
| `hreflang`    | Defines the **language** of the linked resource (e.g., `en`, `fr`).                                                                                                  |
| `rel`         | Defines the **relationship** between the current document and the linked one (e.g., `external`, `noopener`, `noreferrer`).                                           |
| `target`      | Specifies **where to open the link**: <br>`_blank` = new tab/window <br>`_self` = same tab <br>`_parent`, `_top`, or specific frame (deprecated).                    |
| `title`       | Adds **tooltip text** when hovered. Can be used on most HTML tags.                                                                                                   |
| `download`    | Forces the link to **download** a file instead of opening it. Optional value sets the downloaded filename.                                                           |

## **Section 6.1: Link to Another Site**

**Basic Example:**

```html
<a href="http://example.com/">Link to example.com</a>
```

Displays as a clickable hyperlink.

**External link example:**

```html
<a href="http://example.com/" rel="external">example site</a>
```

**FTP link example:**

```html
<a href="ftp://example.com/">This could be a link to an FTP site</a>
```

→ Uses the **File Transfer Protocol (FTP)** instead of HTTP.

## **Section 6.2: Link to an Anchor (Bookmark Links)**

- You can **jump to specific sections** on a page by linking to elements with an **`id` attribute**.

**Example:**

```html
<h2 id="Topic1">First topic</h2>
<p>Content about the first topic</p>

<a href="#Topic1">Go to First Topic</a>
```

Clicking the link scrolls to the element with `id="Topic1"`.

**Table of Contents Example:**

```html
<h1>Table of Contents</h1>
<a href="#Topic1">First Topic</a>
<a href="#Topic2">Second Topic</a>
```

**Cross-page link example:**

```html
<a href="page1.html#Topic1">Look back in the First Topic</a>
```

## **Section 6.3: Link to a Page on the Same Site**

Use **relative paths** for internal links.

**Example:**

```html
<a href="/example">Text Here</a>
```

Both examples below go to the same page:

```html
<a href="/page">Text Here</a> <a href="http://example.com/page">Text Here</a>
```

## **Section 6.4: Link That Dials a Number**

**Example:**

```html
<a href="tel:11234567890">Call us</a>
```

- Works on **mobile devices** and apps like **Skype** or **FaceTime**.
- Prompts the user before dialing.

## **Section 6.5: Open Link in New Tab/Window**

**Example:**

```html
<a href="example.com" target="_blank">Text Here</a>
```

- Opens the link in a **new tab** or **window**.

  **Security Warning:**

- Using `target="_blank"` gives the new page **access to your `window.opener` object** - a potential **phishing risk**.
- Always add:

  ```html
  rel="noopener noreferrer"
  ```

  Prevents malicious access and ensures safety.

## **Section 6.6: Link That Runs JavaScript**

**Example 1: Using JavaScript protocol**

```html
<a href="javascript:myFunction();">Run Code</a>
```

**Example 2: Using onclick event**

```html
<a href="#" onclick="myFunction(); return false;">Run Code</a>
```

**Alternative (avoid scrolling):**

```html
<a href="#!" onclick="myFunction();">Run Code</a>
```

**Best Practice:**

- Avoid inline JavaScript.
- Instead, bind functions in **external JavaScript files** using event listeners.
- If it’s meant to perform an action (not navigation), consider using a `<button>` instead.

## **Section 6.7: Link That Runs Email Client**

**Basic Example:**

```html
<a href="mailto:example@example.com">Send email</a>
```

Opens the user’s default email client with the **recipient** pre-filled.

**Add CC and BCC:**

```html
<a href="mailto:example@example.com?cc=john@example.com&bcc=jane@example.com"
  >Send email</a
>
```

**Add Subject and Body:**

```html
<a href="mailto:example@example.com?subject=Example+subject&body=Message+text"
  >Send email</a
>
```

_Tip:_ Use **URL encoding** (`+` for spaces, `%0A` for new lines).

---

# **Chapter 7: Lists**

HTML provides **three types of lists**:

1. **Ordered Lists (`<ol>`)** –> numbered, where order _matters_.
2. **Unordered Lists (`<ul>`)** –> bulleted, where order _does not matter_.
3. **Description Lists (`<dl>`)** –> term–description pairs.

## **Section 7.1: Ordered List (`<ol>`)**

### Basic Structure

```html
<ol>
  <li>Item</li>
  <li>Another Item</li>
  <li>Yet Another Item</li>
</ol>
```

**Output:**

1. Item
2. Another Item
3. Yet Another Item

## **Customizing Numbers**

### **1. Start at a specific number**

Use the **`start`** attribute:

```html
<ol start="3">
  <li>Item</li>
  <li>Some Other Item</li>
  <li>Yet Another Item</li>
</ol>
```

→ Produces **3, 4, 5**

### **2. Set a specific value for any list item**

Use the **`value`** attribute:

```html
<li value="7">This starts at 7</li>
```

This affects subsequent numbering:

```html
<ol start="5">
  <li>Item</li>
  <!-- 5 -->
  <li>Some Other Item</li>
  <!-- 6 -->
  <li value="4">Reset</li>
  <!-- 4 -->
  <li>Another Item</li>
  <!-- 5 -->
  <li>Yet Another Item</li>
  <!-- 6 -->
</ol>
```

## **Reversed Numbering (HTML5+)**

```html
<ol reversed>
  <li>Item</li>
  <li>Some Other Item</li>
  <li value="4">Reset</li>
</ol>
```

List counts **downwards**.

## **Change Number Style (`type` attribute)**

| Value | Style             | Example    |
| ----- | ----------------- | ---------- |
| `1`   | Decimal (default) | 1, 2, 3    |
| `a`   | Lowercase letters | a, b, c    |
| `A`   | Uppercase letters | A, B, C    |
| `i`   | Lowercase Roman   | i, ii, iii |
| `I`   | Uppercase Roman   | I, II, III |

Example:

```html
<ol type="A">
  <li>Item</li>
  <li>Next</li>
</ol>
```

## When to Use `<ol>`

Use ordered lists when **sequence or ranking matters**.
If order **does not matter**, use `<ul>` instead.

## **Section 7.2: Unordered List (`<ul>`)**

### Basic Structure

```html
<ul>
  <li>Item</li>
  <li>Another Item</li>
  <li>Yet Another Item</li>
</ul>
```

**Output:** Bulleted list

- Item
- Another Item
- Yet Another Item

### When to Use `<ul>`

Use unordered lists when **order is irrelevant**.

## **Section 7.3: Nested Lists**

Lists can be nested to represent sub-items.

### Nested `<ul>` inside `<ul>`

```html
<ul>
  <li>item 1</li>
  <li>
    item 2
    <ul>
      <li>sub-item 2.1</li>
      <li>sub-item 2.2</li>
    </ul>
  </li>
  <li>item 3</li>
</ul>
```

### Mix list types

```html
<ol>
  <li>Hello, list!</li>
  <li>
    <ul>
      <li>Hello, nested list!</li>
    </ul>
  </li>
</ol>
```

**Important:** The nested list must be **inside** an `<li>` element.

## **Section 7.4: Description List (`<dl>`)**

Description lists consist of:

- **`<dt>`** → Term / name
- **`<dd>`** → Description / value

### Basic Structure

```html
<dl>
  <dt>name 1</dt>
  <dd>value for 1</dd>
  <dt>name 2</dt>
  <dd>value for 2</dd>
</dl>
```

### Multiple names or values

```html
<dl>
  <dt>name 1</dt>
  <dt>name 2</dt>
  <dd>value for 1 and 2</dd>

  <dt>name 3</dt>
  <dd>value for 3</dd>
  <dd>value for 3</dd>
</dl>
```

Useful for:

- Glossaries
- FAQs
- Name–value pairs
- Metadata lists

---

# **Chapter 8: Tables**

HTML tables allow developers to present **tabular data** (text, images, links, etc.) in **rows** and **columns** using the `<table>` element.

## **Section 8.1: Simple Table**

### Basic Structure

```html
<table>
  <tr>
    <th>Heading 1/Column 1</th>
    <th>Heading 2/Column 2</th>
  </tr>
  <tr>
    <td>Row 1 Data Column 1</td>
    <td>Row 1 Data Column 2</td>
  </tr>
  <tr>
    <td>Row 2 Data Column 1</td>
    <td>Row 2 Data Column 2</td>
  </tr>
</table>
```

### Key Elements

- **`<tr>`** → Table row
- **`<th>`** → Header cell (bold & centered by default)
- **`<td>`** → Data cell

You can place **any HTML content** inside `<td>` or `<th>`.

## **Section 8.2: Spanning Columns & Rows**

Use:

- **`colspan`** → span across multiple columns
- **`rowspan`** → span across multiple rows

### Example:

```html
<table>
  <tr>
    <td>row 1 col 1</td>
    <td>row 1 col 2</td>
    <td>row 1 col 3</td>
  </tr>
  <tr>
    <td colspan="3">This second row spans all three columns</td>
  </tr>
  <tr>
    <td rowspan="2">This cell spans two rows</td>
    <td>row 3 col 2</td>
    <td>row 3 col 3</td>
  </tr>
  <tr>
    <td>row 4 col 2</td>
    <td>row 4 col 3</td>
  </tr>
</table>
```

### Notes

- Avoid overlapping column and row spans → **invalid HTML**.
- **Rowspan:**

  - Default: `1`
  - `0` = span to the last row of section

- **Colspan:**

  - Default: `1`
  - `0` = span to last column of the `<colgroup>`

## **Section 8.3: Column Groups**

Use `<colgroup>` and `<col>` to apply styling or structure to columns.

### `<colgroup>`

Groups one or more columns.

```html
<table>
  <colgroup span="2"></colgroup>
  <colgroup span="2"></colgroup>
</table>
```

### `<col>`

Targets individual columns.

```html
<table>
  <colgroup>
    <col id="MySpecialColumn" />
    <col />
  </colgroup>
  <colgroup>
    <col class="CoolColumn" />
    <col class="NeatColumn" span="2" />
  </colgroup>
</table>
```

### Allowed CSS properties on `<colgroup>` & `<col>`

- `border`
- `background`
- `width`
- `visibility`
- `display` (including `display: none` to hide a column)

## **Section 8.4: Table with thead, tbody, tfoot, caption**

HTML tables can include semantic groupings:

| Element     | Purpose                                                             |
| ----------- | ------------------------------------------------------------------- |
| `<caption>` | Table title (first child of `<table>`)                              |
| `<thead>`   | Header group                                                        |
| `<tbody>`   | Body group                                                          |
| `<tfoot>`   | Footer group (displayed at bottom even if placed earlier in markup) |

### Example:

```html
<table>
  <caption>
    Table Title
  </caption>

  <thead>
    <tr>
      <th>Header content 1</th>
      <th>Header content 2</th>
    </tr>
  </thead>

  <tbody>
    <tr>
      <td>Body content 1</td>
      <td>Body content 2</td>
    </tr>
  </tbody>

  <tfoot>
    <tr>
      <td>Footer content 1</td>
      <td>Footer content 2</td>
    </tr>
  </tfoot>
</table>
```

### Behavior

- Browsers **repeat `<thead>`** when printing large tables across multiple pages.
- `<tfoot>` can be placed **before or after** `<tbody>` but always renders **last**.

### Example Style Effects (Summary)

| Element     | Style Behavior Example         |
| ----------- | ------------------------------ |
| `<caption>` | Yellow text / black background |
| `<thead>`   | Bold text, purple background   |
| `<tbody>`   | Blue background                |
| `<tfoot>`   | Green background               |
| `<th>`      | Orange borders                 |
| `<td>`      | Red borders                    |

_(These are just illustrative examples.)_

## **Section 8.5: Heading Scope**

Use `scope` on `<th>` to improve **accessibility** and help screen readers.

### Example:

```html
<table>
  <thead>
    <tr>
      <td></td>
      <th scope="col">Column Heading 1</th>
      <th scope="col">Column Heading 2</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th scope="row">Row Heading 1</th>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <th scope="row">Row Heading 2</th>
      <td></td>
      <td></td>
    </tr>
  </tbody>
</table>
```

### Valid scope values:

- `col` → header for a column
- `row` → header for a row
- `colgroup` → header for a group of columns
- `rowgroup` → header for a group of rows

---

# **Chapter 9: Comments**

HTML comments allow developers to include **notes, explanations, or temporarily disabled code** inside HTML without affecting what the user sees.

## **Section 9.1: Creating Comments**

### Basic Syntax

```html
<!-- This is a comment -->
```

- Everything between `<!--` and `-->` is **ignored by the browser**.
- Comments are useful for **developer notes**, reminders, explanations, or temporarily removing code from rendering.

## Inline Comments

```html
<h1>
  This part shows
  <!-- and this part does not -->.
</h1>
```

Comments inside text **do not display**, but are allowed between elements.

## Multiline Comments

```html
<!-- 
This is a multiline comment.
Everything inside is ignored by the browser.
You can comment out entire sections.
-->
```

## **Invalid Comment Placement**

Comments **cannot appear inside an HTML tag’s opening tag**.

Example (INVALID):

```html
<h1 <!-- testAttribute="something" -->>This will not work</h1>
```

Why?

- The browser treats this as a single corrupted `<h1>` tag, causing **invalid HTML**.

## Comment Body Restriction

For compatibility with XML/SGML-based parsers:

- **Do NOT include `--` inside a comment**, like:

  ```html
  <!-- This is invalid -- because of two dashes -->
  ```

## **Section 9.2: Commenting Out Whitespace Between Inline Elements**

Inline elements (like `<a>`, `<span>`, `<button>`) naturally include **one whitespace character** around them if separated by line breaks in HTML.

This can accidentally cause **spacing in layout**.

### Solution: Comment Out Newline Whitespace

```html
<a href="#">No extra space after this!</a
><!--
--><button>Foo</button>
```

- The comment “swallows” the newline so no extra space appears between the inline elements.

## Example Comparison

### With whitespace removed (using comment):

```html
<a href="#">I hope there will be no extra whitespace after this!</a
><!--
--><button>Foo</button>
```

### Without the comment:

```html
<a href="#">I hope there will be no extra whitespace after this!</a>
<button>Foo</button>
```

❗ You’ll notice a _small space_ between the link and the button in the second version.

---

# **Chapter 10: Classes and IDs**

Classes and IDs are **HTML attributes** used to uniquely or non-uniquely identify elements so they can be targeted by **CSS**, **JavaScript**, and **HTML anchors**.

| Attribute | Meaning                                 | Uniqueness         |
| --------- | --------------------------------------- | ------------------ |
| **class** | A label applied to one or more elements | **Not unique**     |
| **id**    | A unique identifier for one element     | **Must be unique** |

## **Section 10.1: Giving an Element a Class**

### Assigning a Class

```html
<div class="example-class"></div>
```

### Multiple Classes

```html
<div class="class1 class2"></div>
```

### Using Classes in CSS

Classes are used for **styling**, **selecting**, and **targeting groups of elements**.

### Example:

```html
<span></span> <span class="special"></span>
```

**CSS:**

```css
.special {
  color: red;
}
```

All elements with class `special` will receive this styling.

## Targeting Specific Elements

### Without element specificity:

```css
.highlight {
  color: green;
}
```

Affects _all_ elements with class `highlight`.

### With element specificity:

```css
div.highlight {
  color: green;
}
```

Affects only `<div>` elements with class `highlight`.

## Nesting Classes (Combinators)

```css
.main .highlight {
  color: red;
} /* descendant selector */
.footer > .highlight {
  color: blue;
} /* direct child selector */
```

## Chaining Classes

Target elements that have **all** specified classes.

**HTML:**

```html
<div class="special left menu">This text will be pink</div>
```

**CSS:**

```css
.special.left.menu {
  color: pink;
}
```

## **Section 10.2: Giving an Element an ID**

IDs uniquely identify a specific element in the document.

### Example:

```html
<div id="example-id"></div>
```

### Invalid Example (Duplicate ID):

```html
<div id="example-id"></div>
<span id="example-id"></span>
```

Duplicated IDs create **unpredictable behavior**.

## Using IDs in CSS

```css
#example-id {
  color: green;
}
```

## Linking to an Element with Its ID (Anchors)

```html
<a href="#example-id">Jump to the element</a>
```

Or directly from a URL:

```
http://example.com/about#example-id
```

## **Section 10.3: Acceptable Values for ID and Class**

## HTML5 Rules for IDs

Allowed as long as:

1. Unique in the document
2. No spaces
3. Contains at least one character

### Valid HTML5 IDs:

```html
<div id="999"></div>
<div id="♥"></div>
<div id="⌘⌥"></div>
<div id="sample.text"></div>
<div id="#%LV-||"></div>
```

### Invalid:

```html
<div id=" "></div>
<!-- whitespace -->
```

```html
<div id="results"></div>
<div id="results"></div>
<!-- duplicate -->
```

## HTML 4.01 Rules (Stricter)

ID **must start with a letter**, then may include:

- letters
- digits
- hyphens `-`
- underscores `_`
- colons `:`
- periods `.`

### Examples of **valid HTML 4.01** IDs:

```html
<div id="sample-text"></div>
<div id="sample_text"></div>
<div id="sample.text"></div>
<div id="sample:text"></div>
```

### Invalid in HTML 4.01:

```html
<div id="9lions"></div>
<!-- starts with digit -->
```

#### ⚠️ Important Note: CSS & JavaScript Restrictions

Even though HTML5 allows almost anything in IDs/classes, **CSS and JS have different rules**.

### Invalid in CSS:

```css
#9lions {
  color: red;
}
```

Because CSS selectors **cannot start with a digit** unless escaped.

## **Section 10.4: Problems Related to Duplicated IDs**

Having more than one element with the same ID leads to **hard-to-debug issues**.

### Example:

```html
<div id="aDiv">a</div>
<div id="aDiv">b</div>
```

### CSS behavior

```css
#aDiv {
  color: red;
}
```

Both elements may receive the styling.

### JavaScript behavior

```javascript
var html = document.getElementById("aDiv").innerHTML;
```

Will return **only the first matching element** (“a”).

This breaks scripts and causes unpredictable UI problems.

---

# **Chapter 11: Data Attributes**

HTML5 introduced **data attributes** as a simple way to store **custom data** inside HTML elements.
They are written as:

```
data-*="somevalue"
```

Where **`*`** is any name you choose, and the value is always a **string**.

## **Section 11.1: Older Browsers Support**

### Key Point

Older browsers (pre-HTML5) do **not recognize** `data-*` attributes but they **ignore unknown attributes**, which makes them safe to use.

### Why They Still Work

- According to HTML specs, browsers must **ignore unrecognized attributes**, not break.
- Example of a **non-standard attribute** (not part of HTML spec):

```html
<img src="sample.jpg" value="test" />
```

- Even though `<img>` doesn’t have a `value` attribute, the browser:

  - Renders the image normally
  - Ignores the extra attribute
  - Still allows JavaScript to access it using:

    - `.getAttribute()`
    - `.setAttribute()`

### BUT…

Older browsers **cannot use the `.dataset` property**, which is supported only in modern browsers.

## **Section 11.2: Data Attribute Use**

Data attributes allow you to store **custom data** directly in HTML elements.

### Example:

```html
<div data-submitted="yes" class="user_profile">… some content …</div>
```

### Structure

`data-` + **custom name**
Examples:

- `data-id`
- `data-user-name`
- `data-info`
- `data-json`

### Access via JavaScript

#### **1. Modern Browsers (HTML5+)**

```javascript
element.dataset.submitted;
element.dataset.userName;
```

#### **2. All Browsers (including old ones)**

```javascript
element.getAttribute("data-submitted");
element.setAttribute("data-submitted", "no");
```

### Data Attributes Can Store:

- Strings
- Numbers (as strings)
- Paths
- Flags
- Even JSON strings

Example:

```html
<div data-user='{"name":"John","age":30}'></div>
```

---

# **Chapter 12: Linking Resources**

Many assets such as **scripts**, **stylesheets**, **icons**, and **feeds** are best stored in external files and linked into HTML using the `<link>` and `<script>` elements.

Each linking tag may contain attributes that describe **how** and **when** the resource should be loaded.

## **Common `<link>` Attributes**

| Attribute       | Description                                                               |
| --------------- | ------------------------------------------------------------------------- |
| **charset**     | Character encoding of the linked document                                 |
| **crossorigin** | Controls cross-origin request behavior                                    |
| **href**        | The location (URL/path) of the linked resource                            |
| **hreflang**    | Language of the linked document                                           |
| **media**       | Media/device the resource is intended for (e.g., `print`, `screen`)       |
| **rel**         | Required relationship between the current and linked documents            |
| **rev**         | Reverse of `rel` (rarely used)                                            |
| **sizes**       | Only valid with icons size of linked icon file                            |
| **target**      | Where to load the linked document                                         |
| **type**        | MIME type of the linked document                                          |
| **integrity**   | Hash for verifying a resource’s authenticity (SRI: Subresource Integrity) |

## **Section 12.1: JavaScript**

### **Synchronous Loading**

```html
<script src="path/to.js"></script>
```

- Load scripts **just before `</body>`**
- Ensures HTML loads first
- Prevents JS from running on elements that aren’t ready yet

### **Asynchronous Loading (`async`)**

```html
<script src="path/to.js" async></script>
```

- Downloads **in parallel** with HTML
- Executes immediately when downloaded
- Can interrupt HTML parsing
- Use for scripts **not required for initial page rendering**

### **Deferred Loading (`defer`)**

```html
<script src="path/to.js" defer></script>
```

- Downloads in parallel
- Executes **after HTML is fully parsed**
- Keeps execution order (unlike `async`)
- Best practice for most modern JS

### **`<noscript>`**

```html
<noscript>JavaScript disabled</noscript>
```

- Displays content for users with:

  - JavaScript disabled
  - Browsers that don’t support JS

- Can go in `<head>` or `<body>`

## **Section 12.2: External CSS Stylesheet**

```html
<link rel="stylesheet" href="path/to.css" />
```

### Best Practice:

- Place in the **`<head>`** so CSS loads first and prevents “unstyled flash.”

### In HTML5:

```html
<link rel="stylesheet" href="path/to.css" type="text/css" />
```

The `type` attribute is **optional** since HTML5 defaults to CSS.

### CSS Alternative:

```html
<style>
  @import ("path/to.css");
</style>
```

Not preferred for performance loads slower.

## **Section 12.3: Favicon**

```html
<link rel="icon" type="image/png" href="/favicon.png" />
<link rel="shortcut icon" type="image/x-icon" href="/favicon.ico" />
```

Notes:

- A file named `favicon.ico` in the **root directory** is often loaded automatically.
- Browsers may aggressively **cache** favicons.

## **Section 12.4: Alternative CSS Stylesheets**

```html
<link rel="alternate stylesheet" href="path/to/style.css" title="yourTitle" />
```

- Allows user-selectable themes/styles.
- Supported by **Firefox** and **Internet Explorer** (requires UI toggle).
- Chrome needs an extension.

## **Section 12.5: Resource Hints (`dns-prefetch`, `preconnect`, `prefetch`, `prerender`)**

These help browsers optimize performance.

### **1. Preconnect**

```html
<link rel="preconnect" href="URL" />
```

- Resolves DNS
- Starts TCP handshake
- Begins optional TLS
- Experimental

### **2. DNS Prefetch**

```html
<link rel="dns-prefetch" href="URL" />
```

- Resolves DNS ahead of time
- Speeds up future requests

### **3. Prefetch**

```html
<link rel="prefetch" href="URL" />
```

- Fetches resources the browser **expects you’ll need soon**
- Example: next page content

### **4. Prerender**

```html
<link rel="prerender" href="URL" />
```

- Loads AND renders the page in the background
- Makes navigation to that URL instant
- Experimental and heavy on resources

## **Section 12.6: The `media` Attribute**

```html
<link rel="stylesheet" href="test.css" media="print" />
```

- Used to display specific styles for:

  - `print`
  - `screen`
  - `speech`
  - or complex media queries

Example:

```html
<link
  rel="stylesheet"
  href="responsive.css"
  media="screen and (max-width: 600px)"
/>
```

## **Section 12.7: Prev and Next**

Used to link series of pages/articles.

```html
<link rel="prev" href="previous-page.html" />
<link rel="next" href="next-page.html" />
```

Helps search engines and browsers navigate multi-page content.

## **Section 12.8: Web Feed (RSS / Atom)**

```html
<link
  rel="alternate"
  type="application/atom+xml"
  href="http://example.com/feed.xml"
/>
<link
  rel="alternate"
  type="application/rss+xml"
  href="http://example.com/feed.xml"
/>
```

Enables feed discovery for RSS/Atom readers.

---

# **Chapter 13: Include JavaScript Code in HTML**

HTML provides several ways to include and control JavaScript execution in a webpage.
JavaScript can be added **inline**, **linked externally**, or loaded using **async** and **defer** strategies.

## **Script Tag Attributes**

| Attribute       | Description                                                            |
| --------------- | ---------------------------------------------------------------------- |
| **src**         | Path (URL) to an external JavaScript file; can be relative or absolute |
| **type**        | MIME type of the script. Required in HTML4, **optional in HTML5**      |
| **async**       | Loads + executes script asynchronously (external scripts only)         |
| **defer**       | Loads script in background, executes **after HTML parsing**            |
| **charset**     | Character encoding for external script file (e.g., UTF-8)              |
| **crossorigin** | Controls cross-origin request behavior                                 |
| **nonce**       | Cryptographic nonce for Content Security Policy (CSP3)                 |

## **Section 13.1: Handling Disabled JavaScript**

Some browsers:

- do NOT support JavaScript
- have JavaScript manually **disabled** by the user (security or privacy reasons)

Use `<noscript>` to show fallback content:

### Example:

```html
<script>
  document.write("Hello, world!");
</script>

<noscript>This browser does not support Javascript.</noscript>
```

**What happens?**

- If JS is enabled → "Hello, world!" prints.
- If JS is disabled → the `<noscript>` message appears.

## **Section 13.2: Linking to an External JS File**

### Syntax

```html
<script src="example.js"></script>
```

- Works like an anchor `<a href="">` → accepts both **relative** and **absolute** URLs.
- Often placed in `<head>` or (best practice) **before `</body>`**.

## **Section 13.3: Directly Including JavaScript Code**

Instead of linking a separate file, JS can be embedded directly:

```html
<script>
  // Your JavaScript code here
</script>
```

This is useful for:

- Small scripts
- Quick test code
- Page-specific behavior

But for anything large, external `.js` files are recommended.

## **Section 13.4: Including JavaScript Asynchronously**

### Async Script Example

```html
<script type="text/javascript" src="URL" async></script>
```

### Behavior

- Script downloads **in parallel** with HTML.
- Executes immediately when downloaded.
- Does **not** guarantee execution order.
- Best for scripts NOT required for initial page rendering (e.g., ads, analytics).

---

# **Chapter 14: Using HTML with CSS**

CSS is used to **style HTML elements**, controlling appearance, layout, colors, spacing, and more.

There are **three main ways** to add CSS to HTML:

1. **External Stylesheets** (recommended)
2. **Internal Stylesheets**
3. **Inline Styles** (discouraged)

## **Section 14.1: External Stylesheet Use**

### Linking an External Stylesheet

Placed inside the `<head>`:

```html
<head>
  <link rel="stylesheet" type="text/css" href="stylesheet.css" />
</head>
```

### CDN Stylesheets (Example: Bootstrap)

```html
<head>
  <link
    rel="stylesheet"
    href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/css/bootstrap.min.css"
    integrity="sha384-BVYiiSIFeK1dGmJRAkycuHAHRg32OmUcww7on3RYdg4Va+PmSTsz/K68vbdEjh4u"
    crossorigin="anonymous"
  />
</head>
```

Benefits of External CSS:

- Clean separation of **content** (HTML) and **presentation** (CSS)
- Faster loading due to **browser caching**
- Reusability across multiple pages

## **Section 14.2: Internal Stylesheet**

CSS written within the HTML document using `<style>` inside `<head>`:

```html
<head>
  <style type="text/css">
    body {
      background-color: gray;
    }
  </style>
</head>
```

You can include **multiple** internal stylesheets:

```html
<head>
  <style>
    body {
      background-color: gray;
    }
  </style>

  <style>
    p {
      background-color: blue;
    }
  </style>
</head>
```

Use cases:

- Page-specific styling
- Quick prototyping
- Small or temporary style adjustments

## **Section 14.3: Inline Style**

Add CSS directly to an element using the `style` attribute:

```html
<span style="color: red">This text will appear in red.</span>
```

⚠️ **Avoid inline styles**

- Harder to maintain
- Breaks separation of concerns
- Overrides many CSS rules (high specificity)

Use only for:

- Quick demos
- One-off testing
- Dynamic JS-applied styles

## **Section 14.4: Multiple Stylesheets**

You can load **multiple external stylesheets**:

```html
<head>
  <link rel="stylesheet" href="general.css" />
  <link rel="stylesheet" href="specific.css" />
</head>
```

### CSS is Applied in Order

Later stylesheets override earlier ones.

Example:

**general.css**

```css
body {
  background-color: red;
}
```

**specific.css**

```css
body {
  background-color: blue;
}
```

Since `specific.css` is loaded last → **background becomes blue.**

---

# **Chapter 15: Images**

The `<img>` element is used to display images in HTML.
It is a **void element** (no closing tag).

## **Key Image Attributes**

| Attribute       | Purpose                                                                  |
| --------------- | ------------------------------------------------------------------------ |
| **src**         | URL/path of the image                                                    |
| **srcset**      | List of images for responsive behavior (different sizes/resolutions)     |
| **sizes**       | Defines how much viewport space the image takes at breakpoints           |
| **crossorigin** | Controls cross-origin requests                                           |
| **usemap**      | Connects the image to a client-side image map                            |
| **ismap**       | Declares image as a server-side image map                                |
| **alt**         | Alternative text shown when the image can't load; used by screen readers |
| **width**       | Width of image (optional)                                                |
| **height**      | Height of image (optional)                                               |

## **Section 15.1: Creating an Image**

Basic image syntax:

```html
<img src="images/hello.png" alt="Hello World" />
```

Using external URLs:

```html
<img src="https://i.stack.imgur.com/ALgZi.jpg" alt="User Caleb Kleveter" />
```

### Important Notes

- `<img>` **does not insert an image** it creates a **container** that displays an image.
- The image is **linked**, not “embedded,” unless using base64.

### Base64 Embedded:

```html
<img src="data:image/png;base64,iVBOR..." alt="Hello World" />
```

### Link an image:

Wrap `<img>` in `<a>`:

```html
<a href="page.html">
  <img src="hello.png" alt="Hello" />
</a>
```

## **Section 15.2: Choosing Good `alt` Text**

Alt text is used by:

- Screen readers
- Search engines
- When image fails to load

### Incorrect Example:

```html
<img src="anonymous.png" alt="Anonymous user avatar" /> An anonymous user wrote:
<blockquote>Lorem ipsum dolor sed.</blockquote>

<a><img src="edit.png" alt="Edit icon" /></a> /
<a><img src="delete.png" alt="Delete icon" /></a>
```

Output (if images fail):

```
Anonymous user avatar An anonymous user wrote:
Lorem ipsum dolor sed.
Edit icon / Delete icon
```

This is confusing.

### Corrected Version:

```html
<img src="anonymous.png" alt="" /> An anonymous user wrote:
<blockquote>Lorem ipsum dolor sed.</blockquote>

<a><img src="edit.png" alt="Edit" /></a> /
<a><img src="delete.png" alt="Delete" /></a>
```

### Rules for Good `alt` Text:

- **If image adds no meaning**, use: `alt=""`
- **If image is functional**, alt text should describe **action**, not “icon”
- **Never omit `alt` entirely**, this signals a key missing text alternative.

## **Section 15.3: Responsive Images Using `srcset` and `sizes`**

Responsive images help optimize:

- performance
- clarity
- bandwidth usage

### Using `srcset` with `sizes` (width-based)

```html
<img
  sizes="(min-width: 1200px) 580px,
         (min-width: 640px) 48vw,
         98vw"
  srcset="
    img/hello-300.jpg   300w,
    img/hello-600.jpg   600w,
    img/hello-900.jpg   900w,
    img/hello-1200.jpg 1200w
  "
  src="img/hello-900.jpg"
  alt="hello"
/>
```

#### How it works:

- **sizes:** describes how much viewport width the image will occupy
- **srcset:** describes available image widths
- Browser picks best image depending on:

  - viewport width
  - pixel density
  - device capabilities

#### Example Behavior:

- > 1200px → use 580px version
- 640–1200px → use 48% of screen width
- <640px → use 98% of screen width

### Using `srcset` without `sizes` (pixel density based)

```html
<img
  src="img/hello-300.jpg"
  alt="hello"
  srcset="img/hello-300.jpg 1x, img/hello-600.jpg 2x, img/hello-1200.jpg 3x"
/>
```

Browser picks:

- 1x → normal displays
- 2x → Retina
- 3x → high-density screens

**`src` remains a required fallback.**

## **Section 15.4: Responsive Images Using `<picture>` Element**

Use `<picture>` to serve **different images** at different sizes or for different media types.

### Example:

```html
<picture>
  <source media="(min-width: 600px)" srcset="large_image.jpg" />
  <source media="(min-width: 450px)" srcset="small_image.jpg" />
  <img src="default_image.jpg" style="width:auto;" />
</picture>
```

### Behavior:

- > 600px → `large_image.jpg`
- > 450px → `small_image.jpg`
- otherwise → `default_image.jpg`

### Use cases:

- Art direction (change composition of image)
- Different crops for mobile vs desktop

---

# **Chapter 16: Image Maps**

Image maps allow you to create **clickable regions** inside an image each region can be a **link** or interactive area.

Image maps consist of three parts:

1. `<img>` —> the image
2. `usemap` —> links the image to the map
3. `<map>` with `<area>` —> defines clickable shapes

## **Key Tags & Attributes**

### `<img>` (image)

Image-map–related attributes:

| Attribute  | Purpose                                                                                              |
| ---------- | ---------------------------------------------------------------------------------------------------- |
| **usemap** | Connects the image to a `<map>` element. The value must start with `#`. Example: `usemap="#mapName"` |

Other normal `<img>` attributes (src, alt, width, etc.) still apply.

### `<map>` (map definition)

| Attribute | Purpose                                                        |
| --------- | -------------------------------------------------------------- |
| **name**  | Identifier for the map, used by the image’s `usemap` attribute |

Example:

```html
<map name="shapes"> … </map>
```

### `<area>` (clickable region)

Defines a **clickable zone** within the image.

### Main Attributes

| Attribute  | Purpose                                                      |
| ---------- | ------------------------------------------------------------ |
| **shape**  | Defines the shape: `rect`, `circle`, `poly`, or `default`    |
| **coords** | Coordinates for the clickable area (format changes by shape) |
| **href**   | URL to link to (optional)                                    |
| **alt**    | Alternate text (required if `href` is used)                  |

## **coords Attribute Format**

Depending on shape:

### 1. `rect` (rectangle)

Format:

```
left, top, right, bottom
```

### 2. `circle`

Format:

```
centerX, centerY, radius
```

### 3. `poly` (polygon)

Format:

```
x1, y1, x2, y2, x3, y3, ...
```

### 4. `default`

- Selects the entire image
- No `coords` needed

## **Section 16.1: Introduction to Image Maps**

An **image map** is an image with one or more clickable areas.

### Basic Structure

1. Add an `<img>` with a `usemap` attribute
2. Create a `<map>` with `name`
3. Add `<area>` tags to define regions

### **Basic Example**

### Image:

```html
<img
  src="http://jaced.com/blogpix/2007/trisquarecircle/002.gif"
  usemap="#shapes"
/>
```

### Map:

```html
<map name="shapes">
  <area shape="polygon" coords="79,6,5,134,153,134" />
  <area shape="rectangle" coords="177,6,306,134" />
  <area shape="circle" coords="397,71,65" />
</map>
```

### Explanation:

- First shape: triangle (polygon)
- Second shape: square/rectangle
- Third shape: circle

When you hover over these regions, your cursor changes to a pointer confirming interactivity.

---

# **Chapter 17: Input Control Elements**

The `<input>` element is a core part of HTML forms. It supports many types of user inputs (text, email, checkbox, file upload, date, color picker, etc.), each controlled by the `type` attribute.

### **Common `<input>` Attributes**

| Attribute        | Description                                                                                                       |
| ---------------- | ----------------------------------------------------------------------------------------------------------------- |
| **type**         | Defines the type of input control (text, password, email, checkbox, radio, file, date, etc.). Defaults to `text`. |
| **name**         | Name of the input; sent with form submission.                                                                     |
| **id**           | Unique identifier for the input.                                                                                  |
| **class**        | CSS class (not unique).                                                                                           |
| **value**        | Default value.                                                                                                    |
| **placeholder**  | Hint text shown when empty (HTML5).                                                                               |
| **autocomplete** | Browser autofill behavior.                                                                                        |
| **readonly**     | Prevents editing but still submits value.                                                                         |
| **disabled**     | Prevents editing **and** prevents submission.                                                                     |
| **required**     | Input must be filled before submitting.                                                                           |
| **checked**      | Sets default state for radio/checkbox.                                                                            |
| **multiple**     | Allows multiple values (email, file).                                                                             |
| **step**         | Legal numeric intervals for number/date/time types.                                                               |
| **autofocus**    | Field receives focus when page loads.                                                                             |
| **alt**          | Alternative text for image-type inputs.                                                                           |

## **Section Summaries**

## **17.1 - Text Input**

- Most basic input type (`type="text"`).
- Single-line only.
- Default width = 20 characters.
- `size` attribute controls visible width (but not max length).
- For multiple lines → use `<textarea>`.

## **17.2 - Checkbox & Radio**

### Checkbox

- Independent.
- Multiple can be selected.

### Radio button

- Mutually exclusive **within same name group**.

### Example:

```html
<input type="radio" name="color" value="red" />
```

### Labels

Always use `<label>`:

```html
<label><input type="radio" /> Red</label>
```

or

```html
<label for="red">Red</label> <input id="red" />
```

### Grouping controls

Use:

```html
<fieldset>
  <legend>Theme color:</legend>
</fieldset>
```

## **17.3 - Input Validation (HTML5)**

Validation occurs **on form submit** unless:

- input is `disabled` or `readonly`, or
- form has `novalidate`, or
- submit button uses `formnovalidate`.

### Validation Attributes

| Attribute                 | Purpose                              |
| ------------------------- | ------------------------------------ |
| `required`                | Must be completed                    |
| `minlength` / `maxlength` | Length rules                         |
| `min` / `max`             | Range for numbers, dates, times      |
| `pattern`                 | Regex validation                     |
| `accept`                  | Allowed file types (file input only) |

### Example:

```html
<input type="text" minlength="3" maxlength="10" required />
<input type="file" accept="image/*,.zip" />
<input pattern="\d*" title="Numbers only" />
```

## **17.4 - Color Input**

```html
<input type="color" value="#ff0000" />
```

- Opens OS color picker.
- Fallback: normal text input.

## **17.5 - Password**

```html
<input type="password" />
```

- Similar to text box but characters are hidden (masked).

## **17.6 - File Input**

```html
<input type="file" />
```

### Options:

- **multiple**
- **accept="image/\*"**
- Must use a form with:
  `enctype="multipart/form-data"` for upload.

## **17.7 - Button**

```html
<input type="button" value="Click" />
```

Used for JS actions.

Prefer `<button>` when you need HTML inside.

## **17.8 - Submit**

Triggers form submission.

```html
<input type="submit" /> <button type="submit">Submit</button>
```

## **17.9 - Reset**

Resets form fields to their default states.

```html
<input type="reset" />
```

## **17.10 - Hidden**

A hidden value that still submits.

```html
<input type="hidden" name="token" />
```

## **17.11 - Tel**

Telephone input (no automatic validation).

```html
<input type="tel" />
```

## **17.12 - Email**

Validates on submit in modern browsers.

```html
<input type="email" />
```

## **17.13 - Number**

```html
<input type="number" min="0" max="10" />
```

Allows numeric characters (but still needs validation server-side).

## **17.14 - Range**

A slider control.

```html
<input type="range" min="1" max="5" step="1" />
```

## **17.15 - Search**

Search field with OS/browser UI enhancements.

```html
<input type="search" />
```

## **17.16 - Image Button**

Acts like a submit button.

```html
<input type="image" src="submit.png" alt="Submit" />
```

## **17.17 - Week**

Select week of the year.

```html
<input type="week" />
```

## **17.18 - URL**

URL validation.

```html
<input type="url" />
```

## **17.19 - DateTime-Local**

Local date + time (no timezone).

```html
<input type="datetime-local" />
```

## **17.20 - Month**

Month picker.

```html
<input type="month" />
```

## **17.21 - Time**

Time picker (hours:minutes:seconds).

```html
<input type="time" />
```

## **17.22 - Global DateTime (deprecated)**

```html
<input type="datetime" />
```

Rarely supported; replaced by `datetime-local`.

## **17.23 - Date**

Date picker (not supported in older Firefox/IE).

```html
<input type="date" />
```

---

# **Chapter 18: Forms**

Forms allow users to input information and send it to a server.
A `<form>` element contains inputs and controls how the data is submitted.

### **Form Attributes**

| Attribute          | Description                                      |
| ------------------ | ------------------------------------------------ |
| **action**         | URL where form data is sent.                     |
| **method**         | HTTP method (`GET` or `POST`).                   |
| **enctype**        | How to encode data (important for file uploads). |
| **accept-charset** | Allowed character encodings (e.g., UTF-8).       |
| **autocomplete**   | Enables/disables browser autofill.               |
| **name**           | Optional identifier for a form.                  |
| **novalidate**     | Disables HTML5 validation.                       |
| **target**         | Where to display the server response.            |

## **Section 18.1: Submitting Forms**

### action

- Defines where data goes.
- If empty, submits to the **same page**.

```html
<form action="process.php"></form>
```

### method

Two allowed values:

### **GET**

- Appends form data to the URL.
- Used for search, filters, fetching data.
- Example result:

  ```
  page.php?firstname=Bob&lastname=Smith
  ```

### **POST**

- Sends data in the request body.
- Required for anything sensitive or large.
- Cleaner and safer than GET.

### Name is required for submission

```html
<input type="text" name="lastname" />
```

### Additional attributes example

```html
<form
  action="submit.php"
  method="post"
  target="_blank"
  accept-charset="UTF-8"
  enctype="application/x-www-form-urlencoded"
  autocomplete="off"
  novalidate
></form>
```

## **Section 18.2: The target Attribute**

Controls where the response appears.

| Value         | Meaning             |
| ------------- | ------------------- |
| **\_blank**   | New window/tab      |
| **\_self**    | Same page (default) |
| **\_parent**  | Parent frame        |
| **\_top**     | Full window         |
| **framename** | Named iframe        |

Note: Framesets are obsolete in HTML5, but this still works with iframes.

## **Section 18.3: Uploading Files**

To upload files:

1. Use `POST`
2. Use `multipart/form-data`
3. Add a `<input type="file">`

Example:

```html
<form method="post" enctype="multipart/form-data" action="upload.php">
  <input type="file" name="pic" />
  <input type="submit" value="Upload" />
</form>
```

## **Section 18.4: Grouping Inputs with `<fieldset>`**

`<fieldset>` visually groups related input fields.
`<legend>` gives that group a label.

Example:

```html
<form>
  <fieldset>
    <legend>Contact Info</legend>
    Name:<br />
    <input type="text" /><br />
    Email:<br />
    <input type="text" /><br />
  </fieldset>

  <fieldset>
    <legend>Preferences</legend>
    <input type="checkbox" /> Subscribe
  </fieldset>

  <input type="submit" />
</form>
```

Supported by all major browsers.

---
