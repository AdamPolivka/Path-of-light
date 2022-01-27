# Path-of-light



## Gameplay preview
[Path of Light Gameplay preview](https://user-images.githubusercontent.com/12778446/151210283-920eaf49-4ece-46c6-8b5d-b4df0772636b.mp4)

### Orb Dragging mechanic
![OrbDragging](https://user-images.githubusercontent.com/12778446/151213045-46c42690-d1a1-4705-987d-75e4487b2894.gif)

### Tile Dragging mechanic
![TileDragging](https://user-images.githubusercontent.com/12778446/151213061-b83bc44f-e52f-4195-95ba-b5a0c4a934d5.gif)

### Finish effect
![FinishEffect](https://user-images.githubusercontent.com/12778446/151213069-c19c5a77-9a32-4d20-80bd-25db287e1d65.gif)


## Maze design
- Start with a simple path from point A to point B
- Add other directions
- Convert the desing to numbers where each number resembles different type of path piece

![MazeDesign](https://user-images.githubusercontent.com/12778446/151219390-a904cb84-26f7-4c03-9dab-02075e1ea7fc.gif)

## Backend
In charge of keeping track of: 
- Prevents illegal tile movement 
- Current tile position on the grid
- Neighbouring tiles and its nodes
- Updating connections between nodes when tiles move 
- Tracks the path

![image](https://user-images.githubusercontent.com/12778446/151219671-f0721c93-9a03-4695-a77d-9bd9dd5375ad.png)
![image](https://user-images.githubusercontent.com/12778446/151220476-6b89c808-d532-48e0-93a3-fece00cadd7e.png)

### Maze configuration
- On the walls there is 3x5 grid where the tiles can be placed
- Each tile is made of 5x5 node grid

![image](https://user-images.githubusercontent.com/12778446/151266089-8f4cb515-bf28-4078-913c-a3fc08701028.png)


#### Tile cofiguration on the wall
Each wall has its own grid that stores the references to the tiles on that wall. The tile object is placed to
the correct position on the wall according to the information in the grid.

![image](https://user-images.githubusercontent.com/12778446/151221077-79e0d717-740d-4324-8f26-b284b8e36dc0.png)

#### Node configuration on tiles
A node system is used to create pathways on the tiles. In order to create pathways on tiles a node system is used. 
Each tile has a 5x5 matrix of nodes. These nodes are configurated accordingly to the numbers from the configarion matrix. 
Each number resemble different type of pathway piece.

![image](https://user-images.githubusercontent.com/12778446/151223725-9389d5a1-4749-425b-ac9f-c463eefad031.png)

#### Node system
- Each tile contains 5x5 grid of nodes
- Different node types are represented by integers in range from 0 to 11
- Connects neighbouring nodes that are compatible together
- This system serves important role guiding the orb drag directions through the maze. 
- Allows the light trail to be recorded.

#### Create Node system 
After the tiles and its properties are setup _create node system_ method is called on each wall. Each wall
calls similar method on its tiles. Called tile method updates the nodes on the tile. 

These nodes keep track of their neighbouring nodes. This system serves important role guiding the orb drag directions through the maze. 
Also allows the light trail to be recorded.

![image](https://user-images.githubusercontent.com/12778446/151225156-067b6208-d06c-46b5-a119-fe730d132c03.png)




### Updating the grid
- update the neighbour grid after you move a tile
