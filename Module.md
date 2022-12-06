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
