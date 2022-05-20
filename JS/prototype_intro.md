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


When we try to search for <code>cityName</code> from <code>person</code>.It goes to <code>city</code> object and returns the value.

###<ins>__proto__(Dunder Proto)</ins>
<code>"__proto__"</code> is a getter and setter for the prototypical inheritance.It is used to acccess <code>[[Prototype]]</code>. It is been discouraged to use it, but due to legacy/backward compatibility  it exists.We can use <code>Object.getPrototypeOf()</code> and <code>Object.setPrototypeOf()</code>.

//function constructor
//impact of this


### To-DO
1.) What is the difference between java class and javascript class and inheritance(show changing on prototype, impacts linked creation) ?  --> last
2.) What happen with <code>this</code> when we try to access from somewhere? 
3.) Prototypes on function or with new Consturctor ? --> upcoming
4.) Does arrow function does have <code>prototype</code> ?
5.) Can we use <code> new </code> on arrow function ? 
6.) [Use it](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/proto)
7.) this is not super ? <code>obj.t=fun t(){this.t()}</code> <code>this.__proto__.ask()</code> explain using this and this is <code>shadowing prototypes</code> and why it is being used? --> after function constructor and this?
