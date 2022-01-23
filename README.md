# Web Page for Paint Application

## AIM:

To design a static website for Paint Application using HTML5 canvas.

## DESIGN STEPS:

### Step 1:

Requirement collection.

### Step 2:

Creating the layout using HTML,CSS and canvas.

### Step 3:

Write javascript to capture move events.

### Step 4:

Perform the drawing operation based on the user input.

### Step 5:

Validate the layout in various browsers.

### Step 6:

Validate the HTML code.

### Step 6:

Publish the website in the given URL.

## PROGRAM :
```
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Paint Application</title>
    <link rel="icon" href="./img/logo.png" type="image/x-icon" />
    <style>

        #content{
            padding-left: 740px;
           
        }
        #myCanvas{
          background-color: #cecece;
          box-shadow: inset 0 0 5px #b6b6b6; 
          backdrop-filter: blur(15px);
          border-radius: 2px;
          border: 5px solid #0a0e0f;
        }
        #buttonstyle{
          background-color: #d1baba;
          border: 2px solid #9b6a8a;
          border-radius: 5px;
          color: black;
          padding: 15px 32px;
          text-align: center;
          display: inline-block;
          font-size: 16px;
          margin: 4px 2px;
          cursor: pointer;
        }
        #buttonstyle:hover{
            background-color:#ffffff36;
            transition: 0.5s;
        }
        #bgimg{
            background-image: url(./painting.png);
        }
        #shooky{
            border: 2px solid #ffffff;
            border-radius: 25px;
            padding: 25px 25px;
            text-align: center;
            display: inline-block;
            font-size: 16px;
            margin: 4px 2px;
            cursor: pointer;
        }
        #shooky:hover{
            opacity: 20%;
            transition: 0.21s;
        }
        </style>
  </head>
  <body id="bgimg">
    <div id="content">
      <canvas id="myCanvas" width="800" height="800" onclick="showCoords(event)"></canvas></div>
      <center>
      <button onclick="shape=1" id="buttonstyle" >SOLID CIRCLE</button>
      <button onclick="shape=2" id="buttonstyle">CIRCLE</button>
      <button onclick="shape=3" id="buttonstyle">SOLID SQUARE</button>
      <button onclick="shape=4" id="buttonstyle">SQUARE</button>
      <button onclick="shape=5" id="buttonstyle">SOLID TRIANGLE</button>
      <button onclick="shape=6" id="buttonstyle">TRIANGLE</button>
      <br>
      <button onclick="size()" id="buttonstyle" >CHANGE SIZE</button></center>
      <center>
      <button onclick="change_color(this)" id="shooky" style="background: rgb(253, 253, 253);"></button>
      <button onclick="change_color(this)" id="shooky" style="background: rgb(153, 39, 39);"></button>
      <button onclick="change_color(this)" id="shooky" style="background: rgb(126, 73, 30);"></button>
      <button onclick="change_color(this)" id="shooky" style="background: rgb(148, 150, 65);"></button>
      <button onclick="change_color(this)" id="shooky" style="background: rgb(63, 126, 44);"></button>
      <button onclick="change_color(this)" id="shooky" style="background: rgb(149, 196, 147);"></button>
      <button onclick="change_color(this)" id="shooky" style="background: rgb(20, 106, 117);"></button>
      <button onclick="change_color(this)" id="shooky" style="background: rgb(35, 63, 124);"></button>
      <button onclick="change_color(this)" id="shooky" style="background: rgb(141, 45, 170);"></button>
      <button onclick="change_color(this)" id="shooky" style="background: rgb(89, 62, 107);"></button>
      <button onclick="change_color(this)" id="shooky" style="background: rgb(115, 101, 134);"></button>
      <button onclick="change_color(this)" id="shooky" style="background: rgb(31, 27, 27);"></button>
      </center>

      <script>


        const canvas = document.getElementById("myCanvas");
        const ctx = canvas.getContext("2d");
        ctx.fillStyle = "#FF0000";
        canvas.height = canvas.width;
        ctx.transform(1, 0, 0, -1, 0, canvas.height);
        let xMax = canvas.height;
        let yMax = canvas.width;
        let csize= 20;
        let sqsize= 50;
        let tsize=50;
        let tata="black";
        function size(){   
          if (shape==1 ||shape==2){
            let c= prompt("Please enter size of circle", "ex:100,50");
            csize=c;
          } 
          if (shape==3 ||shape==4){
            let s = prompt("Please enter size of square", "ex:100,20");
            sqsize=s;
          }
          if (shape==5 || shape==6){
            let t= prompt("Please enter size of triangle","ex:50,84");
            tsize=t;
          }
        }
        function change_color(element){
          tata=element.style.background;
        }
        function showCoords(event)
        {
          var x = event.clientX-545;
          var y = yMax-event.clientY;
          var coords = "X coords: " + x + ", Y coords: " + y;
          document.getElementById("demo").innerHTML = coords;
    
          if (shape==1){
            ctx.beginPath();
            ctx.arc(x, y, csize, 0, 2 * Math.PI);
            ctx.fillStyle=tata;
            ctx.fill();
          }
          if (shape==2){
            ctx.beginPath();
            ctx.arc(x, y, csize, 0, 2 * Math.PI);
            ctx.strokeStyle=tata;
            ctx.stroke();
          }
          if (shape==3){
            ctx.beginPath();
            ctx.rect(x-(sqsize/2),y-(sqsize/2), sqsize,sqsize);
            ctx.fillStyle=tata;
            ctx.fill();
          }
          if (shape==4){
            ctx.beginPath();
            ctx.rect(x-(sqsize/2),y-(sqsize/2), sqsize,sqsize);
            ctx.strokeStyle=tata;
            ctx.stroke();
          }
          if (shape==6){
            ctx.beginPath();
            ctx.moveTo(x, y);
            ctx.lineTo(x-(tsize/2),y-(tsize*0.86602));
            ctx.lineTo(x+(tsize/2),y-(tsize*0.86602));
            ctx.lineTo(x,y)
            ctx.strokeStyle=tata;
            ctx.stroke();
          }
          if (shape==5){
            ctx.beginPath();
            ctx.moveTo(x, y);
            ctx.lineTo(x-(tsize/2),y-(tsize*0.86602));
            ctx.lineTo(x+(tsize/2),y-(tsize*0.86602));
            ctx.fillStyle=tata;
            ctx.fill();
          }    
        }
      </script>
    <center><p id="demo" style="color: rgb(255, 255, 255);"></p></center>
    <p 
    style="font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif; 
    text-align: center;
    color:#320C0E;
    font-weight: bold;
    font-size: larger;">PAINT APPLICATION PROGRAM, Developed by B.PAVIZHI</p>
  </body>
</html>
```
## OUTPUT:
![output](./paintapplication.png)
![output](./paint.png)

## Result:

Thus a website is designed and validated for paint application using HTML5 canvas.
