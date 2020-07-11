```javascript
    if (typeof Promise.all !== "function"){
        Promise.prototype.all = (arr) => {
            const results = [];
            return new Promise((resolve => {
                arr.forEach((item, index) => {
                    item.then((res) => {
                        results.push(res);
                        if (index === arr.length - 1){
                            resolve(results);
                        }
                    });
                });
            }));
        }
    }
    let a = new Promise( resolve => {
        setTimeout(() => {
            console.log('a');
            resolve('a');
        }, 1000)
    });
    let b = new Promise( resolve => {
        setTimeout(() => {
            console.log('b');
            resolve('b');
        }, 2000)
    });
    let c = new Promise( resolve => {
        setTimeout(() => {
            console.log('c');
            resolve('c');
        }, 3000)
    });
    Promise.all([a,b,c]).then((data) => {
        console.log(data);
    });
```
