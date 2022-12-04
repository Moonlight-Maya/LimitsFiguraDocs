## Particle Effects

Particle effects are a fun way to add some action and movement to your avatar, and with the right usage they can look really spectacular as well. Let's see how Figura lets you add particles to your avatar. The general code to summon a particle is as follows:

```lua
particles:newParticle("particle name"):<Some modifiers for the particle>
```

Here's an example of some code that will summon a flame particle at your player's feet every tick, moving in the positive x direction.

```lua
function events.tick()
    local position = player:getPos()
	particles:newParticle("flame"):pos(position):velocity(0.33, 0, 0)
end
```

Run this code to see fire particles appearing at your feet, and travelling towards the positive X direction for a short distance before disappearing. What's happening here, exactly?

1. We put this whole thing inside our `function events.tick()`, as we learned before, to make a particle be spawned each tick.
2. We use the built in Figura variable `player`, and use the function `:getPos()` on the player, to get the player's position in the X, Y, and Z coordinates. Then we store that position in a variable, called "position".
3. Follow the format above, beginning with `particles:newParticle("flame")`, because we want to summon a "flame" particle.
4. Now we add our first modifier, using `:pos()`. The "pos" modifier will set the position of the particle. We want this particle to be at the position of the player, so we send in our position to the function.
5. Finally, we wanted our particle to move in the x direction, so we use the "velocity" modfifier. This modifier needs 3 values, the X, Y, and Z velocity, and we set the X velocity to 0.33 and left the others at 0.

## Particle Explosion through the Action Wheel

Now, we'll use a bit more math as well as the introduction of some of Lua's control structures, to cause a "poof" of particles when we make the die disappear. From the last section, we already have a function that's called when the die disappears: `pings.toggleCube`. So if we want something to happen when the cube disappears, we'll want to add some extra code there.

Let's do a quick once-over of what we want to happen in this function. Then, I'll show to code that, and explain how the code does the things we want.
1. We want all of this stuff to happen when we make the die *disappear*. When it appears, we don't need to do anything.
2. We want to summon, say, 200 particles when the cube disappears.
3. Each particle should fly off in a different direction, to make it really look like an explosion.

How do we translate something like this into code? The first step can be solved using an **if-statement**. An if-statement is a concept from many programming languages that allows certain code to only happen sometimes. Specifically, when a certain condition is met. Let's add an empty `if` statement to our function that will activate only when we turn the cube invisible.

```lua
function pings.toggleCube(isToggled)
	models.die.cube:setVisible(isToggled)
	if isToggled == false then

	end
end
```

An `if` statement is written with the word `if`, then some expression, followed by the word `then`. We can place some code inside, and once we're done, we finish the `if` statement with the word `end`. Everything between `then` and `end` will now only happen when we turn the cube off, not when we turn it on. Now, step 2:

```lua
function pings.toggleCube(isToggled)
	models.die.cube:setVisible(isToggled)
	if isToggled == false then
		for _ = 1,200 do

		end
	end
end
```

Now, we've introduced a `for` loop. This one is a bit more in-depth, but all you need to understand from this code block is that everything between the `do` and the `end` will happen 200 times. And now the third part: summoning a particle that moves in a random direction.

```lua
function pings.toggleCube(isToggled)
	models.die.cube:setVisible(isToggled)
	if isToggled == false then
		for _ = 1,200 do
			local position = player:getPos()
			position.y = position.y + 2.5
			local xSpeed = math.random() * 2 - 1
			local ySpeed = math.random() * 2 - 1
			local zSpeed = math.random() * 2 - 1
			particles:newParticle("poof"):pos(position):velocity(xSpeed, ySpeed, zSpeed)
		end
	end
end
```

1. Again, we get the player's position using `player:getPos()`. This refers to the position of the player's feet, but we want the particles to spawn at the die! That's why we move the `y` of the position up by 2.5 blocks, making the particles spawn where the die is.
2. Next, we calculate 3 random numbers. `math.random()` is a Lua function that gives back a random number from 0 to 1 each time you run it. We multiply by 2, giving us a random number from 0 to 2, then subtract 1, giving us a random number from -1 to 1. Since the number could be positive or negative, the particles can go in any direction.
3. Finally, we use these values we've calculated in our modifiers for the particle. I chose to use the Minecraft particle "poof" for this, but you can replace that with any particle you want!

And there we have it! We've changed `pings.toggleCube` to also cause an explosion of "poof" particles when we disable the cube.

## Playing a Sound

Playing a vanilla sound through script is done using the `sounds:playSound` command. For example, the following code will play the "UI Toast In" sound, at the position of the player:

```lua
local position = player:getPos()
sounds:playSound("minecraft:ui.toast.in", position)
```

The first value to send into `playSound` is the name of the sound. You can look for sound names using the vanilla command `/playsound`, and the game will auto-complete them for you. The name you send into the Figura function is the same as the one in that command.
The second value is the location where you want the sound to play. Just like the particle from before, we want to play this sound at the position of the player, so we grab their position in the same way and send it into `sounds:playSound`.
Finally, let's say that we want this sound to be played every time we make the cube visible or invisible. For that, all we have to do is add this code to our `pings.toggleCube` function like we did with the particle:

```lua
function pings.toggleCube(isToggled)
	models.die.cube:setVisible(isToggled)
	if isToggled == false then
		for _ = 1,200 do
			local position = player:getPos()
			position.y = position.y + 2.5
			local xSpeed = math.random() * 2 - 1
			local ySpeed = math.random() * 2 - 1
			local zSpeed = math.random() * 2 - 1
			particles:newParticle("poof"):pos(position):velocity(xSpeed, ySpeed, zSpeed)
		end
	end
	local position = player:getPos()
	sounds:playSound("minecraft:ui.toast.in", position)
end
```

Note that we didn't put it inside of the `if isToggled == false then ... end` block. This is because we wanted the sound to happen when we turn the cube visible **or** invisible, whereas with the particles, we wanted that to only happen when turning it invisible.

At last, we've come to the (current) end of the introductory guide to creating Figura avatars! There is so, *so* much more to Figura that we haven't had the chance to cover in this brief introduction, but hopefully this will have given you a solid foundation in the art of avatar creation. Of course, if you wish to learn more, feel free to join the [Discord server](https://discord.com/invite/ekHGHcH8Af)! There are plenty of people there willing to help you master the tools Figura provides, and even more who will be excited to see what amazing stuff you can create with the mod. Thank you for following along, and I hope to see you there!

The final tutorial cube avatar is available here:

<a href="../FinishedTutorialCube.zip" download>Finished Tutorial Cube Download</a>
