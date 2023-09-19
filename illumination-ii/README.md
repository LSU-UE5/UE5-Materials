![](../images/line3.png)

### Emissive Material II

<sub>[previous](../illumination/README.md#user-content-emissive-material) • [home](../README.md#user-content-ue5-intro-to-materials) • [next](../two-sided/README.md#user-content-two-sided-material)</sub>

![](../images/line3.png)

<img src="https://via.placeholder.com/1000x4/45D7CA/45D7CA" alt="drawing" height="4px"/>

Lets add a spotlight to the glowing material to bring this effect to its full realization.

<br>

---

##### `Step 1.`\|`UE5MAT`|:small_blue_diamond:


![rotate player start](images/emissiveTint.png)


![](../images/line2.png)

##### `Step 2.`\|`UE5MAT`|:small_blue_diamond: :small_blue_diamond: 

Adjust tint NEED SCREENSHOT

![add spotlight as child of lamp in scene](images/.png)



![](../images/line2.png)

##### `Step 3.`\|`UE5MAT`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

![mark light as movable](images/lightColor.png)




![](../images/line2.png)

##### `Step 4.`\|`UE5MAT`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

![change spotlight color](images/spotLight.png)

![](../images/line2.png)

##### `Step 5.`\|`UE5MAT`| :small_orange_diamond:

Now duplicate the bracket, lamp and light and rotate it and move it to the ceiling pointing straight down. Make sure you are moving the location with the bracket and rotating along a single axis on the lamp.  The light should then point in the right direction.

![move a duplicate light to ceiling](images/dupeMove.png)

![](../images/line2.png)

##### `Step 6.`\|`UE5MAT`| :small_orange_diamond: :small_blue_diamond:

Repeat this 5 more times to a have a total of 7 lights in the room.  Point them at the wall and adjust the brightness so they show up correctly.

![alt_text](images/add5MoreLights.png)

![](../images/line2.png)

##### `Step 7.`\|`UE5MAT`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

Ranme **MI_Spotlight** to `MI_Spolight_Orange` (or whatever color your light and glow are). Right click and duplicate this material 6 times. 

![add 6 more materials](images/duplicate6.png)

![](../images/line2.png)

##### `Step 8.`\|`UE5MAT`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Rename each material instance copy and change both the **Emissive Tint** in the material and the **Light Color** in the spotlight. Name it the new color of the light and glow.  So if you have a yellow light call it `MI_Spotlight_Yellow`.

![renaming all lights and adjust colors](images/adjust6tintsColors.png)

![](../images/line2.png)

##### `Step 9.`\|`UE5MAT`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

*Press* the <kbd>Play</kbd> button and make sure that the glow matches the color of the light on the wall.  Make any adjustments, like its brightness and get it to look like it matches the environment.

https://user-images.githubusercontent.com/5504953/186139493-95a4de1c-5d3d-49b4-89ef-86b6d03a2315.mp4

![](../images/line2.png)

##### `Step 10.`\|`UE5MAT`| :large_blue_diamond:

Now make sure that all the objects are in the **Room 4** folder and rename anything that is generic and can't be understood by the name.

![organize and rename outliner](images/organizeAndRenameOutliner.png)

![](../images/line2.png)

##### `Step 11.`\|`UE5MAT`| :large_blue_diamond: :small_blue_diamond: 

Select the **File | Save All** then press the <kbd>Revision Control</kbd> button and select **Submit Content**.  If you are prompted, select **Check Out** for all items that are not checked out of source control. Update the **Changelist Description** message and with the latest changes. Make sure all the files are correct and press the <kbd>Submit</kbd> button. A confirmation will pop up on the bottom right with a message about a changelist was submitted with a commit number.

![save all and submit to perforce](images/submitP4.png)

![](../images/line.png)

<!-- <img src="https://via.placeholder.com/1000x100/45D7CA/000000/?text=Next Up - Two Sided Material"> -->
![next up next tile](images/banner.png)

![](../images/line.png)
| [previous](../illumination/README.md#user-content-emissive-material)| [home](../README.md#user-content-ue5-intro-to-materials) | [next](../two-sided/README.md#user-content-two-sided-material)|
|---|---|---|
