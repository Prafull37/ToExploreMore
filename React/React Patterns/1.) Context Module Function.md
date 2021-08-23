# Context Module Function
 If we are familiar with  `useContext()` and `useReducer()` of React Hooks. Then its too easy to learn.
 
 
Combination of `useReducer` and `useContext` .Let see in below code":-

Let's Define our Reducer
```
** Reducer.js **

function reducer(initialState,action){
 .....
}
```
Lets create a ContextProvider and useCount() custom hooks.

```
** ContextProvider.js **
const CountContext=React.createContext();
//import reducer from Reducer.js

function ContextProvider(props){
  const [state,dispatch]= React.useReducer(reducer,initState);
    
  const value=[state,dispatch]
  return (
  <CountContext.Provider value={value} {...props} >
  {props.children}
  </CountContext.Provider>);
}

function useCount(){
  const context=useContext(CountContext);
  return context;
}

//App.js
function App(){
return <CountProvider>
        <Count /> 
      </CountProvider>
}

```
Let's useCount() custom hooks

```
function Count(props)
{
  const [state,dispatch]= useCount();
  ....
}
```

#### 🥇 Congrats Its Done,You have learned something new !!

But,But,But there is something i want to tell you something.

Inline function is being created new during every render, Which may raise a performance concern.
*Ex of inline function- *

```
function Count(props)
{
  const [state,dispatch]= useCount();
  
  const increment=()=>dispatch({type:`increament`});
  const decrement=()=>dispatch({type:`decreament`});
  //This is an inline function and being created on every render
  ....
}
```

If you think to create helper function and wrap them using `React.useCallback()` inside CountProvider component like this:-

```
function ContextProvider(props){
  ...
  const increment=()=>React.useCallback(()=>dispatch({type:`increment`}),[dispatch]);
  const decrement=()=>React.useCallback(()=>dispatch({type:`decrement`}),[dispatch]);
  const value=[state,dispatchl,increment,decrement]
  return (
  <CountContext.Provider value={value} {...props} >
  {props.children}
  </CountContext.Provider>);
}
```
Then think of this bro and try to use it like below :
👎

```
const increment=(dispatch)=>dispatch({type:`increament`});
const decrement=(dispatch)=>dispatch({type:`decreament`});

function Count(props)
{
  const [state,dispatch]= useCount();
  ...
  
 return (<>
 <button onClick={()=>increment(dispatch)}>Count</button>
 <button onClick={()=>decrement(dispatch)}>Count</button>
 </>
 )
}

```

In first version React has to do calculation in order to compare the same function on every Render.

Personally I found  1st slow on during 1st render only.

In some blog i found people to use two different context for state and dispatch.

```
function reducer(state,action){
...
}

function CounterProvider() {
  const [state, dispatch] = React.useReducer(
    reducer,
    {count: initialCount},
  )
  ...

  return (<CounterContextValue.Provider value={state} {...props}>
            <CounterContextDispatch.Provider value={dispatch}>
              ...
            </CounterContextDispatch.Provider>
        </CounterContextValue.Provider> )
}

function useCounterValue() {
  const context = React.useContext(CounterContextValue)
   ...
  return context
}
function useCounterDispatch() {
    const context = React.useContext(CounterContextDispatch)
    ...
    return context
  }

function useCounter(){
    const value=useCounterValue();
    const dispatch=useCounterDispatch();
    return [value,dispatch];
}

const increment = dispatch => dispatch({type: 'increment'})
const decrement = dispatch => dispatch({type: 'decrement'})

function Counter() {
  const [state, dispatch] = useCounter();
  ....
}

function App() {
  return (
    <CounterProvider>
      <Counter />
    </CounterProvider>
  )
}

```

That's it 👋👋.

If you have to learn more You can enroll in [Epic React workshop](https://epicreact.dev) by Kent'C Dodds.



