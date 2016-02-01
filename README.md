# Gameboard

Gameboards built in a playground

#### Games

- [x] Chess
- [x] Checkers
- [x] TicTacToe
- [ ] Mancala
- [ ] Backgammon
- [ ] Sudoku
- [ ] MineSweeper

#### Features

- [x] Swift Player Per Turn
- [x] Coordinate System
- [x] Ability to Reset
- [ ] Available Moves : *hint system*
- [ ] Piece Collection
- [ ] Time Control
- [ ] Simple Move AI

#### Overall Validation

- [x] Stop friendly fire : *checks if target piece is yours*
- [x] Only play on your turn : *checks against pieces for player*
- [x] No piece available : *checks for no piece*
- [x] Off the board : *checks if target square is on board*

## Chess

- [x] Coordinates
	- columns A - H
	- rows 8 - 1

```swift
var chess = GameBoard(.Chess)

// collection of moves

let moves: [(ChessSquare,ChessSquare)] = [
    
    (B7,B5), // pawn leaps
    (C2,C4), // pawn leaps
    (B5,C4), // pawn takes pawn
    (B1,C3), // knight charges
    (C8,A6), // bishop advances
    (E2,E4), // pawn leaps
    (G7,G6), // pawn creeps
    (F1,C4), // bishop take pawn
    (A6,D3), // blocked move throws error
    
]

// loop moves

for move in moves {
    
    do {
        
        try chess.move(pieceAt: move.0, toSquare: move.1)
        
    } catch {
        
        error
    
    }
    
}


chess.visualize()
```

![Chess](./images/chess.png?raw=true)

#### Validation

- [x] Standard Moves
	- [x] Pawn
	- [x] Rook 
	- [x] Knight 
	- [x] Bishop 
	- [x] Queen 
	- [x] King

- [ ] Special Moves
	- [ ] Castling
	- [ ] En passant : *pawn take down in passing*
	- [ ] Pawn Promotion
	- [ ] Check & Checkmate

## Checkers

- [x] Coordinates
	- columns 0 - 7
	- rows 0 - 7

```swift
var checkers = GameBoard(.Checkers)

// collection of moves

let moves: [(Square,Square)] = [

    ((2,1),(3,2)), // move
    ((5,2),(4,3)), // move
    ((2,3),(3,4)), // move
    ((4,3),(2,1)), // jump
    ((2,5),(4,3)), // cannot jump yourself
    ((2,5),(3,4)), // cannot land on your own piece
    ((1,0),(2,1)), // cannot land on another piece

]

// loop moves

for move in moves {
    
    do {
        
        try checkers.move(pieceAt: move.0, toSquare: move.1)
    
    } catch {
        
        error
    
    }
    
}


checkers.visualize()
```

![Checkers](./images/checkers.png?raw=true)

#### Validation

- [x] Standard Moves
	- [x] Diagonal -> 1
	- [x] Diagonal Jump

- [ ] Special Moves
	- [ ] Multiple Jumps
	- [ ] Promotion

## Sudoku

- [x] Coordinates
	- columns 0 - 8
	- rows 0 - 8

```swift
var sudoku = Gameboard(.Sudoku)

// collection of guesses

let guesses: [(Square,Guess)] = [
    
    // guesses
    
]

// loop moves

for guess in guesses {
    
    do {
        
        try sudoku.guess(toSquare: guess.0, withGuess: guess.1)
        
    } catch {
        
        print(error)
        
    }
    
}


sudoku.visualize()
```

![Sudoku](./images/sudoku.png?raw=true)

#### Validation

- [ ] Standard Moves
	
## TicTacToe

- [x] Coordinates
	- columns 0 - 2
	- rows 0 - 2

```swift
var tictactoe = GameBoard(.TicTacToe)

// collection of moves

let moves: [Square] = [
 
    (1,1),
    (0,0),
    (0,2),
    (2,0),
    (1,0),
    (1,2),
    (0,1),
    (1,1), // cant play filled spot
    (2,1),
    (2,2), // stalemate
    
]

// loop moves

for move in moves {
    
    do {
        
        try tictactoe.move(toSquare: move)
        
    } catch {
        
        error
        
    }
    
}


tictactoe.visualize()
```

![TicTacToe](./images/tictactoe.png?raw=true)

#### Validation

- [x] Standard Moves