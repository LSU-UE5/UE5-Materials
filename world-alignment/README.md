![](../images/line3.png)

### World Aligned Materials

<sub>[previous](../export-textures/README.md#user-content-export-textures) • [home](../README.md#user-content-ue5-intro-to-materials)

![](../images/line3.png)

What happens if I want a long stretch of brick wall that follows different shaped and placed geometries.  It would take a lot of painstaking tweaking to align all the UV's.  There is a better way in unreal to use world coordinates to place the UVs as opposed to locally with the model.

<br>

---


##### `Step 1.`\|`UE5MAT`|:small_blue_diamond:

Open up the UE5 Editor and drag the three brick textures you made in the last module into the **Textures | Surfaces** folder.

![drag three brick wall textures into surfaces folder](images/importNewBrickFiles.png)

![](../images/line2.png)

##### `Step 2.`\|`UE5MAT`|:small_blue_diamond: :small_blue_diamond: 

Create a new material function called **MF_WorldAligned_MSRAO**.  Open up the new material function and add a **Texture Object Parameter** node,

![add three texture object parameters](images/newMatThreeTextObj.png)

![](../images/line2.png)

##### `Step 3.`\|`UE5MAT`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Name the first **Texture Object Parameter** `Base Color`.  Assign  `T_Base_BCH` to the **Texture** slot.  Change the **Group** to `WorldAligned` and **Sort Priority** of `0`.

Add another **Texture Object Parameter** `Normal`.  Assign  `T_Base_N` to the **Texture** slot.  Change the **Group** to `WorldAligned` and **Sort Priority** of `1`.

Name the first **Texture Object Parameter** `MSRAO`.  Assign  `T_Base_MSRAO` to the **Texture** slot.  Change the **Group** to `WorldAligned` and **Sort Priority** of `2`.


![add three texture object parameters](images/threeTextObj.png)

![](../images/line2.png)

##### `Step 4.`\|`UE5MAT`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Add twp **WorldAlignedTexture** node to the graph.  This will adjust the UVs so the textures are in world space. Connect the output pins of the **BaseColor** and **MSRAO** nodes to the top pin in the **WorldAlignedTexture** node.

Normal maps are different so add a **WorldAlignedNormal** node for the normal maps.  Connect the output of the **Normal** objeect to the **Texture Object** pin of the **WorldAlignedNormal** node.

![add worldaligned textures node](images/baseTexturesAlgined.png)

![](../images/line2.png)

##### `Step 5.`\|`UE5MAT`| :small_orange_diamond:

Now we have an RGBA texture in our MSRAO.  Now the output pins just carry three values (XYZ Textue).  We need to add a **Static Bool** node and set it to `true`.  Plug it inot the **Export Float 4** node of the **World Aligned Texture** node used for the **MSRAO**.

![turn on export float 4](images/vector4Bool.png)

![](../images/line2.png)

##### `Step 6.`\|`UE5MAT`| :small_orange_diamond: :small_blue_diamond:

Lets create a material instnace for these textures.  Go to **Materails | Master** and right click on **M_SolidTexture** and select **Create Material Instance**.  Call it `MI_BrickWall`.  Move it to the **Material | Surfaces** folder.

![create mi_brickwall material instance](images/materialInstance.png)


Open up **MI_BrickWall** and assign the **Base Color**, **Normal Map** and **MSRAO** textures.  You should see a nice brick wall material.

![assign brick wall material](images/brickWallMI.png)

Scoot over to **Room 9** and and drag a copy of **Meshes | Supplied | SM_Wall** to the level.  Change the **Transoform | Scale** to `0.35` on all axis.

![add wall make smaller](images/addFirstWallPiece.png)

Copy them into a cluster where they are next to each other in an asymetric pattern on a plane.  Make sure if there is z-fighting that you adjust the depth so there are no rendering issues. 

![make cluster of wall pieces](images/firstWall.png)

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



![](../images/line2.png)

##### `Step 10.`\|`UE5MAT`| :large_blue_diamond:



![](../images/line2.png)

##### `Step 11.`\|`UE5MAT`| :large_blue_diamond: :small_blue_diamond: 

![](../images/line2.png)


##### `Step 12.`\|`UE5MAT`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: 



![alt_text](images/worldAlignedM.png)

![](../images/line2.png)

##### `Step 13.`\|`UE5MAT`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 



![](../images/line2.png)

##### `Step 14.`\|`UE5MAT`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 

Pull out from the **XYZ Texture** pin from the **MSRAO | World Aligned Texture** pin.  Add a **Break Out Float 4 Components** node.

![break out 4 floats](images/breakOut4.png)

![](../images/line2.png)

##### `Step 15.`\|`UE5MAT`| :large_blue_diamond: :small_orange_diamond: 

Connect the **Base Color | World Aligned Texture | XYZ Texture** to **Base Color**. Take the output of the **World Aligned Normal | XYZ Texture** node to the **Normal** pin.  Connet the **Break Out Float 4 Components** **R** to **Metallic**, **G** to **Specular**, **B** to **Roughness** and **A** to **Ambient Occlusion**.

![connect all material pins](images/connectPins.png)

![](../images/line2.png)

##### `Step 16.`\|`UE5MAT`| :large_blue_diamond: :small_orange_diamond:   :small_blue_diamond: 

Now we want to adjust the scale of the textures symmetrically.  The input pin for **Texture Size** askes for a **V3** (Three floats). So we need a single float with the same value in all three positions.  Create a **Scalar Parameter** and call it `Texture Size`.  Take the output and add an **Append** node.  This is now a **V2**.  Now add another **Append** node and send the output of the first append node and another **Texture Size** to pin **B**.  Now we have a **V3**.

![make single parameter a v3](images/appendThreeParams.png)

![](../images/line2.png)

##### `Step 17.`\|`UE5MAT`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

Send the output of the **Append** node to the three **TextureSize** pins in the three world aligned ndoes.

![output to texture size](images/connectUVs.png)

![](../images/line2.png)

##### `Step 18.`\|`UE5MAT`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Right click on **Materials | Master** and select **Create Material Instance** and call it `M_BricksWorldSpace`.  Move this to the **Materials | Surfaces** folder.

![make material instance for world bricks](images/addMI.png)

![](../images/line2.png)

##### `Step 19.`\|`UE5MAT`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Open up **MI_BricksWorldSpace** and assign the same three textures you assigned to the previous brick wall material.

![add three textures to instance](images/addTextures.png)

![](../images/line2.png)

##### `Step 20.`\|`UE5MAT`| :large_blue_diamond: :large_blue_diamond:

Add this material instance to the wall pieces on the right and adjust the **Texture Size** variable so that the scale is roughly the same as the ones on the left.

![add world aligned texture to right wall pieces](images/addMi2.png)

![](../images/line2.png)

##### `Step 21.`\|`UE5MAT`| :large_blue_diamond: :large_blue_diamond: :small_blue_diamond:

*Press* the <kbd>Play</kbd> button and look at the textures.  The ones on the right are all aligned.  Stop the game and move the wall pieces on the left.  The material moves with the object.  If you move the wall pieces on the right you texture stays fixed to world space and the object moves (almost like it is a window).  This is an effective way to get geometric materials to align between surfaces with no tweaking.  Organize your **Outliner** as this will be it for this walk through!

https://user-images.githubusercontent.com/5504953/187112628-a2ecda52-f583-448c-a08b-08a3d31dc6bc.mp4

![](../images/line2.png)

##### `Step 22.`\|`UE5MAT`| :large_blue_diamond: :large_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Select the **File | Save All** then press the <kbd>Revision Control</kbd> button and select **Submit Content**.  If you are prompted, select **Check Out** for all items that are not checked out of source control. Update the **Changelist Description** message and with the latest changes. Make sure all the files are correct and press the <kbd>Submit</kbd> button. A confirmation will pop up on the bottom right with a message about a changelist was submitted with a commit number.

![save all and submit to perforce](images/submitP4.png)

| `materials.ue5`\|`THE END`| 
| :--- |
| **That's All Folks!** Thanks for sticking around. That's it for this lesson. |

![](../images/line.png)

<!-- <img src="https://via.placeholder.com/1000x100/45D7CA/000000/?text=Thats All Folks!"> -->
![next up next tile](images/banner.png)

![](../images/line.png)

| [previous](../export-textures/README.md#user-content-export-textures)| [home](../README.md#user-content-ue5-intro-to-materials)
|---|---|
