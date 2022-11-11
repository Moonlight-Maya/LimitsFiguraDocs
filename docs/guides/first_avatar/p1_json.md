# Making your first avatar

In this page, you will learn the fundamentals of:
*Figura's file system
*Creating models with Blockbench

Because you're just starting out, we're going to begin with creating a very basic avatar - just a single cube, that will float above your player's head. The first step is to navigate to your avatar folder, as described in the previous section - it should be located at `.minecraft/figura/avatars/`, and accessible from the button in the wardrobe screen.

Once you reach your avatar folder, we want to create a new avatar here. Each avatar is stored inside a folder, so let's create a new folder inside, and call it "tutorial". You should now have a folder `.minecraft/figura/avatars/tutorial/`. Now, we need something to indicate to Figura that "Hey, this 'tutorial' folder actually contains an avatar! Come look in here!"

To make this indicator, all we have to do is create one thing - a file called `avatar.json`, inside of `tutorial`. Typing things in this file will be useful later on, but all we need to make our indicator is for the file to exist. It doesn't have to have anything inside.

Now let's test that your avatar worked! In game, get back to the wardrobe screen and look on the left. If all went well, you should see an option for "tutorial" on the left.
> Troubleshooting - What if I don't see it on the left?
>>*Ensure that you created a **file** and not a **folder** called avatar.json. The two are distinct concepts, and the distinction of "file" versus "folder" will be maintained on this wiki.
>>*Check that _file extensions are enabled_ in your file explorer. In Windows, this can be enabled by clicking the "View" tab at the top, and activating the check box for "File Name Extensions." With this check box active, ensure that your file is _really_ called avatar.json, and not avatar.json.txt, and Windows was hiding the ".txt" part from you.

You now technically have an avatar! It's a really boring avatar, since nothing is actually in there, but it is still an avatar, for the sole reason of it having that `avatar.json` file inside.

Anyway, past that, let's move on to the next step: creating a basic model in Blockbench.
