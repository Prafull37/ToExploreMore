### Prototype and Function Constructor
We know, there is another way to create an Object. That is via Constructor... But let's see an example. In this section, we will learn how function constructor and prototype is associated.


<ins>__Create an Object(via Constructor)__</ins> <br/>


    1. function MyClass(teacher,school){
    2.   this.teacher = teacher;
    3.   this.school = school;
    4. }
    5. let teacherInSchool = new MyClass("RUTHER","jr.High");
    6. console.log(teacherInSchool) 

"It's Your Job is too go through above code and do your analysis"

You may have one question in your mind... What will be its <code>[[Prototype]]</code> of <code>teacherInSchool</code>?

Let's See...

If we spread <code>teacherInSchool</code> in browser <code> console</code> , It will look something like below picture.Let's call this image as **No-1** .

<figure >
<img width="506" alt="Prototype of a object created with constructor" src="https://user-images.githubusercontent.com/30550365/170083900-0aee5567-21e3-46eb-a68e-678f2d12dcad.png" style="max-width: 100%;justify-content:center;">
  <figcaption > <b><i>Img-1: Prototype of a Object from a Constructor</i> </b></figcaption>
 </figure>
  </p>
<br/>
  
Woooow!!!!

We haven't assigned any prototype to that <code>teacherInSchool</code>. It should be default right???  You must have this question in your mind.

Let's See ...

Before Explainig this let me start with what happen when we create a Function.

So, when we create a function ,JS assign a hidden property called <code>prototype</code> to that function. <code>prototype</code>  holds an Object of its type (i.e; type of <code> function</code>) which has <code> constructor</code> and <code>[[Prototype]]</code> for the given function. The value of <code>constructor</code> always points to that given function, Until unless we change the prototype.<br/>
<br/>
So you can consider as an <code>prototype</code> works as an road between <code>function</code> and <code>object</code> and <code>constructor</code> is used for the vice versa.<br/>
 ![IMG_20220602_222631](https://user-images.githubusercontent.com/30550365/171684084-53b59781-eb3e-4165-a9fc-fbaceaad9cab.jpg)

  
This is first step. It happens by default .Even when we do not assign anything to <code>prototype</code> explicitly, JS takes cares for you.
 
The next is constructor invocation...
  So when we do <code> new functionName()</code>. JS creats a new Object and assign the Object linked to <code> F.prototype</code> as an <code>[[Prototype]]</code> of the object.
  ![IMG_20220602_222650](https://user-images.githubusercontent.com/30550365/171684431-651c37da-04a0-486a-ab32-15441380e82f.jpg)
  
  So In our case , when JS reaches at the end of line 4. it creates a <code>prototype</code> Object to that function , And at line 5. It assign that Object as an <code>[[Prototype]]</code> of <code>teacherInClass</code>.
  
**Note**: <code>prototype</code> and <code>[[Prototype]]</code> both are different terms.<code>prototype</code> property is only available to the functions.

Have you observed anything new in Img-1 or Img-3?? 

I will give you a hint "take a look of the image teacherInSchool".

Another hint, "try to find another <code>[[Prototype]]</code> and <code>[[constructor]]</code> ".
Have you find it ??? If not let's see...

<figure >
<img width="506" alt="Screenshot 2022-05-24 at 9 35 49 PM" src="https://user-images.githubusercontent.com/30550365/170101470-34962a51-6c5c-4cc3-bf7d-3e369517fb2c.png">
  <figcaption > <b><i>Img-4: Prototype of Function</i> </b></figcaption>
 </figure>
  </p>
<br/>
  
What !!! 

  Why we have Another <code>[[Prototype]] </code> ?Why <code>constructor</code> is pointing to <code>Object</code> ? 
  Can you do some google and find , before moving ahead....
  I will try to put at the end of this section... 😃


When we create an Object <code> new</code> uses <code> F.prototype</code> to set the <code>[[Prototype]]</code> of the Object.The creation is static, if something changes on <code>F.prototype</code>

    

//function constructor
//impact of this

#### TO-DO of Section.
1.) What is <code>new</code> ?
2.) <code> new </code> is used to create an Object and <code>new</code> demands a constructor property after that.
3.) Internally Every Object created via <code>new</code> ?

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
