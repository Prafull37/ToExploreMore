# <ins>Prototypical inheritance and Prototypes </ins>

### <ins> Prototypical inheritance </ins>
JS is a prototypical language.Every Object holds a special hidden property called <code>[[Prototype]]</code> that is either an object or <code>null</code>. Using this <code>[[Prototype]]</code> JS acheive inheritance. Whenever we try to access any property that is not inside the object then the JS search it from its prototype until null is encountered.<code>[[Prototype]]</code> can be accessible via <code>\_\_proto\_\_</code> .
Lets See with an Example.

Consider the following code:-
    
       let obj={
           name:"Xyz"
       }
       
       console.log(obj.toString()); // "[object Object]"

Let's not focus on result as of now . We do not have implemented <code>toString</code> inside <code>obj</code> , So what do you think from where it does came? How obj is able to access <code>toString</code> ?

Let's see<br/>
![prototypical inheritaance](https://user-images.githubusercontent.com/30550365/162847996-fdb3ac33-40a7-4be5-b2be-b53baa08887a.png)
<br/>
1.)Here a new question arised what is <code>\_\_proto\_\_ (dunder proto)</code> ? That we will See in the upcoming section.
Through <code>\_\_proto\_\_</code>, we can access <code>[[Prototype]]</code>.(there are other ways, that we will see that later).
If you see <code>obj.\_\_proto\_\_</code> is pointing to <code>Object</code> and that contains our method <code>toString()</code>.

This brings us to new concept that is called <code>prototype chain</code> . So Let's understand what is prototype chain.

### <ins>Protoype Chain</ins>
Let's Assume the below example
<code>
        let city={
            cityName:"Seoul"
        }
        let person={
            personName:"Roh"
            __proto__:city
        }
 </code>
Here, using Dunder proto(<code>\_\_proto\_\_</code>) we prototypically linked/inherit city to the person. So now if we do <code>person.cityName</code>, what do you think what will be the answer.

Guess.... 

Guess.....

It will be <code>"Seoul"</code>. But How ? Any idea.

So when we access any property on an object, JS Engine first try to look within that.If the proprerty is not found , then it moves towards the linked object. and so on , until unless it reaches to null. If there is no property, it return undefined.
Let's understand using below toodler's creativity.

![IMG-20220521-WA0000](https://user-images.githubusercontent.com/30550365/169594749-5329d64d-5d78-44d7-a232-84d0505fc8d9.jpg)

In the above image, When we type <code> person.x</code>. Then JS search it within <code> person </code>  , if that  is not available.Then It moves towards <code>city</code> with the help of Dunder proto. Then it searches there , if the property is not available then it moves towards <code>object</code> and at last <code> null</code> .

<b>Do you know every object is inherited from Object by default and that Object has  prototype of null ? </b>

When we try to search for <code>cityName</code> from <code>person</code>.It goes to <code>city</code> object and returns the value.

### <ins>\_\_proto\_\_(Dunder Proto)</ins>
<code>"\_\_proto\_\_"</code> is a getter and setter for the prototypical inheritance.It is used to acccess <code>[[Prototype]]</code>. It is been discouraged to use it, but due to historical reason it exists.We can use <code>Object.getPrototypeOf()</code> and <code>Object.setPrototypeOf()</code>.

Now we understand about the Prototypical Inheritance and <code>\_\_proto\_\_  </code>. I hope you must be in a good position for answering the below question.

    let x={a:5};
    let y={b:6};
    x.__proto__ = y; //(*)
    y.__proto__ = x; //(**) 
    let oldProto = y.__proto__;
    console.log(y.__proto__); // I want you to find and note about its output !!!
    y.__proto__ = 5;
    console.log(oldProto ==== y.__proto__) //(***) (Guess the output !!)


I want you to guess what will happen/output at  <code>*</code>  <code>**</code> <code> *** </code> checkpoints ?

......


.......

So, you must have figured out!

At <code>*</code> , we are linking x with y and setting y as an prototype of x. And this will happen without any issue .
But at <code>**</code> , We will get an <code>Error</code>.
That will be 

<code>
    Uncaught TypeError:Cyclic __proto__.
</code>

The question is why we got this error ? 

Well, <b> The reference of <b>Prototypical Inheritance</b> or <code> \_\_proto\_\_ </code> can't go in circle</b> .

This is one of the limitations.

Now, we left with what will output from <code>***</code> !!!
The Answer is <code>true</code>. But we just replaced its <code>\_\_proto\_\_ </code> by 5. So why ! why we get <code> true</code> .

Well <b>the value of <code> \_\_proto\_\_ </code> can only either be <code>Object</code> or <code> null </code></b> .That's another limitation.
Even we are replacing it by a number , we will not get any error, Javascript ignores it. Hence there is no change. The output before and after setting <code>\_\_proto\_\_</code> will remain same .

### <ins>Limitiation of Prototypical Inheritance </ins>
1.) The reference of <b>Prototypical Inheritance</b> or <code> \_\_proto\_\_ </code> can't go in circle or 
2.) the value of <code> \_\_proto\_\_ </code> can only either be <code>Object</code> or <code> null </code> .

<b>BrainHack Q1</b>:- Suppose there is an object<code> m</code> , What will happen when we assign <code>arr</code>,<code> myFunc</code>, and <code>bool</code> as the prototype of m?


    let m={a:5};
    let arr=['1','12'];
    function myFunc(){} ;
    let bool=true ;


I want you to guess and the answer you will find at the last...

<b> Take a Break Here.... </b> 

Another Question....

I promise, it will be last one for this section.

Suppose, Roy and Martha ,two persons both lives in different street of Seoul. You have to design an object so ,Your company can track their details whenever we want . You just learn about the <code>Prototypical Inheritance</code> and <code>Dunder Proto</code>. By using it , you want to showcase your knowledge. So you have created a <code>city</code> object and assign as the <b>prototype</b> of royDetails and marthaDetails. Just like below

    let city={cityName:"Seoul"};
    let royDetails ={name:"Roy"};
    let marthaDetails = {name:"Martha"}
    royDetails.\_\_proto\_\_ = city;
    marthaDetails.\_\_proto\_\_ = city

Now Roy moves to the Sydney 

    royDetails.cityName = 'Sydney'

Now I want you to guess !!!
1.) By changing the cityName from <code>royDetails</code> , Will impact original object <code> city </code>
2.) What will be the cityName for martha?
3.) How may key value pairs are there in <code> royDetails </code> ?

Take 5 min of your time ... Google it and then get back to it ... , <br/>
..........

..........

Answers for the 1st will be <code> No,There will be no impact on original object </code>.2nd CityName for Martha will be still <code>Seoul </code> and For 3rd There will be <b>2</b> key-value pair..... 🤐🤐😶  What !!! How ?

Yes, There will be <b>2</b> key value pair .
Now if we see <code>royDetails</code> , it will look like 👇👇

    { 
    name :"Roy"
    cityName:"Sydney"
    }


#### <b> Writing does not use prototype. So, when we write to any object that time it does not impact the prototype. The property will be added to the object itself not on the prototype.</b>

Q:- <b>What will happen when we use getter and setter for writing ?Let's see by an example from javascript.info</b>
    
    let user = {
      name: "John",
      surname: "Smith",

      set fullName(value) {
        [this.name, this.surname] = value.split(" "); 
      },

      get fullName() {
        return `${this.name} ${this.surname}`;
      }
    };
    
    let admin = {
      __proto__: user,
      isAdmin: true
    };
    
    admin.fullName = "Alice Cooper";
    
    console.log(admin);
    { 
        name:"Alice", //Due to setter function we got name in the admin
        surname:"Cooper", //Due to setter function we got name in the admin
        isAdmin:true,
        fullName:"Alice Cooper" 
     }

There will be no change .... , Still everything will be added to the object... .

### Brainhack Questions

**Q1**:- Well, We know <code>arr</code> and <code> myFunc</code> is an array and function respectively. And we know array and function both are <b>Object</code> in javascript , so as an result we will be able to sucessfully assign them as proto. But in case of variable <code>bool</code> , there will be no change. and it will be ignored. 
