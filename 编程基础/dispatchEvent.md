## element.dispatchEvent

```js
var evt= document.createEvent("HTMLEvents");
evt.initEvent("alert", false,false);

var dom = document.querySelector("#id");
dom.addEventListener("alert", function(event) {
	console.log(event);    
}, false);

dom.dispatchEvent(evt);
```

