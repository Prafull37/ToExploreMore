### useMemo()

useMemo is similar to useCallback. Instead of keeping track of function like useCallback(), useMemo keeps track of the value. 
Similar to useCallback(), useMemo() takes an function and array of dependencies and whenever dependencies changes useMemo will run the function and provide the output.
Using useMemo we can memoize any function written inside of functional component.

`
  const work = useMemo(()=>function,[x,y])
`

### Web workers 

Since Javascript is Single threaded, we can use  web workers to enhnace the performance. Webworkers run seperately from the main script and both communication occurs <br/>
by a async way.

In React we can make use of `[workerize](https://www.npmjs.com/package/workerize)` and `[workerize-loader](https://github.com/developit/workerize-loader)` for the webpack.
