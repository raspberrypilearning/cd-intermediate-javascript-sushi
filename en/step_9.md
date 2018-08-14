## Loading the list
To load the list you need to reverse everything you did to save it, but you also need to check if there's anything to load first. You do this by checking if the key doesn't have a `null` value. **Null** is just a fancy word for empty, or nothing.

--- task ---
Create a `loadList` function and have it:
  - check if the `toDos` key exists in local storage
  - if it does, load it into a variable as an array
  - loop over the array and use `newToDoItem` to create new todos for each item on the list

```JavaScript
function loadList() {
    if (localStorage.getItem("toDos") != null) {
        var toDos = JSON.parse(localStorage.getItem("toDos"));

        for (var i = 0; i < toDos.length; i++) {
            var toDo = toDos[i];
            newToDoItem(toDo.task, toDo.completed);
        }
    } 
}
```
--- /task ---

--- task ---
Call the `loadList` function after you've created it.
```JavaScript
loadList();
```
--- /task ---
--- challenge ---
## Challenge: Example todo items
See if you can make the `loadList` function create some example todos if there aren't any saved.
--- /challenge ---