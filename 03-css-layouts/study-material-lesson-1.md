# Module 3: Layout & Positioning

## Lesson 1: Block vs. Inline & Positioning

### 1. Objectives
-   Understand the difference between "Block" and "Inline" elements.
-   Learn how to move elements around using `position` (Relative, Absolute, Fixed).

### 2. Relevance to React
In React, you build components. Some components (like a `<Card />`) stack on top of each other, while others (like a `<Badge />` or `<Icon />`) sit next to text. Understanding **Block vs. Inline** tells you *why* they behave that way.
**Positioning** is crucial for things like:
-   **Modals/Popups** (Fixed position)
-   **Notification Badges** on icons (Absolute position)
-   **Sticky Headers** (Sticky position)

### 3. ELI5 Explanation (Block vs. Inline)
Imagine your webpage is a piece of notebook paper.
-   **Block Elements (`<div>`, `<p>`, `<h1>`)**: These are like **paragraphs**. They always start on a new line and take up the full width of the page, from left to right. Even if you only write one word, they claim the whole line.
-   **Inline Elements (`<span>`, `<a>`, `<b>`)**: These are like **words** in a sentence. They sit next to each other on the same line. They only take up as much space as they need.

### 4. Code Example (Block vs. Inline)
```html
<!DOCTYPE html>
<html>
<head>
    <style>
        .block-box {
            background-color: #ffcccc; /* Light Red */
            border: 2px solid red;
            margin-bottom: 10px;
        }
        .inline-box {
            background-color: #ccffcc; /* Light Green */
            border: 2px solid green;
        }
    </style>
</head>
<body>
    <h3>Block Elements</h3>
    <div class="block-box">I am a DIV (Block). I take the full width.</div>
    <div class="block-box">I am another DIV. I start on a new line.</div>

    <h3>Inline Elements</h3>
    <span class="inline-box">I am a SPAN (Inline).</span>
    <span class="inline-box">I sit next to my neighbor.</span>
</body>
</html>
```

### 5. ELI5 Explanation (Positioning)
### 5. ELI5 Explanation (Positioning)
Let's try a different analogy: **Standing in a Line**.

1.  **Static (The Soldier)**
    *   **Scenario:** Imagine soldiers standing in a straight line for inspection.
    *   **Behavior:** They stand exactly where the sergeant tells them. They cannot step out of line. If Soldier A is first, Soldier B *must* be second.
    *   **In CSS:** This is the default. You cannot use `top`, `left`, `right`, or `bottom` to move them. They are locked in place.

2.  **Relative (The Ghost Spot)**
    *   **Scenario:** Imagine Soldier B decides to take one step forward.
    *   **The Magic Part:** The *spot* where Soldier B was standing stays reserved! Soldier C does **not** move up to fill the gap. It's like Soldier B left a "ghost" behind to save their seat.
    *   **In CSS:** You can move the element (using `top`, `left`, etc.), but it doesn't mess up the layout for anyone else. The space it used to occupy stays empty.

3.  **Absolute (The Sticker on a Box)**
    *   Now, imagine you have a small cardboard box (the "Parent") on your desk.
    *   You put a sticker (the "Element") on the top-right corner of that box.
    *   **Key Point:** The sticker doesn't care about the paper anymore. It only cares about the box. If you move the box, the sticker moves with it. It floats *on top* of everything else inside the box.

4.  **Fixed (The Sticker on your Glasses)**
    *   Imagine you put a sticker right on the lens of your glasses (or the computer screen).
    *   **Key Point:** No matter how much you scroll the page or look around, that sticker stays right in front of your eye. It never moves. This is perfect for "Chat" buttons or "Navigation Bars" that always stay visible.

### 6. Code Example (Positioning)
```html
<!DOCTYPE html>
<html>
<head>
    <style>
        .container {
            position: relative; /* The Anchor */
            width: 300px;
            height: 200px;
            border: 2px solid black;
            background-color: #f0f0f0;
            margin-top: 50px;
        }
        .box {
            width: 50px;
            height: 50px;
            color: white;
            display: flex;
            align-items: center;
            justify-content: center;
        }
        .static { background: gray; } /* Normal */
        
        .absolute { 
            background: red; 
            position: absolute; /* Ghost mode */
            top: 10px;
            right: 10px; /* Top-Right corner of container */
        }

        .fixed {
            background: blue;
            position: fixed; /* Stuck to screen */
            bottom: 20px;
            right: 20px;
            width: 100px;
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="box static">1</div>
        <div class="box static">2</div>
        <div class="box absolute">X</div> <!-- Floating in corner -->
    </div>

    <div class="box fixed">Chat</div> <!-- Always visible -->
</body>
</html>
```

### 7. Line-by-Line Breakdown
-   `position: relative;`: On the `.container`. This makes it the "anchor" for any absolute children inside it.
-   `position: absolute;`: On the Red Box. It ignores the other gray boxes and jumps straight to the coordinates we gave it (`top: 10px`, `right: 10px` inside the container).
-   `position: fixed;`: On the Blue Chat button. It ignores the container completely and positions itself relative to the **browser window**.

### 8. Practice Task
1.  Open `lesson-1-position.html`.
2.  Create a "Notification Badge" (a small red circle with a number).
3.  Position it on the top-right corner of a "Profile Picture" box using `absolute` positioning.
