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

Press the <kbd>+ Add</kbd> button.  Create a new material to place on this plane.  Call it `M_TwoSide_Poster`.  Make sure it is in the **Materials | Master** folder.

![add new material](images/newTwoSidedMat.png)

![](../images/line2.png)

##### `Step 6.`\|`UE5MAT`| :small_orange_diamond: :small_blue_diamond:



![](../images/line2.png)

##### `Step 7.`\|`UE5MAT`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:


![](../images/line2.png)

##### `Step 8.`\|`UE5MAT`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Drag **T_Base_MSRAO** to the **Textures** directory.

![](images/copyMRAO.png)

![](../images/line2.png)

##### `Step 9.`\|`UE5MAT`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:
 


![](../images/line2.png)

##### `Step 10.`\|`UE5MAT`| :large_blue_diamond:

Drag the **Player Start** actor to the front of room 5.

![move player start to room 5](images/movePlayerStartToRm5.png)

![](../images/line2.png)

##### `Step 11.`\|`UE5MAT`| :large_blue_diamond: :small_blue_diamond: 


![](../images/line2.png)


##### `Step 12.`\|`UE5MAT`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: 



![](../images/line2.png)

##### `Step 13.`\|`UE5MAT`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 



![](../images/line2.png)

##### `Step 14.`\|`UE5MAT`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 



![](../images/line2.png)

##### `Step 15.`\|`UE5MAT`| :large_blue_diamond: :small_orange_diamond: 

Open up the materail and add a **T_Base_MSRAO** texture to the level.  Connect the output pins with the pins of the same name on the main materail node.

![add ceil node](images/connetMatPropPins.png)

![](../images/line2.png)

##### `Step 16.`\|`UE5MAT`| :large_blue_diamond: :small_orange_diamond:   :small_blue_diamond: 

Open up **M_TwoSide_Poster**. Add a **Texture Sample Parameter 2D** node and assign the **T_PosterSide1** to it. Call it `Front of Poster`.

![add clamp node](images/frontTexture.png)

![](../images/line2.png)

##### `Step 17.`\|`UE5MAT`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

Repeat this for **T_PoserSide2** and assign texture **T_PosterSide2_BC** and call it `Back of Poster`.

![add clamp node](images/backOfPoster.png)

![](../images/line2.png)

##### `Step 18.`\|`UE5MAT`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Add a **Linear Interpolation** (LERP) ndoe to the level. Plug in the two textures to the **A** and **B** input.  Remember the A side of the LERP is shown when **Alpha** is `0` and the **B** input when the Alpha is `1`. It is a blend when it is between 0 and 1.

![group and comment nodes](images/addLerpNode.png)

![](../images/line2.png)

##### `Step 19.`\|`UE5MAT`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Add a **Camera Vector WS** and **Vertex Normal WS** node.  This will be the start of our vector arithmetic to determine the side of the plane that the player (camera) is on. The camera looks at us, and the vertex normal looks at foraward from the player's point of view. 

If the camera angle and the vertex normal angle (the direction of the face of the polygon) are facing each other then the return value is > 0 and if they are not facing each other will return a value that is < 0.

![group and comment nodes](images/CmVectorVertexNrml.png)


![](../images/line2.png)

##### `Step 20.`\|`UE5MAT`| :large_blue_diamond: :large_blue_diamond:

Add a **Dot Product** node and connect the two vectors to the inputs.  This will multiply them together and return a single vector. We need a bit of calculus and look at two vectors, the camera and the plane normal in world space.  We take the dot product of both.  If it is negative the lines are looking away from each other if it is above 0 they were looking at each other.  We will round up the dot product and use the Lerp even so that there is only going to be 0 and 1 out of the Lerp node. Now we will set a ceiling by adding a ceil node so it rounds up to an interger.

![group and comment nodes](images/dotCeiling.png)

![](../images/line.png)

<!-- <img src="https://via.placeholder.com/1000x100/45D7CA/000000/?text=Next Up - Two Sided Materials II"> -->
![next up next tile](images/banner.png)

![](../images/line.png)

| [previous](../illumination-ii/README.md#user-content-emissive-material-ii)| [home](../README.md#user-content-ue4-intro-to-materials) | [next](../two-sided-ii/README.md#user-content-two-sided-material-ii)|
|---|---|---|
