![](../images/line3.png)


### Two Sided Material

<sub>[previous](../illumination-ii/README.md#user-content-emissive-material-ii) • [home](../README.md#user-content-ue4-intro-to-materials) • [next](../two-sided-ii/README.md#user-content-two-sided-material-ii)</sub>

![](../images/line3.png)

Normals point in a single direction so we don't waste compute cycles calculating how light reacts to the inside of shapes that we can't see or enter.  In some cases we want both sides of a polygon to have normals.  You can make adjustments in the shader to affect this without having to do anything in a 3-D modeling package.

<br>

---

##### `Step 1.`\|`UE5MAT`|:small_blue_diamond:

Lets put a poster in the middle of **Room 5**.  Lets put a separate image on each side of a flat plane like having a poster floating in the middle of the room.  Now go to the **Textures | Props** folder and import **[T_PosterSide1_BC.tga](../Assets/T_PosterSide1_BC.tga)** and **[T_PosterSide2_BC.tga](../Assets/T_PosterSide2_BC.tga)**. Drag then into the **Textures | Props** folder

![drag poster files to unreal](images/copyPosterTexture.png)

![](../images/line2.png)

##### `Step 2.`\|`UE5MAT`|:small_blue_diamond: :small_blue_diamond: 

Enter modelling mode and select a **Rect**.  Make the **Width** and **Dept** `400` cm square.  Make the **Width Subdivsions** & **Depth Subdivision** `5`. Place the plane in the level.  Rotate it to face the camera. Press the <kbd>Complete</kbd> button.

![enter moeeling mode and add plane](images/make300Plane.png)


![](../images/line2.png)

##### `Step 3.`\|`UE5MAT`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Go to **Transform | BaseRS** and make sure **BakeRotation** is set to `true`. Press the <kbd>Acept</kbd> button.  Now you will see that the rotation zeroes out and the plan faces towards the camera and is no longer paralell to the ground.

![bake rotation](images/bakeRotation.png)

![](../images/line2.png)

##### `Step 4.`\|`UE5MAT`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Go to **UVs | Layout** and change the **Material Mode** to `Checkerboard`. The uvs are looking good. Press the <kbd>Accept</kbd> button.

![check uvs](images/checkUVs.png)

![](../images/line2.png)

##### `Step 5.`\|`UE5MAT`| :small_orange_diamond:

*Right click* on **Materials | Master | M_Opaque_MSRAO** and duplicate it calling the new material `M_TwoSided_Poster`.

![add new material](images/newTwoSidedMat.png)

![](../images/line2.png)

##### `Step 6.`\|`UE5MAT`| :small_orange_diamond: :small_blue_diamond:

We need to add a second texture to use for the other side of the post. Open up **M_TwoSided_Poster** and add a **TextureSampleParemeter2D** node. and call it `Back of Poster`.  Put it in category **Back of Poster** and make it a **Sort Priority** of `10`.

![add new material](images/addSecondTexture.png)

![](../images/line2.png)

##### `Step 7.`\|`UE5MAT`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

Add a **Camera Vector WS** and **Vertex Normal WS** node.  This will be the start of our vector arithmetic to determine the side of the plane that the player (camera) is on. 

the Vertex Normal WS is used to calculate the direction of the surface normal at a particular vertex in world space, while the Camera Vector WS is used to calculate the position of the camera in world space. The Vertext Normal returns a vector that is perpendicular to the plane the camera is looking at the the camera returns the vector of where the camera is looking.

![group and comment nodes](images/CmVectorVertexNrml.png)

![](../images/line2.png)

##### `Step 8.`\|`UE5MAT`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Now if we take the dot product of the two vectors we can determine if we are looking at one side of the poster or ther other.   If the dot product of two vectors is greater than 0, then both vectors are pointing in the same direction. If the dot product is less than 0, then the two vectors are facing in opposite directions.

The dot product returns a range between -1 and 1.  So if we take the output of the dot product and then round up (**ceil** takes it to the next highest integer) we will be a value of 0 (when the vectors point away from each other) or 1 (when the vectors are facing each other).

![group and comment nodes](images/dotAndCeil.png)


![](../images/line2.png)

##### `Step 9.`\|`UE5MAT`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:
 
Even though it is not necessary it is never a bad idea to add **Saturate** node to limit the return value between 0 and 1.  

We can use this 0 or 1 to drive a LERP node to show 100% of the A image or 100% of the B image (and never a value in between.  Add a **Linear Interpolation** (LERP) ndoe to the level. Plug in the two textures to the **A** and **B** input.  Remember the A side of the LERP is shown when **Alpha** is `0` and the **B** input when the Alpha is `1`. It is a blend when it is between 0 and 1.

Click on the main material node and make sure **Two Sided** is set to `true`.

![group and comment nodes](images/addLerpNode.png)


![](../images/line2.png)

##### `Step 10.`\|`UE5MAT`| :large_blue_diamond:

Now assign a material to the **BackOfPoster** and rotate around the plane, you should see two images - one on each side.

https://github.com/LSU-UE5/UE5-Materials/assets/5504953/8b465714-12a3-4526-b1ce-1786a0b4e23d

![](../images/line2.png)

##### `Step 11.`\|`UE5MAT`| :large_blue_diamond: :small_blue_diamond: 

Right click on **Materials | M_TwoSidedPoster** and select **Create Material Instance** and call it `MI_TwoSidedPoster`.  Move it to the **Materials |  Material Instances** folder.

![group and comment nodes](images/createMI.png)

![](../images/line2.png)


##### `Step 12.`\|`UE5MAT`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: 

Go back to the editor and assign the **MI_TwoSidedPoster** to the plane.

![group and comment nodes](images/assignMat.png)

![](../images/line2.png)

##### `Step 13.`\|`UE5MAT`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 

Drag the **Player Start** actor to the front of room 5.

![move player start to room 5](images/movePlayerStartToRm5.png)

![](../images/line2.png)

##### `Step 14.`\|`UE5MAT`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 

 Play the game and make sure the poster works correctly.

https://github.com/LSU-UE5/UE5-Materials/assets/5504953/2a8ee51f-a0a3-476d-8972-30644c303ecc

![](../images/line2.png)

##### `Step 15.`\|`UE5MAT`| :large_blue_diamond: :small_orange_diamond: 

We might want to reuse this double sided node somewhere else so it is worth turning it into a **Material Function**.  Select the **Materials | Material Functions** folder and create a new **Material | Material Function** and acall it `MF_BackSideReverse`. 

Open up **M_TwoSidedPoster** and copy and cut all the new non material function nodes out of it.

![move player start to room 5](images/createMF.png)

![](../images/line2.png)

##### `Step 16.`\|`UE5MAT`| :large_blue_diamond: :small_orange_diamond:   :small_blue_diamond: 

Open up the new **Material Function** and paste the nodes into it. We now need the **A** side of the lerp and need to input this from the base material function.  Right click on the graph and select a **Input Function** node.

![add clamp node](images/pastMF.png)

![](../images/line2.png)

##### `Step 17.`\|`UE5MAT`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

![add clamp node](images/mfInput.png)

![add clamp node](images/.png)

![](../images/line2.png)

##### `Step 18.`\|`UE5MAT`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

![add clamp node](images/completeMat.png)


![](../images/line.png)

<!-- <img src="https://via.placeholder.com/1000x100/45D7CA/000000/?text=Next Up - Two Sided Materials II"> -->
![next up next tile](images/banner.png)

![](../images/line.png)

| [previous](../illumination-ii/README.md#user-content-emissive-material-ii)| [home](../README.md#user-content-ue4-intro-to-materials) | [next](../two-sided-ii/README.md#user-content-two-sided-material-ii)|
|---|---|---|
