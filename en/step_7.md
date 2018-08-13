## Clearing the list
Once you've marked items completed, you want a way to remove all those completed items from the list. Also, if you come back to your list after a long time, or just want to work on something totally new, you might want to clear everything off it. To do this you just need to update two functions you've already connected to buttons: `clearCompletedToDoItems` and `emptyList`.

### Clearing completed items
Just like you can select all the elements in a HTML document, you can select the elements *inside* any other element. Elements inside another element are called the **children** of that element. Likewise, just like you can select them by id, you can select them by class too.

--- task ---
In order to clear completed items, update `clearCompletedToDoItems` to select items inside `toDoList` by the `completed` class and then loop through them and remove them. 

```JavaScript
function clearCompletedToDoItems() {
    var completedItems = toDoList.getElementsByClassName("completed");

    while (completedItems.length > 0) {
        completedItems.item(0).remove();
    }
}
```
--- /task ---

Notice that you're always removing the item at position `0` in the list. This is because the list gets shorter every time you remove an item and this way you'll eventually remove them all!

### Clearing everything
--- task ---
To clear everything on the list, do the same thing as above, but select *all* the children of `toDoList`.

```JavaScript
function emptyList() {
    var toDoItems = toDoList.children;
    while (toDoItems.length > 0) {
        toDoItems.item(0).remove();
    }
}
```
--- /task ---