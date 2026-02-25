# 20260225_dot



#pragma warning (disable:4996)
#include <stdio.h>
#define MAP_WIDTH  10
#define MAP_HEIGHT  10

#define RODE  0
#define WALL 1
#define GEM 2

#define UP 1
#define DOWN 2
#define LEFT 3 
#define RIGHT 4
#define EXIT 0

int main()
{
	unsigned char map[MAP_WIDTH][MAP_HEIGHT] = {
		{0, 1, 1, 1, 1, 1, 1, 1, 1, 1},
		{0, 0, 0, 0, 0, 0, 0, 0, 0, 1},
		{1, 1, 1, 1, 1, 1, 1, 0, 0, 1},
		{1, 0, 0, 0, 0, 0, 1, 1, 0, 1},
		{1, 0, 0, 0, 2, 0, 1, 1, 0, 1},
		{1, 1, 1, 1, 0, 0, 1, 1, 0, 1},
		{1, 0, 0, 0, 0, 0, 0, 0, 0, 1},
		{1, 0, 0, 0, 0, 0, 0, 0, 0, 1},
		{1, 0, 0, 0, 0, 0, 0, 0, 0, 1},
		{1, 1, 1, 1, 1, 1, 1, 1, 1, 1},
	};

	int playerX = 0;
	int playerY = 0;
	int direction = 0; 

	while (true)
	{
		for (int y = 0; y < MAP_WIDTH; y++)
		{
			for (int x = 0; x < MAP_HEIGHT; x++)
			{
				if (map[y][x] == WALL)
					printf("■");

				else if (map[y][x] == RODE)
				{
					if (playerX == x && playerY == y)
						printf("▲");

					else
					printf("□");
				}
				else if (map[y][x] == GEM)
					printf("◈");
			}
			printf("\n");
		}

		printf("1. 위  2.아래  3.왼쪽  4.오른쪽  5.종료\n");
		scanf("%d", &direction);

		switch (direction)
		{
		case UP :
			if (playerY - 1 >= 0)
			{
				if (map[playerY - 1][playerX] == RODE)
					playerY--;

				else if (map[playerY - 1][playerX] == GEM)
				{
					printf("게임클리어!!!\n");
					playerX = 0;
					playerY = 0;
				}
			}
			break;

		case DOWN:
			if (playerY + 1 < MAP_HEIGHT)
			{
				if(map[playerY+1][playerX] == RODE)
					playerY++;

				else if (map[playerY + 1][playerX] == GEM)
				{
					printf("게임클리어!!!\n");
					playerX = 0;
					playerY = 0;
				}
			}
			break;

		case LEFT:
			if (playerX + 1 < MAP_WIDTH)
			{
				if (map[playerY][playerX-1] == RODE)
					playerX--;

				else if (map[playerY][playerX - 1] == GEM)
				{
					printf("게임클리어!!!\n");
					playerX = 0;
					playerY = 0;
				}
			}
			break;

		case RIGHT:
			if (playerX + 1 < MAP_WIDTH)
			{
				if (map[playerY][playerX + 1] == RODE)
					playerX++;

				else if (map[playerY][playerX + 1] == GEM)
				{
					printf("게임클리어!!!\n");
					playerX = 0;
					playerY = 0;
				}
			}
			break;

		default:
			if (direction == EXIT)
			{
				return  0;
			}
			printf("너 틀림\n");
			break;
		}
	}




}
