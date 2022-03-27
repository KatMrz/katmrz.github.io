## Cloud Watermelon Code

**Project description:** I first drew my watermelon when I was learning the basics of Javascript, only knowing basic shapes such as ellipse, rect, and triangle. As I learned more principles, I turned my watermelon into a function, added clouds as objects, and animated it all! Here's the first version of Cloud Watermelon, first made in September 2021.

### 1. Javascript Code

Sed ut perspiciatis unde omnis iste natus error sit voluptatem accusantium doloremque laudantium, totam rem aperiam, eaque ipsa quae ab illo inventore veritatis et quasi architecto beatae vitae dicta sunt explicabo. 

```function setup() {
	createCanvas(400, 400);
}
var watermelonPosY = 50;
var watermelonPosX = 200;
var watermelonSpeed = 0.2

//**cloud object code begin*/

var LeftCloud = function (x, y, l, speed, r, g, b) 
  {
    this.x = x;
    this.y = y;
    this.l = l;
    this.speed = speed;
    this.r = r;
    this.g = g;
    this.b = b;
  }

var RightCloud = function (x, y, l, speed, r, g, b) 
  {
    this.x = x;
    this.y = y;
    this.l = l;
    this.speed = speed;
    this.r = r;
    this.g = g;
    this.b = b;
  }

LeftCloud.prototype.draw = function()
{
  fill (this.r, this.g, this.b);
  rect (this.x, this.y, this.l, 20, 20);
  //** cloud levitation */
  if (this.x > 90)
  {
  this.speed = -0.2;
  }
  if (this.x < 40)
  {
  this.speed = 0.2;
  }
  this.x = this.x + this.speed;
  //** cloud levitation end */
}

RightCloud.prototype.draw = function()
{
  fill (this.r, this.g, this.b);
  rect (this.x, this.y, this.l, 20, 20);
  //** cloud levitation */
  if (this.x > 270)
  {
    this.speed = -0.2;
  }
  if (this.x < 240)
  {
    this.speed = 0.2;
  }
  this.x = this.x + this.speed;
  //** cloud levitation end */
}

var yellowCloud1 = new LeftCloud (100, 270, 100, 0.2, 242, 255, 143);
var blueCloud1 = new LeftCloud (70, 285, 50, 0.2, 168, 232, 255);
var yellowCloud2 = new RightCloud (260, 310, 100, 0.2, 242, 255, 143);
var blueCloud2 = new RightCloud (280, 300, 50, 0.2, 168, 232, 255);

//**cloud object code end */


function draw() {
background (196, 196, 255); // periwinkle background
noStroke ();
  
// watermelon function
var drawWatermelon = function (watermelonX, watermelonY)
  {
  //fruit
  fill (255, 94, 94);
  triangle (watermelonX, watermelonY, watermelonX - 100, watermelonY + 250, watermelonX + 100, watermelonY + 250);
  fill (255, 130, 130);
  triangle (watermelonX + 16, watermelonY + 40, watermelonX - 60, watermelonY + 250, watermelonX + 100, watermelonY + 250);
  
  //periwinkle block that covers watermelon point
  fill (196, 196, 255);
  triangle (watermelonX - 20, watermelonY + 40, watermelonX, watermelonY - 1, watermelonX + 17, watermelonY + 40);

  //rind
  fill (115, 255, 131);
  rect (watermelonX - 100, watermelonY + 230, 200, 40, 10);
  fill (99, 219, 107);
  rect (watermelonX - 100, watermelonY + 230, 50, 40, 7);
  
  //seed end
  fill(48, 25, 25);
  ellipse (watermelonX + 50, watermelonY + 200, 10, 20);
  ellipse (watermelonX - 10, watermelonY + 200, 10, 20);
  ellipse (watermelonX + 20, watermelonY + 150, 10, 20);
  }
  drawWatermelon (watermelonPosX, watermelonPosY);

  //** watermelon levitation!! */

  if (watermelonPosY < 20)
  {
    watermelonSpeed = -0.3;
  }
  if (watermelonPosY > 60)
  {
    watermelonSpeed = 0.2;
  }
  watermelonPosY = watermelonPosY - watermelonSpeed;

  //** watermelon levitation end */
  

  yellowCloud1.draw()   
  yellowCloud2.draw()
  blueCloud1.draw()
  blueCloud2.draw()


  textSize (20);
  fill(255, 255, 255);
  text("^^^ CLOUD WATERMELON ^^^", 60, 350, 800, 200);
};
```
