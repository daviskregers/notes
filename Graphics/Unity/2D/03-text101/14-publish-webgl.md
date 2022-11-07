# Publish game via WebGL

If we change our aspect ratio in the `Game` window to `16:9`, we'll see that the camera is smaller than the game menu.

We can change canvas `UI Scale Mode` from `Constant Pixel Size` to `Scale With Screen Size`. And then changing the `Reference resolution` to `1920x1080`.

This will make it so that everything will fit no matter what screen resolution player has.

We can no go to `File -> Build Settings`, under it we can choose `WebGL`. If that does not show, you will need to add module to Unity. Click on `Build And Run`, save it somewhere.

You can publish it in `sharemygame.com` and link it somewhere. Be ready for feedback.