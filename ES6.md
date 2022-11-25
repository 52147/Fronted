# ES6

## 1. Class

```html
    <script>
        // class is another way to write constructor
        class Point {}
        typeof Point // Point type is class
        Point === Point.prototype.constructor // true
    </script>
```
## 2. Class

```html
        class Point {
            constructor() {}
            toString() {}
            toValue() {}
        }
        // class function define on prototype 
        Point.prototype = {
            constructor() {},
            toString() {},
            toValue() {},
        };
```
https://es6.ruanyifeng.com/#docs/class
