## टू-डू आइटम्स जोड़ें
बटनों का ठीक से काम करने का समय! यह चरण आपको यह दिखाएगा कि सूची में एक टू-डू आइटम कैसे जोड़ा जाए।

### HTML सूचियाँ
आप इस चरण में थोड़े से HTML का उपयोग करने जा रहे हैं। सूची एक **आदेशित सूची** है - इसका मतलब है कि यह संख्यांकित है। एक आदेशित सूची के लिए HTML टैग `<ol>` है, और प्रत्येक व्यक्तिगत **सूची आइटम** को एक `<li>` टैग की जरूरत है।

### सूची आइटम जोड़ना
पेज `<ol>` ऑर्डर की गई सूची के साथ आया था, इसलिए आपको बस प्रत्येक नए टू-डू आइटम के लिए `<li>` टैग जोड़ने के लिए कुछ JavaScript लिखने की आवश्यकता है। उपयोगकर्ता को पेज पर बॉक्स में टेक्स्ट (text) दर्ज करने में सक्षम होना चाहिए, और फिर **Add** बटन पर क्लिक करने से यह सूची पर एक गिने आइटम के रूप में दिखाई देता है।

--- task ---

सबसे पहले, जैसे आपने बटनों के साथ किया, टेक्स्ट बॉक्स (text box) और सूची का चयन करने के लिए वैरिएबल बनाएं। उनके पास पहले से ही `todo-entry-box` और `todo-list` Id है ।

```JavaScript
var toDoEntryBox = document.getElementById("todo-entry-box");
var toDoList = document.getElementById("todo-list");
```

--- /task ---

--- task ---

अब आप अपने प्रोग्राम के अंदर से बॉक्स और सूची को आसानी से देख सकते हैं।

एक `newToDoItem` नामित फ़ंक्शन बनाएं जिससे सूची में आइटम जोड़ा जा सके। इस फ़ंक्शन को दो बातें जानने की आवश्यकता होगी:
  - आइटम का टेक्स्ट (text) क्या है?
  - क्या आइटम को पूर्ण के रूप में चिह्नित किया जाना चाहिए?

बेशक, कोई नया टू-डू आइटम कभी पूरा नहीं होगा, लेकिन आप यहां आगे की योजना बना रहे हैं: जब आप उस पर कुछ पूर्ण किए गए आइटम सहेजे गए सूची को लोड कर रहे हैं, तो आप फिर से उसी फ़ंक्शन का उपयोग कर पाएंगे!

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

एक `li` एलिमेंट बनाता है जिसे अपने नए सूची आइटम के रूप में उपयोग करे ।

कोड का यह टुकड़ा:

```JavaScript
var toDoText = document.createTextNode(itemText);
```

एक **text node** बनाता है - टेक्स्ट (text) के लिए एक विशेष कंटेनर जिसे आप JavaScript का उपयोग करके एक HTML एलिमेंट के अंदर रखना चाहते हैं - और इसे `itemText` वेरिएबल की सामग्री से भरता है जो फंक्शन को **पास (pass)** किया जाता है ।

`appendChild` फंक्शन आप यहाँ उपयोग कर रहे हैं:

```JavaScript
toDoItem.appendChild(toDoText);
```

एलिमेंट, या टेक्स्ट नोड (text node) लेता है, जो आप इसे पास करते हैं (इस मामले में `toDoText` ), और इसे `toDoItem` के अंदर डालता है । यदि पहले से ही उस के अंदर एलिमेंट हैं, तो आप जो अभी जोड़ रहे हैं वह अंतिम होगा।

यह टुकड़ा:

```JavaScript
if (completed) {
    toDoItem.classList.add("completed");
}
```

जाँच करता है कि `completed` वेरिएबल का मूल्य जो हमने `newToDoItem` में दिए था, क्या वो `true` है। यदि यह **true** है, तो यह `class` `completed` को `li` एलिमेंट से जोड़ देगा, जो पेज पर कैसा दिखता है, इसे बदल देगा। `style.css` में , `li` टैग के लिए विशेष स्टाइल नियम हैं जो `completed` क्लास के साथ `style.css` में आता है - उन्हें जाँच करें, और यदि आप चाहे तो बदल भी सकते है!

पहले की तरह, यहाँ `appendChild`:

```JavaScript
toDoList.appendChild(toDoItem);
```

यह `toDoItem`(`<li>` एलिमेंट) को `toDoList` के अंदर डालता है (`<ol>` एलिमेंट)।

अंत में, कोड की यह पंक्ति:

```JavaScript
toDoItem.addEventListener("dblclick", toggleToDoItemState);
```

**double-click** के लिए इवेंट लिस्टनेर (event listener) को `toDoItem` से जोड़ता है , और जवाब में इसे `toggleToDoItemState` नामक एक फ़ंक्शन को कॉल करने के लिए कहता है। आप अगले कार्ड के साथ उस फंक्शन को बनाएँगे !

--- /collapse ---

--- task ---

अब, **Add** बटन को फ़ंक्शन से कनेक्ट करें: बस अपना `addToDoItem` फंक्शन बदलें ताकि बॉक्स से टेक्स्ट प्राप्त कर पाए और `newToDoItem` फ़ंक्शन को पास करे, जो आपने अभी बनाया है।

```JavaScript
function addToDoItem() {
    var itemText = toDoEntryBox.value;
    newToDoItem(itemText, false);
}
```

चूंकि एक नया टू-डू आइटम कभी पूरा नहीं होता है, आप हमेशा `completed` पैरामीटर में `false` पास कर सकते हैं जो `newToDoItem` फंक्शन में हैं ।

--- /task ---

अब सूची में एक टू-डू कार्य जोड़ने की कोशिश करो!
