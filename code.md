TicTacToe
=========

Tic Tac Toe, with no player input. The computer plays itself by choosing spots at random.


#define OFF     0
#define X       1
#define O       2

#define ROWS    3
#define COLS    3

int Led = 0;

static uint8_t board[ROWS][COLS] = {
    {OFF, OFF, OFF},
    {OFF, OFF, OFF},
    {OFF, OFF, OFF},
};

uint8_t current_player = 1;

void lights(x,y)
{
  if( x==0 && y==0){
    digitalWrite(2,HIGH);
    }else if(x==1 && y==0){
      digitalWrite(3,HIGH);
      }else if(x==2 && y==0){
        digitalWrite(4,HIGH);
          }else if(x==0 && y==1){
             digitalWrite(5,HIGH);
            }else if(x==1 && y==1){
              digitalWrite(6,HIGH);
               }else if(x==2 && y==1){
                digitalWrite(7,HIGH);
                    }else if(x==0 && y==2){
                    digitalWrite(8,HIGH);
                        }else if(x==1 && y==2){
                        digitalWrite(9,HIGH);
                            }else if(x==2 && y==2){
                            digitalWrite(10,HIGH);
    
void drawBoard()
{
    for (uint8_t x = 0; x != COLS; ++x)
    {
        for (uint8_t y = 0; y != ROWS; ++y)
        {
            // TODO: Set LED to board[x][y]...
            
        }
    }
}

void getPlayerMove()
{
    uint8_t x = 0;
    uint8_t y = 0;

    if (current_player == X)
    {
        do
        {   
            random(0,2) = x;
            random(0,2) = y;
            
        } while (board[x][y] == OFF);
            
    } else {
        // Player 2 is O
        do
        {
            random(0,2) = y;
            random(0,2) = x;
            
        } while (board[x][y] == OFF);
    }
  
    board[x][y] = current_player;
    board[x][y] 
}

void switchPlayer()
{
    current_player = (current_player == X) ? O : X;
}

bool gameOver()
{
    uint8_t i;

    for (i = 0; i != ROWS; ++i)
    {
        // Check rows
        if (board[i][0] == board[i][1] && board[i][1] == board[i][2])
            return true;

        // Check columns
        if (board[0][i] == board[1][i] && board[1][i] == board[2][i])
            return true;
    }

    // Check diagonals
    if (board[0][0] == board[1][1] && board[1][1] == board[2][2])
        return true;

    if (board[0][2] == board[1][1] && board[1][1] == board[2][0])
        return true;

    return false;
}

void blinkWinningRow()
{
    // TODO: drawBoard() will turn LEDs on. Turn them off here once per sec or so...
}

void setup()
{
    // TODO: Initialize ports, pins etc...
}

void loop()
{
    drawBoard();
    getPlayerMove();

    if (gameOver())
        blinkWinningRow();
    else
        switchPlayer();
}

