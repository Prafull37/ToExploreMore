
### React Performance

  #### 1. Lazy Loading with Suspense
  We can lazy load any component  using `Suspense` and `React.lazy(()=>import(file))`.<br/>
  Meaning of lazy loading is load the component whenever it is required.<br/>
  Usually the webpack load the complete code in a single chunk.<br/>
  But when we use lazy loading it will split and load the chunk whenever it is requested.<br/>
   `<Suspense/>` will take `fallback` as props that can be React Element and this fallback will display if it takes time to load.<br/>
   `React.lazy()` only supports default export. <br/>
   Example of lazy loading:-    
    ```
    
    //B.jsx
    
    function B(){
      ..... 
    } 
    
    export default B; 
    ```
   ```
    //A.jsx
    
   const B= React.lazy(()=>import("./B")) 
  
   function A(){
      return ( 
         <Suspense 
          fallback={Loader}
          >
            <B/>
          </Suspense>
        )
      }
    ```
  
