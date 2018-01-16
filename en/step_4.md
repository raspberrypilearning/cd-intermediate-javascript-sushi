## Creating a list

Right now, the to-do list on the page is just some HTML that I put in there so you'd have something to look at! Time to make it yours: 

+ Go into `index.html` and delete the four lines that start with `<li>` tags. If nothing's changed, they'll be lines 23–26. Then reload `index.html` in your browser. It looks a little empty, but you'll fix that soon!

+ Inside the `runWhenPageLoads` function, call the `runWhenPageLoads` function. Reload `index.html` to check that it's being called. If you got the **alert** then you're all set!

Now you need to make the `loadList` function actually load a list! For now, it's going to be a sort of a “demo list”. Later, I'll show you how to save a to-do list and load it when you re-open the page. 

First, let's talk about lists in JavaScript. Lists, or **arrays** as they're called in JavaScript, are groups of the same kind of **variable** \(number, text, etc.\) in order. They don't need individual names, since you can look them up from the **array**. You use square brackets \(`[]`\) to create an **array**. They're also a kind of **variable**, so you can give them names like any other **variable** \(and yes, you can have **arrays** of **arrays**, but we're not doing that just yet!\). 

+ Change the contents of the `loadList` to create an empty **array** called `toDoItems` like this:

```JavaScript
  toDoItems = [ ]
```

You now need to add some things to that **array**. There's a problem, though: a to-do has two parts! You need to know what it is \(a **string** of text\) **and** whether or not it has been completed yet \(a true/false value\). Because the need to know if things are true or false is so common \(is the user signed in? does the player have more than 10 points? etc.\) JavaScript has a special kind of variable for true/false values. It's called a **boolean** and it can only be either `true` or `false`. 

+ Now you know what you need, make up three to-do items for your list and decide which one you'll mark done \(to show the user they can do that\).

So, with three to-dos to add to your **array**, how do you do that? You can create an **object variable** in JavaScript that contains related **variables**. In the case of your to-dos that will be their `text` and their `completed` state \(either `true` or `false`\). Here's an example object:

```JavaScript
  exampleToDo = {
              text: "Buy milk",
              completed: false
              }
```

The **object** is wrapped in curly braces \(`{ }`\) and stores pairs of **keys** \(`text`\) and **values** \(`Buy milk`\). 

+ Now it's time to put your **objects** into your **array** to make a list you can load when the page does! So, change the contents of the `loadList` function like this \(but use the to-dos you made up!\):

```JavaScript
  toDoItems = [
    {
      "text": "My",
      "completed": false
    },
    {
      "text": "to-do",
      "completed": true
    },
    {
      "text": "list",
      "completed": true
    }
  ]
```

You can see that these three items each have their `text` and their `completed` status and that they're stored in an **array**. However, you still need to put them on the page. 

+ Inside the `getToDoItemHTML` function, add this bit of code:

```JavaScript
  var listItem = document.createElement("li")
  var itemText = document.createTextNode(toDoItem.text)
  listItem.appendChild(itemText)

  if(toDoItem.completed === true){
  listItem.classList.add("completed")
  }

  return listItem
```

This code:
  1. Creates a piece of HTML \(a `li` or list item element\) and stores it in the `listItem` variable. 
  2. Then an `itemText` variable is created and a `TextNode` \(the bit of text that'll sit inside the HTML tag\) is stored in it with the `text` of the `toDoItem` that was passed into the function. 
  3. Then it adds \(“appends”\) the `itemText` inside the `listItem` element.
  4. If the `toDoItem`'s `completed` property is `true`, then it adds a `class` to the item. This tells the HTML page to display the completed task differently \(based on some code I wrote for you\). If you've done the **HTML/CSS Sushi Cards** then you can take a look at the CSS files and edit what they look like if you want!

+ Now you can create the HTML for a list item, you need to add it to the list. Add this to the `loadList` function, after the **array** of items.

```JavaScript
  toDoList = document.getElementById("todo")

  toDoItems.forEach(function(toDoItem){
    itemHTML = getToDoItemHTML(toDoItem)
    toDoList.append(itemHTML)
  })
```

This code uses `forEach`, which goes through every item in the **array** and **appends** it to the to-do list, selected by its `id` in the HTML.



