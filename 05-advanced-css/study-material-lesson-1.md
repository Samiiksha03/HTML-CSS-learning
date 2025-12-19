# Module 5: Advanced CSS

## Lesson 1: CSS Variables (Custom Properties)

### 1. Objective
Learn to store values (colors, sizes) in **Variables** so you can reuse them and change them instantly.

### 2. Why it matters for React ⚛️
**React Rule:** Dynamic Theming.
*   **Dark Mode:** Instead of writing 2 separate CSS files (one for light, one for dark), we just change the *values* of the variables.
*   **Global Themes:** If your marketing team says "Change our brand blue to purple", you change it in **one place** (`:root`), and every button, link, and border in your entire React app updates instantly.

### 3. Simple Explanation (ELI5)
Imagine you have 100 buckets of paint.
*   **Old Way (Hardcoded):** You pour "Blue Paint" into every single bucket manually. If you want to change to "Red", you have to empty and refill all 100 buckets.
*   **New Way (Variables):** You connect all 100 buckets to a **Main Hose**. You pour "Blue Paint" into the hose. All buckets fill with Blue. If you want Red, you just change what you pour into the hose.

### 4. Runnable Code Example
```html
<!DOCTYPE html>
<html>
<head>
<style>
  /* 1. DEFINE VARIABLES (The Hose) */
  :root {
    --main-color: #0984e3; /* Blue */
    --box-size: 100px;
  }

  /* 2. USE VARIABLES (The Buckets) */
  .box {
    background-color: var(--main-color); /* Use the variable */
    width: var(--box-size);
    height: var(--box-size);
    margin: 10px;
  }

  .text {
    color: var(--main-color); /* Use it again! */
    font-weight: bold;
  }
</style>
</head>
<body>
  <div class="box"></div>
  <div class="box"></div>
  <p class="text">I am the same color!</p>
</body>
</html>
```

### 5. Line-by-Line Explanation
*   `:root`: This is the highest level (the `<html>` tag). Variables defined here are visible everywhere.
*   `--main-color`: Variable names MUST start with two dashes `--`.
*   `var(--main-color)`: This is how you *read* the value. It grabs whatever is currently inside `--main-color`.

### 6. Real-World Scenarios
1.  **Dark Mode:**
    *   Light: `--bg: white; --text: black;`
    *   Dark: `--bg: black; --text: white;`
2.  **Brand Spacing:** `--spacing-md: 16px;`. Use this for all margins. If you want more space later, change it to `20px` globally.

### 7. Real Website Example
*   **YouTube:** When you toggle "Dark Theme", YouTube doesn't load a new website. It just changes the CSS variables on the `<html>` tag from "Light Values" to "Dark Values".

### 8. Practice Task
1.  Open `lesson-1-variables.html`.
2.  You will see a "Theme Switcher" demo.
3.  **Task:**
    *   Define `--bg-color: white` and `--text-color: black` inside the `:root`.
    *   Update the `body` to use `var(--bg-color)` and `var(--text-color)`.
    *   Inside the `.dark-mode` class, redefine the variables to be Black and White.
4.  **Result:** Clicking the button will toggle the class, and the colors should flip instantly!

### 9. Quiz
(I will ask you this after you finish the practice task!)

### 10. DOM Explanation (ELI5) - "The Bucket Cascade" 🪣

**How the Browser handles Variables:**
1.  **Inheritance:** Variables flow down the DOM tree like water. If you define `--color: blue` on the `<body>`, every child inside the body can see it.
2.  **The Override:** If you have a specific child that needs to be different, you can redefine the variable *just for that child*.
    ```css
    .special-card {
      --color: red; /* Only red inside this card */
    }
    ```
3.  **React & Dynamic Updates:**
    *   You can update CSS variables using JavaScript: `document.documentElement.style.setProperty('--color', 'purple')`.
    *   This is super fast because the browser just repaints the pixels without needing to rebuild the React component tree.

### 11. Interview Questions 🎤
*   **Q: What is the difference between CSS Variables and SASS/SCSS Variables?**
    *   **A:**
        *   **SASS Variables (`$color`)**: Compiled away before the browser sees them. You cannot change them live in the browser (e.g., with JS).
        *   **CSS Variables (`--color`)**: Live in the browser (DOM). You can update them instantly with JavaScript or Media Queries.
*   **Q: What is the scope of a CSS variable defined in `:root`?**
    *   **A:** Global scope. It can be accessed by any element on the page.
