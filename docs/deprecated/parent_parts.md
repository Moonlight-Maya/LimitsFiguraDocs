## Parent Parts

One thing you might want to do in a Figura avatar is to have certain blockbench parts follow your vanilla character's body movement. To do this, Figura provides the system of **Parent Parts**. When a part has a parent type, that part will copy the rotation and movement of the vanilla part it's parented to.

Let's turn that previous model into an example. We'll have our cube rotate like the player's head! In Figura, the most common way to give a part a parent type is to change its name. In order for a part to be parented to the head, it needs to start with `Head` or `HEAD`.
Naming your part `Head`, `HEAD_SUNGLASSES`, or `Headphones` will all parent the part to the head, because these names all **start with** one of those prefixes.

## Making a Head Parent Part

In order to see this in action in-game, we'll need to change a few things around in Blockbench. Keywords can only be applied to **groups**, not just regular cubes. We need to add a new group to our outliner. Click the `Add Group` button to add a group, set its name to "Head" (without the quotes), and drag the cube inside the group. Save the model and return to the game, and you should see the cube rotating around as you move your head!

Some of you will notice something strange here - the cube isn't just rotating, it's also moving around weirdly, ending up in front and behind you instead of staying above your head! What's happening is related to the idea of the **Pivot Point**. Each part has a pivot point, which is the location where it rotates around. If you select your group named Head, and check its pivot point, you'll see it's at 0,0,0. It's on the floor! Move the pivot point of the group to be in the bottom middle of the cube, and try again. You should see that the cube stays in place as you rotate your head - it rotates around the pivot point.

There are many other keywords in Figura to choose from. The six basic ones related to parts of your model are: 

* `Head` or `HEAD`
* `Body` or `BODY`
* `LeftLeg` or `LEFT_LEG`
* `RightLeg` or `RIGHT_LEG`
* `LeftArm` or `LEFT_ARM`
* `RightArm` or `RIGHT_ARM`

Keywords are a powerful tool in your arsenal for creating avatars, but what *really* makes Figura special is what's coming up next: [Scripting with Lua](p4_lua_intro.md)!
