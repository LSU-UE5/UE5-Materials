![](../images/line3.png)

### Basic Material III

<sub>[previous](../basic-ii/README.md#user-content-basic-material-ii) • [home](../README.md#user-content-ue5-intro-to-materials) • [next](../solid-material/README.md#user-content-solid-material)</sub>

![](../images/line3.png)


Final clean up of room 1.

<br>

---


##### `Step 1.`\|`UE5MAT`|:small_blue_diamond:

Now make sure all the material balls are in the **Room 1** folder.  Also, give them appropriate names.  I have named the material balls and the materials so I know which one pairs with which one.

![name objects in room 1](images/nameRoom1.png)

![](../images/line2.png)

##### `Step 2.`\|`UE5MAT`|:small_blue_diamond: :small_blue_diamond: 

Now you can add some more materials to test out the material instance in this room if you like.  Then play the game, make sure everything is to your liking.

https://user-images.githubusercontent.com/5504953/185446475-3f9fc9c9-ac30-4016-8016-86c348917640.mp4


![](../images/line2.png)

##### `Step 3.`\|`UE5MAT`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Create a new folder called **Materials | MaterialInstances** and drag the material instances (all files with `MI_` from the **Master** folder to the **Material Instances** folder.

![move instances into own folder](images/moveRename.png)

![](../images/line2.png)

##### `Step 4.`\|`UE5MAT`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:


Select the **File | Save All** then press the <kbd>Revision Control</kbd> button and select **Submit Content**.  If you are prompted, select **Check Out** for all items that are not checked out of revision control. Update the **Changelist Description** message and with the latest changes. Make sure all the files are correct and press the <kbd>Submit</kbd> button. A confirmation will pop up on the bottom right with a message about a changelist was submitted with a commit number.

https://user-images.githubusercontent.com/5504953/185447657-6a67db19-b2c8-4eef-88d1-05c0ffd41009.mp4

![](../images/line2.png)

##### `Step 5.`\|`UE5MAT`| :small_orange_diamond:

Sometimes not all files get submitted to Unreal especially for files that don't show up in the editor.  It is good practice one you submit in **Unreal** and quit the game to right click on the top most project folder and select **Reconcile Offline Work...**.

This will either give a message saying ther is nothing to reconcile or bring up a tab.  Make sure that these are **NOT** files in the **Intermediate** and **Saved** folders as these should be ignored from the `.p4ignore`.

If the files are in **Content** or **Configuration** then press the <kbd>Reconcile</kbd> button.  Then submit the changes with a message and press the <kbd>Submit</kbd> button.

![reconcile offline work](images/reconcile.png)

![](../images/line.png)

<!-- <img src="https://via.placeholder.com/1000x100/45D7CA/000000/?text=Next Up - Solid Material"> -->
![next up next tile](images/banner.png)

![](../images/line.png)

| [previous](../basic-ii/README.md#user-content-basic-material-ii)| [home](../README.md#user-content-ue5-intro-to-materials) | [next](../solid-material/README.md#user-content-solid-material)|
|---|---|---|
