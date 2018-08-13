## Completing items
There's not much point in a todo list if you can't mark things off it! Time to add that!

You've already setup the listener for a double click on each todo item. All you need to do is setup a function that will toggle between complete and not complete when that double click happens.

Remember that you're using the `complete` class to mark items complete. Not having that class means they're not complete. All your function needs to do is add and remove the class from the item's **class list**, adding it if it's not there and removing it if it is. 

### this
The tricky bit is knowing *which* item to toggle the class on. You'll need to use a new JavaScript **keyword** to identify the item that was clicked: `this`. 

The `this` keyword is a complicated part of JavaScript, but all you need to know for now is that, when used with a function called by an event listener, it means 'the element the listener was bound to'. So you can use `this` to identify the specific `<li>` that was clicked.

--- task ---
Add the `toggleToDoItemState` function to your script like so:

```JavaScript
function toggleToDoItemState() {
    if (this.classList.contains("completed")) {
        this.classList.remove("completed");
    } else {
        this.classList.add("completed");
    }
}
```
--- /task ---