![](../images/line3.png)

### Animation II

<sub>[previous](../animation/README.md#user-content-animation) • [home](../README.md#user-content-ue5-intro-to-materials) • [next](../export-textures/README.md#user-content-export-textures)</sub>

![](../images/line3.png)

Finish up the UV translation.  Then lets rotate a UV.  Finally we will give the glass texture a watery effect! Lets get to it.

<br>

---


##### `Step 1.`\|`UE5MAT`|:small_blue_diamond:

Now lets rotate the UVs.  Download [T_Gear.tif](../Assets/T_Gear.tif) and drag it to the **Textures | Poster** folder.  This is a mask and is in the shape of a round gear that we will spin.

![create mi_rotate material instance](images/addGear.png)

![](../images/line2.png)

##### `Step 2.`\|`UE5MAT`|:small_blue_diamond: :small_blue_diamond: 

Now open up **MF_UVs** and add the output of **RotateUVs?** to the input **Panner | Coordinate** pin.  This will combine both the panning and rotating.

![create mi_rotate material instance](images/rotateAndPan.png)

![](../images/line2.png)

##### `Step 3.`\|`UE5MAT`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Add a **Scalar Parameter** node and call it `RotationSpeed`.  Change the **Group** to `UVs` and **SortPriority** to `62`.

![add T_Gear](images/rotSpeed.png)

![](../images/line2.png)

##### `Step 4.`\|`UE5MAT`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Now to animate the angle you multiply **RotationSpeed** variable by **Time**.

![add T_Gear](images/rotTime.png)

![](../images/line2.png)

##### `Step 5.`\|`UE5MAT`| :small_orange_diamond:

Now our **UVAngle** is the starting angle and we might want to change hte angle without animating it.  So we can add the **UVAngle** with the **Multiply** node and send it to the **Custom Rotator | Rotation Angle** node.

![add T_Gear](images/addStarting.png)

![](../images/line2.png)

##### `Step 6.`\|`UE5MAT`| :small_orange_diamond: :small_blue_diamond:

Right click on **Materials | MaterialInstances | M_Chevron** and select **Duplicate**.  Call it `MI_Rotate`.

![create mi_rotate material instance](images/miRotate.png)

![](../images/line2.png)

##### `Step 7.`\|`UE5MAT`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

Add another **Plane** actor to the level. Rotate it towards the camera and set the **Scale X** and **Scale Y** to `4.0`.  Drag the newly created **MI_Rotate** onto the plane and you should see the gear.

![create plane for mi_rotate](images/addScalePlane.png)

![](../images/line2.png)

##### `Step 8.`\|`UE5MAT`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Now we will need to add another **Custom 
Rotator** node that we will animate.  Hook up the output of **Translate UVs?** node to the **UVs** input of the custom rotator.

![add custom rotator node](images/addCustomRotator.png)

![](../images/line2.png)

##### `Step 9.`\|`UE5MAT`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

 Open up **MI_Rotate** and assign `T_Gear` as the **Base Color** texture. Adjust the **Emissive Tint**. Set **RotateUVs** to true and play with positive nad negative speeds.  Notice that you can combine rotation and panning, albeit some issue with smearing in the renderer. *Press* the <kbd>Play</kbd> button and look at the animations!  Now lets create a water like effect.

https://github.com/LSU-UE5/UE5-Materials/assets/5504953/d1090896-efef-4e21-81ad-5f23358f15ab

![](../images/line2.png)

##### `Step 10.`\|`UE5MAT`| :large_blue_diamond:

Lets animate the normal map. Duplicate the **MI_GlassFrosted** ball and title from Room 7 and drag it to Room 8.

![drag normal ball from room 7](images/dupeNormalBall.png)

![](../images/line2.png)

##### `Step 11.`\|`UE5MAT`| :large_blue_diamond: :small_blue_diamond: 

Now open up **MF_Normal** and add a **Static Switch Parameter** called `PanNormals?`. Set it to **Group** `Normals` and **Sort Priority** of `41`.  Put this between **Normal** and the **Output** through the **False** pin.

![drag normal ball from room 7](images/panNormals.png)

![](../images/line2.png)


##### `Step 12.`\|`UE5MAT`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: 

Copy the normal nodes twice (we will reuse the same texture). Add two **Panner** nodes.  We will hard code the animation, you could turn these into variables as we did before.  Set the first panner to an **X** of `0.25` and **Y** of `0.1` and the second to an **X** of `0.18` and **Y** of `0.23`

![drag normal ball from room 7](images/finishNormal.png)

![](../images/line2.png)

##### `Step 13.`\|`UE5MAT`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 

Send the **TexCoord** node into both the **Panner** nodes. Now for normal maps we combine them with a **BlendAngleCorrectedNormals** node that then gets sent to the **PanNormals? | True** pin.

![add coordinate and panner](images/blendNormals.png)

![](../images/line2.png)

##### `Step 14.`\|`UE5MAT`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 

Duplicate **Materials | Material Instances | MI_GlassFrosted** and call it `MI_GlassFrostedAnimated`.  Change the text title to `MI_GlassFrostedAnimated`.

![dupe normal panner](images/miglassanim.png)

![](../images/line2.png)

##### `Step 15.`\|`UE5MAT`| :large_blue_diamond: :small_orange_diamond: 

Assign the **MI_GlassFrostedAnimated** material to the material ball in Room #8.

![blended adjusted normals node](images/assignMat.png)

![](../images/line2.png)

##### `Step 16.`\|`UE5MAT`| :large_blue_diamond: :small_orange_diamond:   :small_blue_diamond: 

Open up **MI_AnimatedGlass** and turn **Animate UVs?** to `true`.  *Press* the <kbd>Play</kbd> button  and look at the fabulous effect of water rippling on/in the ball.

https://github.com/LSU-UE5/UE5-Materials/assets/5504953/e716b32e-a05b-473f-b2d4-ecb6ab94670c

![](../images/line2.png)

##### `Step 17.`\|`UE5MAT`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

Organize the **Outliner** and have your actors match what is in the scene.  Take your time to clean up your files.

![organize files](images/organize.png)

![](../images/line2.png)

##### `Step 18.`\|`UE5MAT`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Select the **File | Save All** then press the <kbd>Revision Control</kbd> button and select **Submit Content**.  If you are prompted, select **Check Out** for all items that are not checked out of source control. Update the **Changelist Description** message and with the latest changes. Make sure all the files are correct and press the <kbd>Submit</kbd> button. A confirmation will pop up on the bottom right with a message about a changelist was submitted with a commit number.

![save all and submit to perforce](images/submitP4.png)

![](../images/line2.png)

##### `Step 19.`\|`UE5MAT`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Sometimes not all files get submitted to Unreal especially for files that don't show up in the editor.  It is good practice one you submit in **Unreal** and quit the game to right click on the top most project folder and select **Reconcile Offline Work...**.

This will either give a message saying ther is nothing to reconcile or bring up a tab.  Make sure that these are **NOT** files in the **Intermediate** and **Saved** folders as these should be ignored from the `.p4ignore`.

If the files are in **Content** or **Configuration** then press the <kbd>Reconcile</kbd> button.  Then submit the changes with a message and press the <kbd>Submit</kbd> button.

![reconcile offline work](images/reconcile.png)

![](../images/line.png)

<!-- <img src="https://via.placeholder.com/1000x100/45D7CA/000000/?text=Next Up - Export Textures"> -->
![next up next tile](images/banner.png)

![](../images/line.png)

| [previous](../animation/README.md#user-content-animation)| [home](../README.md#user-content-ue5-intro-to-materials) | [next](../export-textures/README.md#user-content-export-textures)|
|---|---|---|
