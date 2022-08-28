![](../images/line3.png)

### Animation

<sub>[previous](../refract-ii/README.md#user-content-refraction-and-fresnel-ii)) • [home](../README.md#user-content-ue5-intro-to-materials) • [next](../animation-ii/README.md#user-content-animation-ii)</sub>

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

Add a **Time** node. This will return the time from the computer.  We then feed it into a **Sine** node.  This converts it to a sine wave which is a smooth wave going between -1 and 1.  So we need to get it to go between 0 and 1, so we put an **Add** node after and add a avlue of `2`, bringing the curve to a value of 0 to 2.  Then we **Divide** it by `2` in a new **Divide** node to bring it back to a value of 0 to 1. Press the <kbd>Apply</kbd> button.

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

Right click on **M_AnimatedGlow** and select **Create Material Instance**.  Call it `MI_AnimatedGLow`.
Drag it into the **Materials | Surfaces** folder.  Drag it onto the material ball.

![create MI_AnimatedGLow](images/makeMaterialInstance.png)

![](../images/line2.png)

##### `Step 13.`\|`UE5MAT`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 

*Press* the <kbd>Play</kbd> button  and look at the animation. It went a bit fast for me so I added another **Divide** node and divided time by `4`.   I place dit inbetween the **Time** and **Sine** node to slow it down.  You could also add a **Scalar Parameter** so you can adjust the speed. Press the <kbd>Apply</kbd> button.

![create MI_AnimatedGLow](images/divideNode.png)

![](../images/line2.png)

##### `Step 14.`\|`UE5MAT`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 

*Press* the <kbd>Play</kbd> button and I like the speed better.

https://user-images.githubusercontent.com/5504953/187080763-a41f368f-0763-44a1-a8ad-d124a09c71c2.mp4

![](../images/line2.png)

##### `Step 15.`\|`UE5MAT`| :large_blue_diamond: :small_orange_diamond: 

OK, lets animate the UV's so the texture inside the material animates.  Right click on **Material | Master |  M_EmissiveTexture** and select **Create Material Instance**.  Call it `MI_Chevron`.  Drag it to the **Materials | Surfaces** folder and move it there.

![create mi_chevron](images/createChevron.png)

![](../images/line2.png)

##### `Step 16.`\|`UE5MAT`| :large_blue_diamond: :small_orange_diamond:   :small_blue_diamond: 

Download [T_Chevron_BC.tga](../Assets/T_Chevron_BC.tga) and drag it to to your **Textures | Surfaces** folder.  A chevron is the sign on the road that tells you that the road is curving.  It is a simple black and white texture that we will use as a mask reusing the illumination mask material but adding functionality to the UVs. 

![drag T_Chevron_BC to textures folder](images/chrevron.png)

![](../images/line2.png)

##### `Step 17.`\|`UE5MAT`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

Open up **MI_Chevron** and assign the **Base Color** as `T_Chevron_BC`. Notice the glow.

![assign T_Chevron_BC](images/openChevron.png)

![](../images/line2.png)

##### `Step 18.`\|`UE5MAT`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Select the **Place Actors** menu and select **Shapes | Plane** and drag it into Room 8.  Rotate it so it faces the camera and change the **Transform | Scale** to `4`, `2`, `1`.  Drag **MI_Chevron** onto the plane to use as its material.  It lights up but doesn't animate.

![add plane with mi_chevron](images/addPlane.png)

![](../images/line2.png)

##### `Step 19.`\|`UE5MAT`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Duplicate the plane and place it next to it so we have two chevrons right next to each other.

![duplicate chevron](images/DupeChevron.png)

![](../images/line2.png)

##### `Step 20.`\|`UE5MAT`| :large_blue_diamond: :large_blue_diamond:

Open up **MF_UVs** and add a **Panner** node between the **Custom Rotator** and the **Output UVs** node.  Notice it has a **Speed X** and **Speed Y** of `0`.  This means there is no panning.  We will leave these defaults as we don't want all our other textures to pan.

![add panner node](images/addPanner.png)

![](../images/line2.png)

##### `Step 21.`\|`UE5MAT`| :large_blue_diamond: :large_blue_diamond: :small_blue_diamond:

Now the **Speed** is actually two floats.  So lets add two **Scalar Parameters** that we will leave at their `0` default value and call one `Speed X` and the other `Speed Y`.  NOw these have to fit in a single **Speed** node we we will add an **Append** node that will make these two scalars a **Vector 2**.  Then pug the output of **Append** to the time node.  This way we can control the x and y direction seperately.

![add speed x and y then append](images/vector2Construct.png)


![](../images/line.png)

<!-- <img src="https://via.placeholder.com/1000x100/45D7CA/000000/?text=Next Up - Animation II"> -->
![next up next tile](images/banner.png)

![](../images/line.png)

| [previous](../refract-ii/README.md#user-content-refraction-and-fresnel-ii))| [home](../README.md#user-content-ue5-intro-to-materials) | [next](../animation-ii/README.md#user-content-animation-ii)|
|---|---|---|
