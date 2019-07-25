# Calculate guess variable

Now we are recalculating introducting the `guess` variable, showing it and recalculating based on player's input.

```csharp
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class NumberWizard : MonoBehaviour
{
    int min = 1;
    int max = 1000;
    int guess = 500;

    // Start is called before the first frame update
    void Start()
    {
        Debug.Log("Welcome to number wizard!");
        Debug.Log("Pick a number, don't tell me what it is.");
        Debug.Log("The highest number you can pick is " + max);
        Debug.Log("The lowest number you can pick is " + min);

        Debug.Log("Tell me if your number is higher or lower than " + guess);
        Debug.Log("Push Up = higher, Push down = lower, Push enter = Correct");

        guess++;

    }

    // Update is called once per frame
    void Update()
    {

        if ( Input.GetKeyDown(KeyCode.UpArrow) )
        {
            min = guess;
            guess = (min + max) / 2;

            Debug.Log("Higher it is.");
            Debug.Log("Tell me if your number is higher or lower than " + guess);
        }

        else if (Input.GetKeyDown(KeyCode.DownArrow))
        {
            max = guess;
            guess = (min + max) / 2;

            Debug.Log("Lower it is.");
            Debug.Log("Tell me if your number is higher or lower than " + guess);
        }

        else if (Input.GetKeyDown(KeyCode.Return))
        {
            Debug.Log("Correct!");
        }

    }
}
```

![](../../../../images/2019-07-25-12-00-15.png)