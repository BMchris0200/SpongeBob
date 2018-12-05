#include<stdio.h>
#include<stdlib.h>
#include<time.h>

#define SNAKE_MAX_LENGTH 20
#define SNAKE_HEAD '	H'
#define SNAKE_BODY 'X'
#define BLANK_CELL ' '
#define SNAKE_FOOD '$'
#define WALL_CELL '*'

void snakeMove(int,int);
void put_money(void);
void output(void);
void gameover(void);
void printmap(void);
void printSnake(void);
void makeAnotherFood(void);
void lengthen(void);
void clear(void);
char map[12][13]=
	{"************",
	"*XXXXD     *",
	"*          *",
	"*          *",
	"*          *",
	"*          *",
	"*          *",
	"*          *",
	"*          *",
	"*          *",
	"*          *",
	"************",
	};

int snakeX[SNAKE_MAX_LENGTH] = {1,2,3,4,5};
int snakeY[SNAKE_MAX_LENGTH] = {1,1,1,1,1};
int length = 5;
int TailX = 1;
int TailY = 1;
int food = 0;
int foodX = 0, foodY = 0;
int TouchFood();
int TouchWall();

int main(){
	char order;
	printmap();
	makeAnotherFood();
	while(scanf("%c",&order) != EOF){
		if(order == 'w'){
			snakeMove(0,-1) ;
		}
		if(order == 'a'){
			snakeMove(-1,0);
		}
		if(order == 's'){
			snakeMove(0,1);
		}
		if(order == 'd'){
			snakeMove(1,0);
		}
		if(TouchFood){
			makeAnotherFood();
			lengthen();
		}
		else if(TouchWall){
			gameover();
		}
		printmap();
	}
	
} 

void snakeMove(int a,int b){
	clear();
	TailX = snakeX[length - 1];
    TailY = snakeY[length - 1];
	for (int i = length - 1; i >= 1; i--)
        {
            snakeX[i] = snakeX[i - 1];
            snakeY[i] = snakeY[i - 1];//移动
        }
	if(a == 1 && b == 0){
		snakeX[0]++;
	}
	if(a == 0 && b == 1){
		snakeY[0]++;
	}
	if(a == -1 && b == 0){
		snakeX[0]--;
	}
	if(a == 0 && b ==-1){
		snakeY[0]--;
	}
}

void clear(void){
    for (int i = 0; i < length; i++)
        map[snakeY[i]][snakeX[i]] = BLANK_CELL;
}

void printSnake(void){
    map[snakeY[0]][snakeX[0]] = SNAKE_HEAD;
    for (int i = 1; i < length; i++)
        map[snakeY[i]][snakeX[i]] = SNAKE_BODY;
}

void printMap(void){
	printSnake();
		for(int i = 0;i < 13;i++){
			printf("%s\n",map[i]);
		}	
	}

void makeAnotherFood(){
	srand(time(NULL));

    if (food == 0)
    {   
        foodX = rand() % 10 + 1;
        foodY = rand() % 10 + 1;
        if (map[foodX][foodY] == ' ')
        {
            map[foodX][foodY] = SNAKE_FOOD;
            food++;
        }
	}
}

int TouchFood(){
	if (snakeY[0] == foodX&&snakeX[0] == foodY){
		return 1;
	}
}

void lengthen(){
	if(length < SNAKE_MAX_LENGTH){
		length++;
		snakeX[length - 1] = TailX;
        snakeY[length - 1] = TailY;
	}
}

int TouchWall(){
	if(snakeX[0] == 0||snakeX[0] == 12||snakeY[0] == 0||snakeY[0] == 12){
		return 1;
	}
	else
	return 0;
}