![](../images/line3.png)

### Animation

<sub>[previous](../) • [home](../README.md#user-content-ue5-intro-to-materials) • [next](../)</sub>

![](../images/line3.png)

<img src="https://via.placeholder.com/1000x4/45D7CA/45D7CA" alt="drawing" height="4px"/>

Materials can also be animated.  You can make the texture move along the uv's and create interesting effects. You an also use time to animate various aspects of the material.

<br>

---


##### `Step 1.`\|`UE5MAT`|:small_blue_diamond:

We can animate many parts of a material.  There are too many to get into in one exercise. We will do two techniques.  This first is to animate a Linear Interpolation (LERP).  This allows us to change between two input pints gradually over time based on whether it is `0` - pin A or `1` - pin B. Scoot the camera over to **Room 8** and add a **Meshes | Supplied | SM_MatPreviewMesh_02** to the level changing its angle to face the middle of the room.

![add material ball to room](images/dragBallToRoom.png)

![](../images/line2.png)

##### `Step 2.`\|`UE5MAT`|:small_blue_diamond: :small_blue_diamond: 

Create a new **Material** in the **Materials | Master** called `M_AnimatedGlow`.

![create new material called M_AnimatedGlow](images/newMaster.png)

![](../images/line2.png)

##### `Step 3.`\|`UE5MAT`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Add a **Vector Parameter** node and name it `Glow Color`. Make it a bright vibrant color and connect the output to **Base Color**.

![add vector parameter called glow color to base color pin](images/textureParameter.png)

![](../images/line2.png)

##### `Step 4.`\|`UE5MAT`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Add three **Scalar Parameters**.  The first is called `Metallic` with a value of `0`.  The second is `Specular` with a value of `0.5` and the final is called `Roughness` with a value of `0`.

![add three scalar parameters](images/addThreeScalarParams.png)

![](../images/line2.png)

##### `Step 5.`\|`UE5MAT`| :small_orange_diamond:

Add a **LinearInterpolate** (LERP) node. We are going to have no flashing glow at the B input so add a **Constant** node and leave it as its default `0` and place it in the **B** pin of the LERP node. Add comment box around **Surface Properties** and **Base Color** and organize your node chart.

![lerp and constant node](images/firstLerpNode.png)

![](../images/line2.png)

##### `Step 6.`\|`UE5MAT`| :small_orange_diamond: :small_blue_diamond:

Add a **Vector Parameter** node calling it `Glow Color 2` and make it a slightly different version of the first color.  Plug the white output to the **Lerp | A** node.

![alt_text](images/glowColor2.png)

![](../images/line2.png)

##### `Step 7.`\|`UE5MAT`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

Add a **Multiply** node.  Feed the output of the **Constant 3 Vector** into the **A** input of a **Multiply** node.

Add a **Multiply** node with the **A** pin begin between **Base Color 2** and **Lerp | A** nodes.  Add another **Constant Scalar** and make it a value of `20`.  Remember that the illumination channel takes values over 1.0 to be even brighter (making the color more white, the hotter it gets). Send the output of **Lerp** to the **Emissive** color node on the main shader node.

![multiply glow color 2](images/multiplyGlow2.png)

![](../images/line2.png)

##### `Step 8.`\|`UE5MAT`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

So when the Alpha in the LERP node is set to `1` we get no glow as it selects the B input which sends 0 to the glow. Change the Alpha to `0` and you get the A input which is a multiplied glow. Notice how it lights the ground!  This is new to UE5.

![alt_text](images/lerpOneZero.png)

![](../images/line2.png)

##### `Step 9.`\|`UE5MAT`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Add a **Time** node. This will return the time from the computer.  We then feed it into a **Sine** node.  This converts it to a sine wave which is a smooth wave going between -1 and 1.  So we need to get it to go between 0 and 1, so we put an **Add** node after and add a avlue of `2`, bringing the curve to a value of 0 to 2.  Then we **Divide** it by `2` in a new **Divide** node to bring it back to a value of 0 to 1.

![time sign normalize](images/timeSine.png)

![](../images/line2.png)

##### `Step 10.`\|`UE5MAT`| :large_blue_diamond:

Add a **Saturate** node to clamp the value between 0 and 1 just in case it goes beyond this range for whatever reason.  Plug the output of the **Saturate** node to the input pin on the **Lerp | Alpha**.

![saturate to alpha](images/saturateAlpha.png)

![](../images/line2.png)

##### `Step 11.`\|`UE5MAT`| :large_blue_diamond: :small_blue_diamond: 

Adjust the **Group** and **Sort Priority** of all the parameters in this master material.

![mast glow animation sort and groups](images/groupsPrioritiesGlow.png)

![](../images/line2.png)


##### `Step 12.`\|`UE5MAT`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: 

![alt_text](images/.png)

![](../images/line2.png)

##### `Step 13.`\|`UE5MAT`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 

![alt_text](images/.png)

![](../images/line2.png)

##### `Step 14.`\|`UE5MAT`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 

![alt_text](images/.png)

![](../images/line2.png)

##### `Step 15.`\|`UE5MAT`| :large_blue_diamond: :small_orange_diamond: 

![alt_text](images/.png)

![](../images/line2.png)

##### `Step 16.`\|`UE5MAT`| :large_blue_diamond: :small_orange_diamond:   :small_blue_diamond: 

![alt_text](images/.png)

![](../images/line2.png)

##### `Step 17.`\|`UE5MAT`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

![alt_text](images/.png)

![](../images/line2.png)

##### `Step 18.`\|`UE5MAT`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

![alt_text](images/.png)

![](../images/line2.png)

##### `Step 19.`\|`UE5MAT`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

![alt_text](images/.png)

![](../images/line2.png)

##### `Step 20.`\|`UE5MAT`| :large_blue_diamond: :large_blue_diamond:

![alt_text](images/.png)

![](../images/line2.png)

##### `Step 21.`\|`UE5MAT`| :large_blue_diamond: :large_blue_diamond: :small_blue_diamond:

![alt_text](images/.png)


![](../images/line.png)

<!-- <img src="https://via.placeholder.com/1000x100/45D7CA/000000/?text=Next Up - ADD NEXT TITLE"> -->
![next up next tile](images/banner.png)

![](../images/line.png)

| [previous](../)| [home](../README.md#user-content-ue5-intro-to-materials) | [next](../)|
|---|---|---|
