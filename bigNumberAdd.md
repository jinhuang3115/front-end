```javascript
    function add(r1, r2) {
        const len = Math.max(r1.length, r2.length);
        const str1 = r1.padStart(len, '0');
        const str2 = r2.padStart(len, '0');
        let result = [];
        let flag = 0;
        let num = 0;
        for(let i = len; i--;){
            num = Number(str1[i]) + Number(str2[i]) + flag;
            result[i] = num % 10;
            flag = parseInt(num / 10, 10);
        }
        if (flag){
            result.unshift(flag);
        }
        return result.join('');
    }
```
