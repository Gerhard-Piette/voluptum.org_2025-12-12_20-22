# history of Vlpt










## 2025 12 14

Major breaking changes.

Vlpt comprises 3 languages:
- program language
- net language
- app language
 
Changed purpose of Vlpt.

Added:
- mod marker
- Type
- Module
- Functions
- Type parameter
- ...










## 2025 12 14 - 14 44

- Again memo because AI makes a distinction between doc and memo.
- Removed HTML as basis. Now: All tags are chosen by Gemini 3 Pro so that Vlpt is optimal for the intended usage. 










## 2025 12 14

Major breaking changes.

### Implementation

- Probably with Vue.js for performance, features (no build step like svelte and solid), and libraries.
- With paged.js and Gotenberg for printing.

### Block system

- Most markers are names of block types and parameters.

### Template system

- Vlpt is Vlpt first and only. Vlpt can import only Vlpt text.
- Vlpt is not an orchestrator.
- Vlpt does not offer computation, branching, and iteration like other template systems.
- The Vlpt compiler offers an API that allows to create Vlpt blocks and to pass arguments to block parameters.
- No if marker.
- No else marker.
- No for marker.
- No code.
- No variables except parameters.

### Package system

- Filesystem based.
- import is used as alias for a folder of file or package.

### Removed markers

- Removed com marker.
- Removed do marker.
- Removed let marker.
- Removed def marker.
- Removed = marker.
- Removed private marker.
- Removed , marker.
- Removed memo marker.

### Added concepts and markers

- Parameter
- Argument
- param marker for implicit parameter.
- css marker
- Block content
- Inner block
- Outer block
- Template system
- HTML in Vlpt
- CSS in Vlpt
- UI system
- Modifier

### Improved

- Dot marker. Before: smart marker.
- Doc marker










## 2025 12 13

- Changes to improve Vlpt for AI according to Gemini 3 Pro:
    - Replaced # comment with // comment.
    - Strict closing of blocks.
    - No context dependent use of :.
    - Replaced "end" with "/..." to close a block. 
    - Added allowed characters of the Z and C category.  
    - Removed h, hh, and similar markers.
    - Removed the _ marker.
    - Added [...] for declaration of a styled section in a line with space marker. 
    - Added the pre marker.
- Added com marker for components.
- Replaced presented output with printed output.
- Added def marker.
- Added do marker.










## 2025 12 12

- I had the idea of markers this morning.
- I had the idea of using the name Vlpt for Voluptum Script this morning.






