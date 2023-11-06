# allow_select
## A simple script that allows you to bypass most website select and copying prevention measures.

### Minified:
```javascript
!function(){function e(e){e.stopPropagation()}document.body.oncopy=null,document.body.oncut=null,document.body.onpaste=null,document.body.onselectstart=null,document.body.onmousedown=null,document.body.onmouseup=null,document.body.oncontextmenu=null,document.body.ondragstart=null,["copy","cut","paste","selectstart","mousedown","mouseup","contextmenu","dragstart"].forEach(function(t){document.body.addEventListener(t,e)});let t=document.styleSheets;try{for(let o=0;o<t.length;o++){let l=t[o].cssRules||t[o].rules;for(let n=0;n<l.length;n++)l[n].style&&("none"===l[n].style.userSelect||"none"===l[n].style.webkitUserSelect)&&(l[n].style.userSelect="auto",l[n].style.webkitUserSelect="auto")}}catch(s){console.warn("Cannot modify CSS rules from a different domain for security reasons!")}let r=document.querySelectorAll("*");for(let u=0;u<r.length;u++)r[u].style.setProperty("user-select","auto","important"),r[u].style.setProperty("-webkit-user-select","auto","important");console.log("Text selection and copying should now be enabled.")}();
```

### Full code:
```javascript
(function () {
	document.body.oncopy = null;
	document.body.oncut = null;
	document.body.onpaste = null;
	document.body.onselectstart = null;
	document.body.onmousedown = null;
	document.body.onmouseup = null;
	document.body.oncontextmenu = null;
	document.body.ondragstart = null;

	const events = ['copy', 'cut', 'paste', 'selectstart', 'mousedown', 'mouseup', 'contextmenu', 'dragstart'];
	events.forEach(function (event) {
		document.body.addEventListener(event, preventDefaultActions)
	});

	function preventDefaultActions(e) {
		e.stopPropagation();
	}

	const styleSheets = document.styleSheets;
	try {
		for (let i = 0; i < styleSheets.length; i++) {
			const rules = styleSheets[i].cssRules || styleSheets[i].rules;
			for (let j = 0; j < rules.length; j++) {
				if (rules[j].style && (rules[j].style.userSelect === 'none' || rules[j].style.webkitUserSelect === 'none')) {
					rules[j].style.userSelect = 'auto';
					rules[j].style.webkitUserSelect = 'auto';
				}
			}
		}
	} catch (e) {
		console.warn('Cannot modify CSS rules from a different domain for security reasons!');
	}

	const allElements = document.querySelectorAll('*');
	for (let i = 0; i < allElements.length; i++) {
		allElements[i].style.setProperty('user-select', 'auto', 'important');
		allElements[i].style.setProperty('-webkit-user-select', 'auto', 'important');
	}

	console.log('Text selection and copying should now be enabled.');
})();
```
