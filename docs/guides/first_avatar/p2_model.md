## Creating a Model

Figura uses the program [Blockbench](https://www.blockbench.net/) for model creation. If you've been following along the guide so far, you [should already have access](../mod_setup.md) to it. There are many amazing guides out there for using Blockbench already, so it's outside the scope of this guide for Figura to discuss the topic. If you don't have any prior experience with Blockbench and want to learn, you can look around for some tutorials online, visit the [Blockbench Discord](http://discord.blockbench.net), or just play around in it on your own. The program is not exceedingly complicated to use, and with a bit of experimentation you'll be making models in no time.

> IMPORTANT: Many video guides for Blockbench that exist on the internet are designed for creating models in the CEM (Custom Entity Models) format, or for creating item models for resource packs. However, FIGURA DOES NOT USE THOSE FORMATS! Figura models use the "Generic Model" type, and do not need any special kind of folder structure to function. These videos are still a good resource for learning the basics of Blockbench, like manipulating cubes and groups, but they are not a perfect step-by-step guide for Figura specifically. Use them simply to gain general information about Blockbench.

## Adding the Model to Your Avatar

Adding a model to an avatar is as simple as placing the `.bbmodel` file into the same folder as your `avatar.json` file. Unlike `avatar.json`, your `<NAME>.bbmodel` file can have any name you like, as long as it ends in the `.bbmodel` file extension. If you enter into the game now, and select your avatar on the left from the wardrobe, you should see your model appear over your player.

> Troubleshooting: I don't see the model appear when I click my avatar in the wardrobe!

> > * Make sure your model file ends in the `.bbmodel` file extension. If it doesn't, Figura won't detect it.

> > * Make sure that your model has textures. In blockbench, models without textures are given a placeholder, but in Figura there is no placeholder and these cubes will simply not show up.

> > * If your model is really tiny, like only a single 1 pixel cube, you might not be able to see it because it could be inside of your player. Try making the model a bit larger to ensure it's not hidden inside your vanilla player model.

## Texture Loading

Figura will search for textures inside the `.bbmodel` file itself, and take the data from there. However, if you have a texture of the same name **outside** of the `.bbmodel`, then Figura will use that texture instead. This is useful for people who don't like the paint tool in Blockbench and prefer to use a different image editor.

The other interesting thing about Figura texture loading is the "emissive" texture feature. If you have two textures with the same name, except one has an `_e` appended at the end, then Figura will treat the second texture as an "emissive" texture, meaning it will use that to make the avatar glow the same way enderman and spider eyes do.

## Keywords

Using certain special words, called "Keywords", at the **start** of a Blockbench group's name will confer additional effects onto that model part in game. Most keywords can be generally split into two types: keywords that cause a blockbench group to act like something from vanilla, and keywords that will cause vanilla things to move like the blockbench group. These two types are often described using the terms "Parent Type" and "Pivot Type" respectively. There are also some special keywords, which are explained in the table below.

| Keyword | Description |
|---|---|
| <u>**Parent Type Keywords**</u> | --- |
| `Head`, `HEAD` | Makes the part act like the vanilla player's head. |
| `Body`, `BODY` | Makes the part act like the vanilla player's torso. |
| `LeftArm`, `LEFT_ARM` | Makes the part act like the vanilla player's left arm. |
| `RightArm`, `RIGHT_ARM` | Makes the part act like the vanilla player's right arm. |
| `LeftLeg`, `LEFT_LEG` | Makes the part act like the vanilla player's left leg. |
| `RightLeg`, `RIGHT_LEG` | Makes the part act like the vanilla player's right leg. |
| `LeftElytra`, `LEFT_ELYTRA`, <br />`LeftElytron`,  `LEFT_ELYTRON` | Makes the part act like the elytra's left wing. |
| `RightElytra`, `RIGHT_ELYTRA`, <br />`RightElytron`, `RIGHT_ELYTRON` | Makes the part act like the elytra's right wing. |
| `Cape`, `CAPE` | Makes the part act almost like the vanilla cape.  (It's slightly<br /> off because Minecraft's cape rendering code is annoying.) |
| <u>**Pivot Type Keywords**</u> | --- |
| `LeftItemPivot`, `LEFT_ITEM_PIVOT` | Causes your player's left item to appear at this part. |
| `RightItemPivot`, `RIGHT_ITEM_PIVOT` | Causes your player's right item to appear at this part. |
| `LeftSpyglassPivot`, `LEFT_SPYGLASS_PIVOT` | Causes your player's spyglass to appear at this part<br />  when held in the left hand. |
| `RightSpyglassPivot`, `RIGHT_SPYGLASS_PIVOT` | Causes your player's spyglass to appear at this part<br />  when held in the right hand. |
| `HelmetItemPivot`, `HELMET_ITEM_PIVOT` | Causes a worn helmet item (like a pumpkin or other block <br /> on the head, NOT the armor model) to appear at this part. |
| `LeftParrotPivot`, `LEFT_PARROT_PIVOT` | Causes your player's left shoulder parrot to appear at this<br /> blockbench part. |
| `RightParrotPivot`, `RIGHT_PARROT_PIVOT` | Causes your player's right shoulder parrot to appear at this<br /> blockbench part. |
| <u>**Special Keywords**</u> | --- |
| `World`, `WORLD` | Causes this blockbench part to appear in the world itself,<br />  and not attached to your player. It will likely need to be <br /> moved through scripting in order to set its <br />position to be near your player, instead of <br /> near 0,0,0 in the world. |
| `Hud`, `HUD`, `Gui`, `GUI` | Causes this part to be drawn directly on your screen.<br />  The coordinates 0,0 are in the top left of the screen. <br /> The negative X direction is to the right, and <br /> the negative Y direction is down. |
| `Camera`, `CAMERA` | Causes this part to always be drawn pointing <br /> towards the camera, the same way that particles do. |
| `Skull`, `SKULL`, &#x1F480; | Causes this part to be drawn as your player head when <br /> placed on the ground or held as an item. |
| `Portrait`, `PORTRAIT` | Causes this part to be drawn in your portrait in the <br /> tab-list in multiplayer. |

