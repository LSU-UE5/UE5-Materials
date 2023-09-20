![](../images/line3.png)

### Emissive Material II

<sub>[previous](../illumination/README.md#user-content-emissive-material) • [home](../README.md#user-content-ue5-intro-to-materials) • [next](../two-sided/README.md#user-content-two-sided-material)</sub>

![](../images/line3.png)

Lets add a spotlight to the glowing material to bring this effect to its full realization.

<br>

---

##### `Step 1.`\|`UE5MAT`|:small_blue_diamond:

Now we want to be able to change the color of the light and the glow emissive.  Open up **MF_Base_Texture** and add a **Vector Parameter** to the node chart and call it `EmissiveTint`.  Make it pure white `1,1,1`.  Send it to a new **Multiply** node.  Multiply the **Emissive Scalar** and send the output the the **Multiply** pin that the scalar once was in (the Multiply node before the Scale Emissive?).

![rotate player start](images/emissiveTint.png)


![](../images/line2.png)

##### `Step 2.`\|`UE5MAT`|:small_blue_diamond: :small_blue_diamond: 

*Click* on the lamp in room 4 and select the **Lamp** component.  Change the hue to a shade of green.  Remember this setting.

![add spotlight as child of lamp in scene](images/ChangeSpotlightColor.png)


![](../images/line2.png)

##### `Step 3.`\|`UE5MAT`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Rename **MI_Spotlight** to `MI_Spotlight_Green`.  Open up the material instance and change the **Emissive Tint** to a similar (same?) shade of green.

![add spotlight as child of lamp in scene](images/emissiveTintGreen.png)

![](../images/line2.png)

##### `Step 4.`\|`UE5MAT`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Now go into the game and we now have a green light with a green glow. 

https://github.com/LSU-UE5/UE5-Materials/assets/5504953/6fe029c9-adb7-4f50-8e9f-602625606d49

![](../images/line2.png)

##### `Step 5.`\|`UE5MAT`| :small_orange_diamond:

*Right click* and duplicate **MI_Spotlight_Lamp_Green** and duplicate it calling the new material instance `MI_Spotlight_Lamp_Orange`.  Change the color of the emissive tint to orange.

![move a duplicate light to ceiling](images/orangeMI.png)

![](../images/line2.png)

##### `Step 6.`\|`UE5MAT`| :small_orange_diamond: :small_blue_diamond:

Repeat the above step and create `MI_Spotlight_Lamp_Blue` and chnage the color of the glow to blue.

![alt_text](images/blueMI.png)


![](../images/line2.png)

##### `Step 7.`\|`UE5MAT`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

Now repeat the blueprint of the lap 6 times to have seven lamps around the room.  It should look something like this:

https://github.com/LSU-UE5/UE5-Materials/assets/5504953/e5c3f12d-47e4-4b3d-88a0-cd0f7269e85b


![](../images/line2.png)

##### `Step 8.`\|`UE5MAT`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Assign the three material instances to a couple of lights around the room.  Now when you press play you should have a multicolor room!

https://github.com/LSU-UE5/UE5-Materials/assets/5504953/846b6afe-f907-4b44-b12d-5a621efedde1

![](../images/line2.png)

##### `Step 9.`\|`UE5MAT`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Now make sure that all the objects are in the **Room 4** folder and rename anything that is generic and can't be understood by the name.

![renaming all lights and adjust colors](images/organizeFolder.png)
*
![](../images/line2.png)

##### `Step 10.`\|`UE5MAT`| :large_blue_diamond:

Select the **File | Save All** then press the <kbd>Revision Control</kbd> button and select **Submit Content**.  If you are prompted, select **Check Out** for all items that are not checked out of source control. Update the **Changelist Description** message and with the latest changes. Make sure all the files are correct and press the <kbd>Submit</kbd> button. A confirmation will pop up on the bottom right with a message about a changelist was submitted with a commit number.

![save all and submit to perforce](images/submitP4.png)

![](../images/line2.png)

##### `Step 11.`\|`UE5MAT`| :large_blue_diamond: :small_blue_diamond: 

Sometimes not all files get submitted to Unreal especially for files that don't show up in the editor.  It is good practice one you submit in **Unreal** and quit the game to right click on the top most project folder and select **Reconcile Offline Work...**.

This will either give a message saying ther is nothing to reconcile or bring up a tab.  Make sure that these are **NOT** files in the **Intermediate** and **Saved** folders as these should be ignored from the `.p4ignore`.

If the files are in **Content** or **Configuration** then press the <kbd>Reconcile</kbd> button.  Then submit the changes with a message and press the <kbd>Submit</kbd> button.

![reconcile offline work](images/reconcile.png)

![](../images/line.png)

<!-- <img src="https://via.placeholder.com/1000x100/45D7CA/000000/?text=Next Up - Two Sided Material"> -->
![next up next tile](images/banner.png)

![](../images/line.png)
| [previous](../illumination/README.md#user-content-emissive-material)| [home](../README.md#user-content-ue5-intro-to-materials) | [next](../two-sided/README.md#user-content-two-sided-material)|
|---|---|---|
