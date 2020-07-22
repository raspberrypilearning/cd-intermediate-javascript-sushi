## सूची को सहेजें
अपनी टू-डू सूची को और अधिक उपयोगी बनाने के लिए, आप इसे उपयोगकर्ता के कंप्यूटर पर **लोकल स्टोरेज (storage)** में सहेज सकते हैं । फिर, जब तक वे उसी ब्राउज़र में इसे खोलते हैं, यह उनकी टू-डू सूची को याद रखेगा!

इसके दो हिस्से हैं: सूची को सहेजना और, यदि यह वहां है, तो पेज को फिर से लोड किए जाने पर इसे फिर से लोड करना।

यह थोड़ा मुश्किल हो जाता है: लोकल स्टोरेज HTML को स्टोर नहीं कर सकता है, इसलिए आपको HTML कोड को शुद्ध JavaScript में बदलने की आवश्यकता है। ऐसा करने के लिए, आपको **ऐरे (array)** की आवश्यकता होगी ।

### ऐरे (Arrays)
एक ऐरे (array) एक विशेष प्रकार का वेरिएबल है जो की वेरिएबल की एक सूची है। आप वर्ग कोष्ठक (ब्रैकेट) `[]` के साथ एक ऐरे बना सकते हैं, और `push` तरीका (method) के साथ इसमें आइटम जोड़ें । एक विशिष्ट ऐरे आइटम (specific array item) की `alert` (चेतावनी) का उपयोग और आइटम की ऐरे में **स्थिति (position)** अपने आप को याद दिला सकते हैं । याद रखें कि JavaScript `0` पर गिनना शुरू करता है!

```JavaScript
var myArray = [];
myArray.push("something to store");
myArray.push("something else to store");
alert(myArray[0]);
//This will alert "something to store"
```

अगला, आपको `toDoList` सूची पर **लूप** करने की आवश्यकता है और ऐरे में प्रत्येक आइटम जोड़ें। याद रखें कि आपको न केवल कार्य को संग्रहीत करने की आवश्यकता है, बल्कि यह भी कि यह पूरा हुआ है या नहीं। इसका सबसे अच्छा तरीका JavaScript **ऑब्जेक्ट्स (objects)** का उपयोग करना है ।

### JavaScript ऑब्जेक्ट्स (objects)
एक ऑब्जेक्ट **गुणों (properties)** और **मान (values)** से निर्धारित होती है । आप इस तरह एक बनाएँ:

```JavaScript
var toDoInfo = {
    "task": "Thing I need to do",
    "completed": false
};
```

एक बार जब आप सभी टू-डू आइटम्स को ऑब्जेक्ट (object) में परिवर्तित कर लेते हैं, तो आपको बस उन्हें लोकल स्टोरेज में सहेजने की आवश्यकता होती है। लोकल स्टोरेज केवल स्ट्रिंग्स (strings) को संग्रहीत कर सकता है, लेकिन सौभाग्य से JavaScript आपके लिए ऐरे को स्ट्रिंग्स में बदल देता है यदि आप `stringify` फंक्शन का उपयोग करते हैं!

यह कोशिश करने का समय है!

### सब कुछ एकसाथ लाना और जोड़ना

--- task ---

`saveList` फंक्शन को अपडेट करना:
  - एक ऐरे (array) बनाये
  - `for` लूप का उपयोग करके सभी `toDoList` के आइटम्स को ऐरे (array) में ऑब्जेक्ट (object) बनाकर रखे
  - ऐरे (array) को `stringify` करे और इसे लोकल स्टोरेज में **key** `toDos` का उपयोग करके रखे

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
