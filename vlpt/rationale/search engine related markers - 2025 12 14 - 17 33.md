# Search engine related markers






## Question

Generate a section with optimal search engine related markers 





## Reply of Gemini 3 Pro

Here is a generated section defining optimal SEO markers for Vlpt. This section adheres to the Vlpt syntax specifications (markers, parameters, blocks) and addresses the 2025 SEO standards identified in the analysis (Schema/JSON-LD, semantic structure, and critical metadata).

-----

## Markers for Search Engine Optimization (SEO)

To optimize Vlpt output for search engines (SEO), specific markers are required to control document metadata, semantic structure, and machine-readable structured data.

### Document Metadata

These markers control the `<head>` of the compiled HTML document. They are critical for ranking and click-through rates (CTR).

| Marker | Behavior |
| :--- | :--- |
| **`title`** | **Page Title**. The most critical SEO signal. Sets the browser tab title and search result headline. |
| **`meta`** | **Metadata**. Defines description, viewport, and robots directives. <br>*Params:* `name`, `content`. |
| **`link`** | **Resource Link**. Defines canonical URLs to prevent duplicate content issues. <br>*Params:* `rel`, `href`. |

#### Example

```vlpt
title "2025 Guide to Sustainable Energy"
meta name="description" content="A comprehensive guide to solar and hydrogen fuel technologies."
link rel="canonical" href="https://example.com/energy-guide"
```

### Structured Data (Schema)

The `schema` marker allows the injection of JSON-LD (JavaScript Object Notation for Linked Data). This is the standard for 2025 to help AI and search engines understand entities (People, Products, Events).

The content of a schema block must be valid JSON text.

#### Example

```vlpt
schema
 {
   "@context": "https://schema.org",
   "@type": "Article",
   "headline": "2025 Guide to Sustainable Energy",
   "author": {
     "@type": "Person",
     "name": "Dr. Sarah Connors"
   }
 }
/
```

### Semantic Containers

These markers replace generic `col` or `row` blocks to provide semantic meaning to the layout. Search engines use these to distinguish the main content from navigation and ads.

| Marker | Behavior |
| :--- | :--- |
| **`main`** | **Primary Content**. The unique content of the page. Contains the `art` or `sect`. |
| **`nav`** | **Navigation**. Links to other pages or sections. |
| **`aside`** | **Sidebar**. Content tangentially related (ads, biography, related links). |
| **`art`** | **Article**. Self-contained content (blog post, news item). |
| **`sect`** | **Section**. A thematic grouping of content, typically with a heading. |

#### Example

```vlpt
nav
 list
  item "Home"
  item "About"
 /
/

main
 art
  head "The Future of Hydrogen"
  txt
   Hydrogen fuel cells are becoming...
  /
 /
/
```

### Semantic Text Modifiers

These markers add context to specific data points within the text flow.

| Marker | Behavior |
| :--- | :--- |
| **`time`** | **Timestamp**. Machine-readable date/time. <br>*Param:* `val` (ISO 8601 format). |
| **`mark`** | **Highlight**. Text that should be highlighted for relevance. |

#### Example

```vlpt
txt
 Published on [time val="2025-05-12" "May 12th"]
/
```