# HTML
## TEXT FORMAT
```HTML
<body>
<p>This is normal text</p>
<p>This is <b>bold</b> text</p>
<p>This is <i>italic</i> text</p>
<p>This is <u>underlined</u> text</p>
<p>This is <del>deleted</del> text</p>
<p>This is <big>big</big> text</p>
<p>This is <small>small</small> text</p>
<p>This is <sub>subscript</sub> text</p>
<p>This is <sup>superscript</sup> text</p>
<p>This is <tt>monospaced</tt> text</p>
<p>This is <mark>normal</mark> text</p>
</body>
```
![[Pasted image 20240416223539.png]]
## Span & Div
![[Pasted image 20240416225418.png]]
## List
```html
 <body>

        <!-- Unordered List -->

        <h4>Groceries</h4>

        <ul>

        <li>milk</li>

        <li>eggs</li>

        <li>bread</li>

        <li>coffee supplies</li>

        <ul>

        <li>coffee beans</li>

        <li>creamer</li>

        <li>sugar</li>

        </ul>

        </ul>

        <!-- Ordered List -->

        <h4>To do list</h4>

        <ol>

        <li>eat breakfast</li>

        <li>go to class</li>

        <li>walk dog</li>

        <li>work</li>

        </ol>

  

        <dl>

            <dt>dragon</dt>

            <dd>

                A dragon is a magical legendary creature that appears in the folklore of multiple cultures worldwide.

            </dd>

            <dt>phoenix</dt>

            <dd>

                The phoenix is an immortal bird that cyclically regenerates or is otherwise born again.

            </dd>

            <dt>vampire</dt>

            <dd>A vampire is a mythical creature that subsists by feeding on the vital essence of the living.</dd>

            </dl>

            </body>
```
![[Pasted image 20240416232537.png]]
## Table
```html
<body>

        <h3>Store Hours</h3>

        <table border="1" style="background-color: black;">

        <tr align="center" style="background-color: lightblue;">

        <th width="100">Sunday</th>

        <th width="100">Monday</th>

        <th width="100">Tuesday</th>

        <th width="100">Wednesday</th>

        <th width="100">Thursday</th>

        <th width="100">Friday</th>

        <th width="100">Saturday</th>

        </tr>

        <tr align="center" style="background-color: aliceblue;">

            <td>Closed</td>

            <td>9-5</td>

            <td>9-5</td>

            <td>9-5</td>

            <td>9-5</td>

            <td>9-5</td>

            <td></td>

            </tr>

        </table>

    </body>
```
![[Pasted image 20240416234508.png]]
## Buttons
```html
  <body>

        <a href="https://www.youtube.com/watch?v=HGTJBPNC-Gw&t=1892s">

            <button style="font-size: 35px; background-color: gray; color:lightblue; border-radius: 25px;">

               GO BRO

            </button>

        </a>

        <a href="link.html">

            <button style="font-size: 35px; background-color: gray; color:lightblue; border-radius: 25px;">

             GO HOME

            </button>

        </a>

    </body>
```
![[Pasted image 20240416235918.png]]
## Forms
```html
<!DOCTYPE html>

<html>
    <head>
        <title>
            Forms
        </title>
    </head>
    <body>
        <form action="index.php" method="post" >
            <label for="username">Username:</label>
            <input type="text" id="username" placeholder="Prakii" minlength="3" maxlength="10" required>
            <br>
            <label for="password">Password:</label>
            <input type="password" id="password" minlength="3" maxlength="10" required>

            <br>

            <label for="email">Email:</label>

            <input type="email" id="email"  required>

            <br>

            <label for="phone">Ph.No :</label>

            <input type="tel" id="phone" placeholder="123-456-7890" pattern="[0-9]{3}-[0-9]{3}-[0-9]{4}" required>

            <br>

            <label for="bday">DOB :</label>

            <input type="date" id="bday"  required>

            <br>

            <label for="quantity">Quantity :</label>

            <input type="number" id="quantity" min="0" max="99" value="0" required>

            <br>

            <label for="title">Title :</label>

            <label for="Mr.">Mr.:</label>

            <input type="radio" id="Mr." value="Mr." name="title">

            <label for="Ms.">Ms.:</label>

            <input type="radio" id="Ms." value="Ms." name="title">

            <label for="PhD.">PhD:</label>

            <input type="radio" id="PhD." value="PhD." name="title">

            <br>

            <label for="payment">Payment:</label>

            <select>

                <option value=""></option>

                <option value="visa">Visa</option>

                <option value="Debit">Debit</option>

                <option value="Mastercard">Mastercard</option>

            </select>

            <br>

            <label for="subcribe" >Subcribe</label>

            <input type="checkbox" id="subcribe">

            <br>

            <label for="comments" >Comments: </label>

            <textarea  id="comments" cols="30" rows="10"></textarea>

            <br>

            <label for="file" >File: </label>

            <input type="file" id="file" accept="image/png, image/jpeg">

            <br>

            <input type="reset">

            <br>

            <input type="submit">

        </form>

    </body>

</html>
```
![[Pasted image 20240423211405.png]]

## HEADER & FOOTER
```html
<!DOCTYPE html>

<html>

    <head>

        <Title>Header</Title>

    </head>

    <body>

        <header style="color: rgb(35, 217, 153); background-color: rgb(36, 26, 103);">

            <h1>

                Welcome Buddyy!

            </h1>

           <a href="" style="color: rgb(218, 172, 4);">Home</a>

           <a href=""  style="color: rgb(218, 172, 4);">Contact</a>

           <a href="" style="color: rgb(218, 172, 4);">mail</a>

           <a href="" style="color: rgb(218, 172, 4);">About us</a>

           <a href="" style="color: rgb(218, 172, 4);">Product</a>

        </header>

        <hr>

        <main>

            <h4>

                Check out !

            </h4>

            <image src="./Images/download.png">

                <p>

                    Lorem ipsum dolor sit amet consectetur adipisicing elit. Necessitatibus molestias mollitia omnis qui quos ut unde soluta non. Sapiente nemo at veniam nam a ea provident molestiae quisquam doloremque quaerat?

                </p>

            </image>

        </main>

        <footer style="color: rgb(35, 217, 153); background-color: rgb(36, 26, 103);">

            <hr>

            Author:Its_prakii<br>

            <a style="color: aquamarine;">

                &copy;copyright Reserved <br></a>

            <a href="mailto:prakash2292004@gmail.com" style="color: aquamarine;">

                @prakii

            </a>

        </footer>

    </body>

</html>
```
![[Pasted image 20240423211703.png]]
# CSS
## Calling CSS using Class and id 
HTML FILE
```html
<h4 class="odd">Groceries</h4>

        <ul>

        <li id="p1"class="even">milk</li>

        <li class="even">eggs</li>

        <li class="even">bread</li>

        <li class="even">coffee supplies</li>

        <ul>

        <li class="eod">coffee beans</li>

        <li class="eod">creamer</li>

        <li class="eod">sugar</li>

        </ul>

        </ul>

        <!-- Ordered List -->

        <h4 class="odd">To do list</h4>

        <ol>

        <li class="even">eat breakfast</li>

        <li class="even">go to class</li>

        <li class="even">walk dog</li>

        <li class="even">work</li>

        </ol>

  

        <dl>

            <dt class="odd">dragon</dt>

            <dd class="eod">

                A dragon is a magical legendary creature that appears in the folklore of multiple cultures worldwide.

            </dd>

            <dt class="odd">phoenix</dt>

            <dd class="eod">

                The phoenix is an immortal bird that cyclically regenerates or is otherwise born again.

            </dd>

            <dt class="odd">vampire</dt>

            <dd class="eod">A vampire is a mythical creature that subsists by feeding on the vital essence of the living.</dd>

            </dl>

            </body>
```
css file
```css
body{

    background-color: blanchedalmond;

}
p1{

}

.odd{

    color: rgb(239, 117, 18);

}

.even{

    color: rgb(43, 226, 64);

}

.eod{

    color: rgb(255, 0, 247);

}
```
![[Pasted image 20240423212454.png]]
## Colors can be used In 4 ways in CSS
![[Pasted image 20240423214415.png]]
## Fonts & Borders
```css
@font-face {

    font-family: Noto;

    src: url(/Fonts/NotoSans-Italic-VariableFont_wdth\,wght.ttf);

}

@font-face {

    font-family: Roboto-light;

    src: url(/Fonts/Roboto-BlackItalic.ttf);

}

h1{

    font-family: Verdana, Geneva, Tahoma, sans-serif;

}

p{

    font-family:Roboto-light,"courier new";

    font-size: 30 px ;

    font-weight: bold;

    font-style: italic;

}
h1{

   /* border-style: solid;

   border-width: 3px;

   border-color: black; */

   border: 3px solid black;

   border-radius: 100px;

}

p{

    border-bottom: 3px dotted black;

    border-left: 3px solid rgb(245, 170, 8);

    border-right: solid rgb(245, 170, 8);

    border-top: dotted 3px black;

}
```
![[Pasted image 20240424093400.png]]

## Shadows
```html
<style>

    h1{

    text-shadow: 3px 3px 5px hsl(0, 100%, 61%),-3px -3px 5px hsl(160, 100%, 61%)

    }

    #box1{

    width: 100px;

    height: 100px;

    background-color: rgb(54, 183, 242);

    box-shadow: 5px 5px 10px;

    }

   </style>

</head>

<body>

    <h1>

        Prakii

    </h1>

    <div id="box1"></div>

</body>
```
![[Pasted image 20240424100836.png]]

## Margins
```html
 <style>

        body{

margin: 0px;

}

.box{

border: 5px solid;

font-size: 5em;

width: 250px;

height: 250px;

margin: auto;

}

#box1{

background-color: hsl(0, 100%, 60%);

}

#box2{

background-color: hsl (189, 100%, 55%);

}

    </style>

</head>

<body>

    <div class="box" id="box1">Box 1</div>

<div class="box" id="box2">Box 2</div>

</body>
```
![[Pasted image 20240424102330.png]]

## Float 
```html
<style>
        body{
            border: solid 5px ;
            margin-top: 20px;
            display: flow-root;
        }
        #image1{
           float: left;
            margin-right: 10px;
        }
        #image2{
            float: right;
            margin-left: 10px;
        }
    </style>
</head>
<body>
    <img src="/Images/download.jpeg" height="150px" id="image1">
    <p >Lorem ipsum, dolor sit amet consectetur adipisicing elit. Molestiae adipisci quis laudantium nobis harum saepe corrupti ad laborum ratione, rerum corporis itaque quas. Quisquam nesciunt ut pariatur voluptatem quia? Corrupti.</p>
    <p>Lorem ipsum, dolor sit amet consectetur adipisicing elit. Molestiae adipisci quis laudantium nobis harum saepe corrupti ad laborum ratione, rerum corporis itaque quas. Quisquam nesciunt ut pariatur voluptatem quia? Corrupti.</p>
    <img src="/Images/images.jpeg" height="150px" id="image2">
    <p>Lorem ipsum, dolor sit amet consectetur adipisicing elit. Molestiae adipisci quis laudantium nobis harum saepe corrupti ad laborum ratione, rerum corporis itaque quas. Quisquam nesciunt ut pariatur voluptatem quia? Corrupti.</p>
    <p>Lorem ipsum, dolor sit amet consectetur adipisicing elit. Molestiae adipisci quis laudantium nobis harum saepe corrupti ad laborum ratione, rerum corporis itaque quas. Quisquam nesciunt ut pariatur voluptatem quia? Corrupti.</p>
    <p>Lorem ipsum, dolor sit amet consectetur adipisicing elit. Molestiae adipisci quis laudantium nobis harum saepe corrupti ad laborum ratione, rerum corporis itaque quas. Quisquam nesciunt ut pariatur voluptatem quia? Corrupti.</p>
</body>
```
![[Pasted image 20240424111950.png]]

## Overflow

***-overflow property that sets the desired behavior when content does not fit in the parent element box (overflows)
overflow: visible
overflow: hidden
overflow: clip
overflow: scroll
overflow: auto*
```html
<style>

        #p1{

            border: 2px solid;

            height: 75px;

            overflow: visible;

            margin-bottom: 70px;

        }

        #p2{

            border: 2px solid;

            height: 75px;

            overflow: hidden;

        }

        #p3{

            border: 2px solid;

            height: 75px;

            overflow: clip;

        }

        #p4{

            border: 2px solid;

            height: 75px;

            overflow: clip;

            overflow-clip-margin: 13px;

        }

        #p5{

            border: 2px solid;

            height: 75px;

            overflow:scroll;

        }

        #p6{

            border: 2px solid;

            height: 75px;

            overflow: auto;

        }

        #p7{

            border: 2px solid;

            height: 75px;

            overflow: auto;

        }

    </style>

</head>

<body>

    <div>

        <p id="p1">Lorem, ipsum dolor sit amet consectetur adipisicing elit. Dolorum culpa iure modi nesciunt doloremque, illo quis, minus ipsam impedit nihil molestias magni vel maiores ea voluptatum repellendus. Nulla, quia magni!Lorem, ipsum dolor sit amet consectetur adipisicing elit. Dolorum culpa iure modi nesciunt doloremque, illo quis, minus ipsam impedit nihil molestias magni vel maiores ea voluptatum repellendus. Nulla, quia magni!</p>

        <p id="p2">Lorem, ipsum dolor sit amet consectetur adipisicing elit. Dolorum culpa iure modi nesciunt doloremque, illo quis, minus ipsam impedit nihil molestias magni vel maiores ea voluptatum repellendus. Nulla, quia magni!Lorem, ipsum dolor sit amet consectetur adipisicing elit. Dolorum culpa iure modi nesciunt doloremque, illo quis, minus ipsam impedit nihil molestias magni vel maiores ea voluptatum repellendus. Nulla, quia magni!</p>

        <p id="p3">Lorem, ipsum dolor sit amet consectetur adipisicing elit. Dolorum culpa iure modi nesciunt doloremque, illo quis, minus ipsam impedit nihil molestias magni vel maiores ea voluptatum repellendus. Nulla, quia magni!Lorem, ipsum dolor sit amet consectetur adipisicing elit. Dolorum culpa iure modi nesciunt doloremque, illo quis, minus ipsam impedit nihil molestias magni vel maiores ea voluptatum repellendus. Nulla, quia magni!</p>

        <p id="p4">Lorem, ipsum dolor sit amet consectetur adipisicing elit. Dolorum culpa iure modi nesciunt doloremque, illo quis, minus ipsam impedit nihil molestias magni vel maiores ea voluptatum repellendus. Nulla, quia magni!Lorem, ipsum dolor sit amet consectetur adipisicing elit. Dolorum culpa iure modi nesciunt doloremque, illo quis, minus ipsam impedit nihil molestias magni vel maiores ea voluptatum repellendus. Nulla, quia magni!</p>

        <p id="p5">Lorem, ipsum dolor sit amet consectetur adipisicing elit. Dolorum culpa iure modi nesciunt doloremque, illo quis, minus ipsam impedit nihil molestias magni vel maiores ea voluptatum repellendus. Nulla, quia magni!Lorem, ipsum dolor sit amet consectetur adipisicing elit. Dolorum culpa iure modi nesciunt doloremque, illo quis, minus ipsam impedit nihil molestias magni vel maiores ea voluptatum repellendus. Nulla, quia magni!</p>

        <p id="p6">Lorem, ipsum dolor </p>

        <p id="p7">Lorem, ipsum dolor sit amet consectetur adipisicing elit. Dolorum culpa iure modi nesciunt doloremque, illo quis, minus ipsam impedit nihil molestias magni vel maiores ea voluptatum repellendus. Nulla, quia magni!Lorem, ipsum dolor sit amet consectetur adipisicing elit. Dolorum culpa iure modi nesciunt doloremque, illo quis, minus ipsam impedit nihil molestias magni vel maiores ea voluptatum repellendus. Nulla, quia magni!</p>

    </div>

</body>
```
![[Pasted image 20240424114408.png]]


## Display Properties

*display = property specifies if/how an element is displayed
block-level = start on a new line, take up the full width available (h1, div, p, form, header, footer)
inline = do not start on a new line, width is limited to what is needed | | | | (span, a, img)*
```html
<style>

        div{

            background-color: aquamarine;

            height: 75px;

            width: 75px;

            display: block;

        }

        span{

            background-color: rgb(218, 225, 13);

            height: 75px;

            width: 75px;

            display: block;

        }

        #d1{

            background-color: aquamarine;

            height: 75px;

            width: 75px;

            display: inline;

        }

        #s1{

            background-color: rgb(218, 225, 13);

            height: 75px;

            width: 75px;

            display: inline;

        }

        #d2{

            background-color: aquamarine;

            height: 75px;

            width: 75px;

            display: inline-block;

        }

        #s2{

            background-color: rgb(218, 225, 13);

            height: 75px;

            width: 75px;

            display: inline-block;

        }

        #d3{

            background-color: aquamarine;

            height: 75px;

            width: 75px;

            visibility: hidden;

            display: inline-block;

        }

        #d4{

            background-color: aquamarine;

            height: 75px;

            width: 75px;

            display: none;

        }

    </style>

</head>

<body>

    <div>Div</div>

    <span>Span</span><br>

    <div id="d1">Div</div>

    <span id="s1">Span</span>

    <div id="d2">Div</div>

    <span id="s2">Span</span>

    <div id="d3">Div</div>

    <div id="d4">Div</div>

    Lorem ipsum dolor sit amet consectetur adipisicing elit. Laudantium illo tempore libero quia, ea at delectus natus est, eveniet reprehenderit quasi blanditiis, quod qui accusantium consectetur. Ducimus amet id aperiam.</P>

</body>

</html>
```
![[Pasted image 20240424122846.png]]

## Height & Width
```html
<style>

       * {

box-sizing: border-box;

}

.container{

background-color: hsl(0, 0%, 24%);

height: 100vh;

}

.box{

background-color: white;

border: 2px solid;

padding: 25px;

height: auto;

width: 50%;

float: left;

text-align: center;

min-height: 50%;

}

    </style>

</head>

<body><div class="container">

    <div class="box"> <h2>This is #1</h2>

    </div>

    <div class="box">

    <h2>This is #2</h2>

    </div>

</div>

</body>
```
![[Pasted image 20240424150630.png]]

## Positions

*position:
relative = positioned relative to where it normally
fixed = positioned relative to the viewport
absolute = positioned relative to nearest ancestor
sticky = positioned based on scroll position
static = default position for an element*
```html
 <style>

        #box1{

width: 200px;

height: 200px;

background-color: hsl(154, 100%, 63%);

position: sticky;

top: 0px;

}

#box5{

width: 200px;

height: 200px;

background-color: hsl(154, 100%, 63%);

position: static;

right: 0px;

top: 0px;

}

#box4{

width: 200px;

height: 200px;

background-color: hsl(154, 100%, 63%);

position: fixed;

right: 0px;

top: 0px;

}

#box3{

width: 200px;

height: 200px;

background-color: hsl(154, 100%, 63%);

position: relative;

left: 400px;

}

#box2{

width: 100px;

height: 100px;

background-color: hsl(8, 100%, 63%);

position: absolute;

top: 50px;

left: 50px;}

    </style>

</head>

<body>

    <div id="box1">Box1->Sticky

        <div id="box2">Box 2->absolute</div>

        </div>

        <div id="box3">

            Box3->relative

        </div>

        <div id="box4">

            Box4->fixed

        </div>  <div id="box5">

            Box5->static

        </div>

        <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Natus, cum ea aut voluptate, adipisci asperiores debitis itaque mollitia non quae error architecto quis saepe! Velit perferendis soluta rerum sequi odit?</p>

        <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Natus, cum ea aut voluptate, adipisci asperiores debitis itaque mollitia non quae error architecto quis saepe! Velit perferendis soluta rerum sequi odit?</p>

        <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Natus, cum ea aut voluptate, adipisci asperiores debitis itaque mollitia non quae error architecto quis saepe! Velit perferendis soluta rerum sequi odit?</p>

        <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Natus, cum ea aut voluptate, adipisci asperiores debitis itaque mollitia non quae error architecto quis saepe! Velit perferendis soluta rerum sequi odit?</p>

        <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Natus, cum ea aut voluptate, adipisci asperiores debitis itaque mollitia non quae error architecto quis saepe! Velit perferendis soluta rerum sequi odit?</p>

        <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Natus, cum ea aut voluptate, adipisci asperiores debitis itaque mollitia non quae error architecto quis saepe! Velit perferendis soluta rerum sequi odit?</p>

        <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Natus, cum ea aut voluptate, adipisci asperiores debitis itaque mollitia non quae error architecto quis saepe! Velit perferendis soluta rerum sequi odit?</p>

        <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Natus, cum ea aut voluptate, adipisci asperiores debitis itaque mollitia non quae error architecto quis saepe! Velit perferendis soluta rerum sequi odit?</p>

        <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Natus, cum ea aut voluptate, adipisci asperiores debitis itaque mollitia non quae error architecto quis saepe! Velit perferendis soluta rerum sequi odit?</p>

        <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Natus, cum ea aut voluptate, adipisci asperiores debitis itaque mollitia non quae error architecto quis saepe! Velit perferendis soluta rerum sequi odit?</p>

        <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Natus, cum ea aut voluptate, adipisci asperiores debitis itaque mollitia non quae error architecto quis saepe! Velit perferendis soluta rerum sequi odit?</p>

        <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Natus, cum ea aut voluptate, adipisci asperiores debitis itaque mollitia non quae error architecto quis saepe! Velit perferendis soluta rerum sequi odit?</p>

        <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Natus, cum ea aut voluptate, adipisci asperiores debitis itaque mollitia non quae error architecto quis saepe! Velit perferendis soluta rerum sequi odit?</p>

        <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Natus, cum ea aut voluptate, adipisci asperiores debitis itaque mollitia non quae error architecto quis saepe! Velit perferendis soluta rerum sequi odit?</p>

        <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Natus, cum ea aut voluptate, adipisci asperiores debitis itaque mollitia non quae error architecto quis saepe! Velit perferendis soluta rerum sequi odit?</p>

        <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Natus, cum ea aut voluptate, adipisci asperiores debitis itaque mollitia non quae error architecto quis saepe! Velit perferendis soluta rerum sequi odit?</p>

        <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Natus, cum ea aut voluptate, adipisci asperiores debitis itaque mollitia non quae error architecto quis saepe! Velit perferendis soluta rerum sequi odit?</p>

        <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Natus, cum ea aut voluptate, adipisci asperiores debitis itaque mollitia non quae error architecto quis saepe! Velit perferendis soluta rerum sequi odit?</p>

        <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Natus, cum ea aut voluptate, adipisci asperiores debitis itaque mollitia non quae error architecto quis saepe! Velit perferendis soluta rerum sequi odit?</p>

        <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Natus, cum ea aut voluptate, adipisci asperiores debitis itaque mollitia non quae error architecto quis saepe! Velit perferendis soluta rerum sequi odit?</p>

        <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Natus, cum ea aut voluptate, adipisci asperiores debitis itaque mollitia non quae error architecto quis saepe! Velit perferendis soluta rerum sequi odit?</p>

        <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Natus, cum ea aut voluptate, adipisci asperiores debitis itaque mollitia non quae error architecto quis saepe! Velit perferendis soluta rerum sequi odit?</p>

        <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Natus, cum ea aut voluptate, adipisci asperiores debitis itaque mollitia non quae error architecto quis saepe! Velit perferendis soluta rerum sequi odit?</p>

        <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Natus, cum ea aut voluptate, adipisci asperiores debitis itaque mollitia non quae error architecto quis saepe! Velit perferendis soluta rerum sequi odit?</p>

        <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Natus, cum ea aut voluptate, adipisci asperiores debitis itaque mollitia non quae error architecto quis saepe! Velit perferendis soluta rerum sequi odit?</p>

        <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Natus, cum ea aut voluptate, adipisci asperiores debitis itaque mollitia non quae error architecto quis saepe! Velit perferendis soluta rerum sequi odit?</p>

        <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Natus, cum ea aut voluptate, adipisci asperiores debitis itaque mollitia non quae error architecto quis saepe! Velit perferendis soluta rerum sequi odit?</p>

        <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Natus, cum ea aut voluptate, adipisci asperiores debitis itaque mollitia non quae error architecto quis saepe! Velit perferendis soluta rerum sequi odit?</p>

        <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Natus, cum ea aut voluptate, adipisci asperiores debitis itaque mollitia non quae error architecto quis saepe! Velit perferendis soluta rerum sequi odit?</p>

</body>
```
![[Pasted image 20240424160713.png]]

## Background Image
```css
  body{

                background-image:url(/Images/moon-1527501_1280.jpg);

                background-repeat: no-repeat;

                background-position: center;

                background-attachment: fixed;

                background-size: cover;

            }
```
![[Pasted image 20240424162420.png]]
## Combinators
combinators = explains the relationship between listed selectors
  space = descendant
  - ">" = child
  - "~" = general sibling
  - "+" = adjacent sibling*
```html
<body>

    <div id="container">

        <p>This is #1</p>

        <p>This is #2</p>

        <div>

        <p>This is #3</p>

        </div>

        </div>

        <p>This is #4</p>

        <p>This is #5</p>

</body>
```
- **For  Descendant**
```css
   <style>

        #container{

            border: 2px solid;

        }

        #container  p{

            background-color: black;

            color: azure;

        }

    </style>
```
![[Pasted image 20240424175501.png]]
 - **For child**
```css
 <style>

        #container{

            border: 2px solid;

        }

        #container > p{

            background-color: black;

            color: azure;

        }

    </style>
```
![[Pasted image 20240424175538.png]]
 - **For General Sibling**
```css
<style>

        #container{

            border: 2px solid;

        }

        #container ~ p{

            background-color: black;

            color: azure;

        }

    </style>
```
![[Pasted image 20240424175620.png]]
- **Adjacent sibling**
```css
<style>

        #container{

            border: 2px solid;

        }

        #container + p{

            background-color: black;

            color: azure;

        }

    </style>
```
![[Pasted image 20240424175703.png]]
## Pseudo Classes
```html
   <style>

button:hover{

color:#f6a32f;

font-size: 1.1em;

}

button:active{

color:#2ff639;

font-size: 1.1em;

}

a:link{

    color: rgb(103, 208, 243);

}

  

a:hover{

    color:#f6a32f;

font-size: 1.1em;

}

a:active{

    color:#2ff639;

font-size: 1.1em;

}

a:visited{

color: hsl(0, 0%, 75%);

}

.L1 li:hover{

background-color :#f6a32f;

}

.L1 li:not(:hover) {

background-color: #c2c2c2;}

li:nth-child(2n) {

background-color: #f6a32f;

}

    </style>

</head>

<body>

    <button>

        Click me

    </button>

    <br>

    <br>

    <a href="https://www.google.com/">Google</a>

    <ul class="L1">

        <li>this #1</li>

        <li>this #2</li>

        <li>this #3</li>

        <li>this #4</li>

    </ul>

    <p> Hover for "2n" lists</p>

    <ul class="L2">

        <li>this #1</li>

        <li>this #2</li>

        <li>this #3</li>

        <li>this #4</li>

    </ul>

</body>
```
![[Pasted image 20240424183341.png]]

## Pseudo Elements
*pseudo-element
keyword added after a selector
that's used to style a specific parts of an element
selector::pseudo-element*
```html
<style>

        h1::first-letter{

font-size: 2em;

font-style: italic;

        }

p::first-line{

background-color: orange;

}

p::selection{

color:

rgb(89, 255, 71);

background-color: hsl(0, 0%, 21%);

}

#apple::after{

content: "🍎";

}

#orange::after{

content: "🍊";

}

#banana::after{

content:"🍌";

}

#fruit li::marker{

content: "✔️";

color:hsl(120, 100%, 64%);

font-size: 1.2em;

}

    </style>

</head>

<body>

    <h1>Hello</h1>

    <p>Lorem ipsum dolor sit, amet consectetur adipisicing elit. Labore, omnis voluptate natus iste dignissimos dolorem reiciendis expedita? Iste quaerat mollitia itaque modi assumenda, neque quasi praesentium hic, perferendis nostrum repellendus!</p>

    <ul id="fruit">

        <li id="apple">apple</li>

        <li id="orange">orange</li>

        <li id="banana">banana</li>

        </ul>

</body>
```
![[Pasted image 20240424185330.png]]
## Pagination
```html
<!DOCTYPE html>

<html lang="en">

<head>

    <meta charset="UTF-8">

    <meta name="viewport" content="width=device-width, initial-scale=1.0">

    <title>Document</title>

  <link rel="stylesheet" href="Style.css">

</head>

<body>

    <h1>Page #1</h1>

    <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Culpa omnis ab sequi! Dicta voluptatum animi, illum ab, deleniti rem, veniam quam laudantium ut tempora quo. Voluptate, dolore aut? Cum, omnis?</p>

    <div class="pagination">

        <a href=""><</a>

        <a href="Pagination.html" class="active">1</a>

        <a href="P2.html">2</a>

        <a href="P3.html">3</a>

        <a href="P4.html">4</a>

        <a href="P2.html">></a>

    </div>

</body>

</html>
```

```css
.pagination{

    padding: 10px ;

    text-align: center;

    background-color: rgb(195, 234, 249);

}

.pagination a{

    color: black;

    text-decoration: none;

    padding: 8px 20px;

    display: inline-block;

}

.pagination a.active{

    background-color: rgb(0, 255, 195);

    border-radius: 10px;

    font-weight: bold;

}

.pagination a:hover:not(.active){

    background-color: darkgray;

    border-radius: 10px;

}
```
![[Pasted image 20240425111358.png]]
## Dropdown
```html
<style>

        .dropdown{

display: inline-block;

}

  

.dropdown button{

background-color: hsl(0, 0%, 80%);

color: white;

padding: 10px 15px;

border: none;

cursor: pointer;

}

.dropdown a{

display: block;

color: black;

text-decoration: none;

padding: 10px 15px;

}

.dropdown .content{

    display: none;

    position: absolute;

    background-color: hsl(0, 0%, 95%);

    box-shadow: 2px 2px 5px black;

}

.dropdown:hover .content{

    display: block;

}

.dropdown a:hover{

background-color: hsl(0, 0%, 90%);

}

    </style>

</head>

<body>

    <div class="dropdown">

        <button>Food</button>

        <div class="content">

        <a href="">Apple</a>

        <a href="">Orange</a>

        <a href="">Banana</a>

        </div>

        </div>

</body>
```
![[Pasted image 20240425115352.png]]
## Navigate Bar
```html
<body id="back">

    <h1>EVENT PORTAL</h1>

<nav class="navbar">

    <ul>

        <li><a href="Events Status.html">Events Status</a></li>

        <li><a href="Event request.html">Event request</a></li>

        <li><a href="IRA.html">IRA</a></li>

        <li><a href="contact.html">Contact</a></li>

    </ul>

</nav>

<main>

<h3>IRA WILL OPEN SOON !</h3>

</main>

</body>
```

```css
body{

    margin: 0px;

    }

    main{

        color: aliceblue;

    margin-left: 20px;

    margin-right: 20px;

    }

    h1{

    color: rgb(113, 246, 197);

        text-align: center;

    }

    .navbar ul{

    list-style-type: none;

    background-color: black;

    padding: 0px;

    margin: 0px;

    overflow: hidden;

    }

    .navbar a{

        color:  rgb(113, 246, 197);

        text-decoration: none;

        padding: 20px;

        display: block;

        text-align: center;

        }

        .navbar a:hover{

            background-color:  rgb(157, 150, 150);

        }

        .navbar li{

        float: left;

        }

        #back{

            background-image: url(moon-1527501_1280.jpg);

            background-repeat: no-repeat;

            background-position: center;

            background-attachment: fixed;

            background-size: cover;

                        background-color: hsl(0, 1%, 31%);

        }

        h3{

            font-weight: bold;

            text-align: center;

            font-size: 25px;

        }
```
## Image Gallery
```html
<style>

        .gallery{

display: inline-block;

border: 1px solid hsl(0, 0%, 60%);

margin: 5px;

width: 200px;

}

.gallery .description{

padding: 10px;

text-align: center;

}

.gallery:hover{

border: 1px solid hsl(0, 0%, 20%);

}

.gallery img{

width: 100%;

height: auto;

}

    </style>

</head>

<body>

    <div class="gallery">

        <a target="_blank" href="./Images/Car.jpeg">

        <img src="./Images/Car.jpeg" alt="Car">

        </a>

        <div class="description">Car</div>

    </div>

    <div class="gallery">

        <a target="_blank" href="Images/Leaf.jpg">

        <img src="Images/Leaf.jpg" alt="Leaf">

         </a>

        <div class="description">Leaf</div>

    </div>

  

    <div class="gallery">

        <a target="_blank" href="./Images/Town.jpg">

            <img src="./Images/Town.jpg" alt="Town">

            </a>

            <div class="description">Town</div>

            </div>

</body>
```
![[Pasted image 20240425160222.png]]