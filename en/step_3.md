## Wiring up buttons

Before getting into the details of how your application is going to work, you should connect all the buttons up to “dummy” functions, to make testing them easier.  

From the *Beginner JavaScript Sushi Cards*, you will hopefully remember that a JavaScript **function** definition looks like this:

```JavaScript
  function newToDoItem(itemText, completed) {
      alert("New item created: "+itemText+"  Completed state: "+completed);
  }
```

Almost all the **functions** you need are in the file already, though they don't do anything cool yet. They just send **alert messages** (pop-up boxes) telling you what **function** was called and what the values in the parameters were. Read through them to understand what's there. 

+ There's one missing, that you need to add. Create a new function in `to-do.js` that:
    1. Is called `toggleToDoItemState`
    2. Accepts a parameter: `listItem`
    3. When called, alerts the message `"Toggling state of item "+itemId`

+ Now you need to tell JavaScript to **listen** for a **click** on the buttons, then do something. Each of the buttons on the page has a unique `id`. You can use that `id` to tell **JavaScript** what to listen to. Add the following code instead of the `alert` into the `runWhenPageLoads` function:
```JavaScript
    document.getElementById("add-button").addEventListener("click", addToDoItem)
```
  
Because `runWhenPageLoads` is called at the end of the file, and the file is loaded at the end of the HTML page, `runWhenPageLoads` will, as you might guess, run once the page loads! This bit of code chains together a lot of functions with dots (`.`), where each function's is acting on the thing fetched by the function before it:
  1. Look in the `document`—the whole page
  2. Find the **element** (HTML tag) on that page that has “add-button” as its `id`
  3. Tell JavaScript to **listen** for the **click** action on the button and then run the `addToDoItem` function whenever it “hears” the action  

+ Reload `index.html` and click the button that says “Add”. You should see an **alert** message pop up!
  
+ Do the same for the other two buttons:
  * Connect `#clear-button` to `clearCompletedToDoItems`
  * Connect `#empty-button` to `emptyList`

+ Don't forget to test them!
