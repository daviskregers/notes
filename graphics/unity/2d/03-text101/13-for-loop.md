# For loop

We are going to fix a bug that is in the state machine, by adding a for loop. Basically, currently we are listening to inputs 1-3 even if there are 1-2 next states. When the state does not exist, it throws an error.

We fix this by modifying the `ManageState` method in `AdventureGame` class.

```csharp
private void ManageState()
{
    var nextStates = state.GetNextStates();

    for (int i = 0; i < nextStates.Length; i++)
    {

        if (Input.GetKeyDown(KeyCode.Alpha1 + i))
        {
            state = nextStates[i];
        }

    }
    textComponent.text = state.GetStateStory();
}
```