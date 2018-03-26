## Cleaning the list

If your user wants to empty their to-do list (say they've been playing with it and added a lot of stuff that's not real), you can let them do that. It's pretty easy actually! All you need to do is empty the ordered list in the HTML. 

+ To empty the *ol* in the HTML isn't too tricky. Just add the following code into the end of your *emptyList* function:

```JavaScript
  document.getElementById("todo").innerHTML = ""
```

This tells JavaScript to get the to-do list and remove all the HTML inside it. That removes all the `<li>` tags, which are the to-do items!

Now, what about those crossed-out items? It's going to get very messy if you don't let users clean them up too. They all have the same **class**—`completed`—so you can use that to pick out the items to remove by selecting based on **class** instead of **id**.

+ Change `clearCompletedToDoItems` like this:

```JavaScript
  function clearCompletedToDoItems() {
    var items = document.getElementsByClassName("completed")
    for(var i=0; i<items.length; i++){
      items[i].remove()
    }
  }
```

This code is slightly tricky, but it's getting an a list of all the HTML **elements** with the `completed` **class** and then using a `for` loop