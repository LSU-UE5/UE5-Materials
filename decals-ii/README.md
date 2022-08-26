![](../images/line3.png)

### Decals II

<sub>[previous](../decals/README.md#user-content-decals) • [home](../README.md#user-content-ue5-intro-to-materials) • [next](../refract/README.md#user-content-refraction-and-fresnel)</sub>

![](../images/line3.png)

<img src="https://via.placeholder.com/1000x4/45D7CA/45D7CA" alt="drawing" height="4px"/>

Lets get the decals onto the road.

<br>

---


##### `Step 1.`\|`UE5MAT`|:small_blue_diamond:

Now the decals do not take a texture slot they lie on top of the textures and act as a layer in photoshop but project over existing polygons and uvs.  So drag **MI_CementCracks** over to the road.  You can move it around, rotate it and scale it.  I made it a bit smaller as it seemed a bit big to me.

![add mi_cementcrack to level](images/addCementCrackLevel.png)

![](../images/line2.png)

##### `Step 2.`\|`UE5MAT`|:small_blue_diamond: :small_blue_diamond: 

Click on the **Base Color Tine** and select the eye dropper and pick a color from the dement.  I made it even darker to make it more realistic.

![alter crack color](images/adjustCrackColor.png)

![](../images/line2.png)

##### `Step 3.`\|`UE5MAT`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Adjust the **Opacity Intensity** to your liking. Now lets move on to the next decal.

![adjust opacity intensity](images/reduceCrackOpacity.png)

![](../images/line2.png)

##### `Step 4.`\|`UE5MAT`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Right click on **Materials | Decals | MI_CementCracks** and call it `MI_DamagedRoad`.

![duplicate MICementCracks and create MI_DamagedRoad](images/dupeMFDamagedRoad.png)

![](../images/line2.png)

##### `Step 5.`\|`UE5MAT`| :small_orange_diamond:

Now open up **MI_DamagedRoad** and assign the textures you downloaded.  Assign `T_DamagedRoad_BCA`, `T_DamagedRoad_N` and `T_DamagedRoad_BCMSRAO`.

![assign three textures](images/damagedRoadTextures.png)

![](../images/line2.png)

##### `Step 6.`\|`UE5MAT`| :small_orange_diamond: :small_blue_diamond:

Drag **MI_DamagedRoad** onto the plane surface in room 6. Adjust the color, tint scale and rotation.  Make any final choices ot make it look as good as possible.

![mi_damangedroad placed on ground](images/adjustDamagedRoadTing.png)

![](../images/line2.png)

##### `Step 7.`\|`UE5MAT`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

*Press* the <kbd>Play</kbd> button make sure the cracks blend into the ground.

https://user-images.githubusercontent.com/5504953/186798673-e2ff4040-cc8b-41ac-b3d4-38eb79f0bafa.mp4

![](../images/line2.png)

##### `Step 8.`\|`UE5MAT`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Organize your folder and make sure the filenames reflect what you see in the room.  Take your time to organize it well.

![organize folder 6 in outlinder](images/cleanUpFolder.png)

![](../images/line2.png)

##### `Step 9.`\|`UE5MAT`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Select the **File | Save All** then press the <kbd>Source Control</kbd> button and select **Submit Content**.  If you are prompted, select **Check Out** for all items that are not checked out of source control. Update the **Changelist Description** message and with the latest changes. Make sure all the files are correct and press the <kbd>Submit</kbd> button. A confirmation will pop up on the bottom right with a message about a changelist was submitted with a commit number.

![save all and submit to perforce](images/submitP4.png)

![](../images/line.png)

<!-- <img src="https://via.placeholder.com/1000x100/45D7CA/000000/?text=Next Up - Refraction and Fresnel"> -->
![next up next tile](images/banner.png)

![](../images/line.png)

| [previous](../decals/README.md#user-content-decals)| [home](../README.md#user-content-ue5-intro-to-materials) | [next](../refract/README.md#user-content-refraction-and-fresnel)|
|---|---|---|
