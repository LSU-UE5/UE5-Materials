![](../images/line3.png)

### Refraction and Fresnel II

<sub>[previous](../refract/README.md#user-content-refraction-and-fresnel) • [home](../README.md#user-content-ue5-intro-to-materials) • [next](../animation/README.md#user-content-animation)</sub>

![](../images/line3.png)

<img src="https://via.placeholder.com/1000x4/45D7CA/45D7CA" alt="drawing" height="4px"/>

Now lets really move it up a notch and add a normal map to give the glass some texture.

<br>

---


##### `Step 1.`\|`UE5MAT`|:small_blue_diamond:

We can add another **Scalar Parameter** and set the default to `5`.  Call it `Fresnel Exponent` and attach it tohe the **ExponentIn** pin.  Now add a **Static Switch Parameter**.

![add scalar paramter called fresnel exponent](images/addFrenelExpScalarParam.png)

![](../images/line2.png)

##### `Step 2.`\|`UE5MAT`|:small_blue_diamond: :small_blue_diamond: 

Call this static switch `Use Normal?`.  Then add a **Textures | T_Base_N` to the graph.

![add static switch use normal?](images/staticSwitchNormal.png)

![](../images/line2.png)

##### `Step 3.`\|`UE5MAT`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Plug the output of the ***Texture Sample** to the **False** pin of the switch.  Add a **TextureSampleParameter2D** and call it `Normal`.  Set it to the **UseNormal? | True** pin.  Send the output of **Use Normal** to **Normal** in the shader node.

![connect parameters](images/param3DNormal.png)

![](../images/line2.png)

##### `Step 4.`\|`UE5MAT`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Assing the **Normal** texture to be `T_FrostedGlass` which I have supplied you.

![assign T_FrostedGlass](images/assignTFrostedGlass.png)

![](../images/line2.png)

##### `Step 5.`\|`UE5MAT`| :small_orange_diamond:

![alt_text](images/normalOnGlass.png)

![](../images/line2.png)

##### `Step 6.`\|`UE5MAT`| :small_orange_diamond: :small_blue_diamond:

![alt_text](images/useNormalFalsePrior.png)

![](../images/line2.png)

##### `Step 7.`\|`UE5MAT`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

![alt_text](images/dupicateMIGlassBasic.png)

![](../images/line2.png)

##### `Step 8.`\|`UE5MAT`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

![alt_text](images/miNormalGlass.png)

![](../images/line2.png)

##### `Step 9.`\|`UE5MAT`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

*Press* the <kbd>Play</kbd> button and go up to both glass material balls.  The textured one really stands out and the refraction is now even more exagerated.

https://user-images.githubusercontent.com/5504953/187051484-0466d17c-11b3-4988-81cb-fb7d4344e1e3.mp4

![](../images/line2.png)

##### `Step 10.`\|`UE5MAT`| :large_blue_diamond:

Now glass can pick up light so this is a bright room.  Lets add an edge glow.  Add a new **Scalar Parameter** called `Edge Glow` and set it's **Default Value** to `10`.

![add edge glow scalar](images/edgeGlowScalar.png)

![](../images/line2.png)

##### `Step 11.`\|`UE5MAT`| :large_blue_diamond: :small_blue_diamond: 

Add a new **Static Switch Parameter** and call it `Edge Glow?`.  Add a **Constant Scalar** set to `0` to the **False** pin.  Send the output of **Edge Glow?** to the **Emissive Color** pi9n on the material.

![add edge glow switch](images/staticSwitchEdge.png)

![](../images/line2.png)


##### `Step 12.`\|`UE5MAT`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: 

Add a **Multiply** node.  Send the output of the **Glass Color** to the **Multiply | A** and the **Edge Glow** to the **B** side.  Now add a **Fresnel** node.  Send the output to another new **Multiply | B** pin.  Send the first **Multiply** output into the **A** side of the second **Multiply** node.  Send the output to the **Edge Glow? | True** pin.  Now when it we have edge glow we can multiply the glass color with a fresnel (greater glow on the edges) to the material.

![multiply glow fresnel](images/multiplyGlowFresnel.png)

![](../images/line2.png)

##### `Step 13.`\|`UE5MAT`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 

On **Edge Glow** set the **Group** to `SurfaceProperties` and **Sort Priority** to `4`.

![set group and sort](images/setGlowProperties.png)

![](../images/line2.png)

##### `Step 14.`\|`UE5MAT`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 

Right click on **Material | Surfaces | M_GlassNormal** and select **Duplicate**.  Call this `MI_GlassGlow`.  Copy and paster another material ball and title to the right.  Call the title text `MI_GlassGlow`.  Drag the **MI_GlassGlow** material onto this third material ball.

![alt_text](images/miGlassGLow.png)

![](../images/line2.png)

##### `Step 15.`\|`UE5MAT`| :large_blue_diamond: :small_orange_diamond: 

Open up **MI_GlassGlow** and set **EdgeGlow** to true.  Adjust the **Edge Glow** amount to your liking.  I set mine to `.5` as I want a subtle effect.

![alt_text](images/tweakEdgeGLow.png)

![](../images/line2.png)

##### `Step 16.`\|`UE5MAT`| :large_blue_diamond: :small_orange_diamond:   :small_blue_diamond: 

*Press* the <kbd>Play</kbd> button and now look at all three material balls.  We have made progressive improvements and our third ball is terrific!

https://user-images.githubusercontent.com/5504953/187051495-bd6a6f21-9790-49b5-89b8-1b49716a05c0.mp4

![](../images/line2.png)

##### `Step 17.`\|`UE5MAT`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

Go to the **Outliner** and make sure eveything is in **Room 7**.  Rename items so they make sense.

![organize outliner](images/organizeOutliner.png)

![](../images/line2.png)

##### `Step 18.`\|`UE5MAT`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Select the **File | Save All** then press the <kbd>Source Control</kbd> button and select **Submit Content**.  If you are prompted, select **Check Out** for all items that are not checked out of source control. Update the **Changelist Description** message and with the latest changes. Make sure all the files are correct and press the <kbd>Submit</kbd> button. A confirmation will pop up on the bottom right with a message about a changelist was submitted with a commit number.

![save all and submit to perforce](images/submitP4.png)

![](../images/line.png)

<!-- <img src="https://via.placeholder.com/1000x100/45D7CA/000000/?text=Next Up - Animation"> -->
![next up next tile](images/banner.png)

![](../images/line.png)

| [previous](../refract/README.md#user-content-refraction-and-fresnel)| [home](../README.md#user-content-ue5-intro-to-materials) | [next](../animation/README.md#user-content-animation)|
|---|---|---|