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
https://markdown.com.cn/intro.html#markdown-%E6%98%AF%E4%BB%80%E4%B9%88%EF%BC%9F
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


## Promise 01

## `No promise`
```javascript
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Lucky Draw</title>
</head>

<body>

    <div calss="container">
        <h1>Promise 01 Lucky Draw</h1>
        <button id="btn">Click to get prize</button>
    </div>

    <script>
        // get the random number
        function rand(m, n) {
            return Math.ceil(Math.random() * (n - m + 1)) + m - 1;
            // Math.ceil() : round up and get the small integer
        }
        // get the html element id
        const btn = document.querySelector("#btn");
        // add event listerner for clicking
        btn.addEventListener("click", function () {
            // set timer, after 1 sec show the res
            setTimeout(() => {
                // if get 1~30 bingo(30% percent get the prize), otherwise no bingo
                let n = rand(1, 100);
                if (n <= 30) {
                    alert("No prize");
                } else {
                    alert("Won the prize");
                }
            }, 1000);
        });
    </script>

</body>

</html>
```
## `With Promise`
```javascript
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Lucky Draw</title>
</head>

<body>

    <div calss="container">
        <h1>Promise 01 Lucky Draw</h1>
        <button id="btn">Click to get prize</button>
    </div>

    <script>
        // // get the random number
        function rand(m, n) {
            return Math.ceil(Math.random() * (n - m + 1)) + m - 1;
            // Math.ceil() : round up and get the small integer
        }
        // get the html element id
        const btn = document.querySelector("#btn");

        // Promise state:
        // resolve : function type, operation complete sucessfully, call reolve
        // reject : function type, operateion failed, call reject
        btn.addEventListener("click", function () {
            const p = new Promise((resolve, reject) => {

                // set timer, after 1 sec show the res
                setTimeout(() => {
                    // if get 1~30 bingo(30% percent get the prize), otherwise no bingo
                    let n = rand(1, 100);
                    if (n <= 30) {
                        resolve(); // set the Promise state to success
                    } else {
                        reject();
                    }
                }, 1000);


            });
            // use then() to define the call back of resolve and rejct state
            // then(function, function)
            p.then(() => {
                alert("No prize");
            }, () => {
                alert("Won the prize");
            });
        });
    </script>

</body>
```
Before click
![image](https://user-images.githubusercontent.com/79159894/204063462-a108e140-8e10-40bf-9847-761641d59ef1.png)
After click
![image](https://user-images.githubusercontent.com/79159894/204063473-8eef8cc6-7f2b-49e3-88ab-a2b90e2c025b.png)


