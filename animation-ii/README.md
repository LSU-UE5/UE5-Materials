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


![dupe normal panner](images/miglassanim.png)

![](../images/line2.png)

##### `Step 15.`\|`UE5MAT`| :large_blue_diamond: :small_orange_diamond: 

Now since normals is vector math and not pixel colors we can't just add them to get a combined normal.  We need to use the **Blend Angle Corrected Normals** node.  Attach both **Normal** outputs to it. Connect the output to the **Use Normal? | True** pin.

![blended adjusted normals node](images/combineNormals.png)

![](../images/line2.png)

##### `Step 16.`\|`UE5MAT`| :large_blue_diamond: :small_orange_diamond:   :small_blue_diamond: 

Now add another **Static Switch Parameter** node and call it `Animate UVs?`. Set the **Group** and the **Sort Priority**.  You can put it where it makes sense to you. 

Make a copy of the **Normal** node and feed it into the **Animated UVs? | False** pin. Send the output of the **BlendAngle** node to the **Animated UVs? | True** pin. Send the output of the **Animated UVs?** node to the **Use Normal? | True** pin. Press the <kbd>Apply</kbd> button.

![alt_text](images/animateUVs.png)

![](../images/line2.png)

##### `Step 17.`\|`UE5MAT`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

Duplicate **MI_GlassNormal** and call it `MI_AnimatedGlass`.  Drag it onto the material ball you placed in Room 8.

![alt_text](images/dupeMIGlass.png)

![](../images/line2.png)

##### `Step 18.`\|`UE5MAT`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Adjust both **Panner** nodes with diffent speeds in **Speed X** and **Speed Y**.  Use some trial and error and get values that you like. We are hard coding these values you could expose them as parameters if you like.

![alt_text](images/pannerSpeeds.png)

![](../images/line2.png)

##### `Step 19.`\|`UE5MAT`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Open up **MI_AnimatedGlass** and turn **Animate UVs?** to `true`.  *Press* the <kbd>Play</kbd> button  and look at the fabulous effect of water rippling on/in the ball.

https://user-images.githubusercontent.com/5504953/187085995-eeb3a255-8edd-40a1-a56c-0d5d843dabf5.mp4

![](../images/line2.png)

##### `Step 20.`\|`UE5MAT`| :large_blue_diamond: :large_blue_diamond:

Organize the **Outliner** and have your actors match what is in the scene.  Take your time to clean up your files.

![organize files](images/organize.png)

![](../images/line2.png)

##### `Step 21.`\|`UE5MAT`| :large_blue_diamond: :large_blue_diamond: :small_blue_diamond:

Select the **File | Save All** then press the <kbd>Revision Control</kbd> button and select **Submit Content**.  If you are prompted, select **Check Out** for all items that are not checked out of source control. Update the **Changelist Description** message and with the latest changes. Make sure all the files are correct and press the <kbd>Submit</kbd> button. A confirmation will pop up on the bottom right with a message about a changelist was submitted with a commit number.

![save all and submit to perforce](images/submitP4.png)

![](../images/line.png)

<!-- <img src="https://via.placeholder.com/1000x100/45D7CA/000000/?text=Next Up - Export Textures"> -->
![next up next tile](images/banner.png)

![](../images/line.png)

| [previous](../animation/README.md#user-content-animation)| [home](../README.md#user-content-ue5-intro-to-materials) | [next](../export-textures/README.md#user-content-export-textures)|
|---|---|---|
