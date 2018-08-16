## Completing items
There's not much point to a to-do list if you can't mark items as done! Time to add that functionality.

You've already set up the listener for a double-click on a to-do item. All you need to do now is write a function that will toggle the item between complete and not complete when that double-click happens.

Remember that you're using the `complete` class to mark items as complete. Not having that class means they're not complete. So all your function needs to do is add or remove the class from the item's **class list**, either adding it if it's not on the list yet, or removing it if it is. 

### this
The trick is knowing on which item to toggle the class. To identify the item that was clicked, you'll need to use a new JavaScript **keyword**: `this`. 

How exactly the `this` keyword works is a bit complicated, but all you need to know here is that, when it's used with a function called by an event listener, it means 'the element the listener was bound to'. So you can use `this` to identify the specific `<li>` item that was clicked!

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
