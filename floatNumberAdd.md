```javascript
    function add(r1, r2) {
        let rg1, rg2, m;
        try{
            rg1 = r1.split('.')[1].length;
        }catch (e) {
            rg1 = 0;
        }
        try{
            rg2 = r2.split('.')[1].length;
        }catch (e) {
            rg2 = 0;
        }
        m = 10 ** Math.max(rg1, rg2);
        return (r1 * m + r2 * m) / m ;
    }
```
