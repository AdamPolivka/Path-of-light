# Path-of-light



## Gameplay preview
[Path of Light Gameplay preview](https://user-images.githubusercontent.com/12778446/151210283-920eaf49-4ece-46c6-8b5d-b4df0772636b.mp4)

### Orb Dragging mechanic
![OrbDragging](https://user-images.githubusercontent.com/12778446/151213045-46c42690-d1a1-4705-987d-75e4487b2894.gif)

### Tile Dragging mechanic
![TileDragging](https://user-images.githubusercontent.com/12778446/151213061-b83bc44f-e52f-4195-95ba-b5a0c4a934d5.gif)

### Finish effect
![FinishEffect](https://user-images.githubusercontent.com/12778446/151213069-c19c5a77-9a32-4d20-80bd-25db287e1d65.gif)

## Backend
In charge of keeping track of: 
- Illegal tile movement 
- Current tile position on the grid
- Neighbouring Tiles and its nodes
- Updating connections between nodes when tiles move 

![image](https://user-images.githubusercontent.com/12778446/151219671-f0721c93-9a03-4695-a77d-9bd9dd5375ad.png)
![image](https://user-images.githubusercontent.com/12778446/151220476-6b89c808-d532-48e0-93a3-fece00cadd7e.png)


### Node system
Each tile contains 5x5 grid of nodes. 
- node types
- neighbouring nodes
Nodes can store references to their neighbouring nodes. Although, the 
This system serves important role guiding the orb drag directions through the maze. 
Also allows the light trail to be recorded.

![image](https://user-images.githubusercontent.com/12778446/151225156-067b6208-d06c-46b5-a119-fe730d132c03.png)


### Maze configuration

#### Tile cofiguration
Each wall has its own grid that stores the references to the tiles on that wall. This grid is send to the front end
which renders tile meshes to proper positions on the wall.

![image](https://user-images.githubusercontent.com/12778446/151221077-79e0d717-740d-4324-8f26-b284b8e36dc0.png)

#### Node configuration on tiles
Generate the nodes resembling paths of the maze from the initial level configuration. Each tile is a 5x5 matrix of nodes. These nodes are configurated 
accodingly to the numbers from the configarion matrix. Each number resemble different type of path piece.

![image](https://user-images.githubusercontent.com/12778446/151223725-9389d5a1-4749-425b-ac9f-c463eefad031.png)

#### Create Node system 
After the tiles and its properties are setup _create node system_ method is called on each wall. Each wall
calls similar method on its tiles. Called tile method updates the nodes on the tile. These nodes keep track of their
neighbouring nodes. This system serves important role guiding the orb drag directions through the maze. 
Also allows the light trail to be recorded.

![image](https://user-images.githubusercontent.com/12778446/151225156-067b6208-d06c-46b5-a119-fe730d132c03.png)

### Updating the grid
- update the neighbour grid after you move a tile

![BackendTileSystem](https://user-images.githubusercontent.com/12778446/151219390-a904cb84-26f7-4c03-9dab-02075e1ea7fc.gif)
