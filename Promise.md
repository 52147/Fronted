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
https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise
## asynchronous programming(use callback function)
- using callback function to fullfill asynchronous programming
- Distadvantage: 
- One async function has one callback function and in callback function has another async function...
```javascript

        // too many callback functions
        asyncFunc1(opt, () => {
            asyncFunc2(opt, () => {
                asyncFunc3(opt, () => {
                    asyncFunc4(opt, () => {
                        // some operation
                    })
                })
            })
        });
```
1. FS File operation
```javascript
require('fs').readFile(',/index.html', (err, data) => {})
// (err, data) => {} is call back function
```

2. Database operation
```javascript
$.get('/server', (data) =>{})
// (data) =>{} is callback function
```
3. AJAX
4. setTimeout
```javascript
setTimeout(()=>{}, 2000);
// ()=>{} is callback function
```


## Promise can prevent to use many callback function

start async task => return Promise object => give Promise object a callback function

