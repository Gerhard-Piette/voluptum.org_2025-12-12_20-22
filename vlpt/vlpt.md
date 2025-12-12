# Vlpt










## About Vlpt

Vlpt stands for Voluptum Script.

Vlpt is pronounced Volupt.

Vlpt is a text notation that offers:
- text structures
- text references
- text formatting for presentation

Vlpt text is compiled HTML and alpine.js.

Alpine.js for compilation of Vlpt at runtime.










## Unusual traits of Vlpt

- A marker is a character or word at the beginning of a line and indicates how the line is compiled.
- The editor is not meant to indent text. Instead section numbers ( e.g. 16.1.2.3 ) and other graphical indicators are used to indicate the current location in the document.
- The programmer can write a marker and some tool might replace the marker with another marker that is less confusing for AI.










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
| **Cc** | **Horizontal Tab** | `U+0009` | Indentation. |
| **Cc** | **Line Feed** | `U+000A` | Newline (Unix). |
| **Cc** | **Carriage Return** | `U+000D` | Newline (Windows). |
| **Cf** | **Zero Width Joiner** | `U+200D` | **Required** for complex emojis (Family, flags, skin tones). |
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
 text
```



### Presented output

The presented output is the line including the line break character but without the ` ` marker.










## `_` marker or style marker

The `_` marker indicates a line with 0 or more styled sections.



### Example

```vlpt
_ text1 _class1 class2: text2_
```

Where:
- class1 and class2 are CSS classes.
- The text between ": " an "_" is the styled text. The text is styled according to the CSS classes.
- Within the styled text: "\_" is an escape sequence for the "_" character.



### Presented output

The presented output is the line including the line break character but without the `_ ` marker.

The styled text is styled according to the CSS classes.










## `#` marker

The `#` marker indicates a comment line.



### Example

```vlpt
# comment text
```



### Presented output

A comment line has no presented output.










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
- \u{1F680} : For Unicode character U+1F680. The number is a hexadecimal number from 0 to 10FFFF included.



### Presented output

The presented output of a string is the string content.










## Package

Vlpt text allows to reference files including files with Ecmascript and Typescript code.

A package is a zip file with a folder structure that can comprise arbitrary files and folder.










## Package management

A package is identified by its name and checksum.

A different name or a different checksum means a different package and different content.

Content of different packages is never considered equal or compatible.

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
```



### Declaration of named memo

The memo marker is followed by the name of the memo. A named memo is not applied implicitly. 

```vlpt
memo name
    content
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
```










## `h` marker or header marker



### Example

```vlpt
h
 text of a h1 header
hh
 text of a h2 header
hhh
 text of a h3 header
hhhh
 text of a h4 header
hhhhh
 text of a h5 header
hhhhh
 text of a h6 header
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










## `end` marker

The end mark indicates the end of the last opened block.










## `:` marker or colon marker

The meaning of the : marker is context dependent.

The : marker the block of the last opened : block.

The : marker opens a new : block.



### Example 1

```vlpt
ul
:
 text of the list item
:
 text of the list item
:
 text of the list item
end
```

Where:
- The : marker serves as separator of list items.
- The : marker the block of the last opened : block.
- The end marker indicates the end of the ul block. 










## `ol` marker for ordered list



### Example 1

```vlpt
ol
:
 text of the list item
:
 text of the list item
:
 text of the list item
end
```

Where:
- The : marker serves as separator of list items.
- The end marker indicates the end of the ol block. 











## `ul` marker for unordered ordered list



### Example 1

```vlpt
ul
:
 text of the list item
:
 text of the list item
:
 text of the list item
end
```

Where:
- The : marker serves as separator of list items.
- The end marker indicates the end of the ul block. 










## s marker

The s marker is for strikethrough.

Like the s tag in HTML.



### Example 1

```vlpt
s
 line
end
```










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
# Row 1: The header row (optional)
tr
th
 Header 1 Text
end
th
 Header 2 Text
end
end
# Row 2: A data row
tr
td
 Cell A Text
end
td
 Cell B Text
end
end
# Row 3: Another data row
tr
td
 Cell C Text
end
td
 Cell D Text
end
end
end
```









---

Copyright &copy; Gerhard Piette. All rights reserved.




