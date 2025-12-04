# Module 3: Layout & Positioning

## Lesson 2: Floats & Clearfix

### 1. Objective
- Understand how `float` works (originally for text wrapping).
- Learn how to fix the "Parent Collapse" bug using `clear` or `flow-root`.

### 2. Why it matters for React ⚛️
**React has moved on.**
In modern React development (2024+), using `float` for the main layout of your page is considered a "Code Smell" (bad practice).

**React Rule:** Use Flexbox/Grid for layout.
**Exception:** The *only* valid reason to use `float` in a modern React component is if you specifically need text to wrap around an image (like in a `<BlogPost />` component).

**React Syntax:** `className` vs `class`
**The Rule:** In HTML we write `<div class="box">`. In React (JSX), we MUST write `<div className="box">`.
**Why:** `class` is a reserved word in JavaScript (used for creating classes). Since JSX is JavaScript, we have to use `className`.

### 3. ELI5 Explanation
Imagine a **Newspaper**.
-   You have a photo of a cat.
-   You want the article text to flow *around* the cat photo, not start below it.
-   **`float: left`** tells the photo: "Go to the left side, and let the text flow around your right side."

**The Problem (The Ghost Parent):**
When you float an element, it's like it levitates. If a Parent Box contains *only* floating children, the Parent thinks it's empty! It collapses to height 0, and the background color disappears. This is a famous CSS bug.

### 4. Code Example (The Fix)
To fix the collapsing parent, we used to use a "hack" called **Clearfix**. Today, we have a modern one-line fix: `display: flow-root`.

```css
/* The Image */
.cat-photo {
    float: left; /* Move to left */
    margin-right: 15px; /* Space for text */
}

/* The Parent Container */
.news-article {
    border: 1px solid black;
    /* MODERN FIX: This forces the parent to wrap around floating children */
    display: flow-root; 
}
```

### 5. Real-World Scenarios
1.  **Blog Posts:** An author's bio picture on the left with their bio text wrapping around it.
2.  **Magazine Layouts:** A "Pull Quote" floating to the right of the main article text.

### 6. Practice Task
1.  Open `lesson-2-floats.html`.
2.  Observe how the "Broken Parent" has no gray background (it collapsed!).
3.  Fix it by adding `display: flow-root;` to the `.broken-parent` class.
4.  Try changing the image float to `float: right`.

### 7. React Component Tip
When converting a floating layout to a React component (like a `ArticleCard`), you would typically rewrite the layout using **Flexbox** unless you specifically need the text-wrap effect.
-   **Old Way:** `float: left` for columns.
-   **React Way:** `<div style={{ display: 'flex' }}>` for columns.
