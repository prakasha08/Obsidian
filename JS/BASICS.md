![[Screenshot 2024-08-26 144550.png]]
# Datatypes
![[Pasted image 20240717173611.png]]

# Variable Declaration
![[Pasted image 20240717171116.png]]
![[Pasted image 20240717171122.png]]
![[Pasted image 20240717171129.png]]

**Constant are only for primitive datatypes and its Variable Name is Always in capital

![[Pasted image 20240717171337.png]]

![[Pasted image 20240801205340.png]]
### Strings
```js
let firstName = "Bro";
let favoriteFood = "pizza";
let email = "Bro123@gmail.com";
console.log(typeof firstName);
console.log(`Your name is ${firstName}`);
console.log(`You like ${favoriteFood}`);
console.log(`Your email is ${email}`);
```
### Boolean
```js
let online = false;
let forSale = true;
let isStudent = true;
console.log(Bro is online: ${online});
console.log(Is this car for sale: ${forSale});
console.log(Enrolled: ${isStudent));
```

## Diff btw declaration of name and "name" to a Variable
![[Pasted image 20240717172004.png]]

# Keywords in JS
![[Pasted image 20240717172329.png]]
# Operators
operator precedence
1. parenthesis ()
2. exponents
3. multiplication & division & modulo
4. addition & subtraction

![[Pasted image 20240717173354.png]]
```js
let students = 31;
students students + 1;
students students - 1;
students = students / 2; //students students / 2;
students = students ** 2;
students += 1;
students -= 1;
students *= 2;
students /= 2;
students **= 2;
students %= 2;
students++;
students--;
let extraStudents students % 3;
console.log(extraStudents);
```
## Ternary Operator
```js 
let age 12;
let message age >= 18 ? "You're an adult": "You're a minor";
console.log(message);
let time 9;
let greeting time < 12? "Good morning!": "Good afternoon!";
 console.log(greeting);
let isStudent = false;
let message isStudent? "You 'You are a student": "You are NOT a student"; console.log(message);
```
# Input
```html
<body>
<h1 id="myHi Welcome</h1>
<label>username: </label>
<input id="my Text"><br><br>
<button id="mySubmit">submit</button>
<script src="index.js"></script>
</body>
```
```js
// How to accept user input
// 1. EASY WAY window prompt
// 2. PROFESSIONAL WAY = HTML textbox
let username;
document.getElementById("mySubmit").onclick = function(){
username = document.getElementById("myText").value;
document.getElementById("myH1").textContent = Hello ${username}
}
```
Find Circumstance of circle using Constant 
```html
<body>
<h1 id="myH1" Enter the radius of a circle:</h3>
<label>radius:</label>
<input type="text" id="myText"><br><br>
<button id="mySubmit">submit</button>
<h3 id="myH3"></h3>
<script src="index.js"></script>
</body>
```

```js
const PI = 3.14159;
let radius;
let circumference;
document.getElementById("mySubmit").onclick = function(){
radius = document.getElementById("myText").value;
radius = Number(radius);
circumference = 2 * PI * radius;
document.getElementById("myH3").textContent circumference "cm"
```
![[Pasted image 20240801220101.png]]
# Type Conversion
```js
// type conversion change the datatype of a value to another // (strings, numbers, booleans)
let age = window.prompt("How old are you?");
age = Number(age);
age += 1;
console.log(age, typeof age);//age+1
```

```js
let x = "pizza";
let y ="pizza";
let z ="pizza";
x = Number(x);
y = String(y);
z = Boolean(z);
console.log(x, typeof x);//Nan Number
console.log(y, typeof y);//pizza String
console.log(z, typeof z);//true Boolean
```
# Math Function
Math - > built-in object that provides a collection of properties and methods
```js
let x = 3;
let y = 2;
let z = 1;
z = Math.round(x);
z= Math.floor(x);
z = Math.ceil(x);
z = Math.trunc(x);
z Math.pow(x, y);
z Math.sqrt(x);
z Math.log(x);
z = Math.sin(x);
z = Math.cos(x);
z = Math.tan(x);
z = Math.abs(x);
z = Math.sign(x);
let max= Math.max(x, y, z);
let min = Math.min(x, y, z);
```
# Functions

Functions are have set of instruction to do some particular task
which can be called by their name. Its look like if you want to call someone through mobile by their Phone number,

![[Pasted image 20240717173710.png]]
![[Pasted image 20240717183154.png]]
```js
function add(x, y){
return x + y;
}
function subtract(x, y) {
return x - y;
}
function multiply(x, y){
return x * y;
}
function divide(x, y) {
return x / y;
}
function isEven (number) {
return number % 2 ===0? true false;
}
function isValidEmail (email){
return email.includes ("@") ? true false;
}
console.log(isValidEmail("Bro@fake.com"));
console.log(isValidEmail("ElonMusk.com"));
console.log(isValidEmail("Zuckerborg@Meta.com"));
```
## Function using return type
![[Pasted image 20240717183223.png]]
# Arrays
```js
let fruits = ["apple", "orange", "banana"];
//fruits.push("coconut");-> apple orange banana coconut
//fruits.pop();-> apple orange 
//fruits.unshift("mango");-> mango apple orange banana
//fruits.shift();-> orange banana
let numOfFruits = fruits.length;//4
let index = fruits.indexOf("orange");//1
let index = fruits.indexOf("mango");//-1
console.log(index);
```

## For loop
```js
let fruits = ["apple", "orange", "banana", "coconut"];
for(let fruit of fruits){ 
console.log(fruit);//->apple orange banana coconut
}
fruits.sort().reverse();
for(let fruit of fruits){
console.log(fruit);//apple banana coconut orange  
}
```

## For Each loop
***forEach()
method used to iterate over the elements of an array and apply a specified function (callback)
to each element
array.forEach(callback)
element, index, array are provided

```js
let numbers = [1, 2, 3, 4, 5];
numbers.forEach(square); numbers.forEach(display);
function double(element, index, array){ array [index] = element 2;
function triple (element, index, array
				  { 
array [index] = element * 3;
function square(element, index, array){ array [index] = Math.pow(element, 2);
function cube(element, index, array){ array[index] = Math.pow(element, 3);
function display(element){ console.log(element); }
```

```js
let fruits = ["apple", "orange", "banana", "coconut"];
fruits.forEach(lowercase);
fruits.forEach(display);
function upperCase(element, index, array){ 
array [index] = element.toUpperCase();}
function lowercase (element, index, array){ 
array [index] = element.toLowerCase();}
function capitalize(element, index, array){
array[index] = element.charAt(0).toUpperCase() + element.slice(1);
function display(element){
console.log(element);}
```
## Map function
***.map() = accepts a callback and applies that function to each element of an array, then return a new array
It same as like foreach loop
```js
const numbers = [1, 2, 3, 4, 5];
const squares = numbers.map(square);
const cubes = numbers.map(cube);
console.log(cubes);
function square(element) {
return Math.pow(element, 2)
}
function cube (element) {
return Math.pow(element, 3)
}
```

```js
const dates = ["2024-1-10", "2025-2-20", "2026-3-30"];
const formattedDates = dates.map(formatDates);
console.log(formattedDates);
function formatDates (element){
const parts = element.split("-");
return ${parts[1]}/${parts [2]}/${parts[0]);
```
## Filter
***.filter() creates a new array by filtering out elements

```js 
let numbers = [1, 2, 3, 4, 5, 6, 7];
let evenNums = numbers.filter(isEven);
let oddNums = numbers.filter(isOdd);
console.log(oddNums);
function isEven (element) {
return element % 2 === 0;
}
function isodd(element){
return element % 2 !== 0;
}
```

```js
const ages = [16, 17, 18, 18, 19, 20, 60];
const adults = ages.filter(isAdult);
const children ages.filter(isChild);
console.log(children);
function isAdult(element){
return element >= 18;
}
function isChild(element){
return element < 18;
}
```

```js
const words ["apple", "orange", "banana", "kiwi", "pomegranate", "coconut"];
const shortWords= words.filter(getShortWords);
const longWords = words.filter(getLongWords);
console.log(longWords);
function getShortWords (element){ return element.length <= 6;
}
function getLongWords (element){ return element.length > 6;
```
## Reduce
***reduce() = reduce the elements of an array to a single value

```js
const prices = [5, 30, 10, 25, 15, 20];
const total prices.reduce(sum);
console.log($${total.toFixed(2)));
function sum(accumulator, element){ 
return accumulator + element;
}
```

```js
const grades = [75, 50, 90, 80, 65, 95];
const maximum = grades.reduce(getMax);
const minimum
grades.reduce(getMin);
console.log(maximum);
console.log(minimum);
function getMax (accumulator, element){
return Math.max(accumulator, element);
}
function getMin (accumulator, element){
return Math.min(accumulator, element);
}
```
## Destructuring(In Arrays)

**destructuring = extract values from arrays and objects, then assign them to variables in a convenient way
[]= to perform array destructuring
()= to perform object destructuring
```js
EXAMPLE 1
// SWAP THE VALUE OF TWO VARIABLES
let a = 1;
let b = 2;
[a, b] = [b, a];
console.log(a);
console.log(b);
```

```js
//
EXAMPLE 2
// SWAP 2 ELEMENTS IN AN ARRA
const colors = ["red", "green", "blue", "black", "white"];
[colors[0], colors [4]] = [colors [4], colors[0]];
console.log(colors);
```

```js
//
EXAMPLE 3
// ASSIGN ARRAY ELEMENTS TO VARIABLES
const colors = ["red", "green", "blue", "black", "white"];
const [firstColor, secondColor, thirdColor, ...extraColors] = colors;
console.log(firstColor);
console.log(secondColor);
console.log(thirdColor);
console.log(extraColors);
```
## Sorting Array
sort() method used to sort elements of an array in place. Sorts elements as strings in lexicographic order, not alphabetical lexicographic (alphabet + numbers + symbols) as strings
```js
let fruits ["apple", "orange", "banana" "coconut", "pineapple");
fruits.sort();
console.log(fruits);
//Number array
let numbers = [1, 10, 2, 9, 3, 8, 4, 7, 5, 6];
numbers.sort((a, b) => a - b);//Ascending Order
numbers.sort((a, b) => b - a);//decending Order
console.log(numbers);
```
# Switch Case
```js

let day = 2;
switch(day){
case 1:
console.log("It is Monday");
break;
case 2:
console.log("It is Tuesday");
break;
case 3:
console.log("It is Wednesday");
case 4:
console.log("It is Thursday");
case 5:
console.log("It is Friday");
case 6:
console.log("It is Saturday");
case 7:
console.log("It is Sunday");
break;
default:
console.log($(day) is not a day);
}
```
# String Methods
```js
let username = "Prakii its"
console.log(username.charAt(1));//r
console.log(username.indexAt("P");//0
console.log(username.length);//9
console.log(username.trim());//Prakiiits
console.log(username.toUpperCase());//PRAKII ITS
console.log(username.toLowerCase());//prakii its
console.log(username.repeat(2));//prakii itsprakii its
console.log(username.startsWith(" "));//false
console.log(username.startsWith("s"));//true
console.log(username.includes(" "));//true
console.log(username.replace(" ","-"));//prakii-its
console.log(username.padStart(11,"-"));//--Prakii its
console.log(username.padend(11,"-"));//Prakii its--
```
## String Slicing
string slicing creating a substring from a portion of another string
```js
string.slice(start, end)
const fullName = "Bro Code";
let firstName = fullName.slice(0, 3);//upto 2nd index
let lastName=fullName.slice(4, 8);//upto 7th index
let lastchar=fullName.slice(-1);//e
let lastchar=fullName.slice(-2);//de
const firstName = fullName.slice(0, fullName.indexOf(""));//bro
const lastName = fullName.slice(fullName.indexOf(" ") + 1);//code

console.log(firstName);//bro
console.log(lastName);//code

```
# Method Chaining

**calling one method after another in one continuous line of code

```js
let username = window.prompt("Enter your username: ");
//NO METHOD CHAINING
username = username.trim();
let letter=username.charAt(0);
letter= letter.toUpperCase();
let extraChars username.slice(1);
extraChars=extraChars.toLowerCase();
username=letter + extraChars;
console.log(username);
//METHOD CHAINING
username = username.trim().charAt(0).toUpperCase() + username.trim().slice(1).toLowerCase();
```

# Logical Operators
**logical operators used to combine or manipulate Boolean values
(true or false)
AND &
OR
NOT 

# Strictly Operators
**assignment operator
== comparison operator (compare if values are equal)
=== strict equality operator (compare if values & datatype are equal)
! inequality operator
!== strict inequality operator

# While Loop
```js
let username = "BroCode";
while(username === ""){
console.log("You didn't enter your name");
console.log(Hello $(username));
```

```js
let loggedIn = false;
let username;
let password;
while(!loggedIn){
username = window.prompt("Enter your username");
password = window.prompt("Enter your password");
if (username === "myUsername" && password === "myPassword") {
loggedIn = true;
console.log("You are logged in!");
}
else{
console.log("Invalid credentials! Please try again");
}
}
```

# Function Expression
***function expressions a way to define functions as Values or variables
```js
setTimeout(function(){ console.log("Hello"); ), 3000);
```

```js
const numbers = [1, 2, 3, 4, 5, 6];
const squares = numbers.map(function(element){
return Math.pow(element, 2);1);
const cubes numbers.map(function(element){
return Math.pow(element, 3);
});
const evenNums numbers.filter(function(element){
return element%20;
});
const oddNums numbers.filter(function(element){
return element %2!=0;
});
const total numbers.reduce(function(accumulator, element) {
return accumulator + element;
});
  ```
# Arrow Function
**arrow functions is a concise way to write function expressions good for simple functions that you use only once (parameters) => some code

```js
setTimeout( )=> console.log("Hello"), 3000);
```

```js
const squares = numbers.map((element) => Math.pow(element, 2));
const cubes = numbers.map((element) => Math.pow(element, 3));
const evenNums = numbers.filter((element) => element % 2 == 0);
const oddNums = numbers.filter((element) => element % 2 != 0);
const total = numbers.reduce((accumulator, element) => accumulator + element;
console.log(total);
```
# Spread operator
***spread operator = allows an iterable such as an array or string to be expanded into separate elements (unpacks the elements)
```js
let numbers = (1, 2, 3, 4, 5);
let maximum = Math.max(...numbers);//5
let minimum = Math.min(...numbers);//1
console.log(minimum);
```

```js
let username = "Bro Code";
let letters = [...username];//['b','r','o',' ','C','o','d','e']
let letters = [...username].join("-");//b-r-o- -C-o-d-e
console.log(letters);
```

```js
let fruits = ["apple", "orange", "banana", "coconut"];
let vegetables = ["carrots", "celery", "potatoes"];
let foods =[... fruits, ...vegetables, "eggs", "milk"];//->["apple", "orange", "banana", "coconut","carrots", "celery", "potatoes","eggs", "milk"];
```
# rest parameters
***rest parameters (...rest) allow a function work with a variable number of arguments by bundling them into an array
spread expands an array into separate elements rest bundles separate elements into an array

```js
function openFridge(...foods){
	console.log(...foods);//spread opertor//pizza hamburger hotdog sushi ramen
}
function getFood(...foods) { 
	return foods;//["pizza","hamburger","hotdog","sushi","ramen"]
}
const food1= "pizza";
const food2= "hamburger";
const food3= "hotdog";
const food4 = "sushi";
const foods = "ramen";
//openFridge(food1, food2, food3, food4, food5);
const foods = getFood (food1, food2, food, food4, food5);
console.log(foods);
```

```js
function getAverage(...numbers){
let result = 0;
for(let number of numbers) {
result += number;
}
return result / numbers.length;
}
const total = getAverage (75, 100, 85, 90, 50);
console.log(total);//80
```

```js
function combineStrings(...strings){
return strings.join(" ");
}
const fullName = combineStrings ("Mr.", "Spongebob", "Squarepants", "III").
console.log(fullName);//Mr. Spongebob Squarepants III
```
# Callback()
***callback a function that is passed as an argument to another function.
used to handle asynchronous operations:
 1. Reading a file
 2. Network requests
 3. Interacting with databases
" Hey, when you're done, call this next."
```js
sum(displayPage, 1, 2);
function sum(callback, x, y) {
let result = x + y;

callback(result);
function displayConsole (result) {
console.log(result);
}
function displayPage(result) {
document.getElementById("myH1").textContent = result;
}
```
# Callback hell
Situation in JavaScript where callbacks
are nested within other callbacks to the
degree where the code is difficult to read. Old pattern to handle asynchronous functions.
Use Promises + async/await to avoid Callback Hell
```js
function task1(callback) {
    setTimeout(() => {
        console.log("Task 1 complete");
        callback();
    }, 2000);
}

function task2(callback) {
    setTimeout(() => {
        console.log("Task 2 complete");
        callback();
    }, 1000);
}

function task3(callback) {
    setTimeout(() => {
        console.log("Task 3 complete");
        callback();
    }, 3000);
}

function task4(callback) {
    setTimeout(() => {
        console.log("Task 4 complete");
        callback();
    }, 1500);
}

function task5(callback) {
    setTimeout(() => {
        console.log("Task 5 complete");
        callback();
    }, 2000);
}

// Start the chain of tasks
task1(() => {
    task2(() => {
        task3(() => {
            task4(() => {
                task5(() => {
                    console.log("All tasks complete");
                });
            });
        });
    });
});

```

# Synchronous vs Asynchronous Programming

**Synchronous Programming**:
- Operations are executed one after another.
- Each operation must complete before the next one starts.
- If an operation takes a long time, the entire program waits for it to finish.

Example:
```javascript
console.log('Start');
console.log('Step 1');
console.log('Step 2');
console.log('End');
```
Output:
```
Start
Step 1
Step 2
End
```

**Asynchronous Programming**:
- Operations can be executed without waiting for previous operations to complete.
- The program can continue running while waiting for other operations to finish.
- Commonly used for operations that take a long time, such as network requests or file I/O.

Example with `setTimeout` (a simple asynchronous function):
```javascript
console.log('Start');
setTimeout(() => {
    console.log('Step 1');
}, 1000);
console.log('End');
```
Output:
```
Start
End
Step 1  // This appears after 1 second
```

# Promise Object
A **Promise** is an object representing the eventual completion (or failure) of an asynchronous operation and its resulting value.

A promise can be in one of three states:
1. **Pending**: The initial state, neither fulfilled nor rejected.
2. **Fulfilled**: The operation completed successfully.
3. **Rejected**: The operation failed.
Wrap a Promise Object around (asynchronous code)
"I promise to return a value"
PENDING -> RESOLVED or REJECTED
new Promise((resolve, reject) => (asynchronous code))
Example of creating a promise:
```javascript
let promise = new Promise((resolve, reject) => {
    let success = true; // Change this to false to simulate a failure
    if (success) {
        resolve("Operation was successful");
    } else {
        reject("Operation failed");
    }
});
```

### `then` Method

The `then` method is used to handle the fulfillment of a promise. It takes two arguments:
1. A callback function to be executed if the promise is fulfilled (resolved).
2. (Optional) A callback function to be executed if the promise is rejected.

Example:
```javascript
promise.then(
    value => { console.log(value); }, // Success handler
    error => { console.error(error); } // Failure handler
);
```

### Using Promises to Sequence Asynchronous Tasks

Now let's look at your example in detail:

```javascript
function walkDog() {
    return new Promise((resolve, reject) => {
        setTimeout(() => {
            const dogwalked = false;
            if (dogwalked) {
                resolve("You walk the dog");
            } else {
                reject("You DIDN'T walk the dog");
            }
        }, 1500);
    });
}

function cleankitchen() {
    return new Promise((resolve, reject) => {
        setTimeout(() => {
            const cleankitchen = true;
            if (cleankitchen) {
                resolve("You clean the kitchen");
            } else {
                reject("You DIDN'T clean the kitchen");
            }
        }, 500);
    });
}

function takeOutTrash() {
    return new Promise((resolve, reject) => {
        setTimeout(() => {
            const trashTakenOut = true;
            if (trashTakenOut) {
                resolve("You take out the trash");
            } else {
                reject("You DIDN'T take out the trash");
            }
        }, 500);
    });
}

walkDog()
    .then(value => {
        console.log(value);
        return cleankitchen();
    })
    .then(value => {
        console.log(value);
        return takeOutTrash();
    })
    .then(value => {
        console.log(value);
        console.log("You finished all the chores");
    })
    .catch(error => {
        console.error(error);
    });
```
# Async/Await 
Async - makes a function return a promise
Await - makes an async function wait for a promise
### The `await` Keyword
The `await` keyword can be used inside an `async` function to pause the execution of the function until the promise is settled (either fulfilled or rejected). When the promise is fulfilled, `await` returns the result of the promise. If the promise is rejected, `await` throws the rejected value

Allows you write asynchronous code in a synchronous manner Async doesn't have resolve or reject parameters Everything after Await is placed in an event queue
```js
async function dochores(){
try{  
	const walkDogResult = await walkDog(); console.log(walkDogResult); 
	const cleankitchenResult = await cleanKitchen(); console.log(cleanKitchenResult); 
	const takeOutTrashResult = await takeOutTrash(); console.log(takeOutTrashResult); 
	console.log("You finsihed all the chores!"); } catch(error) = > { console.error(error);}
	}
dochores();
```
# Error Handling
Error An Object that is created to represent a problem that occurs Occur often with user input or establishing a connection
-try {} finally {} = Encloses code that might potentially cause an error.
-catch {} = Catch and handle any thrown Errors from 
-finally {} = (optional) Always executes. Used mostly for clean up
ex, close files, close connections, release resources
```js
try{
console.log("Hello");
// NETWORK ERRORS
// PROMISE REJECTION
// SECURITY ERRORS
}
catch(error) {
console.error(error);
}
finally{
// CLOSE FILES
// CLOSE CONNECTIONS
// RELEASE RESOURCES
console.log("This always executes");
}
console.log("You have reached the end!");
```

```js
try{
const dividend = Number(window.prompt("Enter a dividend: "));
const divisor = Number(window.prompt("Enter a divisor: "));
if(divisor == 0)
throw new Error("You can't divide by zero!");
if(isNaN(dividend) || isNaN(divisor)) {
throw new Error("Values must be a number");
}
const result = dividend / divisor;
console.log(result);
}
catch(error) { console.error(error);
}
console.log("You have reached the end!");
```
# DOM Manipulation

***DOCUMENT OBJECT MODEL
Object() that represents the page you see in the web browser and provides you with an API to interact with it. Web browser constructs the DOM when it loads an HTML document, and structures all the elements in a tree-like representation. JavaScript can access the DOM to dynamically change the content, structure, and style of a web page.

***" Element selectors" Methods used to target and manipulate HTML elements
They allow you to select one or multiple HTML elements from the DOM (Document Object Model)
```js
1. document.getElementById()// ELEMENT OR NULL
2. document.getElementsClassName()// HTML COLLECTION
3. document.getElementsByTagName()// HTML COLLECTION
4. document.querySelector()// ELEMENT OR NULL
5. document.querySelectorAll()// NODELIST
```

```js
const fruits = document.getElementsByClassName("fruits");
Array.from(fruits).forEach(fruit => {
fruit.style.backgroundColor = "yellow";
}
```
```js
const h4Elements = document.getElementsByTagName("h4");
const liElements = document.getElementsByTagName("li");
for(let h4Element of h4Elements) {
h4Element.style.backgroundColor = "yellow";
}
for(let liElement of liElements){
liElement.style.backgroundColor = "lightgreen";
}
```
```js
const foods = document.querySelectorAll("li");
foods.forEach(food => {
food.style.backgroundColor = "yellow";
});
```

![[Screenshot 2024-07-26 094911.png]]

![[Screenshot 2024-07-26 094647.png]]

![[Screenshot 2024-07-26 094657.png]]
## DOM Navigation

***DOM Navigation The process of navigating through the structure of an HTML document using JavaScript.
- firstElementChild
- lastElementChild
- .nextElementSibling
- previousElementSibling
- parentElement
- children
```html
<ul id="fruits">
<li id="apple">apple</li>
<li id="orange">orange</li>
<li id="banana">banana</li>
</ul>
<ul id="vegetables">
<li id="carrots">carrots</li>
<li id="onions">onions</li>
<li id="potatoes">potatoes</li>
</ul>
<ul id="desserts">
<li id="cake">cake</li>
<li id="pie">pie</li>
<li id="ice cream">ice cream</li>
</ul>
```

```js
//.firstElementChild
const ulElements = document.querySelectorAll("ul");
ulElements.forEach(ulElement => {
const firstChild ulElement.firstElementChild;
firstChild.style.backgroundColor = "yellow";
});// all the 1st element of ul will be yellow
```

```js
//.lastElementChild
const element = document.getElementById("desserts");
const lastChild = element.lastElementChild;
lastChild.style.backgroundColor "yellow";//last element of desserts ul will be yellow
```

```js
//.nextElementSibling
const element = document.getElementById("apple");
const nextSibling element.nextElementSibling;
nextSibling.style.backgroundColor = "yellow";//orange will be yellow
```

```js
//previous ElementSibling
const element = document.getElementById("desserts");
const prevSibling = element.previous.ElementSibling; prevSibling.style.backgroundColor = "yellow";//whole list before dessert ul will yellow
```

```js
// .parentElement(parent access by the childrens)
const element = document.getElementById("ice cream");
const parent = element.parentElement;
parent.style.backgroundColor = "yellow";//it will access the icecream whole lists
```

```js
//.children(childrens acces by parents)
const element = document.getElementById("vegetables");
const children = element.children;
Array.from(children).forEach(child => {
child.style.backgroundColor = "yellow";
});
```
## Events and Event handler

![[Pasted image 20240726100250.png]]
### **"Hello word" content changed into "Bye world" by change function called when the button clicked
```html
<!DOCTYPE html>

<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    <h1 id="title">
        hello world
    </h1>
    <button onclick="change()">
        Button
    </button>
</body>
<script>
    const title = document.getElementById('title');
    function change(){
        title.textContent="Bye world"
    }
</script>
</html>
```
### Add 2 nos
```html
<!DOCTYPE html>

<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    <input type="number" id="n1">
    <input type="number" id="n2">
    <button onclick="add()">
        ADD
    </button>
    <p id="result">
        Result =
    </p>
</body>
<script>
    function add(){
    const n1 = document.getElementById('n1');
    const n2 = document.getElementById('n2');
    const p = document.getElementById('result');
    const total = Number(n1.value)+Number(n2.value);
            p.textContent+=" = "+total;
    }
</script>
</html>
```
![[Pasted image 20240726103707.png]]
![[Pasted image 20240726103557.png]]
### Guess No game using Math function
```html
<h1>
    Guess the number
</h1>
<input id="originalno" type="number">
<button onclick="randomno()">check</button>
<p id="score">Score : 10</p>
<p id="text">You are right/Wrong</p>
<script>
    var  score=document.getElementById('score');
    var  totalScore=10;
    const p=document.getElementById('text');
    function randomno(){
        const Rn=Math.floor(Math.random()*10);
        const N=document.getElementById('originalno');
        const n=Number(N.value);
        if(Rn===n){
            p.textContent=Rn + " - You are Right";
            alert("You WON!!...")
        }
        else{
            totalScore=totalScore-1;
            score.textContent="Score : "+totalScore;
            p.textContent=Rn + " - You are Wrong";
        }
        
    }

</script>
```
![[Pasted image 20240728200709.png]]
![[Pasted image 20240728200725.png]]
### Tasks
#### 1.
```html
<input id="inputbox" onkeyup="update()">
<h1 id="result"></h1>
<script>
var inputbox=document.getElementById("inputbox")
var result= document.getElementById("result")
function update()
{
result.textContent=inputbox.value
}
</script>
```
![[Pasted image 20240728203235.png]]
#### 2.
```html
<button onclick="update()">Add</button> <div id="result"></div>
<script>
//select hi
var div=document.getElementById("result")
function update() {
//create new element
var listitem=document.createElement("h1") 
listitem.textContent="Hello"
div.append(listitem)
}
</script>
```
![[Pasted image 20240728204642.png]]
#### 3.
```html
<h1 id="result">Name</h1>
<button onclick="update(event)">John</button>
<button onclick="update(event)">Praveen</button>
<button onclick="update (event)">Karthick</button>
<script>
var h1=document.getElementById("result")
function update(event)
h1.textContent=event.target.textContent
</script>
```
![[Pasted image 20240728205829.png]]
#### 4.

```html
<h1 onclick="deleteitem(event)">One</h1>
<h1 onclick="deleteitem(event)">Two</h1>
<h1 onclick="deleteitem(event)">Three</h1>
<h1 onclick="deleteitem(event)">Four</h1>
<h1 onclick="deleteitem(event)">Five</h1>
<h1 onclick="deleteitem(event)">Six</h1>
<script>
//h1
function deleteitem(event){
event.target.remove()
}
</script>
```
![[Pasted image 20240728210726.png]]
**After Click "Three"
![[Pasted image 20240728210805.png]]

### Manipulate css using js
```html
<style>
    div{
    background-color: black;
    width: 100px;
    height: 100px;
    transition: 2s;
    }
    .widthmax{
    width: 900px;
    }
    </style>
    <div id="box"></div>
    <button onclick="change()">change color</button>
    <script>
    var box=document.getElementById("box")
    function change(){
        box.setAttribute("class","widthmax")
    }
    </script>
```
![[Pasted image 20240728202525.png]]
![[Pasted image 20240728202528.png]]

# EventListener
 Listen for specific events to create interactive web pages
events: click, mouseover, mouseout
.addEventListener(event, callback);
```js
const myBox = document.getElementById("myBox");
myBox.addEventListener("click", event=> { event.target.style.backgroundColor = "tomato";
event.target.textContent = "OUCH! 😯"});
myBox.addEventListener("mouseover", event => {
event.target.style.backgroundColor = "yellow";
event.target.textContent = "Don't do it";
});
myBox.addEventListener("mouseout", event => {event.target.style.backgroundColor = "lightgreen";
event.target.textContent = "Click Me 😊";
});
```
# Todo list

![[Pasted image 20240728220717.png]]
![[Pasted image 20240728220805.png]]
![[Pasted image 20240729121217.png]]
```html
<div class="one"> Hello
</div>
<script>
//div select
var div=document.querySelector(".one") console.log(div)
</script>
```

```html
<h1 class="ok">One</h1>
<h1 class="ok">Two</h1>
<h1 class="ok">Three</h1>
<script>
//div select
var div=document.querySelectorAll(".ok") for(count=0; count<div.length; count=count+1)
{
console.log(div[count].textContent)
}
</script>
```
![[Pasted image 20240729122411.png]]
![[Pasted image 20240729122554.png]]
![[Pasted image 20240729122556.png]]
![[Pasted image 20240729123406.png]]
```js
//
//EXAMPLE 1 <h1>
// STEP 1 CREATE THE ELEMENT 
const newH1 = document.createElement("h1");
// STEP 2 ADD ATTRIBUTES/PROPERTIES
newH1.textContent = "I like pizza!";
newH1.id "myH1";
newH1.style.color = "tomato";
newH1.style.textAlign="center";
//STEP 3 APPEND ELEMENT TO DOM
document.body.append(newLink);
document.body.prepend(newLink);
document.getElementById("box1").append(newLink);
document.getElementById("box4").prepend(newLink);
const box4 document.getElementById("box4");
document.body.insertBefore(newLink, box4);
const boxes document.querySelectorAll(".box");
document.body.insertBefore(newLink, boxes [4]);
//REMOVE HTML ELEMENT
document.body.removeChild(newLink);
document.getElementById("box1").removeChild(newLink);
```

```js
//EXAMPLE 2 <li>
// STEP 1 CREATE THE ELEMENT 
const newListItem = document.createElement("li");
// STEP 2 ADD ATTRIBUTES/PROPERTIES
newListItem.textContent = "coconut";
newListItem.id = "coconut";
newListItem.style.fontweight = "bold";
newListItem.style.backgroundColor = "lightgreen";
// STEP 3 APPEND ELEMENT TO DOM
document.body.append(newListItem);
document.body.prepend(newListItem);
document.getElementById("fruits").append(newListItem);
document.getElementById("fruits").prepend(newListItem);
const banana = document.getElementById("banana");
document.getElementById("fruits").insertBefore(newListItem, banana);
const listItems document.querySelectorAll("#fruits li");
document.getElementById("fruits").insertBefore(newListItem, listItems[4]);
// REMOVE HTML ELEMENT
```

```html
<input id="input">
<button onclick="add()">Add</button>
<ul id="list-container">
<li>Hello
<button onclick="deleteItem (event)">Delete</button>
</li>
</ul>
<script>
//selecting ul
var ul =document.getElementById("list-container")
var input =document.getElementById("input")
function add()
{
var listitem= document.createElement("li")
listitem.innerHTML=input.value + "<button onclick='deleteItem (event)'>Delete</button
ul.append(listitem)
}
function deleteItem(event)
{
event target parentElement.remove
```
![[Pasted image 20240729125923.png]]
# NodeList
NodeList Static collection of HTML elements by (id, class, element)
Can be created by using querySelectorAll()
Similar to an array, but no (map, filter, reduce)
NodeList won't update to automatically reflect changes
```js
///4 buttons in html code
//ADD HTML/CSS PROPERTIES
buttons.forEach(button => {
button.style.backgroundColor = "green";
button.textContent +="😯";
});

// CLICK event listener
buttons.forEach(button => {
button.addEventListener("click", event => {
event.target.style.backgroundColor = "tomato";
});
});

// MOUSEOVER + MOUSEOUT event listener
buttons.forEach(button => {
button.addEventListener("mouseover", event => {
event.target.style.backgroundColor = "hsl (205, 100%, 40%)";
});
});
buttons.forEach(button => {
button.addEventListener("mouseout", event => {
event.target.style.backgroundColor = "hsl (205, 100%, 60%)";
});
});

// ADD AN ELEMENT
const newButton document.createElement("button"); //STEP 1
newButton.textContent = "Button 5"; //STEP 2
newButton.classList "myButtons";
document.body.appendChild(newButton); //STEP 3

// REMOVE AN ELEMENT
buttons.forEach(button => {
button.addEventListener("click", event => {
event.target.remove();
buttons document.querySelectorAll(".myButtons");//node cannot be updated automatically it.so we can update for each events
});
});
```
# classList
 classList Element property in JavaScript used to interact // with an element's list of classes (CSS classes)
Allows you to make reusable classes for many elements across your webpage.
// add()
// remove()
//toggle(Remove if present, Add if not)
// replace(oldClass, newClass)
// contains()
```css
#myButtons{
font-size: 4rem;
margin: 10px;
border: none;
border-radius: 5px;
padding: 10px 15px;
}
.enabled{
background-color:
hsl (204, 100%, 50%);
color: white;
}
.hover{
box-shadow: 0 0 10px ☐ hsla(0, 0%, 0%, 0.2);
font-weight: bold;
}
.disabled{
background-color:
color:
hsl(0, 0%, 60%);
hsl(0, 0%, 80%);
}
```

```js
// add()
const myButton document.getElementById("myButton");
myButton.addEventListener("mouseover", event => { event.target.classList.add("hover");
));
// remove()
myButton.addEventListener("mouseout", event => { event.target.classList.remove("hover"); });	 
```

```js
//toggle(Remove if present, Add if not)
myButton.addEventListener("mouseover", event event.target.classList.toggle("hover"); });
myButton.addEventListener("mouseout", event event.target.classList.toggle("hover"); });
```

```js
// replace(oldClass, newClass)
// contains()
myButton.classList.add("enabled");
myButton.addEventListener("click", event => {
if(event.target.classList.contains("disabled")) {
event.target.textContent += "😯";
}
else{
event.target.classList.replace("enabled", "disabled");
});
```

```js
//set of buttons with class mybuttons
let buttons document.querySelectorAll(".myButtons");
buttons.forEach(button => {
button.classList.add("enabled");
});
buttons.forEach(button => {
button.addEventListener("mouseover", event {
event.target.classList.toggle("hover"); });
});
buttons.forEach(button
button.addEventListener("mouseout, event {
event.target.classList.toggle("hover"); });
});
buttons.forEach (button => {
button.addEventListener("click", event {
if(event.target.classList.contains("disabled")){
event.target.textContent +="😯";
}
else{
event.target.classList.replace("enabled", "disabled");
});
});
myButton.addEventListener("mouseout", event => { event.target.classList.remove("hover"); });const myButton document.getElementById("myButton");
myButton.addEventListener("mouseover", event => { event.target.classList.add("hover");
));
```
# JSON File
**JSON** (JavaScript Object Notation) is a lightweight data-interchange format that's easy for humans to read and write, and easy for machines to parse and generate. It is widely used for transmitting data between a server and a web application as text.

### **Key Features of JSON:**

1. **Human-Readable:** JSON is formatted in a way that is easy for humans to understand. It consists of key-value pairs and arrays, much like how objects are defined in JavaScript.

2. **Lightweight:** JSON is a compact format that minimizes the amount of data being transmitted over a network, making it efficient for data exchange.

3. **Language Independent:** Although JSON is based on a subset of JavaScript, it is language-independent and can be parsed and generated by most programming languages, including Python, Java, C#, PHP, and many others.

4. **Self-Describing:** JSON is easy to understand because its format closely resembles the way data is structured in many programming languages.

### **Structure of JSON:**

JSON data is structured as a collection of key-value pairs, similar to how dictionaries or objects work in programming languages. The structure typically includes:

- **Objects:** Enclosed in curly braces `{}` and contain key-value pairs.
- **Arrays:** Enclosed in square brackets `[]` and can contain a list of values or objects.
- **Values:** Can be strings, numbers, booleans, null, objects, or arrays.

### **Example of JSON:**

```json
{
  "name": "John Doe",
  "age": 30,
  "isStudent": false,
  "courses": ["Math", "Science", "History"],
  "address": {
    "street": "123 Main St",
    "city": "Anytown",
    "state": "CA",
    "postalCode": "12345"
  }
}
```

- **Objects:** `{"name": "John Doe", "age": 30, "isStudent": false, "courses": [...], "address": {...}}`
- **Arrays:** `"courses": ["Math", "Science", "History"]`
- **Key-Value Pairs:** `"name": "John Doe"`, `"age": 30`, etc.

### **Why Use JSON?**

1. **Data Exchange:** JSON is commonly used to exchange data between a client and a server in web applications. When a client requests data from a server, the server often responds with JSON data.

2. **Configuration Files:** JSON is also used for configuration files in various software applications because of its simplicity and readability.

3. **APIs:** Many RESTful APIs return data in JSON format because it's easy for both humans and machines to understand and process.

### **Advantages of JSON:**

- **Easy to read and write:** Simple and intuitive syntax.
- **Widely supported:** Almost every modern programming language has libraries or built-in support for JSON.
- **Efficient:** Lightweight format, making it faster to transmit over networks.

### **Disadvantages of JSON:**

- **No support for complex data types:** JSON only supports basic data types like strings, numbers, booleans, arrays, and objects.
- **Lacks schema validation:** JSON doesn't natively support data validation, though there are libraries and tools to add this functionality.

JSON has become a standard for data interchange on the web due to its simplicity and flexibility. It's an essential format to understand when working with web development, APIs, and various modern applications.
# Fetch API
***fetch Function used for making HTTP requests to fetch resources.
(JSON style data, images, files)
Simplifies asynchronous data fetching in JavaScript and used for interacting with APIs to retrieve and send data asynchronously over the web.
![[Pasted image 20240814230453.png]]
Sure! Let's break down the JavaScript code step by step for someone who is new to fetching data from an API and using asynchronous functions in JavaScript.

```js
async function fetchData() {
    try {
        // Get the input value and convert it to lowercase
        const pokemonName = document.getElementById("pokemonName").value.toLowerCase();
        
        // Make a network request to fetch the Pokemon data
        const response = await fetch(`https://pokeapi.co/api/v2/pokemon/${pokemonName}`);
        
        // Check if the response is okay (status code 200-299)
        if (!response.ok) {
            throw new Error("Could not fetch resource");
        }
        
        // Parse the response body as JSON
        const data = await response.json();
        
        // Get the Pokemon sprite URL from the JSON data
        const pokemonSprite = data.sprites.front_default;
        
        // Get the image element and set its source to the sprite URL
        const imgElement = document.getElementById("pokemonSprite");
        imgElement.src = pokemonSprite;
        imgElement.style.display = "block";
    } catch (error) {
        // Log any errors that occur
        console.error(error);
    }
}
```
### Step-by-Step Explanation:

1. **HTML Setup:**
    - We have an input field where the user can type the name of a Pokemon.
    - A button that, when clicked, will call the `fetchData` function.
    - An `img` element that will display the Pokemon sprite once it's fetched.

2. **JavaScript Function (`fetchData`):**

    ```javascript
    async function fetchData() {
    ```

    - The `async` keyword before the function declaration allows us to use `await` inside this function. `await` makes the function wait for a promise to resolve, making it easier to work with asynchronous code.

3. **Try-Catch Block:**

    ```javascript
    try {
    ```

    - The `try` block lets us write code that might throw an error, which we can handle gracefully using the `catch` block.

4. **Getting Input Value:**

    ```javascript
    const pokemonName = document.getElementById("pokemonName").value.toLowerCase();
    ```

    - We get the value from the input field (the name of the Pokemon entered by the user) and convert it to lowercase to ensure it matches the API's requirements (Pokemon names are case-sensitive in the API).

5. **Fetching Data from the API:**

    ```javascript
    const response = await fetch(`https://pokeapi.co/api/v2/pokemon/${pokemonName}`);
    ```
    Promises and `await` Work Together
    - The `fetch` function returns a promise. The `await` keyword waits for this promise to resolve.
	- While waiting, the function is paused and other code can run.
	- Once the promise resolves, the `response` object contains the HTTP response.
    - `fetch` is a function that makes a network request to the specified URL. The `await` keyword makes the code wait until the request is complete and returns a response.
    - We use a template literal (backticks) to insert the Pokemon name into the URL dynamically.

6. **Checking Response Status:**

    ```javascript
    if (!response.ok) {
        throw new Error("Could not fetch resource");
    }
    ```

    - `response.ok` is a boolean that indicates if the response status is in the range 200-299, which means the request was successful.
    - If the response is not okay, we throw an error with a custom message.

7. **Parsing the JSON Data:**

    ```javascript
    const data = await response.json();
    ```
    - The `response.json()` method returns a promise that resolves to a JSON object.
	- The `await` keyword waits for this promise to resolve.
	- Once the promise resolves, the `data` object contains the parsed JSON.
    - The `response.json()` method parses the JSON body of the response and returns a promise. We use `await` to wait for this promise to resolve and give us the parsed data.

8. **Extracting the Pokemon Sprite URL:**

    ```javascript
    const pokemonSprite = data.sprites.front_default;
    ```

    - We extract the URL of the Pokemon's front sprite from the parsed data. The API response includes various properties, and `sprites.front_default` is the URL of the front image of the Pokemon.

9. **Displaying the Image:**

    ```javascript
    const imgElement = document.getElementById("pokemonSprite");
    imgElement.src = pokemonSprite;
    imgElement.style.display = "block";
    ```

    - We get the `img` element by its ID.
    - We set the `src` attribute of the `img` element to the URL of the Pokemon sprite, so the image is displayed.
    - We set the `display` style of the image element to `block` to ensure it is visible (it was initially set to `none`).

10. **Handling Errors:**

    ```javascript
    } catch (error) {
        console.error(error);
    }
    ```

    - If any error occurs during the execution of the `try` block (e.g., network error, invalid Pokemon name), the control moves to the `catch` block.
    - The `catch` block logs the error to the console.
### How it Works:

1. The user enters a Pokemon name and clicks the "Fetch Pokemon" button.
2. The `fetchData` function is called.
3. The function gets the entered Pokemon name, converts it to lowercase, and makes a request to the PokeAPI.
4. If the response is successful, it extracts the Pokemon sprite URL from the response data.
5. The function then sets the `src` attribute of the image element to the sprite URL and makes the image visible.
6. If there is an error (e.g., the Pokemon name is invalid), it logs the error to the console.


