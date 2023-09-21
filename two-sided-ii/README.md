![](../images/line3.png)

### Two Sided Material II

<sub>[previous](../two-sided/README.md#user-content-two-sided-material) • [home](../README.md#user-content-ue5-intro-to-materials) • [next](../decals/README.md#user-content-decals)</sub>

![](../images/line3.png)

Lets finish up with the two sided material.

<br>

---


##### `Step 1.`\|`UE5MAT`|:small_blue_diamond:

Clean up the **World Outliner** by naming the file correctly 

![alt_text](images/cleanUpOutliner.png)


![](../images/line2.png)

##### `Step 2.`\|`UE5MAT`|:small_blue_diamond: :small_blue_diamond: 

![alt_text](images/renamAssignMat.png)

![](../images/line2.png)

##### `Step 3.`\|`UE5MAT`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

![alt_text](images/moveToProps.png)

![](../images/line2.png)

##### `Step 4.`\|`UE5MAT`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Now change the **Preview Mesh** to a **Plane** and rotate around it.  Notice that you are not able to see both sides and the back of the poster is comletely transparent (lacks face normals).

Now make sure you are highlighting the main node and look for **Two Sided** and set it to `True`. We should now have both sides rendering (even though only 1 side has normals).

Now the wrong side is showing so we need to reverse which node is going into the **A** and **B** channel of the **LERP** node.

https://user-images.githubusercontent.com/5504953/186299029-7adae8eb-496b-40d7-a247-f30ab56772b8.mp4

![](../images/line2.png)

##### `Step 5.`\|`UE5MAT`| :small_orange_diamond:

Place the **M_TwoSidedPoster** and assign it to the plane in the game in room 5. Rotate the poster so it is upright.  Play the game and make sure the poster works correctly.

https://user-images.githubusercontent.com/5504953/186299085-b2419fc5-17a3-4150-9e32-121294a767fa.mp4

![](../images/line2.png)

##### `Step 6.`\|`UE5MAT`| :small_orange_diamond: :small_blue_diamond:

Select the **File | Save All** then press the <kbd>Revision Control</kbd> button and select **Submit Content**.  If you are prompted, select **Check Out** for all items that are not checked out of source control. Update the **Changelist Description** message and with the latest changes. Make sure all the files are correct and press the <kbd>Submit</kbd> button. A confirmation will pop up on the bottom right with a message about a changelist was submitted with a commit number.

![alt_text](images/submitP4.png)

![](../images/line.png)

<!-- <img src="https://via.placeholder.com/1000x100/45D7CA/000000/?text=Next Up - Decals"> -->
![next up next tile](images/banner.png)

![](../images/line.png)

| [previous](../two-sided/README.md#user-content-two-sided-material)| [home](../README.md#user-content-ue5-intro-to-materials) | [next](../decals/README.md#user-content-decals)|
|---|---|---|
