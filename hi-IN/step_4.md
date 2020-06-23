## टू-डू आइटम्स जोड़ें
Time to get the first of those buttons working properly! यह चरण आपको यह दिखाएगा कि सूची में एक टू-डू आइटम कैसे जोड़ा जाए।

### HTML सूचियाँ
आप इस चरण में थोड़े से HTML का उपयोग करने जा रहे हैं। सूची एक ** आदेशित सूची ** है - इसका मतलब है कि यह संख्यांकित है। एक आदेशित सूची के लिए HTML टैग `<ol>` है, और प्रत्येक व्यक्तिगत ** सूची आइटम ** को एक `<li>` टैग की जरूरत है।

### सूची आइटम जोड़ना
The page came with the `<ol>` ordered list, so you just need to write some JavaScript to add `<li>` tags for each new to-do item. The user should be able to enter text in the box on the page, and then click the **Add** button to see it appear on the list as a numbered item.

--- task ---

First, just like you did with the buttons, create variables to select the text box and the list. उनके पास पहले से ही ` todo-entry-box ` और ` todo-list ` Id है ।

```JavaScript
var toDoEntryBox = document.getElementById("todo-entry-box");
var toDoList = document.getElementById("todo-list");
```

--- /task ---

--- task ---

अब आप अपने प्रोग्राम के अंदर से बॉक्स और सूची को आसानी से देख सकते हैं।

एक ` newToDoItem` नामित फ़ंक्शन बनाएं जिससे सूची में आइटम जोड़ा जा सके। इस फ़ंक्शन को दो बातें जानने की आवश्यकता होगी:
  - आइटम का टेक्स्ट (text) क्या है?
  - क्या आइटम को पूर्ण के रूप में चिह्नित किया जाना चाहिए?

Of course, no new to-do item would ever be complete, but you're planning ahead here: you'll be able to use the same function again when you're loading a saved list that has some completed items on it!

```JavaScript
function newToDoItem(itemText, completed) {
    var toDoItem = document.createElement("li");
    var toDoText = document.createTextNode(itemText);
    toDoItem.appendChild(toDoText);

    if (completed) {
        toDoItem.classList.add("completed");
    }

    toDoList.appendChild(toDoItem);
    toDoItem.addEventListener("dblclick", toggleToDoItemState);
}
```

--- /task ---

--- collapse ---
---
title: "फंक्शन क्या कार्य कर रहा है?"
---

यह नया फंक्शन कुछ चीजें करता है।

कोड का यह टुकड़ा:

```JavaScript
var toDoItem = document.createElement("li");
```

एक ` li` एलिमेंट बनाता है जिसे अपने नए सूची आइटम के रूप में उपयोग करे ।

कोड का यह टुकड़ा:

```JavaScript
var toDoText = document.createTextNode(itemText);
```

creates a **text node** — a special container for text that you want to put inside a HTML element using JavaScript — and fills it with the contents of the `itemText` variable that is **passed** into the function.

` appendChild` फंक्शन आप यहाँ उपयोग कर रहे हैं:

```JavaScript
toDoItem.appendChild(toDoText);
```

takes the element, or text node, that you pass to it (in this case `toDoText`), and puts it inside `toDoItem`. यदि पहले से ही उस के अंदर एलिमेंट हैं, तो आप जो अभी जोड़ रहे हैं वह अंतिम होगा।

यह टुकड़ा:

```JavaScript
if (completed) {
    toDoItem.classList.add("completed");
}
```

checks if the value for the `completed` variable that was passed to `newToDoItem` is `true`. If it is, then it will add the **class** `completed` to the `li` element, which will change how it looks on the page. In `style.css`, there are special styling rules for `li` tags with the `completed` class in `style.css` — check them out, and change them if you like!

पहले की तरह, यहाँ `appendChild`:

```JavaScript
toDoList.appendChild(toDoItem);
```

यह ` toDoItem`(`<li>` एलिमेंट) को ` toDoList` के अंदर डालता है (`<ol>` एलिमेंट)।

अंत में, कोड की यह पंक्ति:

```JavaScript
toDoItem.addEventListener("dblclick", toggleToDoItemState);
```

attaches an event listener for a **double-click** to the `toDoItem`, and tells it to call a function named `toggleToDoItemState` in response. आप अगले कार्ड के साथ उस फंक्शन को बनाएँगे !

--- /collapse ---

--- task ---

Now, connect to the function to the **Add** button: just change your `addToDoItem` function to get the text from the box and pass it to the `newToDoItem` function you've just created.

```JavaScript
function addToDoItem() {
    var itemText = toDoEntryBox.value;
    newToDoItem(itemText, false);
}
```

चूंकि एक नया टू-डू आइटम कभी पूरा नहीं होता है, आप हमेशा `completed` पैरामीटर में ` false` पास कर सकते हैं जो `newToDoItem` फंक्शन में हैं ।

--- /task ---

अब सूची में एक टू-डू कार्य जोड़ने की कोशिश करो!
