# Optimal number regex










## Question

give the rust regexes so that the number spec is optimal for AI.
- rust regex for unsigned integer
- rust regex for signed integer
- rust regex for floating point number
- rust regex for number with scientific notation










## Reply of Gemini 3 Pro

To make the number specification "optimal for multi-modal communication between humans and AI", the regexes should be strict and unambiguous. This prevents "hallucinations" in AI interpretation (e.g., confusing `1,000` as a coordinate vs. a thousand) and aligns with the Vlpt goal of supporting "simpler programs".

Here are the optimal Rust regexes. These patterns use `[0-9]` instead of `\d` to enforce strict ASCII digits, ensuring high compatibility with code parsers and avoiding Unicode normalization issues.

### 1\. Unsigned Integer

Matches strict positive whole numbers.

```rust
r"^[0-9]+$"
```

### 2\. Signed Integer

Matches whole numbers with an optional `+` or `-` sign.

```rust
r"^[+-]?[0-9]+$"
```

### 3\. Floating Point Number (Standard)

Matches decimal numbers. This pattern requires at least one digit before and after the dot (e.g., `0.5` not `.5`) to minimize ambiguity for tokenizers.

```rust
r"^[+-]?[0-9]+\.[0-9]+$"
```

### 4\. Number with Scientific Notation

Matches numbers with an exponent. This covers integer-scientific (`1e10`) and float-scientific (`1.5E-10`) formats.

```rust
r"^[+-]?[0-9]+(?:\.[0-9]+)?[eE][+-]?[0-9]+$"
```

-----

### Why these are "Optimal for AI" in Vlpt

  * **No Underscores:** Vlpt recommends avoiding underscores in names to save "AI context tokens". These regexes strictly exclude underscores (like `1_000`) for the same reason—keeping tokens dense and standard.
  * **Determinism:** They resolve the Vlpt "declared in any sensible way" ambiguity by enforcing a standard JSON-compatible format.
  * **Simplicity:** They avoid look-arounds, making them performant and safe for "simpler programs" that might be parsing the Vlpt output.

**Would you like me to construct a "Combined Number" regex that matches any valid number from these categories for the compiler?**



