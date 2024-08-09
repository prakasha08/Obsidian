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
console.log("Your name is ${firstName));
console.log(You like ${favoriteFood));
console.log(Your email is ${email});
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
Let circumference;
document.getElementById("mySubmit").onclick = function(){
radius= document.getElementById("myText").value;
radius Number(radius);
circumference 2 PI * radius;
document.getElementById("myH3").textContent circumference "cm"
```
![[Pasted image 20240801220101.png]]
# Type Conversion
```js
// type conversion change the datatype of a value to another // (strings, numbers, booleans)
let age = window.prompt("How old are you?");
age Number(age);
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
zMath.round(x);
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
return x y;
}
function multiply(x, y){
return x y;
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
let fruits = ["apple", "orange", "banana", "coconut"];
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
array [index] element.toLowerCase();}
function capitalize(element, index, array){
array[index] = element.charAt(0).toUpperCase() + element.slice(1);
function display(element){
console.log(element);}
```
## Map function
***.map() = accepts a callback and applies that function to each element of an array, then return a new array
It same as like foreach loop
```js
const numbers [1, 2, 3, 4, 5];
const squares = numbers.map(square);
const cubes numbers.map(cube);
console.log(cubes);
function square(element) {
return Math.pow(element, 2)
}
function cube (element) {
return Math.pow(element, 3)
}
```

```js
const numbers [1, 2, 3, 4, 5];
const squares = numbers.map(square);
const cubes numbers.map(cube);
console.log(cubes);
function square(element) {
return Math.pow(element, 2)
}
function cube (element) {
return Math.pow(element, 3)
}
```

```js
const dates ["2024-1-10", "2025-2-20", "2026-3-30"];
const formattedDates dates.map(formatDates);
console.log(formattedDates);
function formatDates (element){
const parts element.split("-");
return ${parts[1])/${parts [2]}/${parts[0]);
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
const prices [5, 30, 10, 25, 15, 20];
const total prices.reduce(sum);
console.log($${total.toFixed(2)));
function sum(accumulator, element){ 
return accumulator + element;
}
```

```js
const grades [75, 50, 90, 80, 65, 95];
const maximum grades.reduce(getMax);
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
const colors ["red", "green", "blue", "black", "white"];
[colors[0], colors [4]] = [colors [4], colors[0]);
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
# Function Expression
***function expressions a way to define functions as Values or variables
```js
setTimeout(function(){ console.log("Hello"); ), 3000);
```

```js
const numbers = [1, 2, 3, 4, 5, 6];
const squares numbers.map(function(element){
return Math.pow(element, 2);
1);
const cubes numbers.map(function(element){
return Math.pow(element, 3);
));
const evenNums numbers.filter(function(element){
return element%20;
});
const oddNums numbers.filter(function(element){
return element %2!=0;
));
const total numbers.reduce(function(accumulator, element) (
return accumulator + element;
));
  ```
# Arrow Function
**arrow functions is a concise way to write function expressions good for simple functions that you use only once (parameters) => some code

```js
setTimeout( => console.log("Hello"), 3000);
```

```js
const squares numbers.map((element) => Math.pow(element, 2));
const cubes = numbers.map((element) Math.pow(element, 3));
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
```
# Synchronous Code
// synchronous = Executes line by line consecutively in a sequential manner Code that waits for an operation to complete.

// asynchronous = Allows multiple operations to be performed concurrently without waiting Doesn't block the execution flow and allows the program to continue (I/O operations, network requests, fetching data) Handled with: Callbacks, Promises, Async/Await
//
```js

function func1(callback) {
setTimeout(() => {console.log("Task 1"); callback()), 3000);
}
function func2(){
console.log("Task 2");
console.log("Task 3"); console.log("Task 4");
func1(func2); 
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
const dividend Number(window.prompt("Enter a dividend: "));
const divisor = Number(window.prompt("Enter a divisor: "));
if(divisor == 0)
throw new Error("You can't divide by zero!");
if(isNaN(dividend) || isNaN(divisor)) {
throw new Error("Values must be a number");
}
const result dividend / divisor;
console.log(result);
}
catch(error) { console.error(error);
}
console.log("You have reached the end!");
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

# DOM Manipulation

![[Screenshot 2024-07-26 094911.png]]

![[Screenshot 2024-07-26 094647.png]]

![[Screenshot 2024-07-26 094657.png]]

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
