## Save the list
To make your to-do list even more useful, you can save it to the **local storage** on the user's computer. Then, as long as they open it in the same browser the next time, it will remember their to-do list!

There are two parts to this: saving the list and, if it's there, loading it again when the page is reloaded.

This gets a bit tricky: local storage can't store HTML, so you need to take the HTML code and turn it into pure JavaScript. To do this, you'll need an **array**.

### Arrays
An array is a special kind of variable that's a list of variables. You can create one with square brackets `[]`, and add items to it with the `push` method. You can remind yourself what a specific array item is using `alert` and the item's **position** in the array. Note that JavaScript starts counting at `0`!

```JavaScript
var myArray = [];
myArray.push("something to store");
myArray.push("something else to store");
alert(myArray[0]);
//This will alert "something to store"
```

Next, you need to **loop** over the `toDoList` list and add each item to the array. Remember that you need to store not just the task, but also whether or not it's completed. The best way to do this is using JavaScript **objects**. 

### JavaScript objects
An object is set of **properties** and **values**. You create one like this:

```JavaScript
var toDoInfo = {
    "task": "Thing I need to do",
    "completed": false
};
```

Once you've converted all the to-do items into objects, you just need to save them to local storage. Local storage can only store strings, but luckily JavaScript can **stringify** an array for you!

Time to try it all out!

### Putting it all together
--- task ---
Update the `saveList` function to:
  - Make an array
  - Use a `for` loop to put every item in `toDoList` into the array as an object 
  - Stringify the array and store it in local storage with the **key** `toDos`

```JavaScript
function saveList() {
    var toDos = [];

    for (var i = 0; i < toDoList.children.length; i++) {
        var toDo = toDoList.children.item(i);

        var toDoInfo = {
            "task": toDo.innerText,
            "completed": toDo.classList.contains("completed")
        };

        toDos.push(toDoInfo);

    }

    localStorage.setItem("toDos", JSON.stringify(toDos));
}
```
--- /task ---
