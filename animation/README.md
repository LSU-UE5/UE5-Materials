![](../images/line3.png)

### Animation

<sub>[previous](../refract-ii/README.md#user-content-refraction-and-fresnel-ii) • [home](../README.md#user-content-ue5-intro-to-materials) • [next](../animation-ii/README.md#user-content-animation-ii)</sub>

![](../images/line3.png)

Materials can also be animated.  You can make the texture move along the uv's and create interesting effects. You an also use time to animate various aspects of the material.

<br>

---


##### `Step 1.`\|`UE5MAT`|:small_blue_diamond:

We can animate many parts of a material.  There are too many to get into in one exercise. We will do two techniques.  This first is to animate a Linear Interpolation (LERP).  This allows us to change between two input pins gradually over time based on whether it is `0` - pin A or `1` - pin B. We will blend in black to have a flasing glow, like a flashing stop light.

Add a **Static Switch Paremeter** node and call it `FlashingEmissive?` and set the **Group** to `BaseColor` and the **Sort Priority** to `6`.

![add material ball to room](images/addStaticParameter.png)

![](../images/line2.png)

##### `Step 2.`\|`UE5MAT`|:small_blue_diamond: :small_blue_diamond: 

Now add a **Constant 3 Vector** and leave at at `0,0,0` (or black).  Add a **Lerp** node and plug the black vector into the **B** side of the lerp.  Then take the **ScaleEmission?** output node and put it in the **A** side of the **Lerp**.  Sned the **Lerp** to the **FlasingEmissive? | True** pin.  Send the output of the **FlasingEmissive?** node to the **UseBaseColorAlpha? | True** pin. Send the **ScaleEmission?** output pin to the **FlasingEmissive? | False** pin.

![add material ball to room](images/addLerp.png)

![](../images/line2.png)

##### `Step 3.`\|`UE5MAT`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Now to animate the Lerp we need the passage of time. Add the **Time** node to have a number that advances. Add a **Sine** node so this will give us a sine wave based on the speed of the time. So it will return a value of -1 to 1.  Now for the Lerp we want a value of 0 to 1.

![add material ball to room](images/addTime.png)

![](../images/line2.png)

##### `Step 4.`\|`UE5MAT`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

So we will now add `1` to the result of the Sine node.  This will bring the range from 0 to 2.  Now we want the lerp to go between 0 and 1 so we will divide the result of the addition by `2` by adding a **Divide** node.  Now send it to a saturate pin just in case to clamp the result between 0 and 1.  Then send the **Saturate** output pin to the **Lerp | Alpha** pin.

![add material ball to room](images/scaleAnims.png)

![](../images/line2.png)

##### `Step 5.`\|`UE5MAT`| :small_orange_diamond:

Scoot the camera over to **Room 8** and add a **Meshes | Supplied | SM_MatPreviewMesh_02** to the level changing its angle to face the middle of the room. Go to **Material Instances** and duplicate **MI_MarbleTile** and call it `MI_FlashingGlow`.

![add material ball to room](images/setUpRoom.png)

![](../images/line2.png)

##### `Step 6.`\|`UE5MAT`| :small_orange_diamond: :small_blue_diamond:

Open up **MI_FlashingGlow** and change **Parent** to `M_Emissive_MSRAO`.

![alt_text](images/changeParenttoEm.png)

![](../images/line2.png)

##### `Step 7.`\|`UE5MAT`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

Assign **MI_FlashingGlow** top the material ball in room 8.

![multiply glow color 2](images/assignGlow.png)

![](../images/line2.png)

##### `Step 8.`\|`UE5MAT`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

*Press* the <kbd>Play</kbd> button  and look at the animation. It went a bit fast for me so I added another **Divide** node and divided time by `4`.   I place dit inbetween the **Time** and **Sine** node to slow it down.  You could also add a **Scalar Parameter** so you can adjust the speed. Press the <kbd>Apply</kbd> button.

https://github.com/LSU-UE5/UE5-Materials/assets/5504953/06ef0a0a-6c3e-49aa-bfed-616aa9c15467

![](../images/line2.png)

##### `Step 9.`\|`UE5MAT`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:



![](../images/line2.png)

##### `Step 10.`\|`UE5MAT`| :large_blue_diamond:

![](../images/line2.png)

##### `Step 11.`\|`UE5MAT`| :large_blue_diamond: :small_blue_diamond: 


![](../images/line2.png)


##### `Step 12.`\|`UE5MAT`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: 

![](../images/line2.png)

##### `Step 13.`\|`UE5MAT`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 



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

Now the **Speed** is actually two floats.  So lets add two **Scalar Parameters** that we will leave at their `0` default value and call one `Speed X` and the other `Speed Y`.  Now these have to fit in a single **Speed** node we we will add an **Append** node that will make these two scalars a **Vector 2**.  Then pug the output of **Append** to the time node.  This way we can control the x and y direction seperately. 

Make the **Group** for both new parameters the same `UV` as the others and make the **Sort Priority** `3` and `4`. Add a comment node around the animation nodes and call it `Animate UVs`. Press the <kbd>Apply</kbd> button.

![add speed x and y then append](images/vector2Construct.png)


![](../images/line.png)

<!-- <img src="https://via.placeholder.com/1000x100/45D7CA/000000/?text=Next Up - Animation II"> -->
![next up next tile](images/banner.png)

![](../images/line.png)

| [previous](../refract-ii/README.md#user-content-refraction-and-fresnel-ii)| [home](../README.md#user-content-ue5-intro-to-materials) | [next](../animation-ii/README.md#user-content-animation-ii)|
|---|---|---|
