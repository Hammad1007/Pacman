#include <iostream>                // header files
#include <conio.h>
#include <map>
#include <windows.h>
#include <ctime>
using namespace std;

void gotoxy(short x, short y)        // function for setting the initial position of the pacman and the enemy

{	
  HANDLE hStdout = GetStdHandle(STD_OUTPUT_HANDLE);
	COORD position = {y, x};
	SetConsoleCursorPosition(hStdout, position);
	
}

void Food(char map[14][24])             // function for setting the food in the map
{
	for( int a = 0; a < 14; a++ )
	{
		for( int b = 0; b < 24; b++ )
		{
			if( map[a][b] == ' ' )
			{
				if((b % 2 == 1 ) && ( a % 2 == 1 ))
				{
				      map[a][b] = '.';
				}
			}
		}
	}
}

void display_Map(char map[14][24])       // function for displaying map
{
    for( int i = 0; i < 14; i++ )
    {
        for( int j = 0; j < 24; j++ )       // using nested loop as it is a 2D array
        {
            cout << map[i][j];
        }
        cout << endl;
    }
    cout << endl;
}
