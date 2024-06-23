# PacMan_OS
This repository contains code of Pac-Man Game in c++ using SFML. It is created using advanced concepts of Operating Systems like Threads and Synchronization.
You can eiher download the zip file or see individual files.
To compile the project, use the following command:
g++ game.cpp -o pacman -lsfml-graphics -lsfml-window -lsfml-system -lpthread -lX11

Project Description:

Phase 1 - Setting up Dedicated Threads for Game Modules:

Game Engine Thread:

● Create a dedicated thread for the game engine, which is responsible for coordinating the
overall game flow, handling input from players, updating the game state, and rendering
graphics.

● This thread will execute the main game loop, continuously updating the game state based
on user input and Ghost movement controller.
User Interface Thread:
● Implement a separate thread to manage the user interface (UI) components of the game,
including menus, scoreboards, and any Heads-up display (HUD) elements.
● This thread will handle input events from the player, such as keyboard or mouse input, and
communicate them to the game engine thread for processing.
Ghost controller Threads:
● Create individual threads for each ghost controller responsible for controlling the behavior
of ghosts in the game. There will be four ghost threads in the beginning of the game. There
may be an increase in the number of ghosts as the game time progresses.
● Each ghost controller thread will execute its ghost algorithm independently, determining
the movement patterns and actions of the ghosts based on the current game state. If you are
developing a slightly intelligent ghost, it should calculate a simple shortest path algorithm
to go in the direction of the Pac-man. Alternatively, for a simpler version each ghost can
follow a pre-defined path set for itself at the time of creation of thread.

Phase 2 - Basic Game Mechanics:
Game Board Initialization:
● Design and implement the layout for the shared game board among all threads, including
walls, paths, pellet positions, and power pellets. All these items in the game board should
be visible / accessible to the concerned threads.
● Initialize the starting positions for Pac-Man and the ghosts. The PacMan can start always
at a predefined location on a board. The ghost house in the center of the game board is
where ghosts start and return to after being eaten. The entrance to the ghost house is a
shared resource that only one ghost can use at a time.
Movement Mechanics
● Implement the movement logic for Pac-Man, allowing user input to dictate direction.
● Design basic AI for ghost movement as defined above in the Ghost controller thread
section, allowing them to roam the board on their paths.
Eating Mechanics
● Enable Pac-Man to eat pellets as he moves over them, updating the game score.
● Define the effects of Pac-Man eating a power pellet, such as ghosts turning blue for a
limited time.
Lives
● Implement a lives system for Pac-Man, allowing the player to have multiple attempts at
completing the game.
● Define the initial number of lives for the player and decrement this count each time Pac-
Man collides with a ghost.

Phase 3 - Synchronization:
Scenario 1 - Ghost Movement: This scenario remains the same. Ghosts need to read the game
board to decide their next move. Pac-Man needs to update the game board by eating pellets.
Students will need to ensure that no read operation happens during a write operation.
Scenario 2 - Eating Power Pellets: This scenario also remains the same. When Pac-Man eats a
power pellet, the ghosts turn blue and can be eaten by Pac-Man. The power pellets are eaten by
Pac-Man and respawned by the game. Students will need to ensure that no two power pellets are
eaten at the same time and that no power pellet is eaten when none are available.
Scenario 3 - Ghost House: Each ghost needs two resources to leave the ghost house: a key and
an exit permit. The keys and exit permits are limited. Students will need to ensure that no deadlock
situation occurs when all ghosts try to leave the ghost house at the same time.
Scenario 4 - Prioritizing Certain Ghosts: Certain ghosts are faster than others. The faster ghosts
need an extra speed boost ingredient from the game. The game has a limited number of speed
boosts i.e. only 2 speed boosts that can be used by any two ghosts. Each speed boost can only boost
one ghost at a time. Students will need to ensure that all faster ghosts get the speed boosts they
need.
