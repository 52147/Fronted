## Import
### `index.html`
either choose
```javascript
<script type="module" src = "main.js"></script>
```
or
```
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
