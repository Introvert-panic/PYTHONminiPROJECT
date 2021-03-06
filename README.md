# PYTHONminiPROJECT
## ID- 191070059  , Name-OMKAR RAGHATWAN  ,Group-1(individual)

### AIM : To make a TIC-TAC-TOE two player game using python tools/liabraries that we've learned in our lectures of Programming LAB

#### PYTHON Constraints:

for making this game i.e. Tic-Tac-Toe we don't need any special liabraries its based on simple python logic
i've used Spider(python 3.8) for the implementation.

rest of the code part is depend on functions of game where 'while loop'plays major role.
variables and 'boolean functions' will also help us to continue the turn and for selecting the winner.

players choices will be sorted in a list of 9 items.

**CODE :**

#### which is basically gonna be our back-end 
```python


#~~~~~TIC-TAC-TOE~~~~~~~

board = ["*", "*", "*",
         "*", "*", "*",
         "*", "*", "*"]

game_still_going = True

winner = None

current_player = "X"


#```````


def play_game():

    display_board()

    while game_still_going:
        handle_turn(current_player)

        check_if_game_over()

        flip_player()

    if winner == "X" or winner == "O":
        print(winner + " won.")
    elif winner == None:
        print("Tie.")


def display_board():
    print("\n")
    print(board[0] + " | " + board[1] + " | " + board[2] + "     1 | 2 | 3")
    print(board[3] + " | " + board[4] + " | " + board[5] + "     4 | 5 | 6")
    print(board[6] + " | " + board[7] + " | " + board[8] + "     7 | 8 | 9")
    print("\n")


def handle_turn(player):
    print(player + "'s turn.")
    position = input("Choose a position from 1-9: ")

    valid = False
    while not valid:

        while position not in ["1", "2", "3", "4", "5", "6", "7", "8", "9"]:
            position = input("Choose a position from 1-9: ")

        position = int(position) - 1

        if board[position] == "*":
            valid = True
        else:
            print("You can't go there. Try again.")

    board[position] = player

    display_board()


def check_if_game_over():
    check_for_winner()
    check_for_tie()

#```````

def check_for_winner():

    global winner

    row_winner = check_rows()
    column_winner = check_columns()
    diagonal_winner = check_diagonals()

    if row_winner:
        winner = row_winner
    elif column_winner:
        winner = column_winner
    elif diagonal_winner:
        winner = diagonal_winner
    else:
        winner = None



def check_rows():

    global game_still_going

    row_1 = board[0] == board[1] == board[2] != "*"
    row_2 = board[3] == board[4] == board[5] != "*"
    row_3 = board[6] == board[7] == board[8] != "*"

    if row_1 or row_2 or row_3:
        game_still_going = False

    if row_1:
        return board[0]
    elif row_2:
        return board[3]
    elif row_3:
        return board[6]

    else:
        return None



def check_columns():

    global game_still_going

    column_1 = board[0] == board[3] == board[6] != "*"
    column_2 = board[1] == board[4] == board[7] != "*"
    column_3 = board[2] == board[5] == board[8] != "*"

    if column_1 or column_2 or column_3:
        game_still_going = False
    if column_1:
        return board[0]
    elif column_2:
        return board[1]
    elif column_3:
        return board[2]
    else:
        return None


def check_diagonals():
    global game_still_going
    diagonal_1 = board[0] == board[4] == board[8] != "*"
    diagonal_2 = board[2] == board[4] == board[6] != "*"
    if diagonal_1 or diagonal_2:
        game_still_going = False
    if diagonal_1:
        return board[0]
    elif diagonal_2:
        return board[2]
    else:
        return None


def check_for_tie():
    global game_still_going
    if "*" not in board:
        game_still_going = False
        return True
    else:
        return False


def flip_player():
    global current_player
    if current_player == "X":
        current_player = "O"
    elif current_player == "O":
        current_player = "X"


# Execution time.....

play_game()

```

#### our frontend will be a single instruction and as per user's choice that will run accordingly & will give a specific output.

```
* | * | *     1 | 2 | 3
* | * | *     4 | 5 | 6
* | * | *     7 | 8 | 9


X's turn.

Choose a position from 1-9:

```

#### LOGIC

 *The logic of game is based on the common rules of TTT:*

* *If you get xxx or ooo in row you win ,so we will check_rows()*
* *If you get xxx or ooo in column you win, so we will check_columns()*
* *If you get xxx or ooo in diagonal you win, so we will check_diagonal()*
* *You cant overwrite ,here we will handle_turn()*
* *If all boxes are filled and no winning conditions occurs then it’s a tie, for this we will define a condition such that if all boxes are filled its a draw in play_game()*

