# 🚀 Modern-JavaScript-Basic
💡 This repo consists of basic core concepts of modern javascript or ES6

📕 Index:
1. Fat Arrow Function
2. Truthy & Falsy
3. Ternary Operator


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

👉 Arrow Function does not have the attribute of a constructor 
- We cannot create a new object of an arrow function which we can do in a normal function.
Normal Function:
```
function Car(name) {
  this.name = name;
}

var BMW = new Car('BMW');
```
💡 The above code will give no error
Arrow Function:
```
var Car = (name) => {
  this.name = name;
}

var BMW = new Car('BMW');
```

💡 The above code will return an error since Arrow function does not have the property of a constructor i.e it cannot build an object. 





# 🏛 Truthy & Falsy

```
var test = "HI";

if(test){
  console.log("I am truthy");
}else {
  console.log("I am falsy");
}
```
This above code returns: ``` I am truthy```

- However,
```
var test = "";

if(test){
  console.log("I am truthy");
}else {
  console.log("I am falsy");
}
```
This code return: ```I am falsy```

- So, in javascript, anything accept ```false``` ```0``` ```-0``` ```0n``` ```""``` ```''``` ``` `` ``` ```null``` ```undefined``` ```Nan``` ```document.all``` will return truthy. 

- Even if we give a space inside cotation will return ```truthy```:
```
var test = " ";

if(test){
  console.log("I am truthy");
}else {
  console.log("I am falsy");
}
```

# 🏛 Ternary operator:
```
var age = 18;

var type;
if(age >= 18){
    type = "adult";
}else{
    type = "child";
}
console.log(type)
```
- The above simple code will print "adult". But with ```Ternary Operator``` we can further simplify the above code: 
```
var age = 18;

var type = (age >= 18) ? "adult" : "child";
console.log(type);
```
- In the above code, the statement before ```?``` is the condition and the statement after the ```?``` is the value that is being returned. In this example, if the age is above 18 then it will return ```adult``` or else ```child```. So, the statement on the left side of ```:``` returns if the condition is true and the right side is returned if the condition is false. 
- 👉 We can also use ternary operator for nested conditions.
```
var age = 6;

var type = (age >= 18) ? "adult" : (age > 10) ? "child" : "young";
console.log(type);
```
- The above code will return "young". In the first check if the age is less than 18, then the condition returns ```false``` and goes to another condition, ```(age > 10) ? "child" : "young"```. In our case the second condition returns false and so our code returns ```young```. 

# 🏛 Array.find() method:
- This method returns the value of the first element that passes a test. 
```
var numbers = [10,2,13,4,20,6];

var result = numbers.find( function(currentNumber) {
    return currentNumber > 10;
});

console.log(result);
```
- In the above code, we took an unsorted array of numbers. Then, we are running a function inside ```find()``` where it iterates the array, ```numbers[]```. In our example, we want the number which is greater than 10. If we look into our array we can see that 20 is the largest number but our code will return ```13``` because while iterating the array the first number that is greater than 10 is printed. The iteration breaks when the function finds the first true statement against the given condition.
- The function inside ```find()``` method can also take currentIndex and arr[] as parameters:
```
find( function(currentNumber, currentIndex, arr) {

```

- 👉 Another important aspect of find() method is ```this``` statement. 
```
class Student{
  constructor(name, age){
    this.name = name;
    this.age = age;
  }
  
  test(){
    console.log("Hello");
  }
  exampleFunction(){
    let array  = [1, 2, 3];
    array.find(function(){
      this.test();
    });
  }
}

let student = new Student("alfi", 23);

student.exampleFunction();
```
-  The above code will throw an error. This happends because the ```find()``` method inside our ```exampleFunction()``` cannot locate the this.test() function. By ```this``` it searches for the ```test()``` globally. For this, find() method also takes a second parameter ```this```.
```
exampleFunction(){
    let array  = [1, 2, 3];
    array.find(function(){
      this.test();
    }, this);
```
💡 However, we can use arrow function to solve this problem. For this, we dont need to use ```this```. 

```
exampleFunction(){
    let array  = [1, 2, 3];
    array.find(() => {
      this.test();
    });
```

# 🏛 Array.findIndex() method:
- If we want to find the index of a number in an array, we can use findIndex() method. Moreover, we can also find if a number exist in an array since ```findIndex()``` returns ```-1``` if a number does not exist.  
```
var numbers = [1,2,3,4,5,6,7];
var result = numbers.findIndex((currentValue, index, arr) => {
  return currentValue > 20;
});

console.log(result);
```
The above code returns ```-1```. 


# 🏛 Array.filter() method:
``
var numbers = [1,2,3,4,5,6,7];
var result = numbers.filter((currentValue, index, arr) => {
  return currentValue > 3;
});

console.log(result);
```
- The above code will print: 
``` [4,5,6,7] ```
- In the above code, filter() method prints all the numbers that are above 3. This is how it is filtering the array.
💡 But the ```filter()``` method is not like ```find()``` or ```findIndex()``` methods. Those methods break when the condition is true even if the full array is not iterated. But for filter() method the whole array is traversed. We can understand this property if we change the array into an unsorted array like this: ```var numbers = [11,2,3,34,5,61,7]; ```
