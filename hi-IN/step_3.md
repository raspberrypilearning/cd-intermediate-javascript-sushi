## अपने बटनों में एक्शन जोड़ें

आपके द्वारा प्राप्त कोड में तीन फाइलें शामिल हैं, जिन्हें आप trinket विंडो में टैब के रूप में देख सकते हैं:
  - ` index.html ` - एक HTML फ़ाइल जो पेज को बताती है कि उस पर क्या होना चाहिए
  - ` style.css ` - एक CSS फ़ाइल जो पेज को बताती है कि उसे कैसा दिखना चाहिए: कहाँ चीजें होनी चाहिए, उनका आकार और रंग कैसा होना चाहिए, आदि।
  - ` script.js ` - एक JavaScript फ़ाइल जो पेज को बताती है कि क्या करना है; आप इस फ़ाइल में अपनी अधिकांश कोडिंग करेंगे

यदि आप पेज देखते हैं, तो आप देखेंगे कि इसमें चार बटन हैं:

  - नए टू-डू आइटम जोड़ने के लिए एक ** Add ** बटन
  - एक ** Clear Completed ** बटन आइटम को साफ़ करने के लिए जिसे आपने पूर्ण के रूप में चिह्नित किया है
  - पूरी तरह से टू-डू सूची खाली करने के लिए एक ** Empty List ** बटन
  - सूची में क्या है इसे सहेजने के लिए एक ** Save List ** बटन

बेशक, चूंकि आपने अभी तक कोई कोड नहीं लिखा है, अभी उनमें से कोई भी कुछ भी नहीं करता है!

चूंकि आप पेज से कुछ **काम करवाना** चाहते है , आपको ` script.js ` फ़ाइल के लिए टैब पर क्लिक करने की आवश्यकता है और वहाँ कुछ कोड जोड़ें। ये निर्देश आपको दिखाएंगे कि **Add** बटन कैसे सेट करें, और फिर आप दूसरों को खुद से सेट कर सकते हैं।

JavaScript को यह बताने की आवश्यकता है कि HTML पेज के कौन से हिस्से महत्वपूर्ण हैं, और इन भागों के साथ उपयोगकर्ता के कौन से इंटरैक्शन पर प्रतिक्रिया करनी चाहिए। इस मामले में, आप इसे **Add** बटन के बारे में बताना चाहते हैं , और जब उपयोगकर्ता इस बटन पर क्लिक करता है तो प्रतिक्रिया करने के लिए कहें।

### बटन प्राप्त करना

--- task ---

बटन के लिए वेरिएबल बनाकर शुरू करें और JavaScript को HTML **डॉक्यूमेंट ** से ** element** प्राप्त करने के लिए  बताएं  जिसमे **Id** `add-button` है ।

```JavaScript
var addButton = document.getElementById("add-button");
```

--- /task ---

एक Id एक वेब पेज के एक हिस्से के लिए एक अनूठा लेबल है, और जब हमने स्टार्टर पेज बनाया, तो हमने प्रत्येक बटन को एक लेबल दिया। यदि आप ` index.html` देखें, तो आप उन्हें देख सकते हैं ।

### लिसनिंग फॉर द क्लिक (Listening for the click)

--- task ---

Now connect your button to a **event listener**, so JavaScript will 'listen' for a particular kind of event and then run a function when it 'hears' it. इस स्थिति में, ईवेंट एक क्लिक है। इसे ` addEventListener` फंक्शन के साथ करें, कुछ इस तरह:

```JavaScript
addButton.addEventListener("click", addToDoItem);
```

--- /task ---

` addButton ` पर यह लिस्टनेर एक क्लिक का इंतजार करेगा , और जब यह क्लिक को 'सुनेगा', तो यह ` addToDoItem ` को चलाकर प्रतिक्रिया करेगा। बेशक, यह अभी तक काम नहीं करेगा, क्योंकि आपने ` addToDoItem` फंक्शन नहीं लिखा है!

### फंक्शन बनाना
बाद में प्रोजैक्ट में आप अपने फंक्शन के लिए कोड लिखेंगे ताकि वे टू-डू आइटम जोड़ें, सूची साफ़ करें, इसे सहेजें आदि। लेकिन अभी के लिए, आप केवल यह देखना चाहते हैं कि आपने अपने ईवेंट लिस्टनेर को ठीक से जोड़ा है।

--- task ---

अपना ` addToDoItem` फंक्शन बनाएँ ताकि यह अलर्ट संदेश को पॉपअप करके उपयोगकर्ता को बताए कि उन्होंने किस बटन को क्लिक किया है।

```JavaScript
function addToDoItem() {
  alert("Add button clicked!");
}
```

--- /task ---

अब बटन पर क्लिक करें और जांचें कि क्या यह काम करता है!

### अन्य बटनों के लिए कोड लिखें
अब अन्य तीन बटन जोड़े ताकि उन्हें क्लिक करने से अलर्ट भेजा जा सके:

--- task ---

**Clear Completed** बटन - जिसमें Id `clear-completed-button` है - को एक ` clearCompletedToDoItems ` नामित चेतावनी फंक्शन से कनेक्ट करें।

--- /task ---

--- task ---

**Empty List** बटन - जिसमें Id `empty-button` है - को एक `emptyList` नामित चेतावनी फंक्शन से कनेक्ट करें।

--- /task ---

--- task ---

**Empty List** बटन - जिसमें Id `save-button` है - को एक `saveList` नामित चेतावनी फंक्शन से कनेक्ट करें।

--- /task ---

--- hints --- --- hint ---

प्रत्येक बटन के लिए आप को जरूरत है की आप:

  - एक वैरिएबल बनाएं और HTML फ़ाइल में इसके Id का उपयोग करके बटन प्राप्त करें
  - क्लिक ईवेंट (click event) के लिए सुनने वाले वैरिएबल में एक ईवेंट लिस्टनेर (event listener) जोड़ें और, इसे सुनने पर, उचित रूप से नामित फ़ंक्शन को कॉल करें
  - उपयुक्त फ़ंक्शन बनाएं (उदाहरण ` clearCompletedToDoItems `) और उपयोगकर्ता को यह सूचित करने के लिए कोड करें कि उन्होंने किस बटन पर क्लिक किया है

--- /hint --- --- hint ---

` addButton ` भाग के नीचे कोड है जिसे आपको जोड़ने की आवश्यकता है:

```JavaScript
var addButton = document.getElementById("add-button");
addButton.addEventListener("click", addToDoItem);
function addToDoItem() {
    alert("Add button clicked!");
}

var clearButton = document.getElementById("clear-completed-button");
clearButton.addEventListener("click", clearCompletedToDoItems);
function clearCompletedToDoItems() {
    alert("Clear button clicked!");
}


var emptyButton = document.getElementById("empty-button");
emptyButton.addEventListener("click", emptyList);
function emptyList() {
    alert("Empty button clicked!");
}


var saveButton = document.getElementById("save-button");
saveButton.addEventListener("click", saveList);
function saveList() {
    alert("Save button clicked!");
}
```

--- /hint --- --- /hints ---
