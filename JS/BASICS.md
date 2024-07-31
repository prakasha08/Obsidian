# Variable Declaration
![[Pasted image 20240717171116.png]]
![[Pasted image 20240717171122.png]]
![[Pasted image 20240717171129.png]]
![[Pasted image 20240717171337.png]]

## Diff btw declaration of name and "name" to a Variable
![[Pasted image 20240717172004.png]]

# Keywords in JS
![[Pasted image 20240717172329.png]]
# Operators
![[Pasted image 20240717173354.png]]
# Datatypes
![[Pasted image 20240717173611.png]]
# Functions

Functions are have set of instruction to do some particular task
which can be called by their name. Its look like if you want to call someone through mobile by their Phone number,

![[Pasted image 20240717173710.png]]
![[Pasted image 20240717183154.png]]
## Function using return type
![[Pasted image 20240717183223.png]]
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
cbutton onclick="update()">Add</button> <div id="result"></div>
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
var ul document.getElementById("list-container")
var input document.getElementById("input")
function add()
{
var listitem document.createElement("li")
listitem.innerHTML=input.value + "<button onclick='deleteItem (event)'>Delete</button
ul.append(listitem)
}
function deleteItem(event)
{
event target parentElement.remove
```
![[Pasted image 20240729125923.png]]
