# Your first code

In this section we are going to make a Hello World application in [[Unity]] to check that everything is set up properly.

## How Unity and Visual Studio Relate

The unity is the game engine that describes what everything is and how it goes together. All the code that does this is being written in [[Visual Studio]], which is an [[IDE]]. 

## Setup

We can go to `Projects` tab in [[unity]].

![](../../../../images/2019-07-25-10-16-26.png)

And create a new project with a 2D template.

![](../../../../images/2019-07-25-10-18-44.png)

Once that's done, you will have a unity project opened.

![](../../../../images/2019-07-25-10-22-02.png)

Now in the assets area, create a new [[C# script]], name it HelloWorld.

![](../../../../images/2019-07-25-10-23-26.png)

Now, when you double click on the script, it will open up [[Visual Studio]].

![](../../../../images/2019-07-25-10-27-21.png)

Now we can modify the script:

```csharp
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class HelloWorld : MonoBehaviour
{
    // Start is called before the first frame update
    void Start()
    {
        print("Hello World!");
    }

    // Update is called once per frame
    void Update()
    {
        
    }
}
```

Now we need to attach the script to an object, we can add it to the [[Main Camera object]], we have. Simply drag the script over it.

![](../../../../images/2019-07-25-10-31-08.png)

Now when we open up console and click on the `Play` button, the `Hello World` script executes.

![](../../../../images/2019-07-25-10-32-40.png)