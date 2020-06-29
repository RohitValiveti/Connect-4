global gamestate
#game state is a data structure that contains the status of each position on the board AND carries info on number of rows and columns AND which players turn is the current turn, AND whether a player has 4 in a row.
#
#Creates the gamestate data structure
#first create the game matrix
gamestate=[]

c0=[]; c1=[]; c2=[]; c3=[]; c4=[]; c5=[]; c6=[]
for i in range(6):
    c0.append(0)
    c1.append(0)
    c2.append(0)
    c3.append(0)
    c4.append(0)
    c5.append(0)
    c6.append(0)
gamestate = [c0,c1,c2,c3,c4,c5,c6]

# add the row/col info
numrows=6
gamestate.append(numrows)
numcols=7
gamestate.append(numcols)

#add the current player turn info
player = 1
gamestate.append(player)

#add the win/lose info
Player1Win = False
Player2Win = False
gamestate.append(Player1Win)
gamestate.append(Player2Win)

#debug print statement
#print(gamestate)

#Make Gameboard
def create_game_board(gamestate):
    numrows=gamestate[7]
    numcols=gamestate[8]
    rectwidth= numcols*100+20*(numcols+1)
    rectheight=numrows*100+20*(numrows+1)
    xoffset = int(rectwidth/2)
    yoffset = int(rectheight/2)
    for row in range (6):
        for col in range (7):     
            xcoord = col*120+70
            ycoord = row*120+20
            pu()
            goto(xcoord-xoffset,ycoord-yoffset)
            pd()
            circle(50)
    pu()
    goto(0-xoffset,0-yoffset)
    pd()
    for i in range(2):
        forward(rectwidth)
        left(90)
        fd(rectheight)
        left(90)
    pu()
    update()
    return()
    
#Horizontal
def check_horizontal_win(gamestate):
  for col in range (4):
    for row in range (6):
      if (gamestate[col][row]==gamestate[col+1][row] and gamestate[col][row]==gamestate[col+2][row] and gamestate[col][row]==gamestate[col+3][row] == 1):
        #player1 win is true
        gamestate[10] = True

      elif  (gamestate[col][row]==gamestate[col+1][row] and gamestate[col][row]==gamestate[col+2][row] and gamestate[col][row]== gamestate[col+3][row]== 2):
        #player2 win is true
        gamestate[11] = True
  return()

#Vertical
def check_win_vert(gamestate):
  for row in range(3):
    for col in range(7):
      if (gamestate[col][row] == gamestate[col][row + 1] == 1 and gamestate[col][row + 1] == gamestate[col][row + 2] == 1 and gamestate[col][row + 2] == gamestate[col][row + 3] == 1):
        #player1 win is true
        gamestate[10] = True
      elif (gamestate[col][row] == gamestate[col][row + 1] == 2 and gamestate[col][row + 1] == gamestate[col][row + 2] == 2 and gamestate[col][row + 2] == gamestate[col][row + 3] == 2):
        #player2 win is true
        gamestate[11] = True
  return()

def FourInARowDownRight(gamestate):
  for row in range (3):
    for col in range (1,3):
      if (gamestate[row][col]== gamestate[row+1][col-1] and gamestate[row][col]== gamestate[row+2][col-2] and gamestate[row][col]== gamestate[row+3][col-3] and gamestate[row][col]==1):
        #player1 win is true
        gamestate[10] = True
      elif(gamestate[row][col]== gamestate[row+1][col-1] and gamestate[row][col]== gamestate[row+2][col-2] and gamestate[row][col]== gamestate[row+3][col-3] and gamestate[row][col]==2):
        #player2 win is true
        gamestate[11] = True
  return ()

def FourInARowDownLeft(gamestate):
  for col in range (4):
    for row in range (3,6):
      if (gamestate[col][row]== gamestate[col+1][row-1] and gamestate[col][row]== gamestate[col+2][row-2] and gamestate[col][row]== gamestate[col+3][row-3] and gamestate[col][row]==1):
        #player1 win is true
        gamestate[10] = True
      elif(gamestate[col][row]== gamestate[col+1][row-1] and gamestate[col][row]== gamestate[col+2][row-2] and gamestate[col][row]== gamestate[col+3][row-3] and gamestate[col][row]==2):
        #player2 win is true
        gamestate[11] = True
  return ()

def dropPiece(ColumnSelected,gamestate):
    print(ColumnSelected)
    #save gamestate to a temp variable - this allows me to compare to the original gamestate after a player has clicked.  If the two are STILL the same that means the player clicked on a column that was full and the game should not continue until a valid move is made by the player
    currentPlayer = gamestate[9]
    #if the top of the column is a zero then this must be a legal move, otherwise it's illegal move
    if (gamestate[ColumnSelected][5] == 0):
        for row in range (6):
            # find the lowest zero value in the selected column and change it to the players number  
            if gamestate[ColumnSelected][row] == 0:
                # change the 0 to the number of the current player  
                gamestate[ColumnSelected][row] = currentPlayer  # 1 or 2
                break # exit out of the for loop
        # alternate to the other player
        currentPlayer = gamestate[9]
        if (currentPlayer == 1):
            currentPlayer = 2
        else:
            currentPlayer = 1
        #update the game state with the new player
        gamestate[9] = currentPlayer
        #must be illegal move so do not alternate to the other player
    return()
        
#window = Screen()
def getClickCoord(x,y):
  #print(x,y)
  XCoordinate = x
  YCoordinate = y
  numrows=gamestate[7]
  numcols=gamestate[8]
  rectwidth= numcols*100+20*(numcols+1)
  rectheight=numrows*100+20*(numrows+1)
  WidthScreen = rectwidth
  HeightScreen = rectheight
  #print(WidthScreen,HeightScreen)
  YUpperLimitCoordinate = HeightScreen // 2
  YLowerLimitCoordinate = HeightScreen // 2 - 0.2 * HeightScreen // 2
  XCoordinateLeftLimit = 0 - WidthScreen//2 
  XCoordinateRightLimit = 0 + WidthScreen//2
  distFromLeft= XCoordinate - XCoordinateLeftLimit
  #print(distFromLeft)
  #print(YLowerLimitCoordinate,YUpperLimitCoordinate)
  #print(XCoordinateLeftLimit,XCoordinateRightLimit)
  colWidth = int(WidthScreen / numcols)
  ColumnSelected = int(distFromLeft / colWidth)
  #print(colWidth)
  #print(ColumnSelected)
  dropPiece(ColumnSelected,gamestate)
  return()

#*********************
from turtle import*
tracer(0,0)
#********************
window = Screen()
window.listen()

#Colors pieces
def piececolor(gamestate):
  pu()
  numrows=6
  numcols=7
  rectwidth= numcols*100+20*(numcols+1)
  rectheight=numrows*100+20*(numrows+1)
  xoffset = rectwidth//2
  yoffset = rectheight//2
  for row in range (6):
    for col in range (7):     
      xcoord = col*120+70
      ycoord = row*120+20
      pu()
      goto(xcoord-xoffset,ycoord-yoffset)
      if (gamestate[col][row] == 1):
        fillcolor("red")
        pd()
        begin_fill()
        circle(50)
        end_fill()
      elif(gamestate[col][row] == 2):
        fillcolor("yellow")
        pd()
        begin_fill()
        circle(50)
        end_fill()
  return()

create_game_board(gamestate)
update()

while (not Player1Win and not Player2Win):
  #get the players move and update the game board matrix  
  window.onclick(getClickCoord,1)
  
  #color the board with the players piece in chosen location
  piececolor(gamestate)
  
  #check if a player has won
  check_win_vert(gamestate)
  check_horizontal_win(gamestate)
  FourInARowDownRight(gamestate)
  FourInARowDownLeft(gamestate)

  #redraw the board  
  update()

  Player1Win = gamestate[numcols+3]
  Player2Win = gamestate[numcols+4]

print("Player 1 Win: ",Player1Win,"Player 2 Win: ",Player2Win)
done()
