## चीज़ें हटाए
एक बार जब आप आइटम को पूर्ण के रूप में चिह्नित कर लेते हैं, तो आप उन सभी पूर्ण आइटम को हटाने का एक तरीका चाहते हैं। Also, if you come back to your list after a long time, or if you just want to work on something totally new, you might want to clear out everything on it. To do this, you just need to update two functions you've already connected to buttons: `clearCompletedToDoItems` and `emptyList`.

### पूर्ण चिह्नित आइटम्स हटाएं
Just like you can select all the elements in an HTML document, you can select the elements **inside** any other element. Elements inside another element are called the **children** of that element. Likewise, just like you can select elements by Id, you can select them by class too.

--- task ---

In order to clear completed items, update the `clearCompletedToDoItems` function with code to select the children of `toDoList` (the items inside it) that have the `completed` class. Then **loop** over the selected items to remove them one by one.

```JavaScript
function clearCompletedToDoItems() {
    var completedItems = toDoList.getElementsByClassName("completed");

    while (completedItems.length > 0) {
        completedItems.item(0).remove();
    }
}
```

--- /task ---

You can see that the code always removes the item at list position `0`, the first item on the list. You need to use `0` to do this, because JavaScript starts counting at `0` and not `1`! You remove this item so that every time the loop runs, it removes the first item, so the list gets shorter and shorter. In this way, no matter how many completed items are on the list, the loop will eventually remove them all.

### Clearing everything

--- task ---

To clear everything off the list, do the same thing as above, but select **all** the children of `toDoList`.

```JavaScript
function emptyList() {
    var toDoItems = toDoList.children;
    while (toDoItems.length > 0) {
        toDoItems.item(0).remove();
    }
}
```

--- /task ---
