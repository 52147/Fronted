# ES6 Class

## 1. class is another way to write constructor

```html
    <script>
        // class is another way to write constructor
        class Point {}
        typeof Point // Point type is class
        Point === Point.prototype.constructor // true
    </script>
```
## 2. class function define on prototype 

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
## 3. use object to call constuctor is equal to use calss prototype
```html
        // use object to call constuctor is equal to use calss prototype
        class B {}
        const b = new B();
        b.constructor === B.prototype.constructor; // true
```

## 4. Use object.assign to add many functions in Point2 class
```javascript

        // Use object.assign to add many functions in Point2 class
        class Point2 {
            constructor() {}
        }
        Object.assign(Point2.prototype, {
            toString() {},
            toValue() {}
        });
 ```       
https://es6.ruanyifeng.com/#docs/class
