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

Right click on **Materials | Master | M_EmissiveTexture** and select **Create Material Instance**.  Call it `MI_Rotate` and drag it to the **Surfaces** folder to move it.

![create mi_rotate material instance](images/miRotate.png)

Add another **Plane** actor to the level. Rotate it towards the camera and set the **Scale X** and **Scale Y** to `2.0`.  Drag the newly created **MI_Rotate** onto the plane and you should see the gear.

![create plane for mi_rotate](images/addScalePlane.png)

![](../images/line2.png)

##### `Step 6.`\|`UE5MAT`| :small_orange_diamond: :small_blue_diamond:

Now open up **MF_UVs**.  Lets not have the panner running unless we turn it on (as opposed to sending it 0). This should be more performant.  Add a **Static Switch Parameter**. Call is `Translave UVs?`.  Make it's **Group** a value of `UV` and it's **Sort Priority** a value of `2`. Leave it as a default of `False`.

Send the output of the **Custom Rotator** into the **Translate UV? | False** pin and the output of the **Panner** node to the **Translate UV? | True** pin. Press the <kbd>Apply</kbd> button.

![add static switch for panner](images/staticSwitch.png)

![](../images/line2.png)

##### `Step 7.`\|`UE5MAT`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

Now this will break the **Chevron** so open up **MI_Chevron** and set **Translave UVs?** to `true` and readjust the **Speed X** if necessary.

![alt_text](images/readjustMIChevron.png)

![](../images/line2.png)

##### `Step 8.`\|`UE5MAT`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Now we will need to add another **Custom Rotator** node that we will animate.  Hook up the output of **Translate UVs?** node to the **UVs** input of the custom rotator.

![add custom rotator node](images/addCustomRotator.png)

![](../images/line2.png)

##### `Step 9.`\|`UE5MAT`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Now add a **Time** node.  Then add a **Scalar Parameter** called `Rotation Speed`.  Make it **Group** `UV` and **Sort Priority** of `6`. Set a **Desc** that says `Number between -1 and 1`.  Change **Slide Min** to -1 and **Slide Max** to `1`.

![add time and scalar](images/addTimeNode.png)

![](../images/line2.png)

##### `Step 10.`\|`UE5MAT`| :large_blue_diamond:

Add a **Multiply** node which will multiply **Time** by **Rotation Speed** scalar.  Send to the **Rotation Angle** input pin of the **Custom Rotator**  node. Add another **Static Switch Parameter** and set the **Group** to `UV` and the **Sort Priority** to `5`.  Send the output of the **Rotated Values** to the **Rotate UVs? | True** pin and the outpuf of the **Translate UVs?** pin to the **Rotate *Vs? | False** pin. Send teh output to the **Output UVs** node.  Press the <kbd>Apply</kbd> button.

![finish up rotation nodes](images/finishRotateUVs.png)

![](../images/line2.png)

##### `Step 11.`\|`UE5MAT`| :large_blue_diamond: :small_blue_diamond: 

 Open up **MI_Rotation** and turn on rotation and adjust the speed and the glow.  *Press* the <kbd>Play</kbd> button and look at the animations!  Now lets create a water like effect.

https://user-images.githubusercontent.com/5504953/187084875-49014055-3f40-4a9b-9452-8f90aadf80f4.mp4

![](../images/line2.png)


##### `Step 12.`\|`UE5MAT`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: 

Now duplicate the Normal Ball from Room 7 and drag it to Room 8.  You don't need the title.

![drag normal ball from room 7](images/dupeNormalBall.png)

![](../images/line2.png)

##### `Step 13.`\|`UE5MAT`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 

Open up **MF_UVs** and add a **TextureCoordinate** node and a **Panner** node going into the top **Normal** node.

![add coordinate and panner](images/addTextCoordPanner.png)

![](../images/line2.png)

##### `Step 14.`\|`UE5MAT`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 

Now we are going to have two players of ripples at different directions and speeds.  So make a copy of the **Normal** and **Panner** nodes and make sure it is hooked up to the **TextCoords** node.

![dupe normal panner](images/dupeNormalPanner.png)

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
