# Basic game body introduction
print("Welcome to Tic-Tac-Toe! (｡♥‿♥｡)")
print("This is how you play, positions are:")
print(" (0,0) | (0,1) | (0,2) ")
print("-----------------------")
print(" (1,0) | (1,1) | (1,2) ")
print("-----------------------")
print(" (2,0) | (2,1) | (2,2) \n")
print("Let's get started! ヽ(^o^)ノ\n")


def layout(body):
    for i in range(3):
        row_string = ""
        for j in range(3):
            row_string += body[i][j]
            if j < 2:
                row_string += " | "
        print(row_string)
        if i < 2:
            print("---------")


def wintest(body, player):
  
    for i in range(3):
        if body[i][0] == player and body[i][1] == player and body[i][2] == player:
            return True

    for j in range(3):
        if body[0][j] == player and body[1][j] == player and body[2][j] == player:
            return True

    if body[0][0] == player and body[1][1] == player and body[2][2] == player:
        return True
    if body[0][2] == player and body[1][1] == player and body[2][0] == player:
        return True
    return False

def draw(body):
    for i in range(3):
        for j in range(3):
            if body[i][j] == " ":
                return False
    return True

def chaliye_shuru_krte_hai():
    body = [[" " for _ in range(3)] for _ in range(3)] 
    chance_now = "Pratham( X )"
    current_symbol = "X"

    while True:
        layout(body)
        print(f"\n{chance_now}'s turn! (｡•̀ᴗ-)✧")
        
        while True:
            try:
                row = int(input("Enter row (0, 1, 2): "))
                col = int(input("Enter column (0, 1, 2): "))
           
                if row in [0, 1, 2] and col in [0, 1, 2]:
                    break 
                else:
                    print("\nInpur not allower!!! 0, 1, or 2 only (╯︵╰,)\n")
            except ValueError:
                print("\nwrong input buddy, enter nos only b/w 0 to 2 (¬_¬)\n")

        if body[row][col] == " ":
            body[row][col] = current_symbol
        else:
            print("\nOops, that spot's already taken! Try again! (¬_¬)\n")
            continue

        if wintest(body, current_symbol):
            layout(body)
            print(f"\n{chance_now} WINS! ＼(＾▽＾)／\n")
            break
        
        if draw(body):
            layout(body)
            print("\nIt's a DRAW! ¯\\_(ツ)_/¯\n")
            break

        if chance_now == "Pratham( X )":
            chance_now = "Dwiteya( O )"
            current_symbol = "O"
        else:
            chance_now = "Pratham( X )"
            current_symbol = "X"

# Start the game
chaliye_shuru_krte_hai()
