## Adding to-dos

So, your to-do list works now, but it's always the same. You can fix that! The “Add” button already calls a **function**, you just need to make that **function** do something.

+ Go to your `to-do.js` file and change the code in `addToDoItem` to get the text from the text field \(named “new-todo”\) and alert it to check you're getting it:

```JavaScript
   itemText = document.getElementById("new-todo").value
   alert("Item added: "+itemText)
```

+ Type something into the text field and click the "Add" button. You should see what you typed pop up in an **alert**.

+ The next step is to get that text onto the to-do list. You'll need a **function** that gets the HTML for the new item and adds it to the end of the list. So, change the `newToDoItem` to have this code inside it:

```JavaScript
   var newItem = {
                "text": itemText,
                "completed": completed
            } // make parameters into a toDoItem
   toDoItems.push(newItem); //use the push function: put newItem at the end of toDoItems
   var toDoList = document.getElementById("todo")
   var itemHTML = getToDoItemHTML(newItem)
   toDoList.append(itemHTML)
```

+ Now, go back to `addToDoItem` and change it again, removing the **alert** and calling `newToDoItem` like this:

```JavaScript
    newToDoItem(itemText,false)
```

### Don't repeat yourself!

+ You can also use `newToDoItem` in `loadList` to reduce the amount of code you've got to manage. You can replace all the code in the **function** with this:

```JavaScript
    newToDoItem("My",false)
    newToDoItem("to-do",true)
    newToDoItem("list",false)
```

You've gone from 17 lines of code to 3, and that's the power of **functions**! Try to understand how this works and how it's doing the exact same job as the old version of `loadList` was.



