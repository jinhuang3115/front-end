```html
<html>
<head>
</head>
<body>
<input v-model="message" type="text"/>
<script>
   const obj = {

   };
   const vModules = document.querySelectorAll('[v-model]');
   vModules.forEach((item) => {
       const type = item.getAttribute('v-model');
       obj[type] = '';
       item.addEventListener('input', (e) => {
           const target = e.target;
           obj[type] = target.value;
       }, false);
       Object.defineProperty(obj, type, {
           get(){
               return obj[`${type}-val`];
           },
           set(val){
               obj[`${type}-val`] = val;
               item.value = val;
           },
       });
   });
</script>
</body>
</html>

```
