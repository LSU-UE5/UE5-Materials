![](../images/line3.png)

### Solid Material IV

<sub>[previous](../solid-material-iii/README.md#user-content-solid-material-iii) • [home](../README.md#user-content-ue5-intro-to-materials) • [next](../color-math/README.md#user-content-material-color-math)</sub>

![](../images/line3.png)

Lets finish up the ***UVs** for the scale.  We will also look at adding the ability to rotate the texture.  

<br>

---


##### `Step 1.`\|`UE5MAT`|:small_blue_diamond:

Lets go to the game and open up **MI_Grass**.  Now look for the new **UV** node.  It is also the first item to edit, we want it to be last and oops, it is in a generic category. Lets fix that by opening up **MF_UVs**. .  

https://github.com/LSU-UE5/UE5-Materials/assets/5504953/0bcbb73c-b334-4a14-82cd-42966c2e8b12

![](../images/line2.png)

##### `Step 2.`\|`UE5MAT`|:small_blue_diamond: :small_blue_diamond: 

Now there is one thing we need to fix.  Open up **MF_Texture**, select the **Input** node. If the input is not named change name to `UVs`. Change the **Input Type** to `Function Input Vector 2`.  We just need a **U** and a **V** value and the default input was for a full **Vector 3**. Press the <kbd>Apply</kbd> button.

![change in put type to 2](images/changeInputType.png)

![](../images/line2.png)

##### `Step 3.`\|`UE5MAT`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Now lets make the final step and open up **M_SolidTexture**.  Drag a copy of **Materials | MaterialFunctions | MF_UVs** to the chart.  Plug the output into **MF_Texture | UV**. Press the <kbd>Apply</kbd> button.

![put uv material function to m_solid_texture](images/uvsToNode.png)

![](../images/line2.png)

##### `Step 4.`\|`UE5MAT`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Go back to the editor and open up **MI_WildGrass** next to it.  Notice that the sizes have all set back to the original default.

![editor with reset material](images/backToOne.png)

![](../images/line2.png)

##### `Step 5.`\|`UE5MAT`| :small_orange_diamond:

Set the **UV** multiplier back to 20. Now the scale is a lot better.

![uv multiplier is 20](images/uv20.png)

![](../images/line2.png)

##### `Step 6.`\|`UE5MAT`| :small_orange_diamond: :small_blue_diamond:

Now lets add the ability to rotate the texture to add another layer of customization. Open up **MF_UVs** and add a **Custom Rotator** node.

![add a custom rotator node](images/customRotator.png)

![](../images/line2.png)

##### `Step 7.`\|`UE5MAT`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

The custom rotator node has three inputs.  One is the UVs which will do the rotation.  The **Rotation Center** allows you to move where the texture rotates from.  We will leave this alone, as it is probably not needed very often.  The rotation angle is a scalar value between `0` and `1`.  This means that all values between 0° and 359° will be fractional between 0 and 1.  So a value of 180 would be 180/359 which is `0.5`.

![custom rotator node](images/threeInputs.png)

![](../images/line2.png)

##### `Step 8.`\|`UE5MAT`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Now take the output of the **Multiply** node and place it into the input **UVs** node in the **Custom Rotator**.  Take the **Return Value** and send it to the **Output UVs** node.  Select all of the 4 nodes and press the <kbd>C</kbd> key and add a comment `UV Adjustements` and select a color.  Right click on the open graph and select a **Scalar Parameter**.

![connect custom rotator and add scalar parameter](images/scalarAdjustments.png)

![](../images/line2.png)

##### `Step 9.`\|`UE5MAT`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Call this scalar parameter `UV Angle`.  Plug the output into the **Rotation Angle** pin of the **CustomRotator** node.  Change the group to `UV` and set the **Sort Priority** to `1`.  Make sure that **UV Multiplier** is in group to `UV` and set to **Sort Priority** of `0`. Now also we need to limit the number between 0 and 1.  So set the **Slider Min** to `0` and **Slider Max** to `1`.

![plug in uv angle and limit between 0 and 1](images/changeAngle.png)

![](../images/line2.png)

##### `Step 10.`\|`UE5MAT`| :large_blue_diamond:

Open up **MI_WildGrass** and adjust the UV angle between 0 and 1. Nwo pick an angle you like.  That will be it for room 2!

https://user-images.githubusercontent.com/5504953/185766950-79a0f8ad-0501-4090-9cf4-43dd57e0691a.mp4

![](../images/line2.png)

##### `Step 11.`\|`UE5MAT`| :large_blue_diamond: :small_blue_diamond: 

Select the **File | Save All** then press the <kbd>Source Control</kbd> button and select **Submit Content**.  If you are prompted, select **Check Out** for all items that are not checked out of source control. Update the **Changelist Description** message and with the latest changes. Make sure all the files are correct and press the <kbd>Submit</kbd> button. A confirmation will pop up on the bottom right with a message about a changelist was submitted with a commit number.

![save all and submit to perforce](images/submitP4.png)


![](../images/line.png)

<!-- <img src="https://via.placeholder.com/1000x100/45D7CA/000000/?text=Next Up - ADD NEXT TITLE"> -->
![next up next tile](images/banner.png)

![](../images/line.png)

| [previous](../solid-material-iii/README.md#user-content-solid-material-iii)| [home](../README.md#user-content-ue5-intro-to-materials) | [next](../color-math/README.md#user-content-material-color-math)|
|---|---|---|
