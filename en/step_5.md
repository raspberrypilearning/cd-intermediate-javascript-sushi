## Adding to-dos
Time to get the first of those buttons working! This step will show you how to add a to-do item to the list.

### HTML Lists
You're going to use a tiny bit of HTML in this step. The list is an **ordered list** — that means it's numbered. The HTML tag for an ordered list is `<ol>` and each individual **list item** is an `<li>` tag.

### Adding list items
 The page came with the `<ol>` so you just need to write some JavaScript to add `<li>` tags for each new todo item. The user should be able to enter text in the box on the page, click the 'Add' button and see it appear on the list as a numbered item.

--- task ---
First, just like you did with the buttons, create variables to select the text box and the list. They already have the ids `todo-entry-box` and `todo-list`.

```JavaScript
var toDoEntryBox = document.getElementById("todo-entry-box");
var toDoList = document.getElementById("todo-list");
```
--- /task ---

--- task ---
Now you can easily access the box and the list from inside your program.

Create a function called `newToDoItem` to add an item to the list. This function will need to know two things:
  - What is the text of the item?
  - Should the item be marked complete?
When adding a new todo it won't ever be complete, but this is planning ahead so you can use the same function again when you're loading a saved list!

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

Try adding a todo once you've filled it in!

--- collapse ---

---
title: “What is the function doing?”
---
This new function does a few things:
```JavaScript
var toDoItem = document.createElement("li");
```
Creates an `li` element to use as your todo.
```JavaScript
var toDoText = document.createTextNode(itemText);
```
Creates a **text node** — a special container for text that you want to put inside a HTML element using JavaScript — and fills it with the contents of the `itemText` variable that is **passed** into the function.
```JavaScript
toDoItem.appendChild(toDoText);
```
The `appendChild` function you're using here takes the element, or text node, that you pass to it (in this case `toDoText`) and puts it inside `toDoItem`. If there are already elements inside that one, the one you're adding will be last.
```JavaScript
if (completed) {
    toDoItem.classList.add("completed");
}
```
This bit checks if the value for the `completed` variable that was passed to `newToDoItem` is `true`. If it is, then it will add the **class** 'completed' to the `li` element, which will change how it looks on the page; We included some special styling rules for `li` tags with the 'completed' class in `style.css` — check them out, change them if you like!
```JavaScript
toDoList.appendChild(toDoItem);
```
Just like before, here `appendChild` is putting `toDoItem` (the `<li>` element) inside of `toDoList` (the `<ol>` element).
```JavaScript
toDoItem.addEventListener("dblclick", toggleToDoItemState);
```
Finally, this is attaching an event listener for a **double-click** to the `toDoItem` and telling it to call a function called `toggleToDoItemState` when it's clicked. You'll be making that one in the next step!
--- /collapse ---

--- task ---
Now, connect to the function to the add button, just change your `addToDoItem` function to get the text from the box and pass it to the `newToDoItem` function you've just created.

```JavaScript
function addToDoItem() {
    var itemText = toDoEntryBox.value;
    newToDoItem(itemText, false);
}
```
Obviously a new todo is never complete, so you can always pass `false` to the `completed` parameter of the `newToDoItem` function.
--- /task ---

Now try adding a todo to the list!