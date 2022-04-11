# <ins>Prototypical inheritance and Prototypes </ins>

### <ins> Prototypical inheritance </ins>
JS is a prototypical language.Every Object holds a special hidden property called <code>[[Prototype]]</code> that is either an object or <code>null</code>. Using this <code>[[Prototype]]</code> JS acheive inheritance. Whenever we try to access any property that is not inside the object then the JS search it from its prototype until null is encountered.
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
Here a new question arised what is <code>__proto__ (dunder proto)</code> ?
Through <code>__proto__</code>, we can access <code>[[Prototype]]</code>.(there are other ways we will see that also).
If you see <code>obj.__proto__</code> is pointing to <code>Object</code> and that contains our method <code>toString()</code>.
This brings us to new concept that is called <code>prototype chain</code>



