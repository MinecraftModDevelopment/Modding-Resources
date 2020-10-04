# Live class reloading
You can use live class reloading to avoid having to restart the game for code changes to be applied. This is generally done by running the game with a debugger. Changes you make will be applied to the running game once you save the game. 

Please keep in mind, class reloading does have some limits to it. You can not create new classes, new fields, or new methods. You also can not change the signature of a field or method. Also keep in mind that code changes are not retroactively applied. For example if you change something in your `preInit` method, changes to that method will not be applied because it is already finished executing. The ideal example of live reloading is something like rendering, where the render method is being called every frame.

Intellij: Click the button left to the launch configurations (Build Project). You will be prompted to reload classes. Accept.

Eclipse: Your IDE is likely configured to build automatically, all you have to do is save. If not, select Project -> Build All.

For live resource reloading, build your project first, then press F3+T in-game.