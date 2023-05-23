# **1. 3D&Texture**

## 1.1 Code

```js
let img;
function preload()
{
  img = loadImage("rb.png");
}

function setup() 
{
  createCanvas(400, 400, WEBGL);
}

function draw() 
{
  background(200);
  rotateX(frameCount * 0.01);
  rotateY(frameCount * 0.01);
  texture(img);
  box(200);
}
```

## 1.2 Image

<img src="https://raw.githubusercontent.com/LSY3375/2023-ComputerGraphics/main/%5B%EA%B0%9C%EC%9D%B8%EA%B3%BC%EC%A0%9C%5D/img/rainbow.gif">


# **2. Eye Class**

## 2.1 Code

```js
let e1, e2, e3;

function setup() 
{
  createCanvas(640, 360);
  noStroke();
  e1 = new Eye(250, 16, 120);
  e2 = new Eye(164, 185, 80);
  e3 = new Eye(420, 230, 220);
}

function draw() 
{
  background(102);
  e1.update(mouseX, mouseY);
  e2.update(mouseX, mouseY);
  e3.update(mouseX, mouseY);
  e1.display();
  e2.display();
  e3.display();
}

class Eye 
{
  constructor(tx, ty, ts) 
  {
    this.x = tx;
    this.y = ty;
    this.size = ts;
    this.angle = 0.0;
  }

  update(mx, my) 
  {
    this.angle = Math.atan2(my - this.y, mx - this.x);
  }

  display() 
  {
    push();
    translate(this.x, this.y);
    fill(255);
    ellipse(0, 0, this.size, this.size);
    rotate(this.angle);
    fill(153, 204, 0);
    ellipse(this.size / 4, 0, this.size / 2, this.size / 2);
    pop();
  }
}
```

## 2.2 Image

<img src="https://raw.githubusercontent.com/LSY3375/2023-ComputerGraphics/main/%5B%EA%B0%9C%EC%9D%B8%EA%B3%BC%EC%A0%9C%5D/img/eye.gif">


# **3. 소감**
```
p5.js를 통해 3D 텍스처 박스와 따라오는 눈동자를 구현 하였습니다.
3D 텍스처 박스 같은 경우는 간단한 구조여서 금방 구현할 수 있었지만 눈동자는 구현해 보는데 시간이 오래 걸렸습니다.
힘은 더 들었지만 오히려 눈동자를 구현하는 과정에서 각 메소드가 왜 필요한지 다시 생각해 보며 더 집중하고 공부해 볼 수 있었습니다.
```


# **4. 기타**
```
앞으로 더 열심히 하겠습니다.
```
