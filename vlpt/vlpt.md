# Vlpt










## About Vlpt

Vlpt is pronounced Volupt.

Vlpt stands for Voluptum Script.

Vlpt is a text notation that offers:
- text structures
- text references
- text formatting for presentation

Vlpt text is compiled HTML and alpine.js.

Alpine.js for compilation of Vlpt at runtime.










## Unusual traits of Vlpt

- A marker is a character or word at the beginning of a line. A marker indicates how the line is compiled.
- Vlpt text can be indented with horizontal tab characters before the marker.
    - Vlpt tools offer the option to add no indentation to Vlpt text.
    - The Vlpt editor can add section numbers ( e.g. 16.1.2.3 ) and other graphical indicators.










## Presented output

Presented output should be presented to the consumer in some form.










## Compiled output

Compiled output is the output of the compilation of Vlpt text.










## Compiler

Vlpt text is compiled to HTML and alpine.js.

Alpine.js allows reactivity of output that is compiled at runtime.

The compiler is implemented in the Rust language.

Rust allows translation at compile time and at runtime with WASM.










## Allowed characters in  text

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










## Marker

A marker is a character or word at the beginning of a line and indicates how the line is compiled.
A marker must be followed by a space character (U+0020 SPACE, ASCII 32 ).










## ` ` marker or space marker

The ` ` or space marker (U+0020 SPACE, ASCII 32 ) indicates a literal line.



### Example

```vlpt
 line with [class1 class2 "formatted"] text
```

Where:
- The space marker indicates a text line with optional styled sections.
- class1 and class3 are CSS classes.
- [class1 class2 "formatted" ] is a styled section. The string content is formatted according to class1 and class2.



### Presented output

The presented output is the line including the line break character but without the ` ` marker.

The string content of the formatted section is translated as span element and style attribute in HTML.










## `pre` marker

The pre marker is like the pre element in HTML and preserves all allowed characters including all whitespace.



### Example

```vlpt
pre
 text where [class1 class2 "text" ] is not recognized for formatting
/
```



### Presented output

The pre block is translated into a pre element in HTML.










## `//` marker or comment marker

The `//` marker indicates a comment line.



### Example

```vlpt
// comment text
```



### Presented output

A comment line has no presented output.










## `/` marker or stop marker

The `/` marker indicates the end or closing of a block.



### Example

```vlpt
/
/xxx
/ xxx
/      xxx
```

Where:
- xxx is optional. xxx stands for a marker or the name of a component. Space characters between / and xxs are allowed. Tools can add the marker or name when absent.










## `let` marker

The `let` marker indicates a line where a variable is defined.



### Example

```vlpt
let a = 4 + 5
```



### Presented output

A let line has no presented output.










## `=` marker

The `=` marker indicates that the output of the following expression or of the defined variable is used as presented output.

Allowed whitespace characters are optional after the = marker.



### Examples

```vlpt
= name1
= name2.name3
= name4(arg5, arg6)
= let name7 = name8.name9(arg11)
```

Where:
- The output of the variable name7 is presented output.



### Presented output

The presented output is the presented output of the expression or variable after assignment.










## Name

A name is a word and like an identifier in other languages.

A name is a public name except when the name is a private name.
- id marker
- private marker

Most Unicode characters can be name characters except:
- In the ASCII range: Only - and _ and digits and latin letters are allowed as name character.
- Space characters are not allowed in a name.



### Naming convention

camelCase names with lowercase first character are preferred because this saves tokens in AI context. 

Respecting naming conventions is recommended but not required.

The Vlpt writer can declare names according to its own preferences.



### Local name

A local name is a name declared after these markers:
- let
- private
- import

A local name can also be declared after the id attribute name.










## Number

A number can be declared in any sensible way.










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



### Presented output

The presented output of a string is the string content.










## Package

Vlpt text allows to reference files including files with Ecmascript and Typescript code.

A package is a zip file with a folder structure that can comprise arbitrary files and folder.










## Package management

A package is identified by its identifier.

The package identifier can be any string and should include the version number.

The package manager should also require a certain checksum for package identification in order verify the content of a package.

There is no compatibility packages with a different identifier.

There is no semantic versioning for Vlpt packages.

(Semantic Versioning)[https://semver.org/]

This removes dependency hell. This facilitates much for the writer and reader of Vlpt text because there is .

[Version SAT](https://research.swtch.com/version-sat)










## version marker

The version marker is followed by the version number of Vlpt in which the text in the Vlpt file is written.

The Vlpt version is important for the VPT reader including the compiler.



### Example 1

```vlpt
version "1.2"
```

Where:
- The version text is a string with arbitrary content.










## import marker

The import marker allows to bind a local name to the content of another file.



### Example 1

```vlpt
import name1 "URI"
import name2 "./script.ts"
```

Where:
- URI is the URI of a file.
- script.ts is some file with Typescript code. All exported symbols must be prefixed with "name2." for use.



### Limitations

- Vlpt does not allow circular references among loaded files. This facilitates much for the writer and reader of Vlpt text.










## private marker

The private marker is used to define a private local name.

A private name is only accessible in the same Vlpt file. A private name is not directly accessible from an imported file.



### Example 1

```vlpt
private name1 = expression
```










## memo marker

The memo marker is used to declare a memo.

A memo contains text about how to understand and interpret Vlpt text.

A memo can be useful to declare anything including special syntax and semantics.



### Declaration of file memo

There is only 0 or 1 file memo per file. The file memo applies to the Vlpt text after the file memo until the end of the file.

A file memo has no name.

```vlpt
memo
    content
/ memo
```



### Declaration of named memo

The memo marker is followed by the name of the memo. A named memo is not applied implicitly. 

```vlpt
memo name
    content
/ memo
```


### Copying a named memo

A named memo can be copied into another memo. The copied memo is part of the receiver memo. The copy of a memo has no other effect.

```vlpt
= memoName
```










## B marker

Every B marker begins a block.










## `,` marker

The `,` marker allows to declare an attribute related to the current block.



### Example

```vlpt
div
, id "some id"
, style = class1 class2
, width = 200px
, height = 200px
 text
 text
/ div
```










## H marker or header marker



### Example

```vlpt
h1
 text of a h1 header
/ h1

h2
 text of a h2 header
/ h2

h3
 text of a h3 header
/ h3

h4
 text of a h4 header
/ h4

h5
 text of a h5 header
/ h5

h6
 text of a h6 header
/ h6
```










## `quote` marker for quotes


### Example

```vlpt
quote
    content
    content
```

Where:
- The > character must be the first non-whitespace character on the line. 



### Example

```vlpt
quote
, source "uri1"
, source "uri2"
 content
 content
```










## `li` marker for list item marker

Like the li element in HTML.










## `ol` marker for ordered list

Like the ol element in HTML.



### Example 1

```vlpt
ol
li
 text of the list item
/
li
 text of the list item
/
li
 text of the list item
/
/ ol
```



### Presented output

As ol element in HTML.










## `ul` marker for unordered ordered list

Like the ul element in HTML.



### Example 1

```vlpt
ul
li
 text of the list item
/
li
 text of the list item
/
li
 text of the list item
/
/ ul
```



### Presented output

As ul element in HTML.










## Table markers

Table markers are similar to HTML table tags.

In Vlpt:
- table
- tr
- th
- td



### Example 1

```vlpt
table
// Row 1: The header row (optional)
tr
th
 Header 1 Text
/ th
th
 Header 2 Text
/ th
/ tr
// Row 2: A data row
tr
td
 Cell A Text
/
td
 Cell B Text
/
/ tr
// Row 3: Another data row
tr
td
 Cell C Text
/
td
 Cell D Text
/
/ tr
/ table
```










## `.` marker or smart marker

The `.` marker can be used as smart marker in order to facilitate typing Vlpt text for a human.

The smart marker is not valid marker.
 
A Vlpt tool must replace smart marker with another marker

- In a ol block: The smart marker is replaced with a li block.
- In a ul block: The smart marker is replaced with a li block.
- In a tr block: The smart marker is replaced with a td block.




### Example 1

Invalid VLPT text wth smart marker:

```vlpt
table
tr
.
ul
.
 text of the list item
.
 text of the list item
.
 text of the list item
/ ul
.
ol
.
 text of the list item
.
 text of the list item
.
 text of the list item
/ ol 
/ tr
/ table
```

That is translated into this valid Vlpt text:

```vlpt
table
tr
td
ul
li
 text of the list item
/ li
li
 text of the list item
/ li
li
 text of the list item
/ li
/ ul
/ td
td
ol
li
 text of the list item
/ li
 text of the list item
li
 text of the list item
/ li
/ ol
/ td 
/ tr
/ table


That is translated this HTML:
<table>
    <tr>
        <td>
            <ul>
                <li>
                    text of the list item
                </li>
                <li>
                    text of the list item
                </li>
                <li>
                    text of the list item
                </li>
            </ul>
        </td>
        <td>
            <ol>
                <li>
                    text of the list item
                </li>
                <li>
                    text of the list item
                </li>
                <li>
                    text of the list item
                </li>
            </ol>
        </td>
    </tr>
</table>










---

Copyright &copy; Gerhard Piette. All rights reserved.




