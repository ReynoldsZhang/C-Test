```c++
#include<graphics.h>
#include<stdlib.h>
#include<dos.h>
#define LEFT 0x4b00
#define RIGHT 0x4d00
#define DOWN 0x5000
#define UP 0x4800
#define ESC 0x011b
int i,key;
int score=0;
int gamespeed=32000;
struct Food /*食物bai的du结zhi构体*/
{
int x; /*食物的横坐标*/
int y; /*食物的纵坐标*/
int yes; /*食物是否出现的变量*/
}food;
struct Snack /*蛇的dao结构体*/
{
int x[N];
int y[N];
int node; /*蛇的节数*/
int direction; /*蛇的方向*/
int life; /*蛇的生命，0活着，1死亡*/
}snake;
void Init(void); /*图形驱动*/
void Close(void); /*关闭游戏函数*/
void DrawK(void); /*画图函数*/
void GameOver(void);/*输出失败函数*/
void GamePlay(); /*游戏控制函数 主要程序*/
void PrScore(void); /*分数输出函数*/
DELAY(char ch)/*调节游戏速度*/
{
if(ch=='3')
{
delay(gamespeed); /*delay是延迟函数*/
delay(gamespeed);
}
else if(ch=='2')
{
delay(gamespeed);
}
}
Menu()/*游戏开始菜单*/
{
char ch;
printf("Please choose the gamespeed:\n");
printf("1-Fast 2-Normal 3-Slow\n");
printf("\nPlease Press The numbers..\n");
do
{ch=getch();}
while(ch!='1'&&ch!='2'&&ch!='3');
clrscr();
return(ch);
}
/*主函数*/
void main(void)
{
int ch;
ch=Menu();
Init();
DrawK();
GamePlay(ch);
Close();
}
void Init(void)
{
int gd=DETECT,gm;
initgraph(&gd,&gm,"c:\\tc");
cleardevice();
}
void DrawK(void)
{
setcolor(11);
setlinestyle(SOLID_LINE,0,THICK_WIDTH);
for(i=50;i<=600;i+=10)
{
rectangle(i,40,i+10,49); /*画出上边框*/
rectangle(i,451,i+10,460); /*画出下边框*/
}
for(i=40;i<=450;i+=10)
{
rectangle(50,i,59,i+10); /*画出左边框*/
rectangle(601,i,610,i+10); /*画出右边框*/
}
}
void GamePlay(char ch)
{
randomize(); /*随机数发生器*/
food.yes=1; /*1代表要出现食物，0表示以存在食物*/
snake.life=0;
snake.direction=1;
snake.x[0]=100;snake.y[0]=100;
snake.x[1]=110;snake.y[1]=100;
snake.node=2;
PrScore();
while(1) /*可以重复游戏*/
{
while(!kbhit()) /*在没有按键的情况下蛇自己移动*/
{
if(food.yes==1) /*需要食物*/
{
food.x=rand()%400+60;
food.y=rand()%350+60; /*使用rand函数随机产生食物坐标*/
while(food.x%10!=0)
food.x++;
while(food.y%10!=0)
food.y++; /*判断食物是否出现在整格里*/
food.yes=0; /*现在有食物了*/
}
if(food.yes==0) /*有食物了就要显示出来*/
{
setcolor(GREEN);
rectangle(food.x,food.y,food.x+10,food.y-10);
}
for(i=snake.node-1;i>0;i--) /*贪吃蛇的移动算法*/
{
snake.x[i]=snake.x[i-1];
snake.y[i]=snake.y[i-1]; /*贪吃蛇的身体移动算法*/
}
switch(snake.direction) /*贪吃蛇的头部移动算法，以此来控制移动*/
{
case 1:snake.x[0]+=10;break;
case 2:snake.x[0]-=10;break;
case 3:snake.y[0]-=10;break;
case 4:snake.y[0]+=10;break;
}
for(i=3;i<snake.node;i++) /*判断是否头部与身体相撞*/
{
if(snake.x[i]==snake.x[0]&&snake.y[i]==snake.y[0])
{
GameOver();
snake.life=1;
break;
}
}
/*下面是判断是否撞到墙壁*/
if(snake.x[0]<55||snake.x[0]>595||snake.y[0]<55||snake.y[0]>455)
{
GameOver();
snake.life=1;
}
if(snake.life==1) /*如果死亡就退出循环*/
break;
if(snake.x[0]==food.x&&snake.y[0]==food.y) /*判断蛇是否吃到食物*/
{
setcolor(0);
rectangle(food.x,food.y,food.x+10,food.y-10); /*吃的食物后用黑色将食物擦去*/
snake.x[snake.node]=-20;snake.y[snake.node]=-20; /*现把增加的一节放到看不到的地方去*/
snake.node++;
food.yes=1;
score+=10;
PrScore();
}
setcolor(4); /*每次移动后将后面的身体擦去*/
for(i=0;i<snake.node;i++)
rectangle(snake.x[i],snake.y[i],snake.x[i]+10,snake.y[i]-10);
delay(gamespeed);
DELAY(ch);
setcolor(0);
rectangle(snake.x[snake.node-1],snake.y[snake.node-1],snake.x[snake.node-1]+10,snake.y[snake.node-1]-10);
}
if(snake.life==1)
break;
key=bioskey(0); /*接受按键*/
if(key==ESC)
break;
else
if(key==UP&&snake.direction!=4)/*判断是否改变方向*/
snake.direction=3;
else
if(key==RIGHT&&snake.direction!=2)
snake.direction=1;
else
if(key==LEFT&&snake.direction!=1)
snake.direction=2;
else
if(key==DOWN&&snake.direction!=3)
snake.direction=4;
}
}
void GameOver(void)
{
cleardevice();
setcolor(RED);
settextstyle(0,0,4);
outtextxy(200,200,"GAME OVER");
getch();
}
void PrScore(void)
{
char str[10];
setfillstyle(SOLID_FILL,YELLOW);
bar(50,15,220,35);
setcolor(6);
settextstyle(0,0,2);
sprintf(str,"scord:%d",score);
outtextxy(55,20,str);
}
void Close(void)
{
getch();
closegraph();
}
```
