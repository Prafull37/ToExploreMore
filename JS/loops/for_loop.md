// 1.) What is the control flow for below for loop
for(var i=0;i<3;i++){
    console.log("1st",i)
}

// What is going to be logged?
for (var i=0;i<2;i++){
    setTimeout(()=>console.log("2nd",i)) //chalghumne--> i=0 //chalghumne--> i=1 //chalghumne i->2
}
//2,2 -- every loop hits same closure

//What will be logged
for(let i=0;i<2;i++){ //its create new scope on every run but the value of i will be copied on every run.
    setTimeout(()=>console.log("3rd",i)) //chalghumne--> i=0 //chalghumne--> i=1 //chalghumne i->2
}
//0,1-- creates lexical scope for each iterations


for(let i=0;i<2;i++){ 
    setTimeout(()=>console.log(i))
    i++;
}
//1

for(let i=0;i<2;i++){
    setTimeout(()=>console.log(i)) 
    i++;
    let heat="work"; //Does this will be recreated or copy over a new scope ? --> recreated it additionally maintain a new scope for this loop on every loop 
}

// with const

// for(const i=0;i<2;i++){
//     console.log("Hello");
// } //Hello 1 time and break


for(let i=setTimeout(()=>console.log("time",i)) ;
i<2;
i++){
    
    i++;
     //7 basically it create two scopes one for returned values and another for the setTimoeut
}
