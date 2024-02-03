Project decription:
A project is portion explosion is game played between two or more player .in this game the each player in his turn take one any random marble from the dispenser like a box which contain the marble of different colour when one marble is taken then the if the same in dispenser come together the explosion occur during the game if the player complete the three portion of same type the player can get 
points or if he completed five different type of portion he then also
get the points each portion also contain the points  which the player can get . In the end the player with the highest score wins the game .


project code parts

 
const int row = 5;
const int col = 5;
int Ingcount = 0;

explanation:
constants row and col are defined for the dimensions of the dispenser (5x5). Ingcount is an integer variable initialized to 0, which will be used to count the number of selected ingredients.

Code part 
Dispenser() {
        char ing[4] = { 'R', 'Y', 'b', 'B' };
        std::random device rd;
        std::mt19937 gen(rd());
        std::uniform_int_distribution<> dis(0, 3);

        for (int i = 0; i < row; i++) {
            for (int j = 0; j < col; j++) {
                disp[i][j] = ing[dis(gen)];
            }
        }
    }

Explanation
This is the constructor of the Dispenser class. It initializes the dispenser with random ingredients. The ingredients are represented by the characters 'R', 'Y', 'b', and 'B'. It uses the <random> library to generate random indices and assigns corresponding ingredients to each cell in the dispenser.



void DispenserDisplay() {
        for (int i = 0; i < row; i++) {
            for (int j = 0; j < col; j++) {
                cout << disp[i][j] << "\t";
            }
            cout << endl;
        }
    }

Explanation:
This function (DispenserDisplay) prints the current state of the dispenser to the console. It iterates over each cell in the dispenser and prints the corresponding ingredient.


void RollBack() {
        for (int i = 0; i < row - 1; i++) {
            for (int j = 0; j < col; j++) {
                if (disp[i][j] == '-') {
                    Char temp = disp[i][j];
                    Disp[i][j] = disp[i + 1][j];
                    Disp [i + 1][j] = temp;
                }
            }
        }
    }

Explanation 
This function (RollBack) is responsible for moving ingredients marked with '-' one row down, simulating the gravity effect. It iterates through the dispenser, and when it finds a cell with '-', it swaps the ingredients in the current cell with the one below it.

void check Explosion(int x, int y) {
    if (disp[x][y] == '-') {
        Return;
    } else if (x > 0 && x < 4) {
        if (disp[x][y] == disp[x + 1][y]) {
            SelectIng(x + 1, y);
        }
        if (disp[x][y] == disp[x - 1][y]) {
            SelectIng(x - 1, y);
        }
        if (disp[x][y] == prev) {
            SelectIng(x, y);
        }
    } else if (x == 0 && disp[x][y] == prev) {
        SelectIng(x, y);
    } else {
        return;
    }
}


Explanation:
This function, check Explosion, seems to be designed to recursively check for and handle explosions in a grid-like structure (represented by the disp array). It is associated with the game logic of selecting ingredients (Selecting) and checking for potential matches or explosions.


Class potion Tiles {
    mutex mtx;
    Styles* Sty;
    Styles Completed Potion[5];
    int potionRec[5] = { 0, 0, 0, 0, 0 };
    Styles* selected;
    int CompletedCount = 0;
public:
    int potionCount = -1;

    potionTiles() {
        Sty = new Styles[5];
        Sty[0].black = 3, Sty[0].blue = 1, Sty[0].red = 0, Sty[0].yellow = 2;
        Sty[1].black = 0, Sty[1].blue = 1, Sty[1].red = 2, Sty[1].yellow = 1;
        Sty[2].black = 2, Sty [2].blue = 0, Sty[2].red = 1, Sty[2].yellow = 2;
        Sty[3].black = 2, Sty[3].blue = 2, Sty[3].red = 0, Sty[3].yellow = 0;
        Sty[4].black = 0, Sty[4].blue = 1, Sty[4].red = 2, Sty[4].yellow = 2;
        selected = new Styles[2];
    }



Explanation

Defines a class potionTiles.
Declares a mutex mtx for synchronization.
Creates dynamic arrays Sty and selected using the new operator.
Initializes the Sty array with predefined values.
Sets initial values for other class members



void DisplayAllPotion() {
        cout << "All 5 styles are : \n";
        for (int i = 0; i < 5; i++) {
            cout << "Style " << i + 1 << " : " << "\tblack : " << Sty[i].black << "\tblue : " << Sty[i].blue << "\tRed : " << Sty[i].red << "\tYellow : " << Sty[i].yellow << endl;
        }
    }

Explanation:
Displays information about all five styles.




 

