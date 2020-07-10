```javascript
    if (typeof Function.bind !== 'function') {
        Function.bind = function () {
            const that = Array.prototype.splice.call(arguments, 0, 1);
            const args = arguments;
            const arThis = this;
            if (typeof arThis === 'undefined'){
                throw new TypeError('arg0 is undefined');
            }
            return function () {
                return arThis.apply(that, Array.prototype.splice.call(arguments).concat(args));
            }
        }
    }
```
