# ChessEngine-Cpp

### This is an engine written in c++ which can be used as a backend for a simple game of chess 

---

## Implementation

As this engine is written in c++ you will have to use some sort of interface compile (e.g. [SWIG](http://www.swig.org/exec.html)) to use it in the language you want.

## Usage

-   In order to start the game you need to declare a GameState object
    -   e.g. `GameState gs = new GameState();`
-   In order to execute a move, you have to call the "playMove" method and pass in 4 arguments:
    -   Row of the piece you want to move
    -   Column of the piece you want to move
    -   Row of the destination sqaure
    -   Column of the destination square
    -   e.g. `gs.playMove(6, 4, 4, 4);`
    -   This method returns an interger value which should be captured, as it tells if a pawn can be promoted and the game awaits an input, else the game wont continue:
        -   `-1: Move could not be performed`
        -   `0: Move executed successfully`
        -   `1: Move executed sucessfully and pawn can be promoted (use the promote method)`
        -   `2: Stalemate`
        -   `3: White is in check`
        -   `4: Black is in check`
        -   `5: White got checkmated`
        -   `6: Black got checkmated`
-   In order to receive the possible moves for a specific piece, you have to call the "getMovesForPiece" mathod and pass in 2 arguments:
    -   Row of the piece
    -   Column of the piece
    -   e.g. `gs.getMovesForPiece(6, 4);`
-   There is also the possibility to undo a move by calling the "undoMove" method, which undoes the last move
    -   e.g. `gs.undoMove();`
-   If you want to access to board state, you can simply access the "board" variable inside the GameState object
    -   e.g. `gs.board;`
-   Once a pawn advances to the end of the board, the "promote" method has to be called, as the program awaits that input
    -   The "promote" method taks an interger value as argument which defines the piece the pawn should become:
    -   `1: Queen, 2: Knight, 3: Bishop, 4: Rook`
    -   e.g. `gs.promote(1);`