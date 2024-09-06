# CodSoft
this is my Codsoft Internship Task Repository where i have completed my all Task regarding this Codsoft internship

Task 1 : NUMBER GUESSING GAME 

CODE : 

    #include <iostream>
    #include <cstdlib>  // for rand() and srand()
    #include <ctime>    // for time()

    using namespace std;

    int main() {
    srand(time(0));  // Seed the random number generator with the current time
    int number_to_guess = rand() % 100 + 1;  // Random number between 1 and 100
    int guess;

    cout << "I'm thinking of a number between 1 and 100. Try to guess it!" << endl;

    while (true) {
        cout << "Enter your guess: ";
        cin >> guess;

        if (guess < number_to_guess) {
            cout << "Too low! Try again." << endl;
        } else if (guess > number_to_guess) {
            cout << "Too high! Try again." << endl;
        } else {
            cout << "Congratulations! You guessed the correct number!" << endl;
            break;
        }
    }

    return 0;
    }




  TASK : 2 
  SIMPLE CALCULATOR 

  CODE :

    #include <iostream>
    using namespace std;

    int main() {
    double num1, num2;
    char operation;

    // Asking user for two numbers
    cout << "Enter first number: ";
    cin >> num1;
    cout << "Enter second number: ";
    cin >> num2;

    // Asking user to select an operation
    cout << "Choose operation (+, -, *, /): ";
    cin >> operation;

    // Perform the selected operation
    switch (operation) {
        case '+':
            cout << "Result: " << num1 + num2 << endl;
            break;
        case '-':
            cout << "Result: " << num1 - num2 << endl;
            break;
        case '*':
            cout << "Result: " << num1 * num2 << endl;
            break;
        case '/':
            if (num2 != 0) {
                cout << "Result: " << num1 / num2 << endl;
            } else {
                cout << "Error: Division by zero is not allowed!" << endl;
            }
            break;
        default:
            cout << "Error: Invalid operation!" << endl;
            break;
    }

    return 0;
}



TASK : 3 
TIC-TAC-TOE GAME 

CODE :

    #include <iostream>
    using namespace std;

    char board[3][3];  // Tic-Tac-Toe board
    char currentPlayer = 'X';  // Current player ('X' or 'O')
    bool gameRunning = true;  // Flag to check if game is still running

    // Function to initialize the board with numbers 1-9
    void initializeBoard() {
    char num = '1';
    for (int i = 0; i < 3; i++) {
        for (int j = 0; j < 3; j++) {
            board[i][j] = num++;
        }
    }
    }

    // Function to display the current state of the board
    void displayBoard() {
    cout << endl;
    for (int i = 0; i < 3; i++) {
        for (int j = 0; j < 3; j++) {
            cout << board[i][j];
            if (j < 2) cout << " | ";
        }
        if (i < 2) cout << "\n---------\n";
    }
    cout << endl;
    }

    // Function to check if the current player has won
    bool checkWin() {
    // Check rows and columns
    for (int i = 0; i < 3; i++) {
        if (board[i][0] == currentPlayer && board[i][1] == currentPlayer && board[i][2] == currentPlayer) return true;
        if (board[0][i] == currentPlayer && board[1][i] == currentPlayer && board[2][i] == currentPlayer) return true;
    }

    // Check diagonals
    if (board[0][0] == currentPlayer && board[1][1] == currentPlayer && board[2][2] == currentPlayer) return true;
    if (board[0][2] == currentPlayer && board[1][1] == currentPlayer && board[2][0] == currentPlayer) return true;

    return false;
    }

    // Function to check if the game is a draw
    bool checkDraw() {
    for (int i = 0; i < 3; i++) {
        for (int j = 0; j < 3; j++) {
            if (board[i][j] != 'X' && board[i][j] != 'O') return false;
        }
    }
    return true;
    }

    // Function to take the player's move input and update the board
    void playerMove() {
    int choice;
    cout << "Player " << currentPlayer << ", enter your move (1-9): ";
    cin >> choice;

    // Map the player's input to the correct board position
    int row = (choice - 1) / 3;
    int col = (choice - 1) % 3;

    // Check if the chosen cell is empty
    if (board[row][col] != 'X' && board[row][col] != 'O') {
        board[row][col] = currentPlayer;
    } else {
        cout << "Cell already occupied! Try again." << endl;
        playerMove();
    }
    }

    // Function to switch players
    void switchPlayer() {
    currentPlayer = (currentPlayer == 'X') ? 'O' : 'X';
    }

    // Main function to run the game
    int main() {
    char playAgain;

    do {
        gameRunning = true;
        currentPlayer = 'X';  // Reset to player 'X'
        initializeBoard();  // Initialize/reset the board

        while (gameRunning) {
            displayBoard();
            playerMove();  // Get the current player's move

            if (checkWin()) {
                displayBoard();
                cout << "Player " << currentPlayer << " wins!" << endl;
                gameRunning = false;
            } else if (checkDraw()) {
                displayBoard();
                cout << "It's a draw!" << endl;
                gameRunning = false;
            } else {
                switchPlayer();  // Switch players
            }
        }

        // Ask if players want to play again
        cout << "Do you want to play again? (y/n): ";
        cin >> playAgain;
    } while (playAgain == 'y' || playAgain == 'Y');

    return 0;
}
