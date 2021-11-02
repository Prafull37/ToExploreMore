
### React Performance

  #### 1. Code-Splitting and Lazy loading with Suspense
  We can lazy load any component  using `Suspense` and `React.lazy(()=>import(file))`.<br/>
  Meaning of lazy loading is load the component whenever it is required.<br/>
  Usually the webpack load the complete code in a single chunk.<br/>
  First you have to load the component with `React.lazy(()=>import(file))`
  and then you have to wrap the component into `<Suspense />`. Unless it will throw error.
  But when we use lazy loading it will split and load the chunk whenever it is requested.<br/>
   `<Suspense/>` will take `fallback` as props that can be React Element and this fallback will display if it takes time to load.<br/>
   `React.lazy()` only supports **default export**. <br/>
   Example of lazy loading:-    
    ```
    const B=React.lazy(()=>import("./B.jsx"))
    function A(){
      return(
      <Suspense 
      fallback={Loader}>
        <B/>
     </Suspense>
      )
    }
    ```
    
  **External Resources:- **
 [Lazy Load the Routes](https://scotch.io/tutorials/lazy-loading-routes-in-react)
 [Lazy Loading](https://www.imperva.com/learn/performance/lazy-loading/)
 [Lazy Loading the image](https://levelup.gitconnected.com/lazy-loading-images-in-react-for-better-performance-5df73654ea05)
 
 [Expolore More about Code splitting from here](https://www.google.com/search?q=code+splitting&rlz=1C1VDKB_enIN953IN953&oq=code+splitting&aqs=chrome.0.0i13l5j69i61l3.3625j0j7&sourceid=chrome&ie=UTF-8)
 
 [Code splitting through webpack](https://webpack.js.org/guides/code-splitting/)
 
  #### 2. Eager Loading
  Suppose with the help of Suspense we were loading a heavy chunk on click of a button , which still take time component to load and show fallback.<br/>
  Instead of loading the chunk on click, we can load it whenever the mouse enter or focus enter. It will save our time and improve user experience.<br/>
  
  The best thing of webpack is it only load the component once. So here once we load through `lazyLoad`, that will be used through all instance.
  
  ```
  const lazyLoad =()=> import("./A.js");
  const A=React.lazy(lazyLoad);
  
  function T(){
     const [state,setState] = useState(false);
     return (
     <div
     onFocus={lazyLoad}
     onMouseEnter={lazyLoad}
     >
     {state && <A/>
     </div>
     )
  }
  ```
  
  **External Resources:- **
  [Eager Loading in Angular](https://enlear.academy/eager-loading-in-angular-7aab94c09ab3)
  [Lazy vs Eager](https://medium.com/@nassersanou23/important-react-lazy-vs-eager-loading-c480508defd0)
  
  ### 3. [Webpack Magic Comments](https://webpack.js.org/api/module-methods/#magic-comments)
  Here we are not taking all magic comments. `webpackPrefatch:true/false` <br/>
  This comment preload the chunk in the cache  and produce it whenever required
  [webpackPrefatch](https://webpack.js.org/guides/code-splitting/#prefetchingpreloading-modules)
  
  In order to see the difference disable `cache` in the network Tab
  
  ```
   const lazyLoad =()=> import(/*webpackPrefetch:true,webpackChunkName:"Globe"*/"./A.js");
  ```
