# ES6 Inheritence

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
