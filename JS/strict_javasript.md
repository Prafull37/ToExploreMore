# 1.) Strict Mode and 'use strict'.

  ### 1.) <ins> What is Strict Mode in Javascript ? </ins>
  Strict Mode in Javascript , is a way to opt in to a strict version of Javascript.It helps us to write more secure and error prone JS code.And It is introduced in ES5.

  As we know JS has backward compatibility and due to this there are some mistakes which stayed permananently.
  By introduction of strict mode , we have options to choose strict version. 
  Strict mode basically catches all the silent errors or issues and throw an proper error for that.
  Browsers not supporting strict mode will run the same code differently than browser's supporting it.
  So it is advised to test feature on different Browsers. Strict Mode is supported By Most of the morden browsers except IE 9. 

  ### 2.) <ins> What are the benefits of Strict mode ? </ins>
  - Strict Mode catches Silent errors and throw them as an error
  - Restrict usage of some syntax that can be introduced in future version of ES.
  - Strict mode can help us to optimize and gain the performance also implicitly .*
  
  ### 3.) <ins> How can we use "Strict Mode" ? </ins>
  In order to use strict mode we have to define "use strict" before any script,function,eval.

  ### 4.) <ins>What is "use strict" ? </ins>
  "use strict" is an literal expression , that can be used to opt-in to stricter version of javascript/ Strict Mode. Older browser(not supporting) can ignore it completely.

  ### 5.) <ins> How to use "use strict" ? </ins>
  "use strict" must be the first statement of the script,function which chooses to run in strict mode.

  ##### <ins>"use strict" in any script</ins>
  
     //something.js

     "use strict"

     ......
       

  ##### <ins>"use strict" in any function</ins>

     //something.js
     function(){
     "use strict"
      ......
     }

  ##### <ins>"use strict" in eval</ins>

     //something.js
       eval("'use strict'; ...");
       
       
       
  ### 6.) <ins>Can we use strict mode in block like if and else? </ins>
  NO, we cannot use "use strict" inside any block/blockscope(if-else).
       
  ### 7.) <ins>How to enable strict mode in modules? </ins>
  Modules always run in "strict mode".So no need to enable it explicitly.
       
  ### 8.) <ins>How to enable strict mode in Class? </ins>
  Classes always run in "strict mode".So no need to enable it explicitly.


  ## <ins>Examples of "strict mode" </ins>
  
  #### 1.) Catching some silent errors
  
  - <b>Creation of global variable/Using undeclared variables.</b><br/>
     ```
     "use strict"
     // x is not defined earlier
     x="something" // ReferenceError
     x={a:5} //ReferenceError
    ```  
     
  - <b>Assignment to get only property / Writing to non-writable properties</b><br/>
     ```
     "use strict"
     // Non-writable Globals
      
      var NaN=45;            //TypeError
      var Infinity =23;      //TypeError
      var undefined=23;      //TypeError
    ``` 
    
    ```
      "use strict"
      //Non-writable Property
      
      var obj={};
      Object.defineProperty(obj,"x",{value:42,writable:false});
      obj.x=23   // TypeError "x" is Read Only
    ```   
    ```
      "use strict"
      //writing to getter only Property
      
      var obj={get x(){return 0}};
      obj.x=23   // TypeError: setting getter only property
    ```     
     
    ```
      "use strict"
      //writing to not extensible Property
      
      var obj={};
      Object.preventExtensions(obj)
      obj.x=23   // TypeError: Object is not extensible
    ```     
  - <b>Delete Undeleteable property</b><br/>
    ```
    "use strict"
    let x=42;
    delete x; //SyntaxError
    
    function F(){}
    delete F; //SyntaxError
    ```     
  - <b>Defining Multiple Arguments/Multiple property</b> <br/>
    ```
      "use strict"
      function F(a,a,b){}  //SyntaxError: Duplicate argument

      let x={a:21,a:21}  //SyntaxError :
    ```
  - <b>Octal expression  and Octal numeral literal</b><br/>
    ```
      "use strict"
         let x = "\010";  // SyntaxError
        //"\u0008" -> WITHOUT strict mode
  
        let x = 010; // SyntaxError    
        //8-> WITHOUT strict mode
       
    ``` 
    <b>BrainHack Question 1:</b>What is the output of below code ? <br/>
    ```
      //1.
      var sum = 015 + 
          197 +
          142;
  
     //2.
      "use strict"
      var sum = 015 + 
            197 +
            142;
    ```
  - <b>Setting property to primitive values</b><br/>
    ```
      "use strict"
      false.true=24;  //TypeError : can't assign to property "true" on false:not an object;
      (14).sailing=232; //TypeError :"use strict" is not a function
      undefined.work=here;  //TypeError :can't access property "work" of undefined
    ```
     <b>BrainHack Question 2:</b>What is the output of below code ? </br>
      ```
        // What kind of Error below code will throw ? a.)TypeError b.) SyntaxError
         
          14.sailing=232; 
          
      ```
  - <b><code>eval</code> and <code>arguments</arguments> keywords cannot be used as an variable, function name, arguments </b><br/>
    ```
    'use strict';
    eval = 17;      //Uncaught SyntaxError: 'eval' can't be defined or assigned to in strict mode code
    arguments = 17 //Uncaught SyntaxError: 'arguments' can't be defined or assigned to in strict mode code
    arguments++;
    ++eval;
    var obj = { set p(arguments) { } };
    var eval;
    try { } catch (arguments) { }
    function x(eval) { }
    function arguments() { }
    var y = function eval() { };
    var f = new Function('arguments', "'use strict'; return 17;");
    ```
  - <b>Changing of arguments </b><br/>
    ```
      //Without "use strict"
      function f(a) {
      'use strict';
        a = 42;
        return [a, arguments[0]];
       }
      var pair = f(17); //[42,42]
      
      //With "use strict"
      function f(a) {
      'use strict';
        a = 42;
        return [a, arguments[0]];
       }
      var pair = f(17); //[42,17]
    ```
  - <b><code>arguments.callee</code> and <code>arguments.caller</code> cannot be used </b><br/>
    ```
      'use strict';
      var f = function() { return arguments.callee; };
      f(); //  TypeError: 'caller', 'callee', and 'arguments' properties may not be accessed on strict mode functions or the arguments objects for calls to them
    ```
  - ****
  #### 2.) Futuristic Restrictions
  Below mentioned keyword cannot be used as an variable , since they are reserved for future version of EcmaScript.They will be introduced in Upcoming version. <code>"use strict"</code> checks for the variable reserved for future reference or not and throw error.
    
    implements
    interface
    let
    package
    private
    protected
    public
    static
    yield
    //SyntaxError: [variableName] is a reserved identifier
    
    
  You can find more about them from below link:-
  [Future Reserved keywords](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Lexical_grammar#future_reserved_keywords) <br/>
  [Web Platform](https://webplatform.github.io/docs/javascript/future_reserved_words/)
  
  #### 3.) Example for optimizations/performance.
  
  
# <ins>Behaviour of this in Strict Mode</ins>
  In  functional Execution Context the Value of this defined upon how this defined on how function is called.But without <code>"use strict"</code> the value of this will not set by this and default value of this will be  browser's Window Object <code>window</code> .
      <code>
        function f1(){
          return this;  
        }
        
        f1() === window // true
      
         function f2(){
          "use strict"
          return this;  
        }
        
        f1() === window // false
        f1() //returns undefined
        
      </code>
 

# <ins>Questions</ins>
  
  
# <ins>BrainHack Questios Answers� </ins>

  1.) BrainHack-1 :-  <br/>
    <code>
      //1.
        var sum = 015 + 
            197 +
            142; // 352

      //2.
      "use strict"
        var sum = 015 + 
              197 +
              142;
        //  syntax error

      // In strict mode define Octal by prefixing 0o
      let x= 0o10 // 8
    </code>
    
  2.) BrainHack-2 :-  <br/>
    <code>  
      SyntaxError
      why ?
    </code>

  
### Pending
  
  | issue no | Issue | Status | 
  | 1 | Reason for BrainHack question 2 . Why it will throw Syntax Error | Not-Started |
