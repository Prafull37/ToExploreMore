
### React Performance

  #### 1. Lazy Loading with Suspense
          We can lazy load any component  using `Suspense` and `React.lazy(()=>import(file))` . Meaning of lazy loading is load the component whenever it is required.              Usually the webpack load the complete code in a single chunk.But when we use lazy loading it will split and load the chunk whenever it is requested.
          `<Suspense/>` will take `fallback` as props that can be React Element and this fallback will display if it takes time to load.
          
          `React.lazy()` only supports *default exports*
         Example of lazy loading:-
         
         ```
          /*A.jsx*/
          const B= React.lazy(()=>import("./B"))
          return (
          <Suspense 
            fallback={Loader}
            >
            <B/>
            </Suspense>
          )
          ```
