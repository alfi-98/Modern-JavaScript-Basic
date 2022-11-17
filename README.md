# 🚀 Modern-JavaScript-Basic
💡 This repo consists of basic core concepts of modern javascript or ES6

📕 Index:
1. Fat Arrow Function



## 🏛 Fat Arrow Function
- 👉 A normal function in javascript is:
```
function name(){
  return "John";
  }
console.log(name());
```

- In modern javascript we can code the above function in this way:
```
let name = () => {
  return "John";
  }
console.log(name());
```

- However, we can reduce the lines in our code by removing the brackets, ```{}``` if there is only one statement to execute.
```
let name = () => "John";
console.log(name());
```
💡 Note than we have also removed the ```return``` statement since we have only one return statement. In this case we cannot keep the return statement in our code block.

- Incase of handling parameters in fat arrow functions,
```
let name = (n) => console.log(n);

name("John");
```

Multiple paramteres:
```
let intro = (name, age) => {
  console.log(name + " is " + age + " years old");
 }

intro("John", 23);
```
👉 Problem of ```this``` in callback function:
```
var intro = {
    name: "John",
    hobbies: ["Dog", "Cars", "Travelling"],
    printHobbies: function(){
        this.hobbies.forEach(function(hobby){
            console.log(`${this.name} loves ${hobby}`)
        });
    },
};

intro.printHobbies();
```
The above code prints:
```
undefined loves Dog
undefined loves Cars
undefined loves Travelling
```
- In the above code, ```this.name``` cannot find the name attribute since this is inside a callback function. But we can modify the code by saving ```this``` inside a variable outside the callback function. 
```
var intro = {
    name: "John",
    hobbies: ["Dog", "Cars", "Travelling"],
    printHobbies: function(){
        var self = this;
        this.hobbies.forEach(function(hobby){
            console.log(`${this.name} loves ${hobby}`)
        });
    },
};
```
- This way the above code will give the correct result. But this is not the most efficient way. This is where fat arrow function comes in. By using arrow function we can solve the problem. 
 ```
 var intro = {
    name: "John",
    hobbies: ["Dog", "Cars", "Travelling"],
    printHobbies: function(){
        this.hobbies.forEach( (hobby) => {
            console.log(`${this.name} loves ${hobby}`)
        });
    },
};

intro.printHobbies();
```
💡 After using the arrow function, javascript remembers the ```this``` function. 


    
