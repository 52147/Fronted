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
 ## 5. All functions in class are non-enumerable
 ```javascript
         // All functions in class are non-enumerable
        class Point3 {
            constructor(x, y) {}
            toString() {}
        }
        // Object.keys() : return a array that contains enumerable properties in Point3
        Object.keys(Point3.prototype) // return []
        // Object.getOwnPropertyNames(): return all properties in Points
        Object.getOwnPropertyNames(Point3.protype) // return ["constructor", "toString"]
        // In ES5 toString() is enumerable
 ```         
https://es6.ruanyifeng.com/#docs/class
