#javascript
### Reloj
- Parte de javascritp:
```javascript
function currentTime() {
let date = new Date();
let hh = date.getHours();
let mm = date.getMinutes();
let time = hh + ":" + mm;
document.getElementById("reloj").innerText = time;
let t = setTimeout(function () { currentTime() }, 1000);
} 
document.addEventListener('DOMContentLoaded', function () {
currentTime();
});
```
- Html
```html
<div id="reloj"></div>
```
- Css
```css
#reloj{
font-size: 6em;
}
```
### Fondo de pantalla Responsive
```html
<div class="backImg"></div>
```
- El css:
```css
.backImg{
	background-imge: url("");
	width: 200px;
	height: 200px;
}
```
### Buscador web minimalista
- Parte del html:
```html
<form role="search" id="form">
<input type="search" id="query" name="q" placeholder="Search..." aria-label="Search through site content">
<button> <svg viewBox="0 0 1024 1024">
<path class="path1"
d="M848.471 928l-263.059-263.059c-48.941 36.706-110.118 55.059-177.412 55.059-171.294 0-312-140.706-312-312s140.706-312 312-312c171.294 0 312 140.706 312 312 0 67.294-24.471 128.471-55.059 177.412l263.059 263.059-79.529 79.529zM189.623 408.078c0 121.364 97.091 218.455 218.455 218.455s218.455-97.091 218.455-218.455c0-121.364-103.159-218.455-218.455-218.455-121.364 0-218.455 97.091-218.455 218.455z">
</path></svg>
</button>
</form>
```
- Parte del javascript: 
```javascript
const f = document.getElementById('form');
const q = document.getElementById('query');
const google = 'https://www.google.com/search?q=';
function submitted(event) {
event.preventDefault();
const url = google + q.value;
const win = window.open(url, '_blank');
win.focus();
}
f.addEventListener('submit', submitted);
```
- Parte del css
```css
form {
background-color: #4654e1;
width: 300px;
height: 44px;
border-radius: 20px;
display: flex;
flex-direction: row;
align-items: center;
}
input {
all: unset;
font: 16px system-ui;
color: #fff;
height: 100%;
width: 100%;
padding: 6px 10px;
text-align: le;
}
::placeholder {
color: #fff;
opacity: 0.7;
}  
button {
all: unset;
cursor: pointer;
width: 44px;
height: 44px;
} 
svg {
color: #fff;
fill: currentColor;
width: 24px;
height: 24px;
padding: 10px;
}
```

