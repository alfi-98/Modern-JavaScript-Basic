# 🚀 Modern-JavaScript-Basic
💡 This repo consists of basic core concepts of modern javascript or ES6

📕 Index:
1. Fat Arrow Function



## 👉 Fat Arrow Function
- A normal function in javascript is:
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



