# [8팀] Snake 게임을 변형하기 🐍

## 1. 구성원 👩‍👧‍👦

|이름|학년|학번|학과|
|---|---|---|---|
|우제현|3학년|20191127|컴퓨터공학과|
|이수용|3학년|20191481|컴퓨터공학과|
|신서영|4학년|20201589|컴퓨터공학과|



## 2. 프로젝트 계획 🕗 
  * 일정: 2023.03.30. AM 11:26 ~ 2023.04.05. PM 11:59
 
## 2.1. 최적화하기

  * 시작할 때는 1점인데 죽고 재시작 될 때 0점으로 시작되는 오류 수정하기
  *  180도 회전이 되버려서 바로 죽어버리는 오류 수정하기

## 2.2. 편의성 추가

  * 사망 시 게임 종료 화면이 나오게 하기
  *  게임 종료 화면에서 스페이스 바를 누르면 재시작 되게 하기


## 2.3. 디자인 변경 ([팀과제-1](https://github.com/LSY3375/2023-ComputerGraphic/blob/main/%5B팀과제-1%5D/캐릭터%20만들기.md))

  * [팀과제-1]에서 제작한 토끼 캐릭터를 바탕으로 뱀 게임을 수정한다.
  * 배경, 먹이, 토끼 등 그래픽을 이미지로 변경한다.
  * 먹이의 색깔을 랜덤으로 할당하고 해당 먹이를 먹게 되면 토끼는 먹은 먹이에 해당되는 색깔로 변경된다.



## 2.4. 전체 구성도 

![16](/img/16.png)
<br/>




## 3. 프로젝트 수행 과정 📝 

### 3.1. 코드 개요 
  * 코드의 목적과 주요 기능에 대해 설명한다. 

```
저희 팀의 뱀 게임은 최적화와 편의성, 그리고 디자인 변경을 통해 게임을 개선하고자 합니다.
최적화 부분에서는 점수 초기화 오류와 180도 회전으로 인한 사망 오류를 수정하였습니다.
편의성 부분에서는 사망 시 게임 종료 화면과 스페이스 바를 누르면 재시작되는 기능을 추가하였습니다.
마지막으로 디자인 부분에서는 배경, 먹이, 토끼 등의 그래픽을 이미지로 변경하고,
먹이 색상을 랜덤으로 설정하여 해당 먹이를 먹으면 토끼가 그 색상으로 변하도록 하였습니다.
```


### 3.2. 코드 구성 요소 
  * 코드의 주요 구성 요소와 각 요소의 역할을 설명한다.

##### 3.2.1. preload()
```
이 함수는 프로그램이 시작되기 전에 이미지를 로드하는 함수입니다.
이 코드에서는 이미지를 불러오기 위해 loadImage() 함수를 사용하여 잔디밭 이미지 파일을 로드하고 있습니다.
```

##### 3.2.2. setup()
```
이 함수는 프로그램이 시작될 때 단 한번 실행되는 함수입니다.
이 함수에서는 캔버스를 생성하고, Snake 객체를 생성하고, 프레임 레이트를 설정하며, 먹이의 위치를 결정합니다.
```

##### 3.2.3. draw()
```
이 함수는 프로그램이 실행되면 계속해서 실행되는 함수입니다.
이 함수에서는 토끼가 먹이를 먹었는지 체크하고, 토끼가 죽었는지 체크합니다.
게임이 종료되면 "GAME OVER!"라는 텍스트를 출력하고, 게임을 다시 시작할 수 있도록 해줍니다.
그리고 토끼의 위치를 업데이트하고, 토끼를 그리고, 먹이를 그립니다.
```

##### 3.2.4. pickLocation()
```
이 함수는 먹이의 위치와 색깔을 랜덤으로 결정하는 함수입니다.
먹이 색깔을 저장하는 변수인 foodColor 변수에 색깔을 저장합니다.
```

##### 3.2.5. scoreboard()
```
이 함수는 게임의 현재 점수와 최고 점수를 나타내는 스코어보드를 그리는 함수입니다.
```

##### 3.2.6. keyPressed()
```
이 함수는 키보드의 입력을 처리하는 함수입니다.
이 함수에서는 방향키의 입력을 처리하고, 게임이 종료된 후 스페이스바를 누르면 게임을 다시 시작할 수 있도록 해줍니다.
```

##### 3.2.7. Snake()
```
이 함수는 뱀 객체를 생성하는 생성자 함수입니다.
이 함수에서는 토끼의 초기 위치와 이동 속도, 길이, 꼬리의 위치, 점수 등의 속성을 설정하고, 토끼의 방향을 조정하며,
먹이를 먹었을 때와 게임이 종료되었을 때의 처리를 담당합니다. 그리고 토끼를 업데이트하고, 그리는 기능을 수행합니다.
```

##### 3.2.8. Snake 객체 내부 함수

```
1) dir(x,y) 함수는 뱀의 이동 방향을 설정하는 함수입니다. 
   x와 y는 각각 x축, y축 방향의 이동을 나타냅니다.

2) eat(pos) 함수는 먹이를 먹을 때 호출되는 함수입니다.
   pos는 먹이의 위치를 나타내는 Vector 객체입니다.
   먹이와 뱀의 머리 사이의 거리가 1보다 작아지면, 
   즉 먹이와 뱀의 머리가 충돌하면 뱀의 길이를 늘리고 점수를 올리는 역할을 합니다.

3) death() 함수는 뱀이 죽었을 때 호출되는 함수입니다. 
   뱀의 꼬리 부분과 머리 부분의 거리가 1보다 작아지면,
   즉 뱀이 자기 자신과 충돌하면 게임을 종료하고, 
   뱀의 길이와 점수를 초기화하는 역할을 합니다.

4) update() 함수는 뱀의 위치를 업데이트하는 함수입니다. 
   머리 부분의 위치를 이전에 먹이를 먹었다면 늘어난 길이만큼 뒤로 이동시키고, 
   이동 방향에 따라 머리 부분의 위치를 변경합니다. 
   이동한 위치가 게임 화면을 벗어나지 않도록 constrain() 함수를 사용하여 제한합니다.

5) show() 함수는 토끼를 화면에 그리는 함수입니다. 
   방향에 따라 맨 앞의 토끼가 바라보는 방향이 결정됩니다.
```

### 3.3. 코드 세부 사항 
   * 각 함수와 객체의 동작 방식에 대한 알고리즘의 작동 원리를 설명한다. 

```
해당 알고리즘은 JavaScript를 사용하여 구현된 Snake 게임입니다.

코드는 크게 3가지 역할을 수행합니다. 
첫째, Snake 클래스를 정의하고 해당 클래스를 통해 뱀의 움직임, 길이, 충돌 등 뱀의 동작을 구현합니다. 
둘째, pickLocation() 함수를 이용하여 랜덤한 위치에 먹이를 생성합니다. 
셋째, keyPressed() 함수를 이용하여 키보드 입력에 따라 뱀의 방향을 조절합니다.

게임은 다음과 같이 동작합니다. 뱀은 초기 위치에서 시작하여 사용자가 방향을 조절합니다. 
뱀은 먹이를 먹을 때마다 길이가 1 증가하며, 먹이가 생성된 위치는 랜덤으로 결정됩니다. 
뱀이 벽이나 자기 자신과 충돌하면 게임이 종료되고, "GAME OVER!"와 "Press spacebar to restart!!!" 문구가 출력됩니다. 
사용자가 스페이스바를 누르면 게임이 재시작됩니다. 게임의 점수는 먹이를 먹을 때마다 1점씩 증가하며, 최고 점수도 함께 출력됩니다.

이 게임은 기본적인 웹 개발 기술과 JavaScript 프로그래밍 지식이 필요합니다. 
또한 p5.js 라이브러리를 이용하여 캔버스에 그래픽을 그리고, 이미지를 로드하고 뱀을 토끼로 변형시키고, 
랜덤한 색상을 생성하는 등의 작업을 수행합니다.
```


### 3.4. 코드 최적화 및 확장
  * 현재 코드를 최적화하거나 확장할 수 있는 방법에 대해 논의한다.

![17](/img/17.png)
<br/>
```
현재 최종 결과물의 코드에서 더 최적화하거나 확장할 수 있는 방법에 대해 논의 했습니다.
d) 와 같이 게임 난이도를 조절하는 기능으로 위 사진과 같이 점수가 올라갈수록 장애물이 증가하며,
장애물이 닿으면 게임이 종료 되도록 하는 기능을 추가하는 방법을 제안합니다. 
추후 최종 결과물(c))과 확장 단계(d))의 결과물을 하나의 프로젝트로 합친 이후, 여러가지 개선책이 필요합니다. 
```
<br/>



##### d ) 코드 확장 단계 
  * 장애물을 추가 구현한 결과물 
  
  * d ) 의 확장 버전 코드 : [링크](https://github.com/LSY3375/2023-ComputerGraphic/blob/main/%5B팀과제-3%5D/snake6.js)

<br/>

![18](/img/18.png)

<br/>



## 4. 코드 💻 [링크](https://github.com/LSY3375/2023-ComputerGraphic/blob/main/%5B팀과제-3%5D/snake4.js)

```js
let s;
let scl = 20;
let food;
let img;
let isGameOver = false;
let foodColor;
let high = 1;
playfield = 600;

function preload()
{
  img = loadImage("https://raw.githubusercontent.com/wjh2335/2023-ComputerGraphics/main/img/17.jpg");
}

function setup()
{
  createCanvas(playfield, 640);
  s = new Snake();
  frameRate(10);
  pickLocation();
}

function draw()
{
  background(img);
  scoreboard();

  if(s.eat(food)) pickLocation();

  s.death();
  if (isGameOver)
  {
    fill(255);
    textSize(50);
    textAlign(CENTER);
    textFont("Georgia");
    text("GAME OVER!", width / 2, height / 2);
    textSize(20);
    fill(0, 255, 20);
    text("Press spacebar to restart!!!", width / 2, height / 2 + 40);
    return;
  }
  s.update();
  s.show();

  translate(food.x - 10, food.y - 10);
  rabbit(foodColor);
}

function pickLocation()
{
  let cols = floor(playfield/scl);
  let rows = floor(playfield/scl);
  food = createVector(floor(random(cols)), floor(random(rows)));
  food.mult(scl);
  foodColor = color(random(255), random(255), random(255));
  
  for (let i = 0; i < s.tail.length; i++)
  {
    let pos = s.tail[i];
    let d = dist(food.x, food.y, pos.x, pos.y);
    if (d < 1) pickLocation();
  }
} 

function scoreboard()
{
  fill(0);
  rect(0, 600, 600, 40);
  fill(255);
  textFont("Georgia");
  textSize(18);
  textAlign(LEFT);
  text("Score: ", 10, 625);
  text("Highscore: ", 450, 625);
  text(s.score, 70, 625);
  text(high, 540, 625);
}

function keyPressed()
{
  if (keyCode === UP_ARROW && s.xspeed != 0 && s.yspeed != 1) { s.dir(0, -1); }
  else if (keyCode === DOWN_ARROW && s.xspeed != 0 && s.yspeed != -1) { s.dir(0, 1); }
  else if (keyCode === RIGHT_ARROW && s.xspeed != -1 && s.yspeed != 0) { s.dir (1, 0); }
  else if (keyCode === LEFT_ARROW && s.xspeed != 1 && s.yspeed != 0) { s.dir (-1, 0); }
  else if (keyCode === 32 && isGameOver)
  {
    isGameOver = false;
    s = new Snake();
    pickLocation();
  }
}

function Snake()
{
  this.x = 0;
  this.y = 0;
  this.xspeed = 1;
  this.yspeed = 0;
  this.total = 0;
  this.tail = [];
  this.score = 1;
  this.headColor = color(255);

  this.dir = function(x,y)
  {
    this.xspeed = x;
    this.yspeed = y;
  }

  this.eat = function(pos)
  {
    let d = dist(this.x, this.y, pos.x, pos.y);

    if (d < 1)
    {
      this.total++;
      this.score++;
      text(this.score, 70, 625);
      
      if (this.score > high) high = this.score;
      
      text(high, 540, 625);
      this.headColor = foodColor;
      return true;
    }
    else return false;
  }

  this.death = function()
  {
    for (let i = 0; i < this.tail.length; i++)
    {
      let pos = this.tail[i];
      let d = dist(this.x, this.y, pos.x, pos.y);

      if (d < 1)
      {
        this.total = 0;
        this.score = 1;
        this.tail = [];
        isGameOver = true;
        this.headColor = color(255);
      }
    }
  }

  this.update = function()
  {
    if (this.total === this.tail.length)
    {
      for (let i = 0; i < this.tail.length-1; i++) this.tail[i] = this.tail[i+1];
    }
    this.tail[this.total-1] = createVector(this.x, this.y);

    this.x = this.x + this.xspeed*scl;
    this.y = this.y + this.yspeed*scl;

    this.x = constrain(this.x, 0, playfield-scl);
    this.y = constrain(this.y, 0, playfield-scl);
  }

  this.show = function()
  {
    for (let i = 0; i < this.tail.length; i++)
    {
      push();
      if(s.xspeed == 0 && s.yspeed == 1) { translate(this.tail[i].x - 10, this.tail[i].y - 10); }
      else if(s.xspeed == 0 && s.yspeed == -1) { translate(this.tail[i].x - 10, this.tail[i].y - 10); }
      else if(s.xspeed == 1 && s.yspeed == 0) { translate(this.tail[i].x - 10, this.tail[i].y - 10); }
      else if(s.xspeed == -1 && s.yspeed == 0) { translate(this.tail[i].x - 10, this.tail[i].y - 10); }
      rabbit(this.headColor);
      pop();
    }

    push();
    if(s.xspeed == 0 && s.yspeed == 1) { translate(this.x + 30, this.y + 30); rotate(radians(180)); }
    else if(s.xspeed == 0 && s.yspeed == -1) { translate(this.x - 10, this.y - 10); rotate(radians(0)); }
    else if(s.xspeed == 1 && s.yspeed == 0) { translate(this.x + 30, this.y - 10); rotate(radians(90)); }
    else if(s.xspeed == -1 && s.yspeed == 0) { translate(this.x - 10, this.y + 30); rotate(radians(270)); }
    rabbit(this.headColor);
    pop();
  }
}

function rabbit(col)
{
  push();
  scale(0.1);
  fill(col);
  strokeWeight(3);
  
  //귀
  push(); //왼쪽 귀
  translate(150, 115);
  rotate(radians(-10));
  ellipse(0, 0, 50, 100);
  pop();
  push(); //오른쪽 귀
  translate(250, 115);
  rotate(radians(10));
  ellipse(0, 0, 50, 100);
  pop();
  
  //귀 내부
  fill(255, 180, 180);
  push(); //왼쪽 귀 내부
  translate(150, 112);
  rotate(radians(-10));
  ellipse(0, 0, 30, 65);
  pop();
  push(); //오른쪽 귀 내부
  translate(250, 112);
  rotate(radians(10));
  ellipse(0, 0, 30, 65);
  pop();
  
  //얼굴
  fill(col);
  ellipse(200, 200, 180, 170);
  
  //눈
  fill(0);
  ellipse(160, 195, 10, 10); //왼쪽 눈
  ellipse(240, 195, 10, 10); //오른쪽 눈

  //코
  ellipse(200, 210, 15, 15);
  
  //입
  fill(col);
  line(200, 220, 200, 225); //인중
  arc(190, 225, 20, 20, 0, PI); //왼쪽 입
  arc(210, 225, 20, 20, 0, PI); //오른쪽 입
  pop();
}
```



## 5. 실행 결과 🎮

![19](/img/19.png)



## 6. 동영상 🎬

[![Video Label](http://img.youtube.com/vi/fSurK7z9mNE/0.jpg)](https://youtu.be/fSurK7z9mNE)



## 7. 참고 자료 📂

### 7.1. 링크

[newgraphics 네이버 카페 : 6강 Snake 게임, 영화와 Graphics](https://cafe.naver.com/newgraphics/152)
