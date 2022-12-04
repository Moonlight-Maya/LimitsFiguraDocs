## Using the Action Wheel to Control the Cube

> IMPORTANT: If you're just here to skim, copy/paste, and leave, ***make sure you read all the way to the bottom of the page!*** There's a common trap that people tend to fall into if they don't realize a key detail, and then they get confused about why the code isn't working as they expect it to.

One thing you may want to do is trigger something to happen whenever you desire. One way that Figura offers to achieve this is through use of the **Action Wheel**. The action wheel can be brought up by pressing **B** by default, though the key can of course be rebound through the settings. If you do this right now, though, you'll find a popup telling you there's no active page. We have to write some code to create a page and activate it. Here's the code:

```lua
local myPage = action_wheel:newPage()
action_wheel:setPage(myPage)
```

1. `action_wheel` is yet another object provided by Figura. We "call" `:newPage()` on the wheel, which generates a page. Then, we store the page in a variable called "myPage".
2. We get the action wheel again, and call `:setPage` on it, sending in that same page. This will set the currently "active" page to this new page we just created.

Now if you open the action wheel in-game with B, you'll find that the message about there being no active wheel has disappeared. However, your wheel doesn't actually have anything in it yet. For this guide, we're going to add an action to the page that will let us make the cube switch between visible and invisible by clicking on it. Here's one way we can do that:

```lua
local myPage = action_wheel:newPage()
local myAction = myPage:newAction()
function myFunction(isToggled)
    models.die.cube:setVisible(isToggled)
end
myAction:onToggle(myFunction)
myAction:toggled(true)
action_wheel:setPage(myPage)
```

1. We have the same code from before, creating a new page and storing it in a variable.
2. On this same page, we call `:newAction()`. This creates a new "action" on that page, and we store that action in a variable "myAction".
3. Next, we again create a function. You can think of a function as a container for some code. This function has one parameter, which we choose to call isToggled. A "parameter" is a value that gets "sent in" to a function when you activate it.
4. Inside the function, we get the cube like before, using `models.die.cube`. Then we use a different function, `:setVisible`. If you send in `true`, then the part becomes visible, and if you send in `false`, then the part becomes invisible. We send in `isToggled`.
5. We are setting this action to have a "Toggle" function, and we use "myFunction" as the function. Since this action is in "toggle" mode, the action can be set to either on or off by clicking it. When we set it to on, `isToggled` will have the value `true`, and when we turn it off, `isToggled` will have the value `false`. Therefore, when we turn this action on, our cube will be made visible, and when we turn it off, the cube will be made invisible.
6. Since our cube is visible at the very beginning, we want our toggle to start in the "on" position. To do this, we can use `:toggled` on the action, sending in `true` to set it to toggled.
7. Finally, we set the active page to be our page, as before.

Return to the game and give it a try! You'll see that if you open the action wheel and click on the right side, the cube will switch between being visible and invisible. Next up, we're going to make our action a bit more advanced, and allow us to change the speed of the spinning as well. This next upcoming code block will organize and show off everything we've made so far!

```lua
local speed = 5
function events.render(delta)
	local time = world.getTime() + delta
	models.die.cube:setRot(0, time * speed, 0)
end

function toggleCube(isToggled)
	models.die.cube:setVisible(isToggled)
end

function changeCubeSpeed(scrollAmount)
	speed = speed + scrollAmount
end

local myPage = action_wheel:newPage()
local myAction = myPage:newAction()
myAction:onToggle(toggleCube)
myAction:toggled(true)
myAction:onScroll(changeCubeSpeed)
action_wheel:setPage(myPage)
```

That's a lot of changes! Let's look through these areas step by step and see what's different.

<u>The spinning code</u><br />
If you remember, our `events.render` function is what causes our cube to spin. All we've changed here is that instead of saying `time * 5` for the rotation, we instead say `time * speed`, and make `local speed` equal to `5`. We've taken that "5" out and stored it in its own variable, so now if we change the `speed` variable, it will change how fast our cube rotates, too.

<u>The toggleCube function</u><br />
This function is actually the same as `myFunction` from before. We just changed its name, to be a bit more descriptive, and also moved it up above a bit, so that it's separate from the rest of the code. It was a bit tricky to read when it was lodged in there with the rest of the action wheel things, so we've separated it out on its own to make it stand out more.

<u>New function: changeCubeSpeed</u><br />
We've added in a new function, `changeCubeSpeed`, which we're going to call (or activate) whenever we use the scroll wheel while hovering over our action. With scroll actions on the action wheel, we send in a number for how far the mouse wheel scrolled. If you scroll up, it sends in `1`, and if you scroll down, it sends in `-1`. Inside this function, we *change* the speed variable, setting it to be equal to its current value, plus or minus 1. If you scroll up, then `speed` will become `speed + 1`, increasing. If you scroll down, `speed` will become `speed - 1`, decreasing.

<u>Connecting these functions to the action wheel</u><br />
Finally, we create our action wheel the same way as before. The only change is that we add a scroll function to our action, using `myAction:onScroll`, and we use `changeCubeSpeed` as the function for it. So now, every time we scroll on the action, the code inside `changeCubeSpeed` will be activated.

Go on and try it out! Clicking will still work the same way as before, turning the cube visible and invisible, but now you can also scroll, affecting the speed of the rotation. There are many, many more things you can do with the action wheel, like giving each action items, names, and colors, but this tutorial is just for getting a solid foundation in how to use it to activate tasks, like changing visibility or changing the rotation speed.

## Synchronizing in Multiplayer Using Pings

There's one major pitfall that people tend to fall into when dealing with the action wheel, which is **syncing**. In Figura, your code runs on multiple people's computers at the same time, which is how your friends can see your cube spinning in multiplayer. However, other people watching you *cannot* see your action wheel running. If you just activate an action wheel function like we've shown so far, *it won't happen on other people's screens when they look at you!*

Thankfully, Figura offers an easy way to get around this problem using a built in API called `pings`. It used to be a bit more complicated, but in modern versions, a function can be synchronized as easily as adding `pings.` before its function name (at least in most cases). Change your action wheel function names to begin with `pings.`, like so:

```lua
function pings.toggleCube(isToggled)
........
function pings.changeCubeSpeed(scrollAmount)
........
myAction:onToggle(pings.toggleCube)
........
myAction:onScroll(pings.changeCubeSpeed)
```

If you do this, you shouldn't notice any differences in single player. But in multiplayer, other people will now be able to see when you change your cube's visibility or speed.
