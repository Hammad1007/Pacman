int main()                       // main function
{
	int score = 0;               // variable for calculating the score
  char h;                      // character variable
  char map[14][24] =           // character array map to show the map where there are 14 rows and 24 coloumns
    {
        "_______________________",
        "|                     |",
		    "| +-------+ +-------+ |",
		    "| |--+----+ +----+--| |",
        "| |--|   Hammad  |--| |",
		    "| |__| +-------+ |__| |",
        "|      | ----- |      |",
		   "| +--+ +-------+ +--+ |",
       "| |--|   Rashid  |--| |",
		  "| |--+----+ +----+--| |",
		 "| |-------+ +-------| |",
    "|                     |",
		"+---------GAME--------+",
    };
	cout << "PAC-MAN " << endl;
  system("cls");                 // clearing the system
	
  Food(map);                     // calling the function of food
  display_Map(map);              // calling the map function in main
  int Cx = 11, Cy = 21;          // setting the psoition of the pacman
	int E1x = 1, E1y = 21;         // setting the position of the enemy
	srand(time(0));
  
  for( int x = 0; x < 5000; x++ )
  {
    int haye = rand() % 4 + 1;
    h = getch();      // setting the movement of pacman
    
    if( h == 's')  // down
		{
			      if(map[Cx + 1 ][Cy] == ' ' || map[Cx + 1][Cy] == '.' )
            {
               Cx++;
            }
    }
    
    if( h == 'w' )  // up
    {	
			      if(map[Cx - 1][Cy] == ' ' || map[Cx - 1][Cy] == '.' )
            {
               Cx--;
            }
	  }
    
    if( h == 'a' )  // left
	  {
			      if(map[Cx][Cy - 1] == ' ' || map[Cx][Cy - 1] == '.' )
            {
               Cy--;
            }
		}
    
    if( h == 'd' )  // right
		{
			      if(map[Cx][Cy + 1] == ' ' || map[Cx][Cy + 1] == '.' )
            {
               Cy++;
            }
		}
		if( haye == 1 )         // enemy down move
		{
			if(map[E1x + 1][E1y] == ' ' || map[E1x + 1][E1y] == '.' )
			{
				E1x++;
			}
		}
    
		if( haye == 2 )          // enemy up
		{
			if(map[E1x - 1][E1y] == ' ' || map[E1x - 1][E1y] == '.' )
			{
				E1x--;
			}
		}
    
		if(haye == 3 )        // enemy left
		{
			if(map[E1x][E1y - 1] == ' ' || map[E1x][E1y - 1] == '.' )
            {
				E1y--;
            }
		}
    
		if( haye == 4 )       // enemy right
		{
			if(map[E1x][E1y + 1] == ' ' || map[E1x][E1y + 1] == '.' )
            {
               E1y++;
            }
		}
    
		if(map[Cx][Cy] == '.')    // calculating score when the pacman swallows coins
		{
			score++;
			map[Cx][Cy] = ' ';
		}
    
		system("cls");
		display_Map(map);      // display map
		gotoxy(Cx, Cy );       // set the pacman
                cout << "H" << endl;
		gotoxy(E1x, E1y);      // set the enemy
		cout << "@";
		gotoxy(14, 2);         // set the coordinates for the word score
		cout << "Score " << score << endl;
    
		if( score == 32 )
		{
			system("cls");
			cout << "You Win. Hurrah!!!! " << endl;
			break;
		}
    
		else if( Cx == E1x && Cy == E1y )
		{
			system("cls");
			cout << "You lose " << endl;
			cout << "Your score is: " << score << endl;
			break;
		}
	}
}
