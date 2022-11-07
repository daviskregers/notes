# Introducting variables

Variables are like boxes:
- They are of a particular `type`.
- Each variable has a name.
- Each variable contains data.

```csharp
int hitPoints = 20;
float speed = 3.8f;
bool isAlive = true;
string name = "Rick";
```

We can use modify the previously made script to use variables for the min and max value.

```csharp
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class NumberWizard : MonoBehaviour
{
    int min = 1;
    int max = 1000;

    // Start is called before the first frame update
    void Start()
    {
        Debug.Log("Welcome to number wizard!");
        Debug.Log("Pick a number, don't tell me what it is.");
        Debug.Log("The highest number you can pick is " + max);
        Debug.Log("The lowest number you can pick is " + min);
    }

    // Update is called once per frame
    void Update()
    {
        
    }
}
```
