## Intro to Lua Scripting for Figura

While making an avatar with parent parts is a great first step, if you want to really take your avatar to the next level you'll need to use a script! Scripting is by far the most powerful part of Figura, but unfortunately it can also be one of the most tricky to get into. If you already know a programming language, you'll have a great head start on this section, but this tutorial doesn't assume you have any such prior knowledge.

In order to begin, we first have to create a file to hold our script. Scripts are written in `.lua` files. By default, Figura will seek out all `.lua` files in your avatar folder and run them when your avatar loads. Create a new text file in the same folder as `avatar.json`, and make sure it has a `.lua` file extension. Many people like to go with names like `script.lua` or `main.lua`.

[Files](p4_ScriptLua.png)

## Making the Vanilla Player Invisible

Inside this file is where we'll start writing our code. Let's start with something that's useful and will let us see an effect right away: making the vanilla player invisible.
Doing this requires only one line of code. In your file, type the following:

```lua
vanilla_model.PLAYER:setVisible(false)
```

Save the file, and return to the game. If you followed all the steps correctly, you shouldn't see yourself anymore!

[Invisible](p4_Invisible.png)

Because we specifically disabled the `PLAYER` part of the vanilla model, things like armor and elytra will still appear as usual. If you want to disable **everything**, instead use this code:

```lua
vanilla_model.ALL:setVisible(false)
```

Want to just disable your head and left leg? You can do that too! Use these two lines of code instead:

```lua
vanilla_model.HEAD:setVisible(false)
vanilla_model.LEFT_LEG:setVisible(false)
```


