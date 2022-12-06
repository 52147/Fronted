# JS Module
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
### `main.js`
0. create function for handle the event
### `index.html`
1. import function
2. get the element id
3. add evnent listener to call the function in main.js

### Example 1: when audio end, alert "The audio has ended."
In `main.js`   
0. create a function for handling the "onended" event in main.js
```javascript
export function end() {
    alert("The audio has ended.");
}
```
In `index.html`     
1. import function "end"
```javascript
    import {
        end
        } from "./main.js"; // ./ => mean from root directory
```
2. get the audio id "aud"
```html
    <div>
      <audio id="aud" controls>
        <source src="images/summer-surf-120252.mp3" type="audio/ogg">
        <source src="images/summer-surf-120252.mp3" type="audio/mpeg">
        Your browser does not support the audio element.
      </audio>
    </div>
 ```
3. Add event listener
 ```javascript
    const element4 = document.getElementById("aud");
    element4.addEventListener("ended", end);
 ```   
### Example 2: when mouse on img, img become larger; when mouse out img, img become normal size
1. We want to change the img height and width to make img bigger, so we want to find where "height" at     
  1-1. check what is paramter "x" in "bigImg" function
     - add console.log(x) in "bigImg" function to check
 ```javascript
export function bigImg(x) {
    console.log(x);
}
 ```
`Output`       
 ![image](https://user-images.githubusercontent.com/79159894/205789536-bfbabf2c-f947-48a3-a684-541e6b3ec022.png)    
> We can see "x" is "MouseEvent"      
1-2. check what is "this" in "bigImg" function
    - add console.log(this) in "bigImg" function to check
```javascript
export function bigImg(x) {
    console.log(this);
}
 ```
`Output`       
![image](https://user-images.githubusercontent.com/79159894/205789902-1f7f03f5-8cc3-42fc-bbcf-b2777555459b.png)          
> We can see "this" is has the style element, which contains "height"     
1-3. So we can use this.style.height to change height value     
```javascript
     this.style.height = "200px";
```
1-4. final function that can change image size
```javascript
export function bigImg(x) {
    this.style.height = "200px";
    this.style.width = "200px";
}
```

In `main.js`   
2. create 2 export functions for handling the "onmouseover" and onmouseout event in main.js
   - "bigImg" function for handling "onmouseover" event
   - "normalImg" function for handling "onmouseout" event
```javascript
export function bigImg(x) {
    this.style.height = "200px";
    this.style.width = "200px";
}

export function normalImg(x) {
    this.style.height = "32px";
    this.style.width = "32px";
}
```


In `index.html`     
3. import function "bigImg" and "normalImg"

```javascript
    import {
        bigImg,
        normalImg
        } from "./main.js"; 
```
4. get the target image id "pi"
```html
      <img id="pi" border="0" src="images/Denver (1).jpg" alt="Smiley" width="32" height="32">
 ```
5. Add event listener "mouseover" and "mouseout" for calling export function "bigImg" and "normalImg"
 ```javascript
    const element2 = document.getElementById("pi");

    element2.addEventListener("mouseover", bigImg);
    element2.addEventListener("mouseout", normalImg);
 ```   
