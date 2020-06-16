## Load the saved list
To load the list, you need to reverse everything you did to save it. But first, you need to check if there's anything to load. You do this by checking if the key you used to store the list doesn't have a `null` value. **'Null'** is just another word for 'empty', or 'nothing'.

--- task ---

Create a `loadList` function and have it:
  - Check if the `toDos` key exists in local storage
  - If it does, load it into a variable as an array
  - Loop over the array, and use `newToDoItem` to create new to-do items for everything in it

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

## Challenge: example to-do items

See if you can make the `loadList` function create some example to-do items if there aren't any saved.

--- /challenge ---
