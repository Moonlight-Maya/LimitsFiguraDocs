## Making a Model

Figura models are made using Blockbench, which you should already have access to if you've been following along thus far. Open up Blockbench and create a new model, using the "Generic Model" format. The name can be anything you want. Advanced techniques for using Blockbench for modeling are beyond the scope of this tutorial; we'll just be making a basic cube that floats above your player's head.

Once inside Blockbench, look on the right for the **Outliner**, the part of the UI that contains all of your cubes, groups, and meshes in a hierarchical format. Just under the word Outliner there are some buttons to create objects of these types. Click the "Add Cube" button to add a cube to your model.

When the cube is created, its bottom is located at (0, 0, 0), and it has a size of 2 by 2 by 2 units. One unit in Blockbench is equivalent to one pixel in Minecraft, so this cube is pretty small. Scale it up by either modifying the "Size" field in the top right, or by pressing "S" to switch to the scale tool and dragging. Just make it a bit bigger in all directions so it's easy to see.

Next, we'll move the cube. The position (0, 0, 0) in Blockbench is located at the bottom of your player's feet, so to make this cube float above your head we want to move it upwards significantly. The player is 32 pixels tall by default, so move it up at least that much to have it float over your head.

Now, in order to have your object be visible in Figura it needs to be given a texture. Your cube has no texture at the moment, so Blockbench supplies it with a basic default texture, but Figura does not do this and instead makes the cube invisible. Blockbench has a nifty feature to auto-generate a texture for cubes: click your cube so it's selected, then on the left side of the screen, click "Create Texture", set the type to "Texture Template", and click "Confirm". You should see your texture appear on the left side of the screen, and the cube in Blockbench should be colored in.

Once you have the cube with a texture, you're ready to put it in your avatar. **Make sure you SAVE the model** by hitting Ctrl+S or choosing File > Save Model. The file, with a `.bbmodel` extension, should be located inside your `tutorial` folder from before. If you're prompted to save your textures as well, it's probably a good idea to save those inside your `tutorial` folder along with the rest, though these textures will be ignored by the mod. Figura will only see the textures actually inside your .bbmodel file.

By the end of this section, your `tutorial` folder should look like this, with an `avatar.json` file and some kind of `.bbmodel` file.
![image](https://user-images.githubusercontent.com/83429328/185455410-bb895e5f-791a-4e90-905f-3782d84c2801.png)

Return back into the game, and if you select the "tutorial" avatar from the wardrobe, you should see your cube above your head!
(WIP, pictures here later)

Now that you have an avatar equipped *locally* (on your own computer), you may wish for others to be able to see your masterpiece. In order for others to see it, you have to *upload* your avatar to the backend. Click the upload button beneath the preview window in the Wardrobe screen, and you should get a toast telling you if your upload worked. If the upload button is grayed out, that means either your current avatar is already uploaded, or you don't have an avatar equipped locally.

Don't get rid of this avatar yet, as we're going to keep on using it and improving it as we move into the next section - [Basics of Parent Parts and Rotation].
