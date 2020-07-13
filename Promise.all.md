```javascript
    if (typeof Promise.all !== "function"){
        Promise.prototype.all = (arr) => {
            const results = [];
            return new Promise((resolve => {
                let i = 0;
                const resolvePromise = (k, v) => {
                    i++;
                    results.push(v);
                    if (i === arr.length){
                        resolve(results)
                    }
                }
                arr.forEach((item, index) => {
                    item.then((res) => {
                        resolvePromise(index, res);
                    });
                });
            }));
        }
    }
    let a = new Promise( resolve => {
        setTimeout(() => {
            console.log('a');
            resolve('a');
        }, 5000)
    });
    let b = new Promise( resolve => {
        setTimeout(() => {
            console.log('b');
            resolve('b');
        }, 1000)
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
