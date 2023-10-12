![](../images/line3.png)

### Masks, Opacity & Translucent

<sub>[previous](../color-math/README.md#user-content-material-color-math) • [home](../README.md#user-content-ue4-intro-to-materials) • [next](../translucent/README.md#user-content-masks-opacity--translucent-ii)</sub>

![](../images/line3.png)

We can also use the multiplication node with black and white textures to act as a mask (like in Photoshop).  We are also able to change the mode from **Solid** to **Opacity Mask** to **Translucent**.  We will investigate all of this in room 3. 

<br>

---


##### `Step 1.`\|`UE5MAT`|:small_blue_diamond:

Open up the editor and move the **Player Start** actor to **Room 3**.

![move playerstart to room 3](images/moveRoom3.png)

![](../images/line2.png)

##### `Step 2.`\|`UE5MAT`|:small_blue_diamond: :small_blue_diamond: 

Lets open up **MF_MSRAO**.  If we don' thave a mask for a particular channel (commmon with metallic and specular) or just want to overide the texture with a single value for all pixels.  Lets add this support.  Right click on the graph to add a **Static Switch Parameter**.  Call it `MetallicUseMask?`and **Default Value** it to `true`. Change the **Group** to `Surface Properties` and the **Sort Priority** to `21`.

![add material called M_MetalMask](images/AddSwitchMetallic.png)

![](../images/line2.png)

##### `Step 3.`\|`UE5MAT`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Add a **Scalar Parameter** node and call it `MetallicAmount`.  Leave the default at `0`. Set the Change the **Group** to `Surface Properties` and the **Sort Priority** to `22`. Connect the ouput of the **Scalar Paremeter** to the **MetallicUseMas? | False** pin.  So if we choose not to use the mask in the texture provided we can have a number used across the entire material. 

![add a tcircle texture and mf_base color material function](images/MetallicAmount.png)

![](../images/line2.png)

##### `Step 4.`\|`UE5MAT`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Connect the Red Pin from the texture not to the **MetallicUseMask? | True** pin.  Connect the output of the **MetallicUseMask?** to the **Metallic Output** node.

Repeat this entire process for specular by adding a **Static Switch Parameter**.  Call it `SpecularUseMask?`and **Default Value** it to `true`. Change the **Group** to `Surface Properties` and the **Sort Priority** to `23`. Add a **Scalar Parameter** node and call it `SpecularAmount` and change the default to `0.5`.  Connect the output pin to the **SpecularUseMask | False** pin. Change the **Group** to `Surface Properties` and the **Sort Priority** to `24`. Connect the **SpecularUseMask?** to the **Output Specular** node.  Connect the Green Pin from the texture to the **SpecularUseMask? | True** pin. 

![connect add to render node](images/specularSwitch.png)
![](../images/line2.png)

##### `Step 5.`\|`UE5MAT`| :small_orange_diamond:

Repeat this entire process for specular by adding a **Static Switch Parameter**.  Call it `RoughnessUseMask?`and **Default Value** it to `true`. Change the **Group** to `Surface Properties` and the **Sort Priority** to `25`. Add a **Scalar Parameter** node and call it `RoughnessAmount` and change the default to `0.5`.  Connect the output pin to the **RoughnessUseMask | False** pin. Change the **Group** to `Surface Properties` and the **Sort Priority** to `26`. Connect the **RoughnessUseMask?** to the **Output Specular** node.  Connect the Blue Pin from the texture to the **RoughnessUseMask? | True** pin. 

![add constant node, set to 0 and add to roughness](images/roughnessSwitch.png)

![](../images/line2.png)

##### `Step 6.`\|`UE5MAT`| :small_orange_diamond: :small_blue_diamond:

Do this one final time and add a **Static Switch Parameter**.  Call it `AOsUseMask?`and **Default Value** it to `true`. Change the **Group** to `Surface Properties` and the **Sort Priority** to `27`. Add a **Scalar Parameter** node and call it `AOAmount` and change the default to `1`.  Connect the output pin to the **AOUseMask | False** pin. Change the **Group** to `Surface Properties` and the **Sort Priority** to `28`. Connect the **AOUseMask?** to the **Output Specular** node.  Connect the White A Pin from the texture to the **AOUseMask? | True** pin.

![move cam to room 3 and add a cube to room](images/AOSwitch.png)
![](../images/line2.png)

##### `Step 7.`\|`UE5MAT`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

Go to the **Materials | Material Instances** folder and right click on **MI_WildGrass** and select **Duplicate**.  Call this new material instance `MI_MetallicMaskExample`.

![add cube to level](images/DupeMIForMask.png)

![](../images/line2.png)

##### `Step 8.`\|`UE5MAT`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Create a new folder under **Textures** called `Masks`. PDrag and drop into thi folder **Import** and select **[T_Circle_BC.png](../Assets/T_Circle_BC.png)**, **[T_CircleMask_01.png](../Assets/T_CircleMask_01.png)** and **[T_CircleMask_02.png](../Assets/T_CircleMask_02.png)**. Double click and see that it is a power of 2 texture and is 512 x 512 with 10 MIP levels.  It is duotone with just black and white.

![add circlemask_d.tga to project](images/tcirclemaskimport.png)

![](../images/line2.png)

##### `Step 9.`\|`UE5MAT`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:


Press the **Place Actors** button and select a **Shape | Cube** to drop in the level.  Position it on the left side of the room. Click the Lock icon next to the **Transform | Scale**. Set the **Scale** to `2.0` to double the size of the cube in all 3 dimensions.

![add cube to level](images/doubleScale.png)


![](../images/line2.png)

##### `Step 10.`\|`UE5MAT`| :large_blue_diamond:

*Drag* the **MI_MetallicExample** material instance to the cube.

![add cube to level](images/addMIMask.png)

![](../images/line2.png)

##### `Step 11.`\|`UE5MAT`| :large_blue_diamond: :small_blue_diamond: 

Open up **MI_MetallicExample** and change the **Base Color** to `T_Circle_BC`.  Change the **Base Color Tint** to a color of your choice so we have a bit of contrast on the dot.

![add cube to level](images/tintNewText.png)

![](../images/line2.png)


##### `Step 12.`\|`UE5MAT`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: 

Assign `T_Base_N` to the normal map to get rid of the grassy bump.  Then we will be playing with a metallic mask.  So turn off **SpecularUseMask?**,. **RoughnessUseMask?**, **AOUseMasks?**.

![remove three masks and disable normal](images/remove3Masks.png)

![](../images/line2.png)

##### `Step 13.`\|`UE5MAT`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 

Now lets create a mask to have some parts metal and some parts not.  Remember **black** or `0` will be no metal and white `1` will be metal.  It is recommended that you use either black or white to make it metal or not metal.  Update the **Metallic | Specular | Roughness | AO** map with `T_CicleMask_01`.  Change the roughness to `0` to exaggerate the metalic effect and make it really obvious.

https://github.com/LSU-UE5/UE5-Materials/assets/5504953/3d00f9a3-caf9-4cf4-95c7-b6df1ffe676b

![](../images/line2.png)

##### `Step 14.`\|`UE5MAT`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 

Now what if we wanted to invert the mask to get the metal inside the dot.  We can duplicate the **Cube** by <kbd>alt</kbd> clicking the transform and make another cube.  Then duplicate **MI_Metallic_Example** and call it `MI_Metallic_ExampleInvert`.  Change the **Base Color Tint** and change the **Metallic | Specular | Roughness | AO** to `T_CircleMask_02`.  Notice the dots are white so it is the only spot that will be metallic.

![remove three masks and disable normal](images/invertMask.png)

![](../images/line2.png)

##### `Step 15.`\|`UE5MAT`| :large_blue_diamond: :small_orange_diamond: 

Lets add an alpha channel to our base material.  Open up **MF_BaseTexture** and add another **Function Output** node.  Call it `Alpha` and set the **Sort Priority** to `1`.

![remove three masks and disable normal](images/dupeOutputAlpha.png)

![](../images/line2.png)

##### `Step 16.`\|`UE5MAT`| :large_blue_diamond: :small_orange_diamond:   :small_blue_diamond: 

Add a **Static Switch Parameter** node and call it `UseBaseColorAlpha`.  Set the **Sort Priority** to `1` and **Group** to **BaseColor**. Add a **Scalar Paremeter** node and set it to `1.0` and put it to the false pin.  So what will happen if it is false then an alpha channel of `1` (completely opaque) will be sent to the alpha channel node.  Take the **Base Color | A** pin and send it into the **UseBaseColorAlpha | True** pin.  Send the output to the new **Output Alpha** node. 

![remove three masks and disable normal](images/addAlpha.png)

![](../images/line2.png)

##### `Step 17.`\|`UE5MAT`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

Now open up **M_OpaqueMSRAO**.  Now we have the ability to activate the opacity channels.  Take the new **Alpha** pin output from **MF_Base_Color** that we just added and feed it into the **Opacity Mask** node in the main render node.

Now it connects but is greyed out.  You can switch the **Blend Mode** to `Masked` and the pin is now highlighted.  DO NOT DO THIS, we will activate it in the material instance.  Press the <kbd>Apply</kbd> button and we will get back to creating an alpha hole.

![connect texture sample to opacity mask](images/addOpacityMask.png)

![](../images/line2.png)

##### `Step 18.`\|`UE5MAT`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Download [T_GradientMask.tif](../Assets/T_GradientMask.tif) and add it to your **Textures | Masks** folder.

![set two sided to true](images/bringGradientTexture.png)

![](../images/line2.png)

##### `Step 20.`\|`UE5MAT`| :large_blue_diamond: :large_blue_diamond:

Now if you look at the this texture in **RGBA** node you see that it has holes cut out.  In the **RGB** channel it is an opaque gradient.  In the Alpha channel you can see black dots.  Now a mask mode does not have levels of transulcency.  It is transparent or opaque (binary, one or the other).  The only color that will create the mask it pure black (rgb 0,0,0).  So those black dots are pure black.  They will cut holes in masked mode.

![set two sided to true](images/rgba.png)

![](../images/line2.png)

##### `Step 21.`\|`UE5MAT`| :large_blue_diamond: :large_blue_diamond: :small_blue_diamond:

Duplicate the cube and drag a third copy into the room. Right click on **MI_Metallic_ExampleInvert** and duplicate the material instance. Drag this new material instance onto the third cube.

![attach metallic, specular and roughness pins](images/connectRestOfPins.png)

![](../images/line.png)

<!-- <img src="https://via.placeholder.com/1000x100/45D7CA/000000/?text=Next Up - Masks, Opacity and Translucent II"> -->
![next up next tile](images/banner.png)

![](../images/line.png)

| [previous](../color-math/README.md#user-content-material-color-math)| [home](../README.md#user-content-ue4-intro-to-materials) | [next](../translucent/README.md#user-content-masks-opacity--translucent-ii)|
|---|---|---|
