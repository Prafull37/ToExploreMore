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
  
  - **Creation of global variable **
  - ****
  #### 2.) Futuristic Restrictions
  #### 3.) Example for optimizations/performance.
  
  
