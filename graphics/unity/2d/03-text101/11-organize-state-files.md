# Organize state files

We are now going to delete the previously created `Room 1` and `Room 2`. Rename the `StartingState` to `A1. Ouside Hangar`.

Create folders `States` and `Scripts`. Organize files into them.

Then into `States` folder we are going to create 3 folders - `Game Over`, `Hangar`, `Intro`. We move the `A1. Outside Hangar` into the `Hangar` directory.

Then in `Intro` folder, we create a new state `A0. Introduction`. Add text to it and update the `Game` object to reference it as the starting state. Then we add the `A1. Outside Hangar` as a next state to it.

We add `X1. Game over` into `Game over` directory. Add text. Add `A1. Outside Hangar` and `A0. Introduction` as nextState.

Now we go to Hangar directory and click `ctrl+d` to duplicate the `A1. Outside Hangar` file up to `A11`. Then we put all the states and texts together.

