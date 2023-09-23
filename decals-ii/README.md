![](../images/line3.png)

### Decals II

<sub>[previous](../decals/README.md#user-content-decals) • [home](../README.md#user-content-ue5-intro-to-materials) • [next](../refract/README.md#user-content-refraction-and-fresnel)</sub>

![](../images/line3.png)

Lets get the decals onto the road.

<br>

---


##### `Step 1.`\|`UE5MAT`|:small_blue_diamond:

Try putting one of the decals onto the wall below the title.  You will notice that there is a direction to the decal. The purple line on the material gizmo needs to be perpendicular to the wall (pointing towards the middle of the room).

![save all and submit to perforce](images/decalsHaveDirection.png)

![](../images/line2.png)

##### `Step 2.`\|`UE5MAT`|:small_blue_diamond: :small_blue_diamond: 

Rotate the material to face the middle of the romo and you will notice that it now renders correctly.  Be careful with decals in corners as one part of the decal will be distored as above.

![save all and submit to perforce](images/rotateDecal.png)

![](../images/line2.png)

##### `Step 3.`\|`UE5MAT`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

I actually like the color and intensity so I will leave it as is. 

![save all and submit to perforce](images/decalOnWall.png)

![](../images/line2.png)

##### `Step 4.`\|`UE5MAT`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Make sure the names in the **World Outliner** are logical and are in the **Room 6** folder.

![save all and submit to perforce](images/putDataRoom6.png)

![](../images/line2.png)

##### `Step 5.`\|`UE5MAT`| :small_orange_diamond:

Select the **File | Save All** then press the <kbd>Revision Control</kbd> button and select **Submit Content**.  If you are prompted, select **Check Out** for all items that are not checked out of source control. Update the **Changelist Description** message and with the latest changes. Make sure all the files are correct and press the <kbd>Submit</kbd> button. A confirmation will pop up on the bottom right with a message about a changelist was submitted with a commit number.

![save all and submit to perforce](images/submitP4.png)

![](../images/line2.png)

##### `Step 6.`\|`UE5MAT`| :small_orange_diamond: :small_blue_diamond:

Sometimes not all files get submitted to Unreal especially for files that don't show up in the editor.  It is good practice one you submit in **Unreal** and quit the game to right click on the top most project folder and select **Reconcile Offline Work...**.

This will either give a message saying ther is nothing to reconcile or bring up a tab.  Make sure that these are **NOT** files in the **Intermediate** and **Saved** folders as these should be ignored from the `.p4ignore`.

If the files are in **Content** or **Configuration** then press the <kbd>Reconcile</kbd> button.  Then submit the changes with a message and press the <kbd>Submit</kbd> button.

![reconcile offline work](images/reconcile.png)

![](../images/line.png)

<!-- <img src="https://via.placeholder.com/1000x100/45D7CA/000000/?text=Next Up - Refraction and Fresnel"> -->
![next up next tile](images/banner.png)

![](../images/line.png)

| [previous](../decals/README.md#user-content-decals)| [home](../README.md#user-content-ue5-intro-to-materials) | [next](../refract/README.md#user-content-refraction-and-fresnel)|
|---|---|---|
