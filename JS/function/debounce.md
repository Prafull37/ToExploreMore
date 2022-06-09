text.addEventListener('keyup',applyChange);
button.addEventListener('click',logValue);


let debouncedApiCall= debounce(makeApiCall,200,)
let debouncedMakeApiCallButton= debounce(makeApiCallButton,200,true)

function applyChange(e){
    logger.innerHTML = e.target.value;
    console.log("Making APi call......",e.target.value)
    debouncedApiCall(e.target.value);
}

function logValue(){
    debouncedMakeApiCallButton()
}


function makeApiCallButton(){
    setTimeout(()=>console.log(`Api call done for click`),200,)
}


/**
 * Debounce
 * long as it continues to be invoked, will not be triggered.
 * The function will be called after it stops being called for N milliseconds .
 * If immediate is passed as an argument to the function, the function triggers immediately and then waits for the interval before being called again.
 *  debounce(func,timeout,immediate)
 */

function debounce(func,timeout,immediate){
    let timerId;
    return (...args)=>{
        console.log("Hey")
        let callNow = immediate && !timerId ;
        
       clearTimeout(timerId);

       timerId=setTimeout(()=>{
            timerId=null
            if(!immediate) return func.apply(this,args)
        },timeout)

        if(callNow){
             console.log("Entering.. to this block")
          return func.apply(this,args)
        }
        
    }
}

function makeApiCall(value){
    setTimeout((searchParam)=>console.log(`Api call done for search term ${searchParam}`),200,value)
}












// function debounce(func, wait, immediate) {
//     var timeout;
  
//     return function executedFunction() {
//       var context = this;
//       var args = arguments;
          
//       var later = function() {
//         timeout = null;
//         if (!immediate) func.apply(context, args);
//       };
  
//       var callNow = immediate && !timeout;
      
//       clearTimeout(timeout);
  
//       timeout = setTimeout(later, wait);
      
//       if (callNow) func.apply(context, args);
//     };
//   };
