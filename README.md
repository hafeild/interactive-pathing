# Interactive Pathing Webapp
This webpage allows users to create a pixel maps that represent mazes that
an agent must traverse, picking up items along the way and avoiding obstacles.
These are solved by a selected path-finding algorithm.


## Key features

Maps can be created using a pixel art canvas with the following color palette:

  * green (s): the agent's starting position; every map has only one of these
  * dark red (e): the exit -- this is where the agent must end up; every map has only one of these
  * black (w): a wall -- the agent cannot enter or pass through walls
  * cyan (o): water; the agent incurs a cost of 3 units by entering into a water spot; a map may have 0 or more of these
  * orange (l): lava; the agent can enter lava, but then dies, so it cannot move to any other spot once it enters lava; it incurs a cost of 1; a map may have 0 or more of these.
  * transparent ( ): an empty space; the agent incurs a cost of 1 by entering an empty space
  * purple (i): represents an item the agent must pick up; entering an item space incurs a cost of 1 and the item is picked up; a map may have 0 or more of these.

The agent must start at the starting spot, pick up all items, and reach the exit to solve the puzzle. 

Maps can be saved as PNGs or text files (using ASCII characters to represent the
various map elements). Maps can also be uploaded as either PNG or map elements.

To solve the maze, the user may select from several search algorithms:

  * uninformed:
    - ignores all costs
        * breadth first search (BFS)
        * depth first search (DFS)
        * iterative deepening (ID)
    - incorporates backwards cost
        * uniform cost search (UCS)
  * informed:
    - greedy
    - A*

Greedy and A* both allow the user to select from several heuristics, including
Euclidean distance to the exit, Manhattan distance to the exit, the distance to
the nearest uncollected item, and the number of uncollected items.

In addition, the user can select the refresh rate of the live map (how many times per second the interface will be updated). 

Once the user selects "solve", the algorithm is employed using Tree Search (with non-repeating states on the same path). While the algorithm is running, a version of the map will be displayed that shows the path from the starting state to the state the agent is currently expanding (with a black line), as well as all spaces that have been explored thus far. In addition, the following stats are shown:

  * the number of states expanded
  * the maximum fringe size
  * the cost of the current path
  * the length of the current path

At the end, the solution path is highlighted in yellow.

Each run is saved to localStorage -- the map, the settings, and the outcome (both the graphic showing the explored states and solution path, as well as the corresponding states). These saved runs can then be loaded and used to jump start a new version with different settings or a different map.