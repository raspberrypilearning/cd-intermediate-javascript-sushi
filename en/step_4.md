## Wiring up buttons

The code you've got to start off with includes three files:
  - `index.html` — a HTML file that tells the page what should be on it.
  - `style.css` — a CSS file that tells the page what it should look like: where things should be, what size and colour they should be, etc.
  - `script.js` — a JavaScript file that tells the page what to do. You'll be doing most of your coding in this file.

If you look at the page, you'll see it has four buttons:

  - An 'Add' button for adding new to-dos
  - A 'Clear Completed' button for clearing to-dos that you've marked as finished
  - An 'Empty List' button for completely emptying the to-do list
  - A 'Save List' button for saving what's on the list

Of course, since you haven't written your program yet, right now none of them work!

Since you want to make the page *do* something, you need to click on the tab for `script.js` and add some code in there. These instructions will show you how to setup the 'Add' button and then you can do the others yourself.

JavaScript needs to be told which parts of the HTML page are important and what things that a user might do to them it should react to. In this case, you want to tell it about the 'Add' button and tell it to react when that button is clicked.

### Getting the button
--- task ---
Start by making a variable for the button and telling JavaScript to get the **element** from the HTML **document** that has the **id** `add-button`. 

```JavaScript
var addButton = document.getElementById("add-button");
```
--- /task ---

An id is a unique label for a part of a web page and when we made the starter page we gave one to each of the buttons. You can see them if you look at `index.html`.

### Listening for the click
--- task ---
Next connect your button to a listener, so JavaScript will 'listen' for a particular kind of event and then run a function when it 'hears' it. In this case, the event is a click. Do this with the `addEventListener` function, like this:

```JavaScript
addButton.addEventListener("click", addToDoItem);
```
--- /task ---

This listener will 'listen' for a click on `addButton` and will then run the `addToDoItem` function when it 'hears' the click. Of course, it won't work right now since you haven't written an `addToDoItem` function yet!

### Creating the function
Later in the project you'll be making functions that create todo items, clear the list, save it, etc. For now though, you just want to check that you've conencted your listeners properly. 

--- task ---
Make a function that will pop an alert to the user telling them which button they clicked.

```JavaScript
function addToDoItem() {
  alert("Add button clicked!");
}
```
--- /task ---

Now click the button and check if it works!

### Connect the other buttons
Now connect the other three buttons:

--- task ---
Connect the 'Clear Completed' button — which has the id `clear-completed-button` — to an alerting function called `clearCompletedToDoItems`.
--- /task ---

--- task ---
Connect the 'Empty List' button — which has the id `empty-button` — to an alerting function called `emptyList`.
--- /task ---

--- task ---
Connect the 'Empty List' button — which has the id `save-button` — to an alerting function called `saveList`.
--- /task ---

--- hints ---
--- hint ---
For each of the buttons you need to:

  - Create a **varaiable** and get the button in the HTML **document** using its **id**
  - Add an **event listener** to the **varaible**, listening for the **click event** and calling the appropriately named **function** when it hears it
  - Create the appropriate **function** (e.g. `clearCompletedToDoItems`) and code it to **alert** the user, telling them which button has been clicked

--- /hint ---
--- hint ---
Here you can see the code you need to add, below the code you've already written:

```JavaScript
var addButton = document.getElementById("add-button");
addButton.addEventListener("click", addToDoItem);
function addToDoItem() {
    alert("Add button clicked!");
}

var clearButton = document.getElementById("clear-completed-button");
clearButton.addEventListener("click", clearCompletedToDoItems);
function clearCompletedToDoItems() {
    alert("Clear button clicked!");
}


var emptyButton = document.getElementById("empty-button");
emptyButton.addEventListener("click", emptyList);
function emptyList() {
    alert("Empty button clicked!");
}


var saveButton = document.getElementById("save-button");
saveButton.addEventListener("click", saveList);
function saveList() {
    alert("Save button clicked!");
}
```
--- /hint ---
--- /hints ---