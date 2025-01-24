---
layout: project
permalink: /:title/
category: projects

meta:
  keywords: "IT Engineering"

project:
  title: "Crosswise"
  type: "Jekyll"
  url: "https://github.com/tylerchao/FHWedel_AdvanceProgramming_CrossWise"
  logo: "/assets/images/projects/crosswise/Interface1x1.png"
  tech: "Java, JavaFx, AI player"

---

<p>This project is primarily developed using the Java programming language, with IntelliJ IDEA serving as the integrated development environment (IDE). To create the desktop application, the JavaFX library is used to build a graphical user interface (GUI). Additionally, Scene Builder is employed to simplify the integration of FXML markup with the IDE, streamlining the GUI development process.

<br>

</p> 

<br>

### Game Description

CrossWise is a simple 6x6 board game that accommodates up to four players, divided into two teams: a vertical team and a horizontal team. The two teams compete against each other, with the vertical team focusing on the vertical lines of the game board, while the horizontal team concentrates on the horizontal lines. 

Each player starts with four tokens. In each round, players have the option to either place a token on the board or use a functional token to achieve a strategic advantage.
<br>
- Player mode:
<br>
This game offers two player modes: two players or four players. Players can be all human, a mix of human and computer players, or all computer players.

<br>

### Token

This game is played with six different symbol tokens which have unique shapes and
colors, and four different action tokens have their own functionality. This increases
game variability and difficulties. The following description is about the utilization
of symbol token and action token:

<br>

Symbol Token
 
<br>

The symbol tokens consist of six different shapes, for example, cross, pentagon, square, star, sun, and triangle. Each symbol token exists seven times in a round of a game. 
The main functionality of those symbol tokens is that player selects one of them as a placing token onto the
chess board to occupy a position on the board.

<br>

<img src="/assets/images/projects/crosswise/symboltokens.png" alt="Description" style="width:50%; height:auto;">
<center><h2>Symbol Tokens</h2></center>

<br>

Action Token

<br>

- Remove
The player moves a token of his choice on the board to another empty
square of his choice (the square does not have to be adjacent).
- Shifter
The player removes a token of his choice on the board. He takes the
removed stone into his hand.
- Exchange
The player swaps two tokens of his choice on the board with each other.
- Replace
The player replaces a token of his choice on the board with one of his
own tokens. He takes the replaced token into his hand.

<br>

<img src="/assets/images/projects/crosswise/actiontokens.png" alt="Description" style="width:50%; height:auto;">
<center><h2>Action Tokens</h2></center>

<br>
### Structure

The program divided into two diagrams: the package of GUI and the package of Logic 

<br>

- The package of GUI:
  
  <br>

  The first **FXML** interface controller is responsible for the main scene and communicates with the logic package. Any user actions are displayed on this primary User Interface. For example, players can operate the game, select options from the menu bar, and observe the current game state.

  The second scene, **UserInterfacePlayer**, manages the initialization of the participants' states. Players can manually enter their names and decide which players will be controlled by the bot.

  Regarding the communication between these two windows, the first interface establishes a reference to the second window to call a getter method that passes the players’ names and states to the main window. It is clear that the flow of information is one-directional, from the first scene to the second scene.

<br>

- The package of Logic:

<br>

  The **Logic** class primarily controls the entire game program, which serves as the core class. It integrates all other classes, including the AI logic algorithm, winner determination logic, and game initialization. The **Logic** class also needs to communicate bidirectionally with other classes to update various game features.

<br>

  In detail, the **Logic** class frequently interacts with the **Player** class to track the current player's status. This information is then passed to the GUI package to display on the main interface, allowing participants to know which player needs to take their turn.

<br>

  Additionally, the **Logic** class interacts with the **Pack** class to manage the global constant representing a full pack, which is responsible for counting the total number of tokens. The program requires not only a full pack of all tokens but also a separate pack to keep track of action tokens. Each time a token is used, the corresponding token pack is diminished by one.

<br>

  Furthermore, the **Move** and **Position** classes are also used in methods for analyzing AI movement. These classes are instantiated as objects of their respective types and serve as tools in the game’s logic.

<br>

<img src="/assets/images/projects/crosswise/projectStructure.png" alt="Description" style="width:50%; height:auto;">
<center><h2> The classes diagram</h2></center>

<br>

### Game Demonstration

<br>

<img src="/assets/images/projects/crosswise/Interface.png" alt="Description" style="width:100%; height:auto;">
<center><h2>Wearable small electronic device</h2></center>

<br>


