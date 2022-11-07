# Manage states

Now we can hook everything up. When a player pushes a key, we swap states.

We'll modify the `AdventureGame` class.

```csharp
using System;
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.UI;


public class AdventureGame : MonoBehaviour
{

    [SerializeField] Text textComponent;
    [SerializeField] State startingState;
    State state;

    // Start is called before the first frame update
    void Start()
    {
        state = startingState;
        textComponent.text = state.GetStateStory();
    }

    // Update is called once per frame
    void Update()
    {
        ManageState();
    }

    private void ManageState()
    {
        var nextStates = state.GetNextStates();

        if(Input.GetKeyDown(KeyCode.Alpha1))
        {
            state = nextStates[0];
        } else if (Input.GetKeyDown(KeyCode.Alpha2))
        {
            state = nextStates[1];
        }
        else if (Input.GetKeyDown(KeyCode.Alpha3))
        {
            state = nextStates[2];
        }


        textComponent.text = state.GetStateStory();

    }
}
```