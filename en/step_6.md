## Completing items

Now you can load your to-do list and add items to it, but what's the point if you can't check them off when you've done them? Next up, you're going to do just that, and it'll be pretty easy. 

+ First, you need to connect double-clicking on a list item (`li` tag) to your `toggleToDoItemState` function. You can do this by having JavaScript **listen** for double-clicking on `li` tags and running a function that calls your `toggleToDoItemState` function. It looks like this:

```JavaScript
  document.getElementById("todo").addEventListener("dblclick",function(event){
    if(event.target && event.target.matches("li")){
      toggleToDoItemState(event.target)
    }
  })
```

What's happening here is:
1. JavaScript is **listening** to all double-clicks that happen on the `todo` list
2. If it “hears” one, it runs a **function**, into which it passes the details of the click `event`
3. If the `event` had a `target` (a thing that was clicked on) and that `target` matches `"li"`, which is the HTML tag for a **list item** then:
    * Run `toggleToDoItemState` and pass it the `event.target` information

+ Next, you need to update your `toggleToDoItemState` function so it adds the `completed` **class** (a HTML property—a **tag**, like `<li>` can have many **classes**) to the item that was double-clicked, which will put a line through it using some of my CSS code. Thankfully, in modern JavaScript, that's pretty simple! Just update this to `toggleToDoItemState`:
```JavaScript
  function toggleToDoItemState(target){
    target.classList.toggle("completed")
  }
```