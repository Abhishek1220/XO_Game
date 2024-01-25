import java.util.Random;
import java.util.Scanner;

class TicTacToe {
    static char[][] board;

    public TicTacToe() { // Constructor
        board = new char[3][3];
        InitBoard();
    }

    void InitBoard() { // making of the board
        for (int i = 0; i < board.length; i++) {
            for (int j = 0; j < board[i].length; j++) {
                board[i][j] = ' '; // initilizing all the 9 blocks with blank spaces
            }
        }
    }

    static void DisplayBoard() { // Displaying the board..
        System.out.println("-------------");
        for (int i = 0; i < board.length; i++) {
            System.out.print("| ");
            for (int j = 0; j < board[i].length; j++) {
                System.out.print(board[i][j] + " | ");
            }
            System.out.println();
            System.out.println("-------------");
        }
    }

    static void PlaceMark(int row, int col, char mark) { // Markin 0 and X in the index..
        if (row >= 0 && row <= 2 && col >= 0 && col <= 2) {
            board[row][col] = mark;
        } else {
            System.out.println("Invalid Positon");
        }

    }

    static boolean CheckColumnWin() { // Checking for column win..
        for (int j = 0; j <= 2; j++) {
            if (board[0][j] != ' ' && board[0][j] == board[1][j] && board[1][j] == board[2][j]) {
                return true;

            }
        }
        return false;
    }

    static boolean CheckRowWin() { // Checking for Row win...
        for (int i = 0; i <= 2; i++) {
            if (board[i][0] != ' ' && board[i][0] == board[i][1] && board[i][1] == board[i][2]) {
                return true;
            }
        }

        return false;
    }

    static boolean CheckDigWin() { // Checking for diagonal win...
        if (board[0][0] != ' ' && board[0][0] == board[1][1] && board[1][1] == board[2][2] ||
                board[0][2] != ' ' && board[0][2] == board[1][1] && board[1][1] == board[2][0]) {
            return true;
        } else {
            return false;
        }
    }

    static boolean DrawCheck() {
        for (int i = 0; i <= 2; i++) {
            for (int j = 0; j <= i; j++) {
                if (TicTacToe.board[i][j] != ' ') {
                    return false;
                }
            }
        }
        return true;
    }
}

abstract class Player {
    String name;
    char mark;

    abstract void MakeMove();

    boolean IsValidMove(int row, int col) { // Checking for valid indeces..
        if (row >= 0 && row <= 2 && col >= 0 && col <= 2) {
            if (TicTacToe.board[row][col] == ' ') {
                return true;
            }
        }
        return false;
    }
}

class HumanPlayer extends Player {
    HumanPlayer(String name, char mark) { // Player constructor..
        this.name = name;
        this.mark = mark;
    }

    void MakeMove() { // getting row and column..
        Scanner sc = new Scanner(System.in);
        int row, col;
        do {
            System.out.println("Enter the row and column");
            row = sc.nextInt();
            col = sc.nextInt();
        } while (!IsValidMove(row, col));
        TicTacToe.PlaceMark(row, col, mark);

    }

}

class Computer extends Player {
    Computer() { // Computer constructor..
        this.name = "Computer";
        this.mark = 'O';
    }

    void MakeMove() { // getting row and column..
        Scanner sc = new Scanner(System.in);
        int row, col;
        do {
            Random r = new Random();
            row = r.nextInt(3);
            col = r.nextInt(3);
        } while (!IsValidMove(row, col));
        TicTacToe.PlaceMark(row, col, mark);
    }
}

public class Game {
    public static void main(String[] args) throws Exception {
        Scanner sc = new Scanner(System.in);
        TicTacToe t = new TicTacToe();
        // ----------------------------//Variables declarations.....
        Player Cp;
        String p1name, p2name;
        char p1mark, p2mark;
        // ---------------------------//
        System.out.println("Enter 1 to play for single player and 2 for tow players");
        int choice = sc.nextInt();

        if (choice == 2) { // For 2 players....
            System.out.println("Enter player 1 name and choose the mark");
            p1name = sc.next();
            p1mark = sc.next().charAt(0);
            HumanPlayer P1 = new HumanPlayer(p1name, p1mark);
            System.out.println("Enter player 2 name and choose the mark");
            p2name = sc.next();
            p2mark = sc.next().charAt(0);
            HumanPlayer P2 = new HumanPlayer(p2name, p2mark);
            Cp = P1;
            while (true) {
                System.out.println(Cp.name + " Your turn");
                Cp.MakeMove();
                TicTacToe.DisplayBoard();
                if (TicTacToe.CheckColumnWin() || TicTacToe.CheckRowWin() || TicTacToe.CheckDigWin()) {
                    System.out.println(Cp.name + " is the Winner !!!!!!");
                    break;
                } else {
                    if (Cp == P1) {
                        Cp = P2;
                    } else {
                        Cp = P1;
                    }
                }
            }

        }

        if (choice == 1) { // For single player..
            System.out.println("Enter player 1 name");
            p1name = sc.next();
            p1mark = 'X';
            HumanPlayer P1 = new HumanPlayer(p1name, p1mark);
            Computer P2 = new Computer();
            Cp = P1;

            while (true) {
                System.out.println(Cp.name + " Your turn");
                Cp.MakeMove();
                TicTacToe.DisplayBoard();
                if (TicTacToe.CheckColumnWin() || TicTacToe.CheckRowWin() || TicTacToe.CheckDigWin()) {
                    System.out.println(Cp.name + " is the Winner !!!!!!");
                    break;
                } else {
                    if (Cp == P1) {
                        Cp = P2;
                    } else {
                        Cp = P1;
                    }
                }
            }
        }
    }
}
