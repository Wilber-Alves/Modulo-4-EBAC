# Modulo-4-EBAC

Scene created for exercise of module-4-EBAC. A objec called AnimalSignSystem (class = ScriptModulo4EBAC) was added to the scene of a maze game. The class containing the ability to recognize 3 different key inputs (Z, X and C); Each recognized key prints the name of a different animal (Bird, Pig and Cat), using switch cases and enums. More details can be seen in the General project summary comments tab and in the other code comments. Real Materials Vol.0 - free samples (Lex4art) from the Asset Store were used and installed with Package Manager. Some prefabs and meshes used in the project were obtained from the Asset Store (mesh of the 'Power Orbs' - Sphere decorative_PHYS from Lex4art). The other prefabs (coins, door, key, level design, and animal symbols) were made by me using primitives available in Unity and models made in Blender 4.4.


* The Maze Game started!
* Collect coins, power orbs and find the exit of the maze.
* Basic Moves - Use arrow keys to rotate the Maze (ground object) and A/S to change speed and guide the orb to the end.
* CHALLENGE: THERE ARE 3 ANIMAL SIGNS ON TABLETS HIDDEN IN THE MAZE, FIND THEM AND UNCOVER USEFUL SECRETS.

Code

using Mono.Cecil;
using System.Reflection;
using System.Runtime.CompilerServices;
using UnityEngine;
using UnityEngine.InputSystem;
using static ScriptModulo4EBAC;
using static UnityEngine.InputManagerEntry;
using static UnityEngine.UI.GridLayoutGroup;

public class ScriptModulo4EBAC : MonoBehaviour
{
    #region General project summary
    // * This script is designed to handle the interaction with animal signs in a maze game; 
    // * It uses a switch-case structure to determine which animal sign is being interacted with; 
    // * and calls the corresponding method to display information about that animal sign; 
    // * The animal signs are Bird, Pig, and Cat, each with its own unique message; 
    // * The script also includes methods to handle key inputs for reading the animal signs; 
    // * The messages provide tips and secrets related to the maze game that will be useful for gameplay; 
    #endregion

    #region Variables
    public enum AnimalSigns
    {
        None, // Added None just to handle default case. The 3 animal signs are Bird, Pig, and Cat.
        Bird,
        Pig,
        Cat

    }
    public AnimalSigns animalSign; // This variable will be used to determine which animal sign is being interacted with.
    #endregion

    #region Methods

    #region Start and Update Methods
    // Start is called once before the first execution of Update after the MonoBehaviour is created
    void Start()

    {
        print("The Maze Game started! Collect coins, power orbs and find the exit of the maze. " +
            "CHALLENGE: THERE ARE 3 ANIMAL SIGNS ON TABLETS HIDDEN IN THE LABYRINTH, FIND THEM AND UNCOVER USEFUL SECRETS. ");
    }
    // Update is called once per frame

    private void Update()
    {
        CheckSwitchCase(animalSign); // This method checks the current animal sign and calls the corresponding method to display its information.
        CheckKeys(); // This method checks for key inputs to read the animal signs.
    }
    #endregion

    #region CheckSwitchCase and CheckKeys Methods
    private void CheckSwitchCase(AnimalSigns a) // This method uses a switch-case structure to determine which animal sign is being interacted with.
    {
        switch (a) 
        {
            case AnimalSigns.Bird:
                OnReadBird();
                break;
            case AnimalSigns.Pig:
                OnReadPig();
                break;
            case AnimalSigns.Cat:
                OnReadCat();
                break;
            default:
                OnReadNone();
                break;
        }
    }
    private void CheckKeys() // This method checks for key inputs to read the animal signs.
    {
        if (Input.GetKeyDown(KeyCode.Z))
        {
            CheckSwitchCase(AnimalSigns.Bird);
        }
        else if (Input.GetKeyDown(KeyCode.X))
        {
            CheckSwitchCase (AnimalSigns.Pig);
        }
        else if (Input.GetKeyDown(KeyCode.C))
        {
            CheckSwitchCase(AnimalSigns.Cat);
        }
    }
    #endregion

    #region OnRead Methods for Animal Signs present in the CheckSwitchCase and CheckKeys methods.
    //they contains the names of the printed animals and the texts of the secrets of the tablets, corresponding to the keys pressed for each Animal Sign.
    private void OnReadBird()
    { 
        Debug.Log("BIRD - 'The Silver Sign' - First Tip: Press the spacebar to jump. " +
            "Use this ability to climb ladders and collect items. " +
            "NOTE: Jumping and moving around the maze do not occur simultaneously. " +
            "Jump first and move the maze afterwards."); // This is the first tip for the Bird sign pressing Z key.
    }
    private void OnReadPig()
    {
        Debug.Log("PIG - 'The Copper Sign' - Second Tip: The second floor has invisible walls, so watch out for holes and traps." +
            "Climb the green stairs." + "Collect the Copper Key to open the maze gate. "); // This is the second tip for the Pig sign pressing X key.
    }
    private void OnReadCat()
    { 
        Debug.Log("CAT - 'The Gold Sign' - Third Tip: Boulders are passive enemies; they won't hurt you, but they will hinder your movement. " +
            "Use the maze's directional buttons to push the boulders; " +
            "Jumping afterward will make them roll more easily, clearing the way. "); // This is the third tip for the Cat sign pressing C key.
    }
    private void OnReadNone()
    { 
        Debug.Log(""); // This is the default case when no animal sign is selected, it does nothing.
    }
    #endregion

    #endregion
}
