# Vlpt










## About Vlpt

Vlpt is pronounced Volupt.

Vlpt stands for Voluptum Script.

Vlpt is a text notation that offers:
- text structures
- text references
- text formatting for presentation










## Intended usage of Vlpt

- For structured text for multimedia communication for humans, AI, and simpler programs. Vlpt text should be optimal for multi-modal communication between humans and AI.
- For websites that are optimal for search engines.
- For reactive user interfaces of applications.
- Features related to printing are welcome but have no priority because Vlpt is meant for an efficient convenient world without polluting, wasteful, limiting, printed documents.










## Unusual traits of Vlpt syntax

- Markers at the begin of a line indicate how the line is compiled.
- Vlpt text is valid and readable with and without indentation.
    - Vlpt tools offer the option to add no indentation to Vlpt text.
    - The Vlpt editor can add section numbers ( e.g. 16_1_2_3 ) and other graphical indicators.










## Printed output

Printed output should be presented to the consumer in some form.










## Compiled output

Compiled output is the output of the compilation of Vlpt text.










## Compiler

The Vlpt compiler translates Vlpt text to HTML and Javascript.










## Allowed characters in Vlpt text

To support "all valid text including emojis" while maintaining security, here is the complete **Allowlist** for Vlpt.



### The Broad Categories (Allow All)
These are safe to allow in their entirety for a specification language that supports natural language text.

* **L (Letters):** All (`Lu`, `Ll`, `Lt`, `Lm`, `Lo`).
* **N (Numbers):** All (`Nd`, `Nl`, `No`).
* **P (Punctuation):** All (`Pc`, `Pd`, `Ps`, `Pe`, `Pi`, `Pf`, `Po`).
* **S (Symbols):** All (`Sm`, `Sc`, `Sk`, `So`). *This covers math and emojis.*
* **M (Marks):** All (`Mn`, `Mc`, `Me`). *This covers accents.*



### The Specific Exceptions (Specific Characters Only)
These categories are generally dangerous, so we only allow specific useful characters and block the rest.

| Category | Character Name | Hex Code | Reason |
| :--- | :--- | :--- | :--- |
| **Zs** | **Space** | `U+0020` | Standard word separation. |
| **Zs** | **No-Break Space** | `U+00A0` | Common in AI/Web input. **Normalize** to `U+0020`. |
| **Cc** | **Horizontal Tab** | `U+0009` | Indentation. |
| **Cc** | **Line Feed** | `U+000A` | Newline (Unix). |
| **Cc** | **Carriage Return** | `U+000D` | Newline (Windows). |
| **Cf** | **Soft Hyphen** | `U+00AD` | Common invisible formatting artifact. **Strip**. |
| **Cf** | **Left-to-Right Mark** | `U+200E` | **Required** for mixed LTR/RTL text (e.g., English inside Arabic). |
| **Cf** | **Right-to-Left Mark** | `U+200F` | **Required** for mixed LTR/RTL text (e.g., Hebrew inside English). |
| **Cf** | **Zero Width Joiner** | `U+200D` | **Required** for complex emojis (Family, flags, skin tones). |
| **Cf** | **Variation Selector-15** | `U+FE0E` | **Required** to force text-style rendering (e.g., black & white symbols). |
| **Cf** | **Variation Selector-16** | `U+FE0F` | **Required** to force emoji rendering (e.g., making "▶" colorful). |



### Summary of the Logic
1.  **Input Character comes in.**
2.  **Is it in L, N, P, S, or M?** -> **✅ Pass.**
3.  **Is it one of the 6 specific exceptions (Space, Tab, LF, CR, ZWJ, Vlpt16)?** -> **✅ Pass.**
4.  **Everything else?** -> **⛔ Reject.**

**Any other character is forbidden.**










## Empty line


### Printed output

An empty line has no printed output.




### Compiled output

An empty line is translated to an empty line by the compiler.










## Marker

A marker is a character or name at the beginning of a line and indicates how the line is compiled.
A marker must be followed by a space character (U+0020 SPACE, ASCII 32 ).



### Key marker

A key marker is like a keyword in other languages.



### Name marker

A name marker is a name that is not a key marker.










## Name

A name is an identifier in other languages.

Vlpt allows names for:
- Files, folders, and packages with the import marker.
- Block types.
- Parameters.



### Reserved names

- Names ( that begin with a lowercase latin letter ) are reserved for key markers.



### Naming convention

- A new name must begin with an uppercase latin letter or non-Ascii character.
- PascalCase is recommended because this avoids AI context tokens for the low_line character (AKA underscore character).










## Stop marker as `/`

The stop marker indicates the end or closing of a block.



### Example

```vlpt
/
/xxx
/ xxx
/      xxx
```

Where:
- xxx is optional. xxx stands for a marker or the name of a component. Space characters between / and xxs are allowed. Tools can add the marker or name when absent.










## Comment marker as `//`

The comment marker indicates a comment line.

// is used because AI in 2025 is trained to use // for comments.



### Example

```vlpt
// comment text
 // as part of some text 
```

Where:
- // as marker indicates a comment.
- // after the space marker is recognized as literal text //.



### Printed output

A comment line has no printed output.










## Block

A block in Vlpt is similar to an element in HTML or a component in a js framework.

A block declaration spans from block marker to stop marker.

Every block has a block type.



### Example

A col block spans from the col marker to the / marker.

```vlpt
col
 text
/
```










## Block content

A block content is the content between the line with the block marker and the line with the corresponding stop marker.



### Example

A col block spans from the col marker to the / marker.

```vlpt
col
 text
/
```

Where:
- text is col content or content of a col block.










## Inner block

An inner block is declared within an outer block.










## Outer block

An outer block contains 1 or more inner blocks.










## Block type

The content of a Vlpt file is a block type declaration.

A black type is used to create a block.










## Parameter

In Vlpt: A parameter means a parameter of a block type.



### Parameter line

A parameter line contains the definition of a parameter on a single line.



### Parameter block

A parameter block is declared as block over multiple lines.



### Implicit parameter declaration

The param marker indicates the implicit parameter.



### Explicit parameter declaration

An explicit parameter has a user defined name.

```vlpt
Name1 = "default text"

Name2 =
 default text
/
```

Where:
- Outside of block content: The = character after a name marker indicates a parameter definition.
- If the parameter name is followed by a string then the parameter definition is a parameter line. Like for the Name1 parameter in the example.
- If the parameter name is followed by block content then the parameter definition is a parameter block. Like for the Name2 parameter in the example.



### Added Parameter

An explicit parameters can be added to an inner block in the outer block.

```vlpt
Name1
Name9 = "default text"
/
```

Where:
- Name9 is an added parameter if Name9 is not defined in the Name1 type.



### Removed Parameter

A explicit parameter can be removed from an inner block in the outer block.

```vlpt
Name1
Name9 #
/
```

Where:
- The # character after Name9 means to remove Name9 from the block with Name1 type.










### Parameter usage

```vlpt
Name1
param
```

Where:
- The parameter Name1 is used as a marker.
- The param marker stands for the implicit parameter.
- A parameter is replaced with the argument of the parameter. 










## Argument

In Vlpt: An argument is a string or block content that is bound to a block parameter.



### Argument line

An argument line contains the binding of parameter and string as argument.



### Parameter block

An argument block contains the binding of parameter and a block content as argument.



### Argument declaration

```vlpt
Name1 = "argument1"

Name2 =
 argument2
/ Name2

box
 style = "class1"
 argument3
/ box
```

Where:
- In block content: The = character after a marker indicates the binding of an explicit parameter to an argument.
- Name1 is a parameter that is bound to the string "argument1" as argument.
- Name2 is a parameter that is bound to the Name2 content as argument.
- The "class1" string is bound to the explicit style parameter of the box block. An explicit parameter is like an attribute in HTML.
- The argument3 box content is bound to the implicit parameter of the box type because that content does not follow any = character.










## Number

These patterns use `[0-9]` instead of `\d` to enforce strict ASCII digits, ensuring high compatibility with code parsers and avoiding Unicode normalization issues.



### Unsigned Integer

Matches strict positive whole numbers.

```rust
r"^[0-9]+$"
```



### Signed Integer

Matches whole numbers with an optional `+` or `-` sign.

```rust
r"^[+-]?[0-9]+$"
```



### Floating Point Number (Standard)

Matches decimal numbers. This pattern requires at least one digit before and after the dot (e.g., `0.5` not `.5`) to minimize ambiguity for tokenizers.

```rust
r"^[+-]?[0-9]+\.[0-9]+$"
```



### Number with Scientific Notation

Matches numbers with an exponent. This covers integer-scientific (`1e10`) and float-scientific (`1.5E-10`) formats.

```rust
r"^[+-]?[0-9]+(?:\.[0-9]+)?[eE][+-]?[0-9]+$"
```



### Why these are "Optimal for AI" in Vlpt

* **No Underscores:** Vlpt recommends avoiding underscores in names to save "AI context tokens". These regexes strictly exclude underscores (like `1_000`) for the same reason—keeping tokens dense and standard.
* **Determinism:** No ambiguity by enforcing a standard JSON-compatible format.
* **Simplicity:** They avoid look-arounds, making them performant and safe for "simpler programs" that might be parsing the Vlpt output.










## String

A string is delimited by string limits of equal length.

A string is recognized as string only in a key line.

A string must start and stop on the same key line and thus must not contain line break characters.



### String limit

Vlpt allows only 2 kinds of string limits:
- `"`
- `"""`



### String content

The string content are the characters between the string limits.

Only allowed characters are allowed in string content.

The Vlpt compiler does not recognize markers in string content. A block with block semantics can not be declared in string content.



### Example 1

```vlpt
"..."
```

Where ... can be any sequence of allowed characters.



### Example 2

```vlpt
"""..."""
```

Where ... can be any sequence of allowed characters.



### Escape sequences

The compiler recognizes escape sequences only in string content.

The only valid escape sequences in Vlpt:
- \" : Literal Double Quote.
- \\ : Literal Backslash.
- \n : Line Feed.
- \r : Carriage Return.
- \t : Tab.
- \u{1F680} : For Unicode codepoint U+1F680. The number is a hexadecimal number from 0 to 10FFFF included. This aligns with Rust strings.



### Printed output

The printed output of a string is the string content.










## Package system



### Package

A package is a zip file that contains a folder that can contain files and folders.



### Package management

A package is identified by its identifier.

The package identifier can be any string and should include the version number.

The package manager can use checksums to verify the content of a package for security and reproducibility.

There is no compatibility packages with a different identifier.

There is no semantic versioning for Vlpt packages.

(Semantic Versioning)[https://semver.org/]

This removes dependency hell. This facilitates much for the writer and reader of Vlpt text because there is .

[Version SAT](https://research.swtch.com/version-sat)










## HTML in Vlpt

Vlpt is not based on HTML.

The compiler translates Vlpt text to HTML and Ecmascript.



### HTML elements in Vlpt

The compiler determines the implementation.



### HTML attributes in Vlpt

Parameters correspond to HTML attributes.










## CSS in Vlpt

Vlpt offers the css marker for use of CSS.










## css marker

The css marker allows to declare CSS rules that can be referenced within the block content in which the css block is declared.

The css content is CSS text.



### Example

```vlpt
box
css
 .class1 {
    width: 100em;
 }
/ css
/ box
```



### CSS overriding

Within a block: The local CSS overrides conflicting CSS from an outer block.



### Implicit CSS classes in Vlpt

Vlpt offer the following CSS classes that can be overridden:
- Class b for bold.
- Class center in CSS.
- Class i for italic.
- Class t for line-through in CSS.
- Class u for underline in CSS.














## Space marker as ` `

The space marker as space character (U+0020 SPACE, ASCII 32 ) indicates a text line that can contain styled sections.



### Example

```vlpt
 line with [class1 class2 "formatted"] text
```

Where:
- The space marker indicates a text line with optional styled sections.
- class1 and class3 are CSS classes.
- [class1 class2 "formatted" ] is a styled section. The string content is formatted according to class1 and class2.



### Printed output

The printed output is the line including the line break character but without the ` ` marker.










## import marker

The import marker allows to bind a local name to:
- a local Vlpt file
- a local folder with Vlpt files
- A remote Vlpt package that is offered by a web service. 



### Import name

The import name is the name that follows the import marker.



### Example with a local file

```vlpt
import Name1 "file2.vlpt"
import Name3 "./file4.vlpt"
import Name5 "folder6/file7.vlpt"
import Name8 "./folder9/file10.vlpt"
```

Where:
- "file2.vlpt" indicates file2f.vlpt in the working folder of the compiler.
- "./file4.vlpt" indicates file4.vlpt besides the importing file.



### Example with a local folder

```vlpt
import Name1 "folder2"
import Name3 "./folder4"
```

Where:
- Name1 stands for the folder2 in the working folder of the compiler.
- Name3 stands for the folder4 besides the importing file.



### Example with a Vlpt package

```vlpt
import Name1 "URI"
```

Where:
- Name1 stands for the Vlpt package at the indicated URI.



### Use of a file name

```vlpt
import Name1 "file"
Name1
```

Where:
- Name1 stands for a file and the block type defined in that file. The content of a Vlpt file is a block type declaration.



### Use of a folder name

```vlpt
import Name1 "folder"
Name1.Name2
```

Where:
- Name1 stands for the folder.
- Name1.Name2 means access of the file or folder in folder Name1.



### Use of a package name

```vlpt
import Name1 "URI"
Name1.Name2
```

Where:
- Name1 stands for a package. The package content is always a folder.
- Name1.Name2 means access of the file or folder in package Name1.



### Limitations

- Vlpt does not allow circular references among loaded files. This facilitates much for the writer and reader of Vlpt text.
    - [Cyclic dependencies are evil](https://fsharpforfunandprofit.com/posts/cyclic-dependencies/)










## version marker

The version marker is followed by the version number of Vlpt in which the text in the Vlpt file is written.

The Vlpt version is important for the VPT reader including the compiler.



### Example 1

```vlpt
version "1.2"
```

Where:
- The version text is a string with arbitrary content.










## param marker

The param marker is the implicit parameter and stands for the argument that is bound to the implicit parameter.










## doc marker

The doc marker is used to instruct the user of a block.

The doc block is related to the outer block.



### Example

```vlpt
doc "some documentation"

doc
 content
/ doc
```










## memo marker

The memo marker is used to instruct the creator of a block.

The memo block is related to the outer block.



### Example

```vlpt
col
doc "Primary user profile card displayed on the dashboard."
memo
 TODO: Refactor the image loading logic.
 AI Instruction: Ensure this block is responsive on mobile screens.
/
/
```










## B marker

Every B marker begins a block.










## Markers for layout and flow

| Marker | Behavior |
| :--- | :--- |
| **`col`** | **Vertical Stack**. Default flow. Items arrange top-to-bottom. |
| **`row`** | **Horizontal Flow**. Items arrange left-to-right. |
| **`grid`** | **2D Grid**. Content flows into defined cells/columns. |
| **`layer`** | **Z-Stack**. Items overlay on top of each other. |
| **`gap`** | **Spacer**. Explicit spacing (e.g., `gap "2em"`). |










## Markers for surface (containers)

| Marker | Role | SEO Value | Visual Behavior |
| :--- | :--- | :--- | :--- |
| **`box`** | **Visual Wrapper** | Low (Generic) | The only element that can be target of CSS for rectangle styles. <br>*Example:* `box style="card"` |
| **`main`** | **Primary Content** | **High** | Invisible container. Marks the unique content. |
| **`nav`** | **Navigation** | **High** | Invisible container. Marks site links. |
| **`aside`** | **Sidebar / Tangential** | Medium | Invisible container. Marks ads/biographies. |
| **`art`** | **Article** | **High** | Invisible container. Marks syndicatable content. |
| **`sect`** | **Section** | Medium | Invisible container. Groups thematic content. |










## Markers for content (Text & Media)

| Marker | Behavior |
| :--- | :--- |
| **` `** | **Text line**. The space marker indicates a text line. |
| **`txt`** | **Text block**. Merges text lines into a single flowing paragraph. Styled sections are recognized. |
| **`code`** | **Text block**. Like txt but preserves characters exactly as written. No styled sections. |
| **`math`** | **Text block**. Renders accessible MathML/Latex (e.g. via MathJax).. |
| **`head`** | **Heading**. The level is automatically determined by the compiler based on block nesting. |
| **`img`** | **Image**. Handles visual assets. |
| **`icon`** | **Icon**. Semantic symbols (SVG/Font). |










## Markers for lists and tables

*Abstract data structures allow the compiler to choose the best view (table vs. grid).*

| Marker | Behavior |
| :--- | :--- |
| **`list`** | **Sequence**. A simple list of items (bullet/numbered). |
| **`item`** | **Entry**. An item within a list. |
| **`data`** | **Structured Set**. Replaces `table`. |
| **`row`** | **Data Row**. A group of fields in the set. |
| **`fld`** | **Data Field**. A single cell of data. |










## Markers for interaction (UI)

*Functional elements only.*

| Marker | Behavior |
| :--- | :--- |
| **`act`** | **Action**. For interaction. Interaction might be multi-modal. E.g. buttons and Links. <br>*Param:* `do="save"` or `to="/home"`. |
| **`inp`** | **Input**. Text fields, checkboxes, etc. |










## Markers for metadata for search engines

| Marker | Behavior |
| :--- | :--- |
| **`title`** | **Page Title**. The most critical SEO signal. Sets the browser tab title and search result headline. |
| **`meta`** | **Metadata**. Defines description, viewport, and robots directives. <br>*Params:* `name`, `content`. |
| **`link`** | **Resource Link**. Defines canonical URLs to prevent duplicate content issues. <br>*Params:* `rel`, `href`. |










## book marker

Vlpt abstracts the complexity of paged media (PDF, Paper). The compiler is responsible for translating these high-level markers into the necessary CSS (e.g., Paged Media Module) and scripts (e.g., Paged.js).

The book marker defines the physical properties of the document and acts as the container for print-specific configuration.



### Parameters
- **`size`**: Sets the paper size (e.g., "A4", "Letter").
- **`margins`**: Sets the global page margins.



### Example

```vlpt
book size="A4" margins="2.5cm"
  // Running elements are defined here
/
```










## run marker

The run marker defines "running content" (headers and footers) that repeats on every page.



### Parameters

**`area`**: The position on the page.
    - `top-left`, `top-center`, `top-right`
    - `bottom-left`, `bottom-center`, `bottom-right`



### Example

```vlpt
book
 run area="top-center"
  txt "Project Documentation"
 /
 run area="bottom-right"
  txt "Page {page} of {pages}"
 /
/
```










## toc marker

The toc marker automatically generates a Table of Contents based on the `head` (heading) blocks in the document.

  - **Web output**: A navigation list with clickable links.
  - **Print output**: A list with leader dots and calculated page numbers.










## note marker

The note marker indicates a footnote or tangential reference.
- **Web output**: Renders as a tooltip or a clickable number linking to an end-of-text section.
- **Print output**: Renders as a traditional footnote at the bottom of the physical page area.



### Example

```vlpt
txt "Revenue grew by 50% "
note "Q3 Financial Report, 2024"
```










## ref marker

The ref marker creates a smart cross-reference to another element (like a figure or table).
- **Web output**: Renders as a hyperlink (e.g., "Table 1").
- **Print output**: Renders as a text reference with page location (e.g., "Table 1 on page 14").










## Parameters for printing

These parameters can be applied to any block (like `box`, `sect`, `table`) to control layout flow without writing CSS.

  - **`keep`**: If set to `"true"`, the compiler ensures the block is not split across two pages (maps to `break-inside: avoid`).
  - **`break`**: Forces a page break. Values: `"before"`, `"after"`.
  - **`context`**: Marks the text content to be used in running headers. For example, `context="chapter"` allows a `run` marker to display the current chapter title.










## Modifier

A modifier can be declared after a block type name or parameter.

Multiple modifiers on the same line are allowed.

The equal modifier must be the last modifier in a sequence of modifiers.



### Example

```vlpt
Name - =
 content
/
```










## Equal modifier as `=`

The equal modifier indicates the binding of an explicit parameter to an argument.










## Minus modifier as `-`

The minus modifier indicates that the printed output is printed on the same line as the previous output.










## Plus modifier as `+`

The plus modifier indicates that the printed output is printed on new line.










## Template system

The Vlpt compiler can use only Vlpt text.

Vlpt can import only Vlpt text.

Vlpt does not offer computation, branching, and iteration like other template systems.

The Vlpt compiler offers an API that allows to create Vlpt blocks and to pass arguments to block parameters.










## UI, script, and reactivity 

UI = user interface.

Vlpt offers:
- The script marker that is like the script element in HTML.
- Parameters that are like attributes in HTML.










## Dot marker as `.`

The dot marker should be immediately replaced by the tool by another marker.

The dot marker is not a valid marker in Vlpt text.



### Dot for li

```vlpt
ol
.
```

Replaced by:

```vlpt
ol
li
/li
```



### Dot for tr

```vlpt
table
.
```

Replaced by:

```vlpt
table
tr
/ tr
```



### Dot for th

```vlpt
table
tr
.
```

Replaced by:

```vlpt
table
tr
th
/ th
```



### Dot for th

```vlpt
table
tr
th
 content
/
.
```

Replaced by:

```vlpt
table
tr
th
 content
/
th
/ th
```



### Dot for td

```vlpt
table
tr
td
 content
/ td
.
```

Replaced by:

```vlpt
table
tr
td
 content
/ td
td
/ td
```










---

Copyright &copy; Gerhard Piette. All rights reserved.




