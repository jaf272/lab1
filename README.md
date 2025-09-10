# CS 1501 - Lab #1 (Boggle Game)

## Table of Contents

- [Overview](#overview)
- [Boggle Game](#boggle-game)
- [Backtracking and Pruning](#backtracking-and-pruning)
- [Tasks](#tasks)
- [Running and Testing](#running-and-testing)
- [Submission Instructions](#submission-instructions)

## Overview

 __Purpose__: In this lab, you will complete the implementation of a backtracking algorithm for the [Boggle game](https://wordshake.com/boggle)
).

The starter project has been provided to you with the following content:

- `BoggleSolver.java` - The file you will edit. It includes two places where you have to finish the code implementation. The `TODO` comments mark them.
- `DictInterface.java` - Used for the dictionary implementation for the lab, __do not modify__.
- `MyDictionary.java` - Used for the dictionary implementation for the lab, __do not modify__.
- `sample.txt` - An example board for the boggle game.
- `dict8.txt` - An example dictionary for the boggle game.
- `ExpectedOutput.txt` - A sample execution and expected output.
## Boggle Game
Given a 4x4 board of letters, find all words with at least three adjacent letters. Adjacent letters are horizontal, vertical, or diagonal neighbors. Any tile in the board can only be used once per word,
but can be used for multiple words.

## Backtracking and Pruning

Pruning is a technique that reduces the number of options to process while doing an exhaustive search of the search space of a problem. For example, if we are searching for the word *buzz* in a dictionary, there is no need to continue searching when we find no dictionary word that starts with *bu*, thus saving us on the search time.

Backtracking is returning to an earlier part of the search to find other paths to the solution. In the case of Boggle, this means going back to the previous tile to try using letters in a different direction to form a word. Like in the example below, we return to the word's first letter to find other options. *Assume the algorithm considers directions clockwise, starting at the right neighbor tile. Also, for simplicity's sake, assume we cannot search diagonally (You can search diagonally in the lab).*

<p align = "center">
An Example Using Backtracking to Find the Word Tug
</p>

![board_backtrack1](./img/Board_Before.png "Board_Before")![board_backtrack2](./img/Board_After1.png "Board_After1")

Assume we have accumulated the letters *TAT*, but we want to continue searching. As the searching algorithm continues, we exhaust all search options out of *TAT* when we discover none of the words we can create using that prefix exists on the board. So, we'll backtrack to the previous prefix, *TA*. There are no more tiles we can visit from our current letter combination. So, we'll backtrack again to *T*.

![board_backtrack3](./img/Board_After2.png "Board_After2")![board_backtrack4](./img/Board_After3.png "Board_After3")

After that, we proceed to the next possible tile coming out of *T* and get *TU*. Then, we check *TUT*, not a word or prefix in the dictionary. So, we backtrack to *TU* and then move down to *TUG*, which ends up being a valid word in the dictionary.

## Tasks

In this lab, we will implement a Boggle-solving program using a backtracking algorithm with pruning.

The backtracking algorithm has been explained in the lectures. Some documentation inside the code files describes how the algorithm is structured. The code will be explained to you more in-depth during your recitation. Given a particular result from the dictionary, you'll have to finish the parts of the algorithm that determine whether a tile in the board is valid to traverse to and what to do next.

## Running and Testing

Compile the Java files inside the lab directory. Once compiled, you can run the class file without any command-line arguments.

``` powershell
cd #YOUR_LAB1_DIRECTORY
javac *.java 
java BoggleSolver
```
You can also [run the program directly from VS Code](https://code.visualstudio.com/docs/java/java-tutorial). 

The input for execution and the corresponding expected output can be found in `ExpectedOutput.txt`.

## Submission Instructions

- The only file you can modify is the `BoggleSolver.java` file.
- `commit` and `push` the finished code to your GitHub repository. You can check the following [page](https://code.visualstudio.com/docs/sourcecontrol/github) to set up GitHub access directly from VS Code. If you think the commit command hangs in VS Code, it probably asks for a commit message in an open file. You would then need to enter a message and close the file before it can commit to GitHub.
- Submit your Github repository to GradeScope for automatic grading.

Note: If you use an IDE, such as NetBeans, Eclipse, or IntelliJ, to develop your programs, make sure the programs will compile and run on the command line before submitting – this may require some modifications to your program (e.g., removing package information).
