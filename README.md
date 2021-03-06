<p align=center>
    <img src="https://github.com/tahazulfiqar/csc290/blob/master/Screenshots/logo.png">
</p>

<p align="center">
  <a href="#installation">Installation</a>
  &nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;
  <a href="#how-to-play">How To Play</a>
  &nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;
  <a href="#documentation">Documentation</a>
  &nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;
  <a href="#individual-contributions">Individual Contributions</a>
  &nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;
  <a href="#license-information">License Information</a>
</p>


# Chess
Chess game created using `python` and `pygame`

## Installation
**NOTE**: Python 3.7 or higher is required to run the game.

```bash
# clone the repo
$ git clone https://github.com/tahazulfiqar/csc290.git

# change the working directory to csc290
$ cd csc290

# install pygame (version 1.9.7 or higher) if it is not already installed
$ python3 -m pip install -U pygame --user

# run GUI.py to start the game
$ GUI.py
```

If further help is needed to install pygame, go to:
https://www.pygame.org/wiki/GettingStarted

## How To Play
When the game launches, the user will be greeted with a title screen where the user can either start the game or change settings.

![Image title screen](https://github.com/tahazulfiqar/csc290/blob/master/Screenshots/menu.PNG)

In the settings screen, the user can choose to display a timer by clicking the timer button.

![Image settings screen](https://github.com/tahazulfiqar/csc290/blob/master/Screenshots/settings.PNG)

After clicking start, the board and pieces will appear in their starting positions. The user can now click on the pieces, which will either flash red if the piece does not belong to the current player, or highlight all the possible moves that the selected piece can move to. Clicking on a possible move will move the selected piece to that position. 

![Image settings screen](https://github.com/tahazulfiqar/csc290/blob/master/Screenshots/capture1.PNG)
![Image settings screen](https://github.com/tahazulfiqar/csc290/blob/master/Screenshots/capture2.PNG)

Chess is a turn based game so after every move, the other player makes the next move. This continues until a player checkmates (when the King is under attack or in "check" and every possible move by the King will also put it in check) the opponent, and the game ends. Our game do not have CPU opponents yet so it is currently a two player game only.

Since all the valid moves are highlighted, this game does not require any knowledge of chess to play. However, you can click [here](https://www.chess.com/learn-how-to-play-chess) if you are interested to learn more.

## Documentation
In our game's current form there are two main classes that we ended up using. The board class and the gui class. I will briefly describe the purpose of each class below:
### Board Class
The board class acts as a representation of the chess board and holds all the positions of the pieces in a nested list. Tiles that are empty are represented in the nested list as a 0. The board class is also responsible for checking the valid moves of selected pieces and actually moving the pieces that the player has moved. In the board class there are a few main functions described below:

#### create_board():
This is where the chess board nested list is created and all the pieces are placed in their starting positions. If you wanted to change the initial starting positions of the pieces this is where you would do it.

#### move(old_coord, new_coord)::
Allows the piece at coordinate old_cord to new_cord. This function is called when the user executes their move.

#### get_valid_moves(self, coordinate):
If a piece is at coordinate, it returns the a list of tuples - where each tuple represents a valid coordinate it can move to. Unique helper functions were created for each piece - for example the logic of the Knight piece movement was done so in the helper function get_knight_moves() - which is potentially called if knight is a coordinate.

### Gui Class
The gui class is where the window is created wherein the user can interact with and see what the board looks like. The gui class is also responsible for handling user input through clicks and displaying the updated board after each move. In the gui class there are many methods some of which will be explained below:
####  init():
This method is responsible for setting up the variables which are used by many of the other methods. If you would like to change the colours of the chess pieces and the background of the board or the window size this is where you would do so. This is also where the window is setup and is named self.screen. it is set currently to be a square, by changing the width variable and/or adding a height varaible and replacing it in the self.screen parameters you can change the size of the window.
#### draw_board(animation):
This method is responsible for drawing the board to the screen and setting up the empty tiles. 
#### draw_pieces(board, animation): 
This method is where the pieces are drawn to the window onto the board that was created in the previous function. This function also depends on the status of the board from the board class.
#### button(msg, x, y, w, h, inactive_colour, active_colour, action):
This method is used to set up necessary buttons like the start butuon and the settings button. If you want to add some buttons use this method to do so, but don't change this method itself.
#### switch(msg, x, y):
This method is used to create the switch for the timers in the settings menu. If you want to add some extra switches for possible features like a handicap or other game modes this would be the method you should use to create those switches. Don't change the actual method itself though.
#### settings(): 
This method is used to set up the settings window when the settings button is pressed in the intro screen. If you want to add some extra settings in the settings window, this is where you can add them, we reccommend using either buttons or switches to do so according to the feature that is being implemented. Follow the way we set up the timer and start features.
#### intro_screen(): 
This method is used to set up the intro screen that appears when the game is first loaded up. If you wanted to add something to the window that appears when the game is first started this would be the place to do so. This method is called when the Gui.py file is first run.
#### main():
This is the main method of the game that is run when the start button is hit from the intro screen. This method is responsible for taking input from the user and updating the board nested list in the board class accordingly. This method is tightly tied in to the board class as it is also responsible for highlighting the possible moves when the user clicks a piece and then updating the board in both the board class and the gui to reflect the changes to the game state. If you notice a gameplay bug and would like to try fixing it this would be the place to do so. This method is also responsible for calling the board classes move method when the player moves a piece. Each time an action is taken, the gui updates the screen to reflect what has been changed. 

## Extending our code
If you wish to extend our code, here are a few things to get you started:
* Fix queen so it cannot jump over king and other pieces
* Fix the rooks on the right hand side so they can move
* Get check and checkmate to work
* Add a game over screen
* Display the game status (whose turn it is, which pieces have been captured, show if players are in check etc.)
* Add other gamemodes
  * blitz chess
  * bullet chess
  * a best of x series
  * player vs ai

## Individual Contributions
### Taha
My prominent role in this project was providing back-end functionality of the board, pieces and piece movement. The main priority was to ensure that valid moves can be selected by the player to ensure accurate game logic is followed. Furthermore, I was able to provide a representation of the game that was understandable and easily integratable for the Front-End team. For the README, I provided documentation on the Board Class - which was also the main class I was working with for this project.  

### Adrian Lam
For the code, I mainly worked on the GUI. This includes initializing the board and pieces, the starting animation, selecting pieces, showing highlighted moves and moving the pieces. To provide some feedback for the user, I made the piece flash red when the user clicks on one of the opponent's pieces. There were also a few GUI issues that I fixed when other features were introduced. For example, the timer flashes whenever the user clicks and the inconsistent piece colours in the board class that caused an issue where certain pieces cannot be selected. For the README, I wrote the How To Play  and Extending Our Code sections.

### Cole Richardson
For this project I worked on the game class which was intended to be used as the main class reponsible for the flow of the game, however this didn't end up getting used as we ended up doing this in the gui class itself. I also worked on the player class which was to be used by the game class and pieces class to keep track of who the owner is, however this class also didn't end up getting used in the games current form. I also worked on the check_capture method in the board class which is responsible for checking if the player can capture a piece and also worked on implementing this into the gui classes main() method so that the player is able to capture pieces. Lastly I worked on refactoring the gui.py file into a class so that it is easier to extend and to add contributions to. In the readme I wrote the description of the board class in the documentation portion, and also worked on the documentation for the gui class and methods. 

### Juan Lamilla
I had a variety of tasks throughout this projects. Firstly, I created the pieces class that was used by placed by the board. Most importantly, these pieces keep track of their colour, and whether or not they have made their first move. Secondly, I created the title and settings screens. This included creating working click button and radio button functions. Finally, I created the chess timer. When selected in the settings screen, timers appear below the board that count down and alternate between players when it is their turn. For the README, I wrote the installation and helped with formatting (such as the links below the title).

## License information
MIT License

Copyright (c) 2019 CSC290Chess

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.

