# HTML CODE EXPLANATION

**HTML Structure:**

* `DOCTYPE`: Declaration specifying the document type as HTML.
* `<html>`: The root element of the HTML document.
* `<head>`: Contains meta information about the document:
    * `<meta charset="UTF-8">`: Defines the character encoding as UTF-8.
    * `<meta name="viewport" content="width=device-width, initial-scale=1.0">`: Sets the viewport for responsive design, ensuring proper scaling on different devices.
    * `<title>To Do List</title>`: Sets the title of the webpage displayed in the browser tab.
    * `<link rel="stylesheet" href="style.css">`: Links the external CSS stylesheet named "style.css" for styling the app.
* `<body>`: Contains the visible content of the webpage.
* `<div class="container">`: A container element to hold the entire To Do List application.
    * `<div class="todo-app">`: The main application container.
        * `<h2>TO-DO List<img src="./images/note.png" alt="note"/></h2>`:
            * The heading "TO-DO List" with an image (presumably a note icon) next to it. The `alt` attribute provides alternative text for accessibility.
        * `<div class="row">`: A row container for user input.
            * `<input type="text" id="input-box" placeholder="Add your text here">`: An input field with the ID "input-box" for users to enter their to-do items. It has a placeholder text "Add your text here" to guide the user.
            * `<button onclick="addTask()">Add</button>`: A button with the text "Add" that triggers the `addTask` function (defined in JavaScript) when clicked. This likely adds the user-entered task to the list.
        * `<ul id="list-container">`: An unordered list element with the ID "list-container". This will hold the list items (to-do tasks) dynamically added using JavaScript.
            * Currently, it contains commented-out example list items with class "checked" (presumably for completed tasks).
* `<script src="script.js"></script>`: Links the external JavaScript file named "script.js" which likely contains the functionality for adding tasks, managing the list, and potentially styling elements using JavaScript.

# CSS CODE EXPLANATION

**Global Styles:**

* `*`: Applies styles to all elements by default.
    * `margin: 0; padding: 0;`: Resets default margins and paddings for a cleaner base layout.
    * `font-family:'Popins', sans-serif;`: Sets the preferred font family to "Popins" if available, otherwise falls back to a generic sans-serif font.
    * `box-sizing: border-box;`: Ensures that padding and border are included within the element's width and height calculations, preventing unexpected layout issues.

**Container Styles:**

* `.container`: Styles the main container element. 
    * `width: 100%;`: Stretches the container to fill the entire viewport width.
    * `min-height: 100vh;`: Sets the minimum height to 100% viewport height, ensuring it covers the entire visible area.
    * `background: linear-gradient(135deg, #153677,#4e085f);`: Creates a background gradient with two shades of blue, transitioning diagonally from left to right.
    * `padding: 10px;`: Adds some padding around the container for better visual separation.

**To Do App Styles:**

* `.todo-app`: Styles the main application area.
    * `width: 100%; max-width: 540px;`: Sets a flexible width that fills the container horizontally while maintaining a maximum width of 540px to prevent it from becoming too wide on larger screens.
    * `background: #fff;`: Sets a white background for the app itself.
    * `margin: 100px auto 20px;`: Applies margins for spacing:
        * `margin-top: 100px;`: Adds a top margin of 100px for vertical spacing from the top of the viewport.
        * `margin-left: auto; margin-right: auto;`: Uses `auto` margins on the left and right to horizontally center the app within the container.
        * `margin-bottom: 20px;`: Adds a bottom margin of 20px for spacing from other elements below.
    * `padding: 40px 30px 70px ;`: Adds padding on all sides with more padding on the bottom (likely for better visual balance).
    * `border-radius: 10px;`: Creates rounded corners for a softer look.

**Heading Styles:**

* `.todo-app h2`: Styles the main heading.
    * `color: #002765;`: Sets the text color to a dark blue.
    * `display: flex; align-items: center;`: Arranges the heading content horizontally (flexbox) and aligns it vertically within the heading element.
    * `margin-bottom: 20px;`: Adds bottom margin for spacing from the content below.
* `.todo-app h2 img`: Styles the image next to the heading.
    * `width: 45px;`: Sets the width of the image.
    * `margin-left: 10px;`: Adds left margin for spacing between the image and the text.

**Row Styles:**

* `.row`: Styles the row containing the input field and button.
    * `display: flex;`: Arranges the input field and button horizontally (flexbox).
    * `align-items: center;`: Aligns the content vertically within the row.
    * `justify-content: space-between;`: Distributes the content horizontally with space between the input field and button.
    * `background: #edeef0;`: Sets a light gray background for the input area.
    * `border-radius: 30px;`: Creates rounded corners for the input area.
    * `padding-left: 20px;`: Adds left padding for spacing within the row.
    * `margin-bottom: 25px;`: Adds bottom margin for spacing from the list below.

**Input Styles:**

* `input`: Styles the input field for adding tasks.
    * `flex: 1;`: Expands the input field to fill most of the row horizontally.
    * `border: none; outline: none;`: Removes default border and outline for a cleaner look.
    * `background: transparent;`: Makes the input field background transparent, revealing the background color behind it.
    * `padding: 10px;`: Adds padding for better readability of the text within the input field.

# JS CODE EXPLANATION

**Variable Assignments:**

* `inputBox`: Stores the reference to the input field element with the ID "input-box".
* `listContainer`: Stores the reference to the unordered list element with the ID "list-container" where tasks will be displayed.

**addTask Function:**

* Checks if the user entered anything in the input field.
  * If empty, an alert message appears prompting the user to enter a task.
  * If there's input:
    * Creates a new list item element (`<li>`) and stores it in the `li` variable.
    * Sets the inner HTML of the list item (`li.innerHTML`) to the value entered in the input field, effectively displaying the task as text.
    * Appends the newly created list item (`li`) to the `listContainer` element, adding it to the list.
    * Creates another element (`span`) to act as a delete button.
    * Sets the inner HTML of the `span` to the Unicode character for a close mark (&#x00d7;), creating a visual button-like element.
    * Appends the `span` element to the `li` element, placing the "delete button" next to the task.
* Clears the input field after adding the task.
* Calls the `saveData` function (presumably to save the updated list).

**Event Listener on List Container:**

* Attaches a click event listener to the `listContainer` element.
  * When an element inside the `listContainer` is clicked (`e.target`):
    * Checks if the clicked element is a list item (`LI`).
      * If yes, it toggles the "checked" class on the clicked list item, likely adding a strikethrough effect to mark the task as completed.
      * Calls the `saveData` function again (presumably to save the updated completion status).
    * Else if the clicked element is a `SPAN`:
      * Removes the parent element (the list item containing the task) of the clicked `SPAN` (the delete button), effectively deleting the task.
      * Calls the `saveData` function again (presumably to save the deletion).

**saveData Function:**

* Saves the current HTML content of the `listContainer` element (which holds the task list) in the browser's local storage under the key "data". This allows the application to persist the task list even after the page reloads.

**showTask Function:**

* Retrieves the data stored under the key "data" from the local storage.
* If data exists, it sets the inner HTML of the `listContainer` element to the retrieved data, effectively restoring the previously saved task list on page load.

