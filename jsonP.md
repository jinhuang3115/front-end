````javascript
   window.jsonP = async function (url) {
        return new Promise(resolve => {
            const script = document.createElement('script');
            const head = document.querySelector('head');
            script.onload = () => {
                return resolve(jsonP.data);
            }
            script.type = 'text/javascript';
            head.appendChild(script);
            script.src = `${url}?callback=window.jsonP.callback`;
        });

   }
    jsonP.callback = function(data){
        jsonP.data = data;
    }

    const getData = async () =>{
        const data = await jsonP('http://127.0.0.1/jsonP');
        console.log(data);
    }
    getData();
````
