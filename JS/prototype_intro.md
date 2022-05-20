# <ins>Prototypical inheritance and Prototypes </ins>

### <ins> Prototypical inheritance </ins>
JS is a prototypical language.Every Object holds a special hidden property called <code>[[Prototype]]</code> that is either an object or <code>null</code>. Using this <code>[[Prototype]]</code> JS acheive inheritance. Whenever we try to access any property that is not inside the object then the JS search it from its prototype until null is encountered.<code>[[Prototype]]</code> can be accessible via <code>"__proto__"</code> .
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
1.)Here a new question arised what is <code>__proto__ (dunder proto)</code> ? That we will See in the upcoming section.
Through <code>"__proto__"</code>, we can access <code>[[Prototype]]</code>.(there are other ways, that we will see that later).
If you see <code>obj.__proto__</code> is pointing to <code>Object</code> and that contains our method <code>toString()</code>.

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
Here, using Dunder proto(<code>__proto__</code>) we prototypically linked/inherit city to the person. So now if we do <code>person.cityName</code>, what do you think what will be the answer.

Guess.... 

Guess.....

It will be <code>"Seoul"</code>. But How ? Any idea.

So when we access any property on an object, JS Engine first try to look within that.If the proprerty is not found , then it moves towards the linked object. and so on , until unless it reaches to null. If there is no property, it return undefined.
Let's understand using below toodler's creativity.

![IMG-20220521-WA0000](https://user-images.githubusercontent.com/30550365/169594749-5329d64d-5d78-44d7-a232-84d0505fc8d9.jpg)

In the above image, When we type <code> person.x</code>. Then JS search it within <code> person </code>  , if that  is not available.Then It moves towards <code>city</code> with the help of Dunder proto. Then it searches there , if the property is not available then it moves towards <code>object</code> and at last <code> null</code> .

<b>Do you know every object is inherited from Object by default and that Object has  prototype of null ? </b>

When we try to search for <code>cityName</code> from <code>person</code>.It goes to <code>city</code> object and returns the value.

### <ins>"__proto__"(Dunder Proto)</ins>
<code>"__proto__"</code> is a getter and setter for the prototypical inheritance.It is used to acccess <code>[[Prototype]]</code>. It is been discouraged to use it, but due to legacy/backward compatibility  it exists.We can use <code>Object.getPrototypeOf()</code> and <code>Object.setPrototypeOf()</code>.

//function constructor
//impact of this


### To-DO
1.) What is the difference between java class and javascript class and inheritance(show changing on prototype, impacts linked creation) ?  --> last <br/>
2.) What happen with <code>this</code> when we try to access from somewhere?  <br/>
3.) Prototypes on function or with new Consturctor ? --> upcoming <br/>
4.) Does arrow function does have <code>prototype</code> ? <br/>
5.) Can we use <code> new </code> on arrow function ?  <br/>
6.) [Use it](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/proto) <br/>
7.) this is not super ? <code>obj.t=fun t(){this.t()}</code> <code>this.__proto__.ask()</code> explain using this and this is <code>shadowing prototypes</code> and why it is being used? --> after function constructor and this? <br/>
8.) See Ducktyping in Js, and figure out if we can make use here? <br/>
9.) Mixins ? <br/>
10.) Object properties and loops....  -> next chapter <br/>
11.) [Behaviour Delegation](https://www.google.com/search?q=Delgation+oriented+design+i+js&rlz=1C5GCEM_enIN1006IN1006&ei=8teHYpPgHcLTz7sP4fGemA0&ved=0ahUKEwiTod_21O73AhXC6XMBHeG4B9MQ4dUDCA4&uact=5&oq=Delgation+oriented+design+i+js&gs_lcp=Cgdnd3Mtd2l6EAMyBwghEAoQoAEyCAghEB4QFhAdOgcIABBHELADOhQIABDqAhC0AhCKAxC3AxDUAxDlAjoFCC4QkQI6BQgAEJECOgsIABCABBCxAxCDAToFCAAQgAQ6CAguELEDEIMBOhEILhCABBCxAxCDARDHARDRAzoFCC4QgAQ6CwguEIAEEMcBEKMCOgQIABBDOgoILhDHARDRAxBDOhAILhCxAxDHARCjAhDUAhBDOggILhCABBCxAzoLCC4QgAQQxwEQrwE6CggAELEDEIMBEAo6BwguELEDEAo6CAguEIAEENQCOg0ILhCxAxCDARDUAhAKOgQIABAKOgkIABAKEEYQ_wE6BwgAELEDEAo6BwgAELEDEEM6BAgAEA06BggAEA0QCjoGCAAQHhAWOggIABAeEA8QFjoICAAQHhAIEA06CggAEB4QDxAIEA06BggAEB4QDToICAAQHhANEAU6CgghEB4QDxAWEB1KBAhBGABKBAhGGABQxgJYlU5g0k9oAnABeAKAAZYCiAHVRZIBBzAuMTAuMzGYAQCgAQGwAQrIAQjAAQE&sclient=gws-wiz) <br/>
