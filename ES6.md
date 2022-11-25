# ES6 Class

## Inheritence

![image](https://user-images.githubusercontent.com/79159894/203930692-be385deb-7699-485c-ada0-03c132b14c51.png)

```javascript
        // ES6 Inheritence :
        class Super {}
        class Sub extends Super {}

        var sub = new Sub()

        Sub.prototype.constructor === Sub // 2. true
        sub.constructor === Sub // 4. ture
        sub.__proto__ === Sub.prototype // 5. true
        Sub.__proto__ === Super // 6. true
        Sub.prototype.__proto__ === Super.prototype // 7.true
```
https://keenwon.com/1524/
## 1. class is another way to write constructor

```javascript
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
 ## 6. default constructor return a object(this) of class
  ```javascript
        // default constructor return a object(this) of class
        // if we change the constructor return object as new object...
        class Foo {
            constructor() {
                return Object.create(null); // use Object.create() creat a new object
            }
        }
        new Foo() instanceof Foo
        // return false because constructor return a new object
   ```
   
 ## 7. use new keyword to initialize the class
   
```javascript   
        // use new keyword to initialize the class
        class Point4 {}

        var point = Point4(2, 3); // return error

        var point = new Point(2, 3); // correct
```


 ## 8. use __proto__ will change the protorype of class
```javascript 
        // use __proto__ will change the protorype of class
        var p1 = new Point(2, 3);
        var p2 = new Point(3, 3);
        p1.__proto__.printName = function () {
            return "Oops"
        };
        p1.printName() // return "Oops"
        p2.printName() // return "Oops"

        var p3 = new Point(4, 2);
        p3.printName() // return "Oops" 
        // Summary:
        // p3 can also use printName() means __proto__ change the prototype
        // So not recommend to use __proto__
 ```       
https://es6.ruanyifeng.com/#docs/class
