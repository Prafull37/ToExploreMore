# Patterns

### 1.) Context Module Functions
      useRedcuer + useContext
      
### 2.) Compound Component
       Use of React.Children and React.cloneElement API to build components like 
        
        `html
          <select>
            <option></option>
             <option></option>
              <option></option>
               <option></option>
          </select>
        `
### 3.) Flexible Compound Component
      Compound component with power of state managemnt like Context,useReducer, state managment library
      
### 4.) Props Collection
    Props Collection is nothing just having an object of all props that is required by your component.
    
### 5.) Props Getter
     A function used by user to pass all the user-defined props without overriding any of the default props behaviour.
     

### 6.) State Reducer
     Handle the library use-case along with user usecase for same action which is unbreakable.
     
 
### 7.) Control Props 
    Control props is similar to controlled component. Provide ability of your component to handle value and eventhandler if user want.Also support an additional; use case  of handling by itself through uncontrolled components using state reducer
     
