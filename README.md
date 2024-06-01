# A Simple Adventurer Game Using Behaviour Trees

This project designs a game of an adventurer getting chased by a haunted forest pumpkin. The adventurer must find its way to the magic mushrooms to be saved from the forest spirit that is haunting the pumpkin. 

The levels are designed using Cellular automata with varying degrees of forest density.

The AI behaviour has mostly been modelled using behaviour trees and simple movements like seek goals and flee enemy.

## Run
The main scene can be run from Assests/Main.unity

To generate a new level, left click the mouse button in the game screen and the players get a fresh start.

## Libraries Used
This project directly uses NPBehave to build the behaviour tree which controls the adventurer agent.
I have also used MovementAI for implementing flee and seek behaviour for the agents.

## Scripts
GameManager.cs: This script controls the generation of levels & is responsible to spawn agents and the goal (magic mushrooms) and maintain the data on a shared blackboad. This shared blackboard can be access by agents and in their behaviour trees.

MapGenerator.cs: The level is generated using cellular automata and smoothed over to get more connected and interesting cave regions on the map. The disconnected regions are then connected through passages to form a connected level that can be navigated by either players. The walls and the path are stored as 1 and 0 respectively in a matrix 'map'.

MeshGenerator.cs: Using the generated map, I used marching squares (referring to Sebastian Lague's work) to build a mesh so the agents can be stopped from running through them.

AdventurerController.cs: This script manages the adventurer's behaviour and maintains its data. This agent mainly tries to reach the goal using the A star algorithm, if it doesn't have too many walls in between, otherwise it wanders the maze looking for the goal. The agent also flees the haunted pumpkin if it gets too close to prevent being captured.

BadPlayerController.cs: This script controls the haunted pumpkin and it tries to find a way to get to the player using the A star algorithm, if it can find a way through the maze to it. If it can't find the adventurer then it simply wanders the maze hoping to spot it.

## Demo
A couple of short video of this game can be found here: https://drive.google.com/drive/folders/1gx32hNQVEmPMXYu-_N4ojpDzGCmRSIEK?usp=sharing
