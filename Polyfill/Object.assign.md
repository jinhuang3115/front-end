````javascript
    if (typeof Object.assign !== 'function') {
        Object.defineProperty(Object, 'assign', {
            value: function assign(target, args) {
                if (target === null || args === undefined) {
                    throw new TypeError('Cannot convert undefined or null to object');
                }
                const obj = target;
                const arr = Array.prototype.slice.call(arguments, 1, arguments.length);
                arr.forEach((item) => {
                    if (item) {
                        Object.keys(item).forEach((i) => {
                            if (Object.prototype.hasOwnProperty.call(item, i)) {
                                obj[i] = item[i];
                            }
                        });
                    }

                });
                return obj;
            },
            writable: true,
            configurable: true
        })
    }
````
