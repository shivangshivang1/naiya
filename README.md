# 3D Maze Game in Unity

This is a simple 3D maze game built using Unity and C#. The game features a procedurally generated maze, a player character that can navigate the maze, and a goal to reach the maze exit.

## Features

- **Procedural Maze Generation**: The maze layout is generated in a grid pattern using customizable dimensions.
- **Player Movement**: Control the player with arrow keys or WASD.
- **Camera Follow**: The camera follows the player as they move through the maze.
- **Win Condition**: Reach the exit to complete the maze!

## Setup Instructions

1. **Clone this Repository** or download the project files.
2. **Open in Unity**:
   - Open Unity Hub and select the version of Unity you’re using.
   - Open this project in Unity to start working with the files.

## Project Structure

- **MazeGenerator.cs**: A script to create a simple maze layout in Unity.
- **PlayerMovement.cs**: Handles player movement based on keyboard input.
- **CameraFollow.cs**: Makes the camera follow the player with an offset.
- **MazeExit.cs**: Detects when the player reaches the maze exit to trigger a win condition.

## How to Play

1. **Start the Game**: Press the Play button in Unity.
2. **Navigate the Maze**:
   - Use the arrow keys or WASD keys to move the player.
3. **Win the Game**: Reach the exit point of the maze.

## Scripts

### MazeGenerator.cs

This script generates a basic grid-based maze layout.

```csharp
using UnityEngine;

public class MazeGenerator : MonoBehaviour
{
    public int width = 10;
    public int height = 10;
    public GameObject wallPrefab;
    private bool[,] grid;

    void Start()
    {
        GenerateMaze();
    }

    void GenerateMaze()
    {
        grid = new bool[width, height];
        
        for (int x = 0; x < width; x++)
        {
            for (int z = 0; z < height; z++)
            {
                if (x % 2 == 0 || z % 2 == 0)
                {
                    var wall = Instantiate(wallPrefab, new Vector3(x, 0, z), Quaternion.identity);
                    wall.transform.parent = transform;
                }
            }
        }
    }
}
