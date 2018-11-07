# 游戏设计
![](images/fp.gif)

## 游戏的策划
曾经一段时间火遍全国的手机游戏flappy bird因其简单的玩法、令人不忍放弃的机制深受许多玩家喜爱。不幸的是，该游戏已从App Store下架，让后来的玩家无法玩到这款游戏，令人惋惜。因此我打算粗略重制这款游戏，重温这款经典的游戏。
角色：flappy bird
玩法：通过点击鼠标左键让flappybird跳跃起来以防止碰到管道，一旦碰到管道flappy bird将死亡。

## 游戏设计
![](images/game.png)

### 1：flappy bird<br/>
![](images/bird.png)<br/>
 Attributes:(30,256)<br/>
 Collaborator ：land，pipe<br/>
 Events & Actions：碰撞 & 下坠<br/>

 ### 2：pipe<br/>
 ![](images/pipe.png)<br/>
 Attributes:(540,random)<br/>
 Collaborator: flappy bird<br/>
 Events & Actions：向左移动，碰撞;到达图层边缘返回位置(540,random)，上下管距离保持250<br/>

 ### 3:background<br/>
![](images/bgg.png)<br/>
Attributes:(0,0)<br/>
Collaborator:无<br/>
Events & Actions：无<br/>

### 4：land<br/>
![](images/land.png)<br/>
Attributes:(256,450)<br/>
Collaborator:flappy bird<br/>
Events & Actions：碰撞，向左运动，到达图层边缘返回位置(256,450)<br/>