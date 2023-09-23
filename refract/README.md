![](../images/line3.png)

### Refraction and Fresnel

<sub>[previous](../decals-ii/README.md#user-content-decals-ii) • [home](../README.md#user-content-ue5-intro-to-materials) • [next](../refract-ii/README.md#user-content-refraction-and-fresnel-ii)</sub>

![](../images/line3.png)

How do we handle materials like glass that are subtle and reflect and distort the light moving through it?  Unreal gives us different strategies and some are more expensive than others.

<br>

---


##### `Step 1.`\|`UE5MAT`|:small_blue_diamond:

Download [M_CastleStructure.zip](../Assets/M_CastleStructure.zip).  *Right click* on **M_CastleStructure.zip** and select **Extract All**.  Select the **Materials | Supplied** folder and press the <kbd>Import</kbd> button and select **M_CastleStructure.gltf**. 

![open up Basic Materials 2 and pupulate room 7.](images/importModelsAndMaterials.png)

![](../images/line2.png)

##### `Step 2.`\|`UE5MAT`|:small_blue_diamond: :small_blue_diamond: 

Press the <kbd>Import</kbd> button with the default settings.  It will download the static mesh, materials and textures.

![open up Basic Materials 2 and pupulate room 7.](images/defaultImportSettings.png)

![](../images/line2.png)

##### `Step 3.`\|`UE5MAT`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Repeat this process for **M_CastleColumn.glhf**.

![open up Basic Materials 2 and pupulate room 7.](images/secondImport.png)

![](../images/line2.png)

##### `Step 4.`\|`UE5MAT`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Rename the static meshes to start with `SM_` instead of `M_` and rename the textures to start with `T_` instead of `M_`.  Move the meshes into the **Meshes | Supplied** folder and the textures to **Textures | Supplied** folder. 

![open up Basic Materials 2 and pupulate room 7.](images/renameFIles.png)

![](../images/line2.png)

##### `Step 5.`\|`UE5MAT`| :small_orange_diamond:

Double click **Maps | BasicMaterials2**.  Go to **Meshes | Supplied** and drag **SM_Castle_Column** and **SM_CastleStructure** multiple times in the scene in **Room 7**.  We will use these as backrounds that will show us behind thes glass.

![open up Basic Materials 2 and pupulate room 7.](images/addPropsRoom7.png)

![](../images/line2.png)

##### `Step 6.`\|`UE5MAT`| :small_orange_diamond: :small_blue_diamond:

Go to **Materials | Master** and *right click* on **M_TransparentMSRAO** and *select* **Duplicate**. Change the name to `M_Glass`. 

![add m_glass material](images/addMGlass.png)


![](../images/line2.png)

##### `Step 7.`\|`UE5MAT`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

We can leave **M_Glass** alone from now and create a material instance by right clicking on **M_Glass** and select **Create Material Instance**.  Call it `MI_Glass` and move it to the **Materials | Material Instances** folder.

![add m_glass material](images/createMI.png)

![](../images/line2.png)

##### `Step 8.`\|`UE5MAT`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Open up **MI_Glass** and change the base color tint to a light blue.

![add m_glass material](images/blueTint.png)

![](../images/line2.png)

##### `Step 9.`\|`UE5MAT`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Now we want to have an alpha scalar we can adjust. Open up **MF_BaseScalar** and right click on the **Scalar** value of `1.0` and select **Convert to Parameter** and call it `Alpha Scalar`.  Set the default value to `1.0` and make it **Group** `BaseColor` and **Sort Priority** of `5`. 

![add m_glass material](images/AlphaScalar.png)

![](../images/line2.png)

##### `Step 10.`\|`UE5MAT`| :large_blue_diamond:

Open up **MI_Glass** and turn **AlphaScalar** to `true`.  Now a value of `0.0` is completely transparent and a value of `1.0` is completely opaque.  So lets set it to `0.3` as a default value.  Notice the ball is transparent.  Now you can't see the other side, lets fix that.

![add m_glass material](images/setAlphaScalar.png)

![](../images/line2.png)

##### `Step 11.`\|`UE5MAT`| :large_blue_diamond: :small_blue_diamond: 

Open up **M_Glass** and turn **Two Sided** to `true`.  Press the <kbd>Apply</kbd> button. Now the rendering is broken in the material window but if you open up **MI_Glass** it is fine.

![add m_glass material](images/twoSided.png)

![](../images/line2.png)

##### `Step 12.`\|`UE5MAT`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: 

Now we want to add refraction to **M_Glass** as a glass bowl should act a lense and refract light. But our refraction pin is greyed out?  Go to the details panel and change the **Refraction Method** to `Index of Refraction`.

![add m_glass material](images/AddRefraction.png)

![](../images/line2.png)

##### `Step 13.`\|`UE5MAT`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 

Add a **Scalar Parameter** and call it `Refraction`. Set it to a default of `1.0` (no refraction).  Set the **Group** to `GlassPreoperties` and *Sort Priority** to `15`.

![add m_glass material](images/setRefraction.png)

![](../images/line2.png)

##### `Step 14.`\|`UE5MAT`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 

Now back in **MI_Glass** we can adust the **Refraction**.  Values between `0` and `1` make the refraction like a wide-angle lens and a value of above `1.0` to be like a zoom lens.

![add m_glass material](images/refractionEffects.png)

![](../images/line2.png)

##### `Step 15.`\|`UE5MAT`| :large_blue_diamond: :small_orange_diamond: 


Drag from **Mesh | Supplied | SM_MatPreviewMesh_02** into the scene. Rotate it to face forward. Assign **Materials | Surfaces | MI_GlassBasic** to the material ball. 

![drag material ball in scene](images/addMatBall.png)

![](../images/line2.png)

##### `Step 16.`\|`UE5MAT`| :large_blue_diamond: :small_orange_diamond:   :small_blue_diamond: 


 I find the glass a bit cloudy so I changee the **Opacity** on the material instance to 0.1.

![add material instance to ball](images/adjustAlphaClearer.png)

![](../images/line2.png)

##### `Step 17.`\|`UE5MAT`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

*Press* the <kbd>Play</kbd> button and run up to the material ball.  It looks good but we can make it better.

https://github.com/LSU-UE5/UE5-Materials/assets/5504953/6770ec34-437c-4bfc-bae7-e18735ba2137

![](../images/line2.png)

##### `Step 18.`\|`UE5MAT`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Turn off **MetallicUseMask?** and set the **Metalic Amount** to `1.0`. Change the **Specular Use Mask?** to `false` and set **Specular Amount** to `0.8`. Change the **RoughnessUseMask?** to `false` and change the **Roughness Amount** to `0.0`.  So we will make the glass really smooth and completely metalic which will help with the reflection and surface properties.

Now I find in game the glass a bit too transparent so I decide to change the **Alpha Scalar** to `2.0`.

![change metalic an droughness](images/changeRoughMet.png)

![](../images/line2.png)

##### `Step 19.`\|`UE5MAT`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Play the game and we have more convincing piece of glass.

![change metalic an droughness](images/moreConvincing.png)

![](../images/line2.png)

##### `Step 20.`\|`UE5MAT`| :large_blue_diamond: :large_blue_diamond:

Now we want the effect of the refraction to be greater at the edges.  So lets add a **Fresnel** node and a **Linear Interpolation** (Lerp) node to the node chart.

Change the **Refraction** scalar parameter to `RefractionEdges`.  Add another **Scalar Parameter** and call it `RefractionCenter`.  Make it a default value of `1.0` and put it in group **GlassProperties** and **Default Value** `16`.

Feed **RefractionCenter** into the **Lerp | A** channel.  Send **RefractionEdges** to the **Lerp | B** channel.  Send the **Fresnel** into the **Lerp | Alpha** channel. Send the output of the **Lerp** node to the **Refraction** pin. Press the <kbd>Apply</kbd> button.

![add fresnel and lerp nodes](images/hookUPFresnellLerp.png)

![](../images/line2.png)

##### `Step 21.`\|`UE5MAT`| :large_blue_diamond: :large_blue_diamond: :small_blue_diamond:

Go into the game and adjust the **RefractionEdges** on **MI_Glass** to `1.3` and the **RefractionCenter** to `1.08`.  This way we have less refraction in the center and more on the edges.  Now the sphere seems to be *more* 3-D.

![add fresnel and lerp nodes](images/addFresnelToMI.png)

![](../images/line.png)

<!-- <img src="https://via.placeholder.com/1000x100/45D7CA/000000/?text=Next Up - Refraction and Fresnel II"> -->
![next up next tile](images/banner.png)

![](../images/line.png)

| [previous](../decals-ii/README.md#user-content-decals-ii)| [home](../README.md#user-content-ue5-intro-to-materials) | [next](../refract-ii/README.md#user-content-refraction-and-fresnel-ii)|
|---|---|---|
