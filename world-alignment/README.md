![](../images/line3.png)

### World Aligned Materials

<sub>[previous](../export-textures/README.md#user-content-export-textures) • [home](../README.md#user-content-ue5-intro-to-materials)

![](../images/line3.png)

<img src="https://via.placeholder.com/1000x4/45D7CA/45D7CA" alt="drawing" height="4px"/>

What happens if I want a long stretch of brick wall that follows different shaped and placed geometries.  It would take a lot of painstaking tweaking to align all the UV's.  There is a better way in unreal to use world coordinates to place the UVs as opposed to locally with the model.

<br>

---


##### `Step 1.`\|`UE5MAT`|:small_blue_diamond:

Open up the UE5 Editor and drag the three brick textures you made in the last module into the **Textures | Surfaces** folder.

![drag three brick wall textures into surfaces folder](images/importNewBrickFiles.png)

![](../images/line2.png)

##### `Step 2.`\|`UE5MAT`|:small_blue_diamond: :small_blue_diamond: 

Lets create a material instnace for these textures.  Go to **Materails | Master** and right click on **M_SolidTexture** and select **Create Material Instance**.  Call it `MI_BrickWall`.  Move it to the **Material | Surfaces** folder.

![create mi_brickwall material instance](images/materialInstance.png)

![](../images/line2.png)

##### `Step 3.`\|`UE5MAT`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Open up **MI_BrickWall** and assign the **Base Color**, **Normal Map** and **MSRAO** textures.  You should see a nice brick wall material.

![assign brick wall material](images/brickWallMI.png)

![](../images/line2.png)

##### `Step 4.`\|`UE5MAT`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Scoot over to **Room 9** and and drag a copy of **Meshes | Supplied | SM_Wall** to the level.  Change the **Transoform | Scale** to `0.35` on all axis.

![add wall make smaller](images/addFirstWallPiece.png)

![](../images/line2.png)

##### `Step 5.`\|`UE5MAT`| :small_orange_diamond:

Copy them into a cluster where they are next to each other in an asymetric pattern on a plane.  Make sure if there is z-fighting that you adjust the depth so there are no rendering issues. 

![make cluster of wall pieces](images/firstWall.png)

![](../images/line2.png)

##### `Step 6.`\|`UE5MAT`| :small_orange_diamond: :small_blue_diamond:

This group will have the normal local space texture.  Now select all the wall pieces and duplicate them to the right.  Also, move the **Player Start** to room 9 and face the back wall.

![duplicate wall pieces](images/playerStartWall.png)

![](../images/line2.png)

##### `Step 7.`\|`UE5MAT`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

Put **MI_BrickWall** on the wall pieces.  Again, make sure there are no rendering issues and make relevant adjustements.

![add brick material](images/assignBricks.png)

![](../images/line2.png)

##### `Step 8.`\|`UE5MAT`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Notice close in that the brick pieces don't line up.  We would have to manually adjust the position of the brick in each material to line them up perfectly and this would take a lot of time!

![close up of bricks](images/tilesDontAlign.png)

![](../images/line2.png)

##### `Step 9.`\|`UE5MAT`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Create a new material called **M_SolidWorld**.  Add 3 **Texture Object Parameter** nodes.  Call them `Base Color`, `Normal` and `MSRAO`.  Call the group **World Textures** and set the **Sort Priority** to `0` for base color, `1` for normal and `2` for MSRAO.

![add three texture object parameters](images/newMatThreeTextObj.png)

![](../images/line2.png)

##### `Step 10.`\|`UE5MAT`| :large_blue_diamond:

Add a **WorldAlignedTexture** node to the graph.  This will adjust the UVs so the textures are in world space.

![add worldaligned textures node](images/baseTexturesAlgined.png)

![](../images/line2.png)

##### `Step 11.`\|`UE5MAT`| :large_blue_diamond: :small_blue_diamond: 

Make a copy so that we have one for the Base Color and the second for the MSRAO nodes.

![two world aligned textures node](images/twoWATextures.png)

![](../images/line2.png)


##### `Step 12.`\|`UE5MAT`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: 

Normal maps are different so add a **WorldAlignedNormal** node for the normal maps.  Connect the output of the three texture objeects to the **Texture Object** pin for the three nodes.  Make sure it is **T_BrickWall_N** to the **World Aligned Normal** node.

![alt_text](images/worldAlignedM.png)

![](../images/line2.png)

##### `Step 13.`\|`UE5MAT`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 

![alt_text](images/.png)

![](../images/line2.png)

##### `Step 14.`\|`UE5MAT`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 

![alt_text](images/vector4Bool.png)

![](../images/line2.png)

##### `Step 15.`\|`UE5MAT`| :large_blue_diamond: :small_orange_diamond: 

![alt_text](images/breakOut4.png)

![](../images/line2.png)

##### `Step 16.`\|`UE5MAT`| :large_blue_diamond: :small_orange_diamond:   :small_blue_diamond: 

![alt_text](images/connectPins.png)

![](../images/line2.png)

##### `Step 17.`\|`UE5MAT`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

![alt_text](images/appendThreeParams.png)

![](../images/line2.png)

##### `Step 18.`\|`UE5MAT`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

![alt_text](images/connectUVs.png)

![](../images/line2.png)

##### `Step 19.`\|`UE5MAT`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

![alt_text](images/addMI.png)

![](../images/line2.png)

##### `Step 20.`\|`UE5MAT`| :large_blue_diamond: :large_blue_diamond:

![alt_text](images/addTextures.png)

![](../images/line2.png)

##### `Step 21.`\|`UE5MAT`| :large_blue_diamond: :large_blue_diamond: :small_blue_diamond:

![alt_text](images/addMi2.png)

![](../images/line2.png)

##### `Step 22.`\|`UE5MAT`| :large_blue_diamond: :large_blue_diamond: :small_blue_diamond: :small_blue_diamond:

https://user-images.githubusercontent.com/5504953/187112628-a2ecda52-f583-448c-a08b-08a3d31dc6bc.mp4

![](../images/line2.png)

##### `Step 23.`\|`UE5MAT`| :large_blue_diamond: :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Select the **File | Save All** then press the <kbd>Source Control</kbd> button and select **Submit Content**.  If you are prompted, select **Check Out** for all items that are not checked out of source control. Update the **Changelist Description** message and with the latest changes. Make sure all the files are correct and press the <kbd>Submit</kbd> button. A confirmation will pop up on the bottom right with a message about a changelist was submitted with a commit number.

![save all and submit to perforce](images/submitP4.png)

![](../images/line.png)

<!-- <img src="https://via.placeholder.com/1000x100/45D7CA/000000/?text=Thats All Folks!"> -->
![next up next tile](images/banner.png)

![](../images/line.png)

| [previous](../export-textures/README.md#user-content-export-textures)| [home](../README.md#user-content-ue5-intro-to-materials)
|---|---|
