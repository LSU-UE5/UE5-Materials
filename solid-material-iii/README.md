![](../images/line3.png)

### Solid Material III

<sub>[previous](../solid-material-ii/README.md#user-content-solid-material-ii) • [home](../README.md#user-content-ue5-intro-to-materials) • [next](../solid-material-iv/README.md#user-content-solid-material-iv)</sub>

![](../images/line3.png)

Chapter introduction here.

<br>

---


##### `Step 1.`\|`UE5MAT`|:small_blue_diamond:

Now go into the game and you will notice that our material ball is white based on the this neutral master texture.  We will fix this.

![white material ball in game](images/whiteBall.png)

![](../images/line2.png)

##### `Step 2.`\|`UE5MAT`|:small_blue_diamond: :small_blue_diamond: 

*Right click* on **M_SolidTexture** and select **Create Material Instance** and call it `MI_WildGrass`. Move **MI_WildGrass** into the **Materials | Surface** folder.   

![create mis_wild grass material instance from solid texture](images/createMIWIldGrass.png)

![](../images/line2.png)

##### `Step 3.`\|`UE5MAT`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

*Select* the material ball and change the **Materials | Element 0** to `MI_WildGrass`. You can change the material by just dragging it onto the model itself and it will light up the area of the model that is changing.

![assign mi_wild grass to material ball in room 2](images/moveAssign.png)

![](../images/line2.png)

##### `Step 4.`\|`UE5MAT`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Open up **MI_WildGrass** and turn on editing on the three textures.  Assign the **Base Color** the texture `T_WildGrass_BCH`, the **Normal Map** the texture `T_WildGrass_N` and finally the four masks the texture `T_Wildgrass_MSRAO`.  Now run the game and you will see that it is back to using the grass texture we originally imported.

https://github.com/LSU-UE5/UE5-Materials/assets/5504953/c54ddcba-1c19-4ecb-a5fd-21256ed7b7f2

![](../images/line2.png)

##### `Step 5.`\|`UE5MAT`| :small_orange_diamond:

If you go to **Meshes | Supplied** and hover the cursor over **SM_Wall** you can get the dimensions of the wall which is 1000 cm squared. This is used for the walls and the floor.

![get wall size](images/wallSize.png)

![](../images/line2.png)

##### `Step 6.`\|`UE5MAT`| :small_orange_diamond: :small_blue_diamond:

Enter modeling mode and select a **Shapes | Rect** to create a plane for the ground to old the grass.  Make it a **Width** of `1000` and a **Depth** of `3000` and a height of `10`.  Set the **Width Subdivision** to `10` and the **Depth Subdivision to `30`. Set **Align to Normal** to `false`.

Place it on the floor and select the <kbd>Accept</kbd> button.

https://github.com/LSU-UE5/UE5-Materials/assets/5504953/7e82def3-c043-4dcd-bcff-390950df6337

![](../images/line2.png)

##### `Step 7.`\|`UE5MAT`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

Position the model in room so it lines up with the floor textures.   Adjust the height so it doesn't get buried by the existing floor or have any rendering issues fighting with it (1 unit above essentially).

![position floor piece](images/positionInRoom.png)

![](../images/line2.png)

##### `Step 8.`\|`UE5MAT`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Go the the **UVs | Layout** and change the **Material Mode** to `Checkerboard`.  Now in my case the UVs look good so I am leaving them alone and pressing the <kbd>Accept</kbd> button.

![confirm uvs are correct](images/UVCheckerboard.png)

![](../images/line2.png)

##### `Step 9.`\|`UE5MAT`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Select the ground plane in the editor and right click and select **Browse to Asset**.  Now rename the mesh `SM_Ground`. Create a new folder under **Meshes** called `Surfaces`.  Drag `SM_Ground` and **Move** it into the new **Meshes | Surfaces** folder.

![find and rename mesh sm_ground](images/findRenameGround.png)

![](../images/line2.png)

##### `Step 10.`\|`UE5MAT`| :large_blue_diamond:

After moving it is always a good idea to right click **Content** and select **Fix up Redirects in Folder**, to clean up the hierachy.  Otherwise hidden files remain that redirect files from their original folder.

![fix up redirects](images/fixUpRedirects.png)

![](../images/line2.png)

##### `Step 11.`\|`UE5MAT`| :large_blue_diamond: :small_blue_diamond: 

Now drag and drop **MI_WildGrass** onto the ground plane.

![add mi_wild grass to plane](images/addWIldGrassM.png)

![](../images/line2.png)


##### `Step 12.`\|`UE5MAT`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: 

*Press* the <kbd>Play</kbd> button and walk around.  Your camera is at 6' in height and the grass texture looks enormous and wrong.  We are 6' off of the ground and it feels like our head is 6" off the ground. Now we can adjust the amount of tiling (size of each tiles) within each object.  Lets add this to our material functions.

![grass is wrong](images/addWIldGrassM2.png)

![](../images/line2.png)

##### `Step 13.`\|`UE5MAT`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 

Now go to the **Materials | Material Functions** folder and right click on the empty area and create a new **Material | Material Function**.  Call it `MF_UVs`.  We will scale the UVs to change the size of the texture and how it tiles.

![add texture coordinates](images/textCoord.png)

![](../images/line2.png)

##### `Step 14.`\|`UE5MAT`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 

Open up the material function and change the name of the output node to `UVs`.  Add a **Texture Coordinate** node.  Then add a **Scalar Parameter** node and call it `UVScalar`.  Set the **Parameter Name** to `UV Scalar`, the **Group** to `UVs` and the **Sort Priority** to `60`.  Add a **Multiply** node and multiply the **UV** by the **Scalar**.  Send the result to the **Output** node.

![add texture coordinates](images/uvScaling.png)

![](../images/line2.png)

##### `Step 15.`\|`UE5MAT`| :large_blue_diamond: :small_orange_diamond: 

Now open up **MF_BaseTexture** and we need to add a **Function Input** node so we can inject the UV's into this material function. Call it **Input UV** and add a default **TextCoord** node as a **Preview** value.  This will make it easier to see what each material function is doing if you need to debug it.

![add texture coordinates](images/AddUvToBaseColor.png)

![](../images/line2.png)

##### `Step 16.`\|`UE5MAT`| :large_blue_diamond: :small_orange_diamond:   :small_blue_diamond: 

Repeat this for **MF_MSRAO** and **MF_Normal**. Add inputs and call them **Input UV**.  Connect a default **TextCoord** node as a **Preview** value. Send the output into the texture input for the UV Scaling.

![add a scalar parameter and mutltiply node](images/2MoreUVs.png)

![](../images/line2.png)

##### `Step 17.`\|`UE5MAT`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:


Now in **MI_WildGrass** it is black and we are getting an error saying there is nothing plugged into the UV Inputs.  This needs to be fixed in the master material.  Open up **M_OpaqueMSRAO** and see there is an error on each of the material functions.

![connect to multiply node](images/uvInputError.png)

![](../images/line2.png)

##### `Step 18.`\|`UE5MAT`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

In **M_OpaqueMSRAO** drag **MF_UVs** and connect it the output pin to **MF_BaseTexture**, **MF_RSAO** and **MF_Normal** as they all require a UV input.

![add material function MF_UVs](images/addMFUV.png)

![](../images/line.png)

<!-- <img src="https://via.placeholder.com/1000x100/45D7CA/000000/?text=Next Up - ADD NEXT TITLE"> -->
![next up next tile](images/banner.png)

![](../images/line.png)

| [previous](../solid-material-ii/README.md#user-content-solid-material-ii)| [home](../README.md#user-content-ue5-intro-to-materials) | [next](../solid-material-iv/README.md#user-content-solid-material-iv)|
|---|---|---|
