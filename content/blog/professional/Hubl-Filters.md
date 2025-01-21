---
title: 'HubL Filters for JavaScript Developers'
date: 2025-01-21 14:54:00
category: 'Professional Projects'
draft: false
---

Shifting my mental model from JavaScript object prototype methods to HubL's pipe syntax has significantly improved my experience with HubSpot development, making it more enjoyable and intuitive as a JavaScript developer. Since I haven’t come across others making this comparison, I wanted to share it. Understanding this parallel would have helped me transition from a JavaScript mindset to a HubL mindset much faster.

For JavaScript developers, HubL filters are comparable to array or string methods in JavaScript, but they use pipe syntax instead of dot notation. Here's the mental model:

```javascript
// JavaScript way
someValue.method(args)

// HubL equivalent
{{ someValue|filter(args) }}
```

For example, these mappings show the parallel:

```javascript
// JavaScript                  // HubL
array.length                   // items|length
string.toLowerCase()           // string|lower
number.toFixed(2)             // number|round(2)
array.join(", ")              // array|join(", ")
```

You can also chain filters in HubL just like you chain methods in JavaScript:

```javascript
// JavaScript
someString.trim().toLowerCase().slice(0, 5)

// HubL equivalent
{{ someString|trim|lower|slice(0, 5) }}
```

The key differences to keep in mind:

1. HubL uses `|` instead of `.` for method calls
2. Filters are functions that transform data, similar to JavaScript's pure functions
3. Like JavaScript's method chaining, filters are processed left to right
4. Some filters take arguments (like `round(0, "ceil")`), similar to JavaScript method parameters

Think of filters as a functional programming pipeline where each filter transforms the data and passes it to the next filter in the chain.
