# Promise
- Promise is the new technique of ES6 for asynchronous development.
- Promise is a constructor.
- Promise is used to encapsulate async function that can recieve tht result of success or fail.
- Javascript object is based on constructor and prototype instead of class. JS can use constructor to initialize object.

```javascript
        // Vehicle is constuctor
        var Vehicle = function () {
            this.price = 1000;
        }
        var v = new Vehicle();
        v.price // 1000

```        
https://javascript.ruanyifeng.com/oop/basic.html


## asynchronous programming
- using callback function to fullfill asynchronous programming
- FS File operation
```javascript
require('fs').readFile(',/index.html', (err, data) => {})
// (err, data) => {} is call back function
```

- Database operation
```javascript
$.get('/server', (data) =>{})
// (data) =>{} is callback function
```
- AJAX
- setTimeout
```javascript
setTimeout(()=>{}, 2000);
// ()=>{} is callback function
```
