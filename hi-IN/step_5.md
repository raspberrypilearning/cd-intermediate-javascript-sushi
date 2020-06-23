## पूरे किए गए काम
यदि आप आइटमों को पूर्ण चिन्हित नहीं कर सकते हैं तो टू-डू सूची का कोई महत्त्व नहीं है! उस कार्य को जोड़ने का समय।

आपने पहले से ही लिस्टनेर (listener) को टू-डू आइटम पर डबल-क्लिक के लिए सेट कर रखा है। अब आपको बस एक ऐसा फंक्शन लिखना है जो उस डबल-क्लिक के पूरा होने पर आइटम को पूर्ण और पूर्ण नहीं के बीच टॉगल कर देगा।

याद रखें कि आप `complete` का उपयोग कर रहे हैं आइटम को पूर्ण के रूप में चिह्नित करने के लिए। उस क्लास के न होने का अर्थ है कि वे पूर्ण नहीं हैं। इसलिए आपके फ़ंक्शन को आइटम की **क्लास सूची** से क्लास जोड़ना या हटाना होगा, या तो इसे जोड़ना अगर यह अभी तक सूची में नहीं है, और यदि है तो इसे हटा दें।

### this कीवर्ड
The trick is knowing on which item to toggle the class. To identify the item that was clicked, you'll need to use a new JavaScript **keyword**: `this`.

How exactly the `this` keyword works is a bit complicated, but all you need to know here is that, when it's used with a function called by an event listener, it means 'the element the listener was bound to'. So you can use `this` to identify the specific `<li>` item that was clicked!

--- task ---

Add the `toggleToDoItemState` function to your script like so:

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
