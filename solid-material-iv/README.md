![](../images/line3.png)

### Solid Material IV

<sub>[previous](../solid-material-iii/README.md#user-content-solid-material-iii) • [home](../README.md#user-content-ue5-intro-to-materials) • [next](../color-math/README.md#user-content-material-color-math)</sub>

![](../images/line3.png)

Lets finish up the **UVs** for the scale.  We will also look at adding the ability to rotate the texture.  

<br>

---


##### `Step 1.`\|`UE5MAT`|:small_blue_diamond:

Lets go to the game and open up **MI_Grass**.  Now look for the new **UV** node.  It is also the first item to edit, we want it to be last and oops, it is in a generic category. Lets fix that by opening up **MF_UVs**. Add a **Category** of `UVs` to it and change the **Sort Priority** to `60`.  Now go back to the game.  Notice that adjust the **UV** mulutiplier to less than `1` it gets larger and higher than `1` it get smaller.  I like a value of `10`, this looks right to my eyes. 

https://github.com/LSU-UE5/UE5-Materials/assets/5504953/0bcbb73c-b334-4a14-82cd-42966c2e8b12

![](../images/line2.png)

##### `Step 2.`\|`UE5MAT`|:small_blue_diamond: :small_blue_diamond: 

Now lets add the ability to rotate the texture to add another layer of customization. Open up **MF_UVs** and add a **Custom Rotator** node.

![add a custom rotator node](images/customRotator.png)

![](../images/line2.png)

##### `Step 3.`\|`UE5MAT`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

The custom rotator node has three inputs.  One is the UVs which will do the rotation.  The **Rotation Center** allows you to move where the texture rotates from.  We will leave this alone, as it is probably not needed very often.  The rotation angle is a scalar value between `0` and `1`.  This means that all values between 0° and 359° will be fractional between 0 and 1.  So a value of 180 would be 180/359 which is `0.5`.

![custom rotator node](images/threeInputs.png)

![](../images/line2.png)

##### `Step 4.`\|`UE5MAT`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Now take the output of the **Multiply** node and place it into the input **UVs** node in the **Custom Rotator**.  Take the **Return Value** and send it to the **Output UVs** node. *Right click* on the open graph and select a **Scalar Parameter** and call it `UVAngle`. Plug it into the **Rotation Angle** input node.    Select all of the 4 nodes and press the <kbd>C</kbd> key and add a comment `Rotate UVs` and select a color.  Set the **Group** to `UVs` and the **Sort Priority** to `61`.

![connect custom rotator and add scalar parameter](images/scalarAdjustments.png)

![](../images/line2.png)

##### `Step 5.`\|`UE5MAT`| :small_orange_diamond:

Now lets add a **Static Switch Parameter** node and call it `RotateUVs?`.  Set the **Group** to `UVs` and the **Sort Priority** to `63`. Take the output from the rotator nad put it into the **True** pin of the switch.  Take the output of the **Multiply** node and put it into the `false` pin of the switch.  Take the output of the **Switch** and put it to the **Output** node.

![connect custom rotator and add scalar parameter](images/AddSwitch.png)

![](../images/line2.png)

##### `Step 6.`\|`UE5MAT`| :small_orange_diamond: :small_blue_diamond:

*Open up* **MI_WildGrass** and turn on the switch to adjust the angle. *Adjust* the UV angle between 0 and 1. Nwo pick an angle you like.  That will be it for room 2!

https://user-images.githubusercontent.com/5504953/185766950-79a0f8ad-0501-4090-9cf4-43dd57e0691a.mp4

![](../images/line2.png)

##### `Step 7.`\|`UE5MAT`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

Select the **File | Save All** then press the <kbd>Source Control</kbd> button and select **Submit Content**.  If you are prompted, select **Check Out** for all items that are not checked out of source control. Update the **Changelist Description** message and with the latest changes. Make sure all the files are correct and press the <kbd>Submit</kbd> button. A confirmation will pop up on the bottom right with a message about a changelist was submitted with a commit number.

![save all and submit to perforce](images/submitP4.png)

![](../images/line2.png)

##### `Step 8.`\|`UE5MAT`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Sometimes not all files get submitted to Unreal especially for files that don't show up in the editor.  It is good practice one you submit in **Unreal** and quit the game to right click on the top most project folder and select **Reconcile Offline Work...**.

This will either give a message saying ther is nothing to reconcile or bring up a tab.  Make sure that these are **NOT** files in the **Intermediate** and **Saved** folders as these should be ignored from the `.p4ignore`.

If the files are in **Content** or **Configuration** then press the <kbd>Reconcile</kbd> button.  Then submit the changes with a message and press the <kbd>Submit</kbd> button.

![reconcile offline work](images/reconcile.png)

![](../images/line.png)

<!-- <img src="https://via.placeholder.com/1000x100/45D7CA/000000/?text=Next Up - ADD NEXT TITLE"> -->
![next up next tile](images/banner.png)

![](../images/line.png)

| [previous](../solid-material-iii/README.md#user-content-solid-material-iii)| [home](../README.md#user-content-ue5-intro-to-materials) | [next](../color-math/README.md#user-content-material-color-math)|
|---|---|---|
