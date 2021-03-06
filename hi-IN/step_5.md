## पूरा करने वाले आइटम्स
यदि आप आइटमों को पूर्ण चिन्हित नहीं कर सकते हैं तो टू-डू सूची का कोई महत्त्व नहीं है! उस कार्य को जोड़ने का समय।

आपने पहले से ही लिस्टनेर (listener) को टू-डू आइटम पर डबल-क्लिक के लिए सेट कर रखा है। अब आपको बस एक ऐसा फंक्शन लिखना है जो उस डबल-क्लिक के पूरा होने पर आइटम को पूर्ण और पूर्ण नहीं के बीच टॉगल कर देगा।

याद रखें कि आप `complete` का उपयोग कर रहे हैं आइटम को पूर्ण के रूप में चिह्नित करने के लिए। उस क्लास के न होने का अर्थ है कि वे पूर्ण नहीं हैं। इसलिए आपके फ़ंक्शन को आइटम की **class list** से क्लास जोड़ना या हटाना होगा, या तो इसे जोड़ना अगर यह अभी तक सूची में नहीं है, और यदि है तो इसे हटा दें।

### this कीवर्ड
जल्दी से करने के लिए आपको पता होना चाहिए कि किस आइटम पर क्लास (class) टॉगल (toggle) करना है | क्लिक किए गए आइटम की पहचान करने के लिए, आपको एक नया JavaScript **संकेत शब्द** का उपयोग करना होगा : `this` ।

`this` कीवर्ड का वास्तव में काम थोड़ा जटिल है, लेकिन आप सभी को यहां यह जानना आवश्यक है कि, जब इसका उपयोग किसी इवेंट लिस्टनेर द्वारा कहे जाने वाले फ़ंक्शन के साथ किया जाता है, तो इसका अर्थ है 'वह तत्व जो लिस्टनेर के लिए बाध्य था'। तो आप विशिष्ट `<li>` आइटम जो क्लिक किया गया था की पहचान करने के लिए `this` का उपयोग कर सकते हैं!

--- task ---

`toggleToDoItemState` फंक्शन को अपनी स्क्रिप्ट (script) से ऐसे जोड़े:

```JavaScript
function toggleToDoItemState() {
    if (this.classList.contains("completed")) {
        this.classList.remove("completed");
    } else {
        this.classList.add("completed");
    }
}
```

--- /task ---
