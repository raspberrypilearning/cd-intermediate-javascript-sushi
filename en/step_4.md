## Add action to your buttons

The code you've got includes three files, which you can see as tabs in the trinket window:
  - `index.html` — a HTML file that tells the page what should be on it
  - `style.css` — a CSS file that tells the page what it should look like: where things should be, what size and colour they should be, etc.
  - `script.js` — a JavaScript file that tells the page what to do; you'll be doing most of your coding in this file

If you look at the page, you'll see it has four buttons:

  - An **Add** button for adding new to-do items
  - A **Clear Completed** button for clearing items that you've marked as finished
  - An **Empty List** button for completely emptying the to-do list
  - A **Save List** button for saving what's on the list

Of course, since you haven't written any code yet, right now none of them do anything!

Since you want to make the page **do** something, you need to click on the tab for the `script.js` file and add some code in there. These instructions will show you how to set up the **Add** button, and then you can set up the others by yourself.

JavaScript needs to be told which parts of the HTML page are important, and which interactions of a user with these parts it should react to. In this case, you want to tell it about the **Add** button, and tell it to react when the user clicks this button.

### Getting the button
--- task ---
Start by making a variable for the button and telling JavaScript to get the **element** from the HTML **document** that has the **Id** `add-button`. 

```JavaScript
var addButton = document.getElementById("add-button");
```
--- /task ---

An Id is a unique label for a part of a web page, and when we created the starter page, we gave a label to each of the buttons. You can see them if you look at `index.html`.

### Listening for the click
--- task ---
Now connect your button to a **event listener**, so JavaScript will 'listen' for a particular kind of event and then run a function when it 'hears' it. In this case, the event is a click. Do this with the `addEventListener` function, like this:

```JavaScript
addButton.addEventListener("click", addToDoItem);
```
--- /task ---

This listener will wait for a click on `addButton`, and when it 'hears' the click, it will react by running the `addToDoItem` function. Of course, it won't work just yet, since you haven't written an `addToDoItem` function yet!

### Creating the function
Later in the project you'll be writing code for your functions so that they add to-do items, clear the list, save it, etc. But for now, you just want to check that you've connected your event listeners properly. 

--- task ---
Create your `addToDoItem` function so that it will pop up an alert message telling the user which button they've clicked.

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
Connect the **Clear Completed** button — which has the Id `clear-completed-button` — to an alerting function called `clearCompletedToDoItems`.
--- /task ---

--- task ---
Connect the **Empty List** button — which has the Id `empty-button` — to an alerting function called `emptyList`.
--- /task ---

--- task ---
Connect the **Empty List** button — which has the Id `save-button` — to an alerting function called `saveList`.
--- /task ---

--- hints ---
--- hint ---
For each of the buttons you need to:

  - Create a variable and get the button using its Id in the HTML file
  - Add an event listener to the variable that listens for the click event and, upon hearing it, calls an appropriately named function
  - Create the appropriate function (e.g. `clearCompletedToDoItems`) and code it to alert the user about which button they've clicked

--- /hint ---
--- hint ---
The code below the `addButton` section is what you need to add:

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
