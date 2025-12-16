# Vlpt










## Table of contents

- [Vlpt](#vlpt)
  - [Table of contents](#table-of-contents)
  - [Introduction](#introduction)
    - [About the name Vlpt](#about-the-name-vlpt)
    - [Purpose of Vlpt](#purpose-of-vlpt)
    - [Unusual traits of Vlpt syntax](#unusual-traits-of-vlpt-syntax)
      - [Example](#example)
    - [Vlpt comprises 4 Vlpt languages](#vlpt-comprises-4-vlpt-languages)
    - [Allowed characters in Vlpt text](#allowed-characters-in-vlpt-text)
      - [The Broad Categories (Allow All)](#the-broad-categories-allow-all)
      - [The Specific Exceptions (Specific Characters Only)](#the-specific-exceptions-specific-characters-only)
      - [Summary of the Logic](#summary-of-the-logic)
  - [General concepts](#general-concepts)
    - [App form](#app-form)
    - [Compiled form](#compiled-form)
    - [Compiler](#compiler)
    - [Empty line](#empty-line)
      - [App form](#app-form-1)
      - [Compiled form](#compiled-form-1)
    - [Marker](#marker)
      - [Key marker](#key-marker)
      - [Name marker](#name-marker)
    - [Name](#name)
      - [Rust regex of a valid Vlpt name](#rust-regex-of-a-valid-vlpt-name)
      - [Reserved names](#reserved-names)
      - [Recommended naming convention](#recommended-naming-convention)
    - [Number](#number)
      - [Unsigned Integer](#unsigned-integer)
      - [Signed Integer](#signed-integer)
      - [Floating Point Number (Standard)](#floating-point-number-standard)
      - [Number with Scientific Notation](#number-with-scientific-notation)
      - [Why these are "Optimal for AI" in Vlpt](#why-these-are-optimal-for-ai-in-vlpt)
    - [String](#string)
      - [String limit](#string-limit)
      - [String content](#string-content)
      - [Example 1](#example-1)
      - [Example 2](#example-2)
      - [Escape sequences](#escape-sequences)
      - [Printed output](#printed-output)
    - [vlpt marker](#vlpt-marker)
      - [Example 1](#example-1-1)
    - [Space marker](#space-marker)
      - [Example](#example-1)
      - [Printed output](#printed-output-1)
    - [Colon marker](#colon-marker)
      - [Example](#example-2)
    - [Stop marker](#stop-marker)
      - [Stop marker without marker name](#stop-marker-without-marker-name)
      - [Stop marker with marker name](#stop-marker-with-marker-name)
    - [Comment marker\`](#comment-marker)
      - [Example](#example-3)
    - [Block](#block)
      - [Example](#example-4)
    - [Block content](#block-content)
    - [Content line](#content-line)
      - [Example](#example-5)
    - [Inner block](#inner-block)
    - [Outer block](#outer-block)
    - [Type](#type)
    - [Modifier](#modifier)
      - [Modifier usage](#modifier-usage)
    - [Doc](#doc)
      - [doc marker](#doc-marker)
      - [Creation of a doc with name](#creation-of-a-doc-with-name)
      - [Creation of a doc without name](#creation-of-a-doc-without-name)
  - [Memo](#memo)
    - [memo marker](#memo-marker)
      - [Example](#example-6)
  - [Package system](#package-system)
    - [Package](#package)
    - [Package management](#package-management)
    - [import marker](#import-marker)
      - [Import name](#import-name)
      - [Example with a local file](#example-with-a-local-file)
      - [Example with a local folder](#example-with-a-local-folder)
      - [Example with a Vlpt package](#example-with-a-vlpt-package)
      - [Use of a file name](#use-of-a-file-name)
      - [Use of a folder name](#use-of-a-folder-name)
      - [Use of a package name](#use-of-a-package-name)
      - [Limitations](#limitations)
  - [Vlpt program language](#vlpt-program-language)
    - [Program language file suffix](#program-language-file-suffix)
    - [Function](#function)
      - [Function type declaration](#function-type-declaration)
      - [Function declaration](#function-declaration)
      - [Static function](#static-function)
      - [Dynamic function](#dynamic-function)
      - [No function overloading](#no-function-overloading)
    - [Class](#class)
      - [class modifier](#class-modifier)
        - [Class type definition](#class-type-definition)
      - [Class value creation](#class-value-creation)
      - [No constructors](#no-constructors)
    - [Module](#module)
      - [module modifier](#module-modifier)
        - [Module type definition](#module-type-definition)
    - [Impl type](#impl-type)
    - [Impl value](#impl-value)
      - [impl modifier](#impl-modifier)
        - [Module implementation](#module-implementation)
        - [Module value creation](#module-value-creation)
    - [Type parameter](#type-parameter)
      - [Example](#example-7)
    - [Type argument](#type-argument)
      - [Monomorphization](#monomorphization)
  - [Vlpt net language](#vlpt-net-language)
    - [Net language file suffix](#net-language-file-suffix)
    - [Example content of a .net.vlpt file](#example-content-of-a-netvlpt-file)
      - [Use of a net name in a .pro.vlpt file](#use-of-a-net-name-in-a-provlpt-file)
  - [Vlpt app language](#vlpt-app-language)
    - [App language file suffix](#app-language-file-suffix)
    - [Parameter in app language](#parameter-in-app-language)
      - [Implicit parameter in app language](#implicit-parameter-in-app-language)
      - [Explicit parameter declaration in app language](#explicit-parameter-declaration-in-app-language)
      - [Parameter usage in app language](#parameter-usage-in-app-language)
    - [Argument in app language](#argument-in-app-language)
      - [Argument declaration in app language](#argument-declaration-in-app-language)
    - [From Vlpt to HTML](#from-vlpt-to-html)
    - [param marker in app language](#param-marker-in-app-language)
    - [Equal marker in app language](#equal-marker-in-app-language)
    - [Layout markers](#layout-markers)
    - [Action markers in app language](#action-markers-in-app-language)
    - [Description markers in app language](#description-markers-in-app-language)
    - [Web markers in app language](#web-markers-in-app-language)
    - [toc marker](#toc-marker)
    - [note marker](#note-marker)
      - [Example](#example-8)
    - [ref marker](#ref-marker)
    - [Parameters for printing](#parameters-for-printing)
  - [Vlpt style language](#vlpt-style-language)
    - [Style language file suffix](#style-language-file-suffix)
    - [Selector in style language](#selector-in-style-language)
    - [Style block style language](#style-block-style-language)
    - [Style in style language](#style-in-style-language)
    - [Property in style language](#property-in-style-language)
    - [Value in style language](#value-in-style-language)
    - [Example content of a .style.vlpt file](#example-content-of-a-stylevlpt-file)
    - [Import content of a style file](#import-content-of-a-style-file)
    - [Style overriding](#style-overriding)
      - [Implicit style classes in Vlpt](#implicit-style-classes-in-vlpt)
  - [Editor for Vlpt text](#editor-for-vlpt-text)
    - [Dot marker](#dot-marker)
      - [Dot for li](#dot-for-li)
      - [Dot for tr](#dot-for-tr)
      - [Dot for th](#dot-for-th)
      - [Dot for th](#dot-for-th-1)
      - [Dot for td](#dot-for-td)










## Introduction










### About the name Vlpt

Vlpt is pronounced Volupt.

Vlpt stands for Voluptum Script.










### Purpose of Vlpt

- Creation of software apps for communication. A static web page is also an app. Intended app users are humans and AI.
- Ease of reading and writing of Vlpt text by humans and AI is extremely important.
- Vlpt text should serve as replacement for:
  - HTML for web pages and web apps.
  - Markdown for documentation.
  - JSON for data structures.
  - Storage of data of social media posts, documents, presentations, spreadsheets, management software, and more.

Features related to printing on surfaces like paper sheets are welcome but have no priority because Vlpt is meant for an efficient convenient world without polluting, wasteful, limiting, inconvenient, printed documents.










### Unusual traits of Vlpt syntax

- Markers at the begin of a line indicate how the line is compiled.
- Vlpt text is valid and readable with and without indentation.
    - Vlpt tools offer the option to add no indentation to Vlpt text.
    - The Vlpt editor can add section numbers ( e.g. 16_1_2_3 ) and other graphical indicators.



#### Example

```vlpt
marker1
 content of marker1 block
marker2
 content of marker2 block
@@
 content of marker1 block
@@
```










### Vlpt comprises 4 Vlpt languages

- Vlpt program language for computations.
- Vlpt net language for interaction with services.
- Vlpt app language for the user interface.
- Vlpt style language for styling the user interface.










### Allowed characters in Vlpt text

To support "all valid text including emojis" while maintaining security, here is the complete **Allowlist** for Vlpt.



#### The Broad Categories (Allow All)
These are safe to allow in their entirety for a specification language that supports natural language text.

* **L (Letters):** All (`Lu`, `Ll`, `Lt`, `Lm`, `Lo`).
* **N (Numbers):** All (`Nd`, `Nl`, `No`).
* **P (Punctuation):** All (`Pc`, `Pd`, `Ps`, `Pe`, `Pi`, `Pf`, `Po`).
* **S (Symbols):** All (`Sm`, `Sc`, `Sk`, `So`). *This covers math and emojis.*
* **M (Marks):** All (`Mn`, `Mc`, `Me`). *This covers accents.*



#### The Specific Exceptions (Specific Characters Only)
These categories are generally dangerous, so we only allow specific useful characters and block the rest.

| Category | Character Name            | Hex Code | Reason                                                                    |
| :------- | :------------------------ | :------- | :------------------------------------------------------------------------ |
| **Zs**   | **Space**                 | `U+0020` | Standard word separation.                                                 |
| **Zs**   | **No-Break Space**        | `U+00A0` | Common in AI/Web input. **Normalize** to `U+0020`.                        |
| **Cc**   | **Horizontal Tab**        | `U+0009` | Indentation.                                                              |
| **Cc**   | **Line Feed**             | `U+000A` | Newline (Unix).                                                           |
| **Cc**   | **Carriage Return**       | `U+000D` | Newline (Windows).                                                        |
| **Cf**   | **Soft Hyphen**           | `U+00AD` | Common invisible formatting artifact. **Strip**.                          |
| **Cf**   | **Left-to-Right Mark**    | `U+200E` | **Required** for mixed LTR/RTL text (e.g., English inside Arabic).        |
| **Cf**   | **Right-to-Left Mark**    | `U+200F` | **Required** for mixed LTR/RTL text (e.g., Hebrew inside English).        |
| **Cf**   | **Zero Width Joiner**     | `U+200D` | **Required** for complex emojis (Family, flags, skin tones).              |
| **Cf**   | **Variation Selector-15** | `U+FE0E` | **Required** to force text-style rendering (e.g., black & white symbols). |
| **Cf**   | **Variation Selector-16** | `U+FE0F` | **Required** to force emoji rendering (e.g., making "▶" colorful).        |



#### Summary of the Logic
1.  **Input Character comes in.**
2.  **Is it in L, N, P, S, or M?** -> **✅ Pass.**
3.  **Is it one of the 6 specific exceptions (Space, Tab, LF, CR, ZWJ, Vlpt16)?** -> **✅ Pass.**
4.  **Everything else?** -> **⛔ Reject.**

**Any other character is forbidden.**











## General concepts










### App form

The app form of some item is the presentation of the item in the user interface.










### Compiled form

The compiled form of some item is that form that the compiler created.










### Compiler

The Vlpt compiler translates Vlpt text to HTML and Javascript.










### Empty line


#### App form

An empty line has no app form.




#### Compiled form

The compiled form of an empty line is an empty line.










### Marker

A marker is a character or name at the beginning of a line and indicates how the line is compiled.
A marker must be followed by a space character (U+0020 SPACE, ASCII 32 ).



#### Key marker

A key marker is like a keyword in other languages.



#### Name marker

A name marker is a name that is not a key marker.










### Name

A name is an identifier in other languages.



#### Rust regex of a valid Vlpt name

```rust
r"^(r#)?(\p{XID_Start}|_)\p{XID_Continue}*$"
```

A valid name can still be invalid because the name equals a key marker.

Different Vlpt versions can have different keywords.



#### Reserved names

- Names ( that begin with a lowercase latin letter ) are reserved for key markers.



#### Recommended naming convention

- PascalCase for type names in European letters.
- camelCase for all other names in European letters.










### Number

These patterns use `[0-9]` instead of `\d` to enforce strict ASCII digits, ensuring high compatibility with code parsers and avoiding Unicode normalization issues.



#### Unsigned Integer

Matches strict positive whole numbers.

```rust
r"^[0-9]+$"
```



#### Signed Integer

Matches whole numbers with an optional `+` or `-` sign.

```rust
r"^[+-]?[0-9]+$"
```



#### Floating Point Number (Standard)

Matches decimal numbers. This pattern requires at least one digit before and after the dot (e.g., `0.5` not `.5`) to minimize ambiguity for tokenizers.

```rust
r"^[+-]?[0-9]+\.[0-9]+$"
```



#### Number with Scientific Notation

Matches numbers with an exponent. This covers integer-scientific (`1e10`) and float-scientific (`1.5E-10`) formats.

```rust
r"^[+-]?[0-9]+(?:\.[0-9]+)?[eE][+-]?[0-9]+$"
```



#### Why these are "Optimal for AI" in Vlpt

* **No Underscores:** Vlpt recommends avoiding underscores in names to save "AI context tokens". These regexes strictly exclude underscores (like `1_000`) for the same reason—keeping tokens dense and standard.
* **Determinism:** No ambiguity by enforcing a standard JSON-compatible format.
* **Simplicity:** They avoid look-arounds, making them performant and safe for "simpler programs" that might be parsing the Vlpt output.










### String

A string is delimited by string limits of equal length.

A string is recognized as string only in a key line.

A string must start and stop on the same key line and thus must not contain line break characters.



#### String limit

Vlpt allows only 2 kinds of string limits:
- `"`
- `"""`



#### String content

The string content are the characters between the string limits.

Only allowed characters are allowed in string content.

The Vlpt compiler does not recognize markers in string content. A block with block semantics can not be declared in string content.



#### Example 1

```vlpt
"..."
```

Where ... can be any sequence of allowed characters.



#### Example 2

```vlpt
"""..."""
```

Where ... can be any sequence of allowed characters.



#### Escape sequences

The compiler recognizes escape sequences only in string content.

The only valid escape sequences in Vlpt:
- \" : Literal Double Quote.
- \\ : Literal Backslash.
- \n : Line Feed.
- \r : Carriage Return.
- \t : Tab.
- \u{1F680} : For Unicode codepoint U+1F680. The number is a hexadecimal number from 0 to 10FFFF included. This aligns with Rust strings.



#### Printed output

The printed output of a string is the string content.










### vlpt marker

The vlpt marker is followed by the version of Vlpt that is used in the file.

The Vlpt version is important for recognition and meaning of key markers.



#### Example 1

```vlpt
vlpt "1.2"
```

Where:
- The version value is a string.










### Space marker

` ` is the space marker.

The space marker as space character (U+0020 SPACE, ASCII 32 ) indicates a text line that can contain styled sections.



#### Example

```vlpt
 line with [class1 class2 "formatted"] text
```

Where:
- The space marker indicates a text line with optional styled sections.
- class1 and class3 are style classes.
- [class1 class2 "formatted" ] is a styled section. The string content is formatted according to class1 and class2.



#### Printed output

The printed output is the line including the line break character but without the ` ` marker.










### Colon marker

`:` is the colon marker.



#### Example

```vlpt
marker1: text1
marker3 : text2
```










### Stop marker 

`@@` is the stop marker.

The stop marker indicates the end or closing of a block.

The editor should add the stop marker automatically when a marker is declared.



#### Stop marker without marker name

```vlpt
@@
```

Where:
- @@ should be used when the closed marker block does not contain another marker block.



#### Stop marker with marker name

```vlpt
@@ name
```

Where:
- name is a marker name.
- The marker name can help humans and AI with reading and writing Vlpt text.
- Vlpt tool settings should allow a rule for when to show or add a marker name after @@.










### Comment marker`

`//` is the comment marker.

The comment marker indicates a comment line.

// is used because AI in 2025 is trained to use // for comments.



#### Example

```vlpt
// comment text
 // as part of some text 
```

Where:
- // as marker indicates a comment.
- // after the space marker is recognized as literal text //.










### Block

A block in Vlpt is similar to an element in HTML or a component in a js framework.

A block declaration spans from block marker to stop marker.



#### Example

A col block spans from the col marker to the stop marker.

```vlpt
marker1 text2
@@

marker2 text3
 text4
@@

marker5
 text6
@@
```

Where:
- The text after the marker is treated like text of any other line of the block.










### Block content

The block content is the sequence of content lines of a block.










### Content line

Every content line begins with a marker.



#### Example

A col block spans from the col marker to the stop marker.

```vlpt
someMarker: text1
 text2
 text3
@@
```

Where:
- text1, text2, and text3 are content lines in the someMarker block.
- text1, text2, and text3 are treated equally.
- text1 begins with the colon marker.
- text2 and text3 begin with the space marker.










### Inner block

An inner block is declared within an outer block.










### Outer block

An outer block contains 1 or more inner blocks.










### Type

A type is used to create something that is according to the type.

A type is like a type in programming languages.

[Type theory](https://en.wikipedia.org/wiki/Type_theory)










### Modifier

A modifier is a character or word that is declared after a marker.

A modifier is treated as key marker.



#### Modifier usage 

Multiple modifiers on the same line are allowed.

The equal modifier must be the last modifier in a sequence of modifiers.

```vlpt
Name
modifier
@@
modifier
@@
 content
@@
```










### Doc 

A doc is used to inform the user of a block. Like a user guide.




#### doc marker

The doc marker indicates a doc block.



#### Creation of a doc with name

A doc block with a name does not give information about the outer block.

The use of a doc name means to give the doc information about the outer block where the doc name is declared.

```vlpt
doc name1 = "some documentation"
@@

doc name2 =
 content
@@ doc

name3
 name1
 name2
@@ name3
```

Where:
- The docs name1 and name2 are applied to the name3 block.



#### Creation of a doc without name

A nameless doc gives information about the outer block.

```vlpt
doc "some documentation"
@@

doc
 content
@@ doc
```










## Memo

The memo marker is used to instruct AI about what to create. E.g. serialization code for a certain class.

A memo for AI for intelligent code generation is used instead of other meta data like e.g. annotations in Java.



### memo marker

The memo marker indicates a memo block.

A memo block without name 

#### Example

```vlpt
col
doc "Primary user profile card displayed on the dashboard."
@@
memo
 TODO: Refactor the image loading logic.
 AI Instruction: Ensure this block is responsive on mobile screens.
@@
@@
```










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










### import marker

The import marker allows to bind a local name to:
- a local Vlpt file
- a local folder with Vlpt files
- A remote Vlpt package that is offered by a web service. 



#### Import name

The import name is the name that follows the import marker.



#### Example with a local file

```vlpt
import Name1 "file2.vlpt"
import Name3 "./file4.vlpt"
import Name5 "folder6/file7.vlpt"
import Name8 "./folder9/file10.vlpt"
```

Where:
- "file2.vlpt" indicates file2f.vlpt in the working folder of the compiler.
- "./file4.vlpt" indicates file4.vlpt besides the importing file.



#### Example with a local folder

```vlpt
import Name1 "folder2"
import Name3 "./folder4"
```

Where:
- Name1 stands for the folder2 in the working folder of the compiler.
- Name3 stands for the folder4 besides the importing file.



#### Example with a Vlpt package

```vlpt
import Name1 "URI"
```

Where:
- Name1 stands for the Vlpt package at the indicated URI.



#### Use of a file name

```vlpt
import Name1 "file"
Name1
```

Where:
- Name1 stands for a file and the block type defined in that file. The content of a Vlpt file is a block type declaration.



#### Use of a folder name

```vlpt
import Name1 "folder"
Name1.Name2
```

Where:
- Name1 stands for the folder.
- Name1.Name2 means access of the file or folder in folder Name1.



#### Use of a package name

```vlpt
import Name1 "URI"
Name1.Name2
```

Where:
- Name1 stands for a package. The package content is always a folder.
- Name1.Name2 means access of the file or folder in package Name1.



#### Limitations

- Vlpt does not allow circular references among loaded files. This facilitates much for the writer and reader of Vlpt text.
    - [Cyclic dependencies are evil](https://fsharpforfunandprofit.com/posts/cyclic-dependencies/)










## Vlpt program language

The program language is for the declaration of types, function and computations.

The program language in Vlpt



### Program language file suffix

The Vlpt compiler recognizes the program language only in a file with `.pro.vlpt` suffix in the file name.










### Function

A function is like a function or method in other languages.



#### Function type declaration

```vlpt
(name1: type2, name3: type4) type5
```

Where:
- name1 is a parameter name.
- type2 is the type constraint of name1.
- type5 is the output type or return type.



```vlpt
()
```

- The function has no parameter.
- The function gives no output.



#### Function declaration

```vlpt
name1 (name2: type3, name4: type5) type6
 content
@@
```

Where:
- name1 is the function name. Every function must be declared with a function name.
- content is the function body



#### Static function

A function ( that is not member of a module ) is a static function.

Static functions are statically dispatched.



#### Dynamic function

A function ( that is member of a module ) is a dynamic function.

Dynamic functions are dynamically dispatched.



#### No function overloading

According to Gemini 3 Pro:
- The "TypeScript Mismatch" Problem
- The "AI Ambiguity" Problem
- The "Compiler Complexity" Problem










### Class

A class is like a class in object oriented programming languages.

Vlpt does not offer inheritance and related supertypes and subtypes.



#### class modifier

The class modifier indicates a class type definition.



##### Class type definition

```vlpt
Name1 class
name2: type3 = value4
@@
name5: type declaration
 over multiple
 lines
@@
name7 (name8: type9) type10 =
 body over
 multiple lines
@@
@@ Name1
```

Where:
- Name1 is the class type.
- name2 and name5 are class fields. The colon indicates a type constraint.
- value4 is an optional default value.
- = is fallowed by the default value.
- name7 is a function.



#### Class value creation

```vlpt
Name1
name2 = expr3
@@
name5 =
 expr6
@@
@@ Name1
```

Where:
- A class value with Name1 type is created.
- The fields name2 and name5 are assigned values.



#### No constructors

According to Gemini 3 Pro:
- Solves the "Overloading" Problem
- Maps clean to TypeScript
- AI Clarity (No Hidden Logic)










### Module

A module is like an interface or trait in other programming languages.

A module value is an instance of a module.



#### module modifier

The module modifier indicates a module type definition.



##### Module type definition

```vlpt
Name1 module
name1(name2: type3) type4
@@
name5() type6
@@
@@ Name1
```

Where:
- Name1 is a module type.



### Impl type

The impl type is the type for which the module type is implemented.

The impl type can be any value type.

A module implementation must follow the impl type definition in the same file. This simplifies much.



### Impl value

An impl value is a value with the impl type.



#### impl modifier

The impl modifier indicates a module type implementation for an impl type.

A module implementation must follow the impl type definition in the same file. This simplifies much.



##### Module implementation

```vlpt
ImplType1 impl ModuleType2
name1(name2: type3) type4 =
 content
@@
name5() type6 = exp7
@@
@@ ImplType1
```



##### Module value creation

The module type declaration is optional.

```vlpt
// Call of fun1 where the compiler creates the module value according to the type of the parameter of fun1.
fun1(implValue)

fun1(ModuleType(implValue))
```

Where:
- ModuleType(implValue) indicates to create a module value with ModuleType type and implValue as impl value.










### Type parameter

A type parameter is declared between `[` and `]` AKA flat brackets AKA angle brackets. 



#### Example

```vlpt
AdvancedGraph[N, E] class
where
  N: Node + Serializable
  E: Edge + Comparable[E]
@@ where
addNode(node: N) =
    ...
@@
@@ AdvancedGraph
```

Where:
- N must be a type that implements Node and Serializable.
- E must be a type that implements Edge + Comparable[E].



### Type argument

The type that is bound to a type parameter.

```vlpt
ArrayList[u16]
```

Where:
- u16 as number type is the type argument for the type parameter of the ArrayList class.



#### Monomorphization

There is no monomorphization for module types.

There is monomorphization for all other types and functions.

There is monomorphization of the functions of an impl type.

```vlpt
name1(name2: List[T]) =
name3 = ""
@@
name2.add(name3)
@@
name4 = ArrayList[u16]
@@
@@ name1
name1(name4)
```

Where:
- u16 is a number type.
- The ArrayList class is monomorphized according to the type argument.
- The List module is not affected by the type argument. The size of the vtable is the same for all module values with the same module type but the pointers in the vtable differ according to the monomorphization of the impl type.










## Vlpt net language

The net language allows to declare the service topology.



### Net language file suffix

The Vlpt compiler recognizes the net language only in a file with `.net.vlpt` suffix in the file name.


### Example content of a .net.vlpt file

```vlpt
name1: type1
uri = "postgres://db-primary"
@@
con = "in select"
@@
name2: type2
uri = "mqtt://broker.example.com"
@@
con = "in subscribe"
@@
@@ name2
name3: type3
uri = "postgres://db-logs"
@@
con = "out insert"
@@
name4: type4
uri = "https://api.myapp.com/users"
@@
con = "out pull"
@@
name5 import "./file.net.vlpt"
@@
@@ name3
@@ name1
```

Where:
- name1 is a net name in the net tree.
- The type after the path segment indicates type of the exchanged value.
- the `uri` parameter indicates the service.
- The `con` parameter is used to specify the kind of connection.
  - `in` indicates the direction and means input taken from another system.
  - `out` indicates the direction and means output given to another system.
  - The direction is followed by other information required for the data transfer like e.g. a verb.
- name5 stands for the imported network tree.



#### Use of a net name in a .pro.vlpt file

```vlpt
import name1 "my.net.vlpt"

name2() =
 name1.nameName.send(value)
 name1.nameName.send(value, "modified connection")
 name1.nameName.get()
 name1.nameName.get("modified connection")
```










## Vlpt app language

The app language is for the declaration of items of the user interface of the Vlpt app.



### App language file suffix

The Vlpt compiler recognizes the app language only in a file with `.app.vlpt` suffix or `.applet.vlpt` in the file name.

- `.app.vlpt` suffix for a file that contains a complete app.
- `.applet.vlpt` suffix for a file that is not meant to be used as complete app.










### Parameter in app language

In the Vlpt app language: A parameter is a marker that can stands for an argument.



#### Implicit parameter in app language

The param marker is a key marker and indicates the implicit parameter in the Vlpt app language.

The implicit parameter is like a slot in JS frameworks.



#### Explicit parameter declaration in app language

An explicit parameter is a user defined name.

```vlpt
name1 =
 default content
@@
```

Where:
- name1 is a parameter as indicated by = after name1. The parameter type is always VlptApp for valid text in the Vlpt app language.



#### Parameter usage in app language

```vlpt
= name1
= param
```

Where:
- The = marker indicates insertion the argument of the following parameter.
- name1 is a parameter name.
- The param marker stands for the implicit parameter.










### Argument in app language

In the Vlpt app language:
- An argument is a value of type VlptApp for valid text in the Vlpt app language.
- An argument is bound to a parameter.



#### Argument declaration in app language

```vlpt
Name1 = "argument1"
@@

Name2 =
 argument2
@@
```

Where:
- The = character after a parameter marker indicates the binding of the parameter to the argument.










### From Vlpt to HTML

Vlpt parameters correspond to HTML attributes.

Vlpt arguments correspond to HTML attribute values.

Vlpt param argument corresponds to the inner text of a HTML element.










### param marker in app language

The param marker is a key marker and indicates the implicit parameter in the Vlpt app language.










### Equal marker in app language

`=` is the equal marker.

The equal marker is used to add the output of the following name to the content of the outer block.










### Layout markers

| Marker     | Purpose                             |
| :--------- | :---------------------------------- |
| **`col`**  | Like flex-direction: column in CSS. |
| **`row`**  | Like flex-direction: row in CSS.    |
| **`grid`** | Like display: grid in CSS.          |
| **`gap`**  | Like gap in CSS.                    |










### Action markers in app language

| Marker         | Purpose                                                                         | Parameters                     |
| :------------- | :------------------------------------------------------------------------------ | :----------------------------- |
| **`form`**     | **Container**. Scope for data submission. Like form in HTML 5.                  | `action`, `method`             |
| **`group`**    | **Container**. Groups radios/checks. Like fieldset in HTML 5.                   | `legend` (or `label`)          |
| **`input`**    | **Typing**. (Text, Password, Email).                                            | `placeholder`, `type`, `value` |
| **`textarea`** | **Long Typing**. (Often distinct in frameworks).                                | `rows`, `placeholder`          |
| **`select`**   | **Dropdown**.                                                                   | `value`                        |
| **`option`**   | **Item**.                                                                       | `value`, `selected`            |
| **`check`**    | **Toggle**.                                                                     | `checked`, `label`             |
| **`radio`**    | **Exclusive Choice**.                                                           | `checked`, `value`, `name`     |
| **`btn`**      | **Button**.                                                                     | `onclick`, `disabled`          |
| **`anchor`**   | **Navigation**. Maps to `<a>` element in HTML. Distinct from `link` (metadata). | `to` (or `href`)               |

The type parameter can be used for different btn types and input types.

The : marker can be used instead of the type parameter.

```vlpt
btn
type = "save"
@@
@@ btn
btn: "save"
@@
btn: "outline"
@@
input: "email"
@@
btn
style
 @ios { "bordered" }
@@
@@ btn
```

Where:
- The style argument block contains a sequence of styles as defined in the Vlpt style language. There is no selector because the style applies only the the outer block.










### Description markers in app language

| Marker        | Purpose                                                                          |
| :------------ | :------------------------------------------------------------------------------- |
| **`h`**       | Header. The Vlpt compiler determines the header level automatically.             |
| **`text`**    | Text block with optional styled sections and strings for whitespace declaration. |
| **`article`** | Like in HTML5.                                                                   |
| **`section`** | Like in HTML5.                                                                   |
| **`aside`**   | Like in HTML5.                                                                   |
| **`main`**    | Like in HTML5.                                                                   |
| **`nav`**     | Like in HTML5.                                                                   |










### Web markers in app language

These markers are used for web pages and search engine optimization (SEO).

| Marker       | Rationale for AI Optimization                   |
| :----------- | :---------------------------------------------- |
| **`title`**  | Translated to `<title>` element.                |
| **`meta`**   | Translated to `<meta>` element.                 |
| **`link`**   | Translated to `<link rel="canonical">` element. |
| **`script`** | Translated to `<script>` element.               |










### toc marker

The toc marker automatically generates a Table of Contents for the content in the outer block of the toc marker.


```
toc
 arguments for TOC creation.
@@
```

Where:
- The parameters and arguments for a toc block are not determined yet.










### note marker

The note marker indicates a footnote or tangential reference.
- **Web output**: Renders as a tooltip or a clickable number linking to an end-of-text section.
- **Print output**: Renders as a traditional footnote at the bottom of the physical page area.



#### Example

```vlpt
txt "Revenue grew by 50% "
note "Q3 Financial Report, 2024"
```










### ref marker

The ref marker creates a smart cross-reference to another element (like a figure or table).
- **Web output**: Renders as a hyperlink (e.g., "Table 1").
- **Print output**: Renders as a text reference with page location (e.g., "Table 1 on page 14").










### Parameters for printing

These parameters can be applied to any block (like `box`, `sect`, `table`) to control layout flow without writing CSS.
- **`keep`**: If set to `"true"`, the compiler ensures the block is not split across two pages (maps to `break-inside: avoid`).
- **`break`**: Forces a page break. Values: `"before"`, `"after"`.
- **`context`**: Marks the text content to be used in running headers. For example, `context="chapter"` allows a `run` marker to display the current chapter title.










## Vlpt style language

The style language allows to style UI blocks in a way that is similar to CSS.



### Style language file suffix

The Vlpt compiler recognizes the style language only in a file with `.style.vlpt` suffix in the file name.

The reasons for having a style file and not a style marker:
- The syntaxes of the style language and the app language are different. The style language is intentionally kept similar to CSS.
- A separate file allows to separate the selection of UI blocks for styling from the nesting of UI blocks for layout.



### Selector in style language

A selector is like a selector in CSS.



### Style block style language

A style block is delimited by the curly brackets `{` and `}`.

A style block is like declaration block in CSS.



### Style in style language

A style is the combination of property and value.

A style is like a declaration in CSS.



### Property in style language

A property is like a property in CSS.



### Value in style language

A value is like a value in CSS.



### Example content of a .style.vlpt file

Vlpt offers a style language that is similar to CSS.

Vlpt offer platform specific properties for styling.

Comments begin with //.

```vlpt
.primary-btn {
  // 1. Shared (Compiler attempts to map these to all platforms)
  // Web: color: white;
  // Android: ButtonColors(contentColor = White)
  // iOS: .foregroundColor(.white)
  color: white; 
  font-size: 16px;

  // 2. Web Specific override
  @web {
    cursor: pointer; // Valid style, but meaningless on touch
    user-select: none;
    transition: all 0.2s;
  }

  // 3. Apple Specific (SwiftUI Modifiers)
  // The compiler expects valid SwiftUI modifier strings here
  @ios {
    shadow: radius=5, y=2; // Specialized Vlpt property
    apple-visual-effect: blur;
  }

  // 4. Android Specific (Compose Modifiers)
  @android {
    elevation: 4dp;
  }
}
```


### Import content of a style file

```vlpt
@import "URI"
```

Where:
- The URI must identify a .style.vlpt file. The content of the file.style.vlpt is copied into the importing file.
- The @import is different from @import in CSS because @import in the style language is done statically and not at runtime.  

@import is required to use styles from other files. There is no implicit inheritance or overriding of styles from different files.



### Style overriding

Within the same style file: A later declared style overrides a previously declared style.



#### Implicit style classes in Vlpt

Vlpt offers the following implicit style classes in the app language:
- Class b for bold.
- Class center.
- Class i for italic.
- Class t for line-through.
- Class u for underline.

The implicit style classes can be overridden.










## Editor for Vlpt text



### Dot marker

`.` is the dot marker.

The dot marker should be immediately replaced by the tool by another marker.

The dot marker is not a valid marker in Vlpt text.



#### Dot for li

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



#### Dot for tr

```vlpt
table
.
```

Replaced by:

```vlpt
table
tr
@@ tr
```



#### Dot for th

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
@@ th
```



#### Dot for th

```vlpt
table
tr
th
 content
@@
.
```

Replaced by:

```vlpt
table
tr
th
 content
@@
th
@@ th
```



#### Dot for td

```vlpt
table
tr
td
 content
@@ td
.
```

Replaced by:

```vlpt
table
tr
td
 content
@@ td
td
@@ td
```










---

Copyright &copy; Gerhard Piette. All rights reserved.




