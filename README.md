# python
# PYTHON-PROGRAM-4
program for tic tac toe
board=[['','',''],['','',''],['','','']]
def print_board(board):
    print(*board[0],sep=" | ")
    print("------------")
    print(*board[1],sep=" | ")
    print("------------")
    print(*board[2],sep=" | ")
def get_markers():
    marker_1=input("player_1 choice:(X or O)").upper()
    marker_2=""
    if marker_1 =='X':
        marker_2 ='O'
        return['X','O']
    elif marker_1 =='O':
        marker_2 ='X'
        return['O','X']
    else:
        print("please enter a valid input!")
        return get_markers()
def get_coordinates():
    x,y=list(map(int, input("enter the coordinates:").split()))
    if x in [0,1,2] and y in [0,1,2]:
        return[x,y]
    else:
        print("invalid input!")
        return get_coordinates()
def check_for_win(board):
    for row in board:
        if row[0] == row[1] and row[1] == row[2] and row[1]!='':
            return True
    for i in range(len(board)):
        if board[0][i] == board[1][i] and board[1][i] == board[2][i] and board[2][i]!='':
            return True
    if board[0][0] == board[1][1] and board[1][1] == board[2][2] and board[2][2]!='':
        return True
    if board[0][2] == board[1][1] and board[1][1] == board[2][0] and board[2][0]!='':
        return True
    return False
def update_board(board, chance, marker, x,y):
    if chance == True:
        board[x][y] = marker
        if check_for_win(board):
            print("player_1 wins")
            return "game over"
        return False
    else:
        board[x][y] = marker
        if check_for_win(board):
            print("player_2 wins")
            return "game over"
        return True
def play_game():
    player_1 = 0
    player_2 = 0
    m1,m2 = get_markers()
    print(f"player_1: {m1},player_2: {m2}")
    chance = True
    while True:
        print_board(board)
        x,y = get_coordinates()
        if chance:
            chance = update_board(board, chance, m1, x,y)
            if chance == "game over":
                break
        else:
                chance = update_board(board, chance, m2, x,y)
                if chance == "game over":
                    break
play_game()
