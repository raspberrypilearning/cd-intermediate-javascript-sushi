## Add to-do items
Time to get the first of those buttons working properly! This step will show you how to make it add a to-do item to the list.

### HTML lists
You're going to use a tiny bit of HTML in this step. The list is an **ordered list** — that means it's numbered. The HTML tag for an ordered list is `<ol>`, and each individual **list item** needs an `<li>` tag.

### Adding list items
The page came with the `<ol>` ordered list, so you just need to write some JavaScript to add `<li>` tags for each new to-do item. The user should be able to enter text in the box on the page, and then click the **Add** button to see it appear on the list as a numbered item.

--- task ---
First, just like you did with the buttons, create variables to select the text box and the list. They already have the Ids `todo-entry-box` and `todo-list`.

```JavaScript
var toDoEntryBox = document.getElementById("todo-entry-box");
var toDoList = document.getElementById("todo-list");
```
--- /task ---

--- task ---
Now you can easily access the box and the list from inside your program.

Create a function called `newToDoItem` to add an item to the list. This function will need to know two things:
  - What is the text of the item?
  - Should the item be marked as completed?

Of course, no new to-do item would ever be complete, but you're planning ahead here: you'll be able to use the same function again when you're loading a saved list that has some completed items on it!

```JavaScript
function newToDoItem(itemText, completed) {
    var toDoItem = document.createElement("li");
    var toDoText = document.createTextNode(itemText);
    toDoItem.appendChild(toDoText);

    if (completed) {
        toDoItem.classList.add("completed");
    }

    toDoList.appendChild(toDoItem);
    toDoItem.addEventListener("dblclick", toggleToDoItemState);
}
```

--- /task ---

--- collapse ---

---
title: “What is the function doing?”
---
This new function does a few things.

This bit of code:
```JavaScript
var toDoItem = document.createElement("li");
```
creates an `li` element to use as your new list item.

This bit of code:
```JavaScript
var toDoText = document.createTextNode(itemText);
```
creates a **text node** — a special container for text that you want to put inside a HTML element using JavaScript — and fills it with the contents of the `itemText` variable that is **passed** into the function.

The `appendChild` function you're using here:
```JavaScript
toDoItem.appendChild(toDoText);
```
takes the element, or text node, that you pass to it (in this case `toDoText`), and puts it inside `toDoItem`. If there are already elements inside that one, the one you're adding now will be last.

This bit:
```JavaScript
if (completed) {
    toDoItem.classList.add("completed");
}
```
checks if the value for the `completed` variable that was passed to `newToDoItem` is `true`. If it is, then it will add the **class** `completed` to the `li` element, which will change how it looks on the page. In `style.css`, there are special styling rules for `li` tags with the `completed` class in `style.css` — check them out, and change them if you like!

Just like before, here `appendChild` :
```JavaScript
toDoList.appendChild(toDoItem);
```
puts `toDoItem` (the `<li>` element) inside of `toDoList` (the `<ol>` element).

Finally, this line of code:
```JavaScript
toDoItem.addEventListener("dblclick", toggleToDoItemState);
```
attaches an event listener for a **double-click** to the `toDoItem`, and tells it to call a function named `toggleToDoItemState` in response. You'll be creating that function with the next card!
--- /collapse ---

--- task ---
Now, connect to the function to the **Add** button: just change your `addToDoItem` function to get the text from the box and pass it to the `newToDoItem` function you've just created.

```JavaScript
function addToDoItem() {
    var itemText = toDoEntryBox.value;
    newToDoItem(itemText, false);
}
```
Since a new to-do item is never complete, you can always pass `false` to the `completed` parameter of the `newToDoItem` function.
--- /task ---

Now try adding a to-do to the list!
