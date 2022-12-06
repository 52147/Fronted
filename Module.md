## Import
### `index.html`
either choose
```javascript
<script type="module" src = "main.js"></script>
```
or
```javascript
    import {
        Square,
        img,
        myFunctionSubmit,
        changePart,
        calcRectArea,
        mouseDown,
        mouseUp,
        dragStart,
        allowDrop,
        drop,
        vol,
        myFunctionOn,
        myFunctionWel,
        myFunctionP,
        bigImg,
        normalImg,
        myFunctionI,
        end,
        submitForm
        } from "./main.js"; // ./ => mean from root directory
```
Only use one script tag, so put every function in it.

## Export
### `main.js`
use export keyword at every function    
export function     
```javascript
export function bigImg(x) {
    this.style.height = "200px";
    this.style.width = "200px";
}
```

export class
```javascript
export class Square {
    constructor(length) {
        this.length = length;
    }
    // function expression: can omit the function name to create anonymous name
    // is differnece with function declaration
    getArea() {
        return this.length * this.length;
    }

    // squart
    getSqua() {
        return Math.sqrt(this.length * this.length);
    }
}
```
## Use export function in html page
### `index.html`
1. import function
2. get the element id
3. add evnent listener to call the function in main.js

### Example: when audio end, alert "The audio has ended."
`main.js`
0. create a function for handling the "onended" event in main.js
```javascript
export function end() {
    alert("The audio has ended.");
}
```
1. import function "end"
```javascript
    import {
        end
        } from "./main.js"; // ./ => mean from root directory
```
3. get the audio id "aud"
```html
    <div>
      <audio id="aud" controls>
        <source src="images/summer-surf-120252.mp3" type="audio/ogg">
        <source src="images/summer-surf-120252.mp3" type="audio/mpeg">
        Your browser does not support the audio element.
      </audio>
    </div>
 ```
 4. Add event listener
 ```javascript
    const element4 = document.getElementById("aud");
    element4.addEventListener("ended", end);
 ```   
