![](../images/line3.png)

### Refraction and Fresnel

<sub>[previous](../decals-ii/README.md#user-content-decals-ii) • [home](../README.md#user-content-ue5-intro-to-materials) • [next](../refract-ii/README.md#user-content-refraction-and-fresnel-ii)</sub>

![](../images/line3.png)

<img src="https://via.placeholder.com/1000x4/45D7CA/45D7CA" alt="drawing" height="4px"/>

How do we handle materials like glass that are subtle and reflect and distort the light moving through it?  Unreal gives us different strategies and some are more expensive than others.

<br>

---


##### `Step 1.`\|`UE5MAT`|:small_blue_diamond:

Double click **Maps | BasicMaterials2**.  Go to **Meshed | Supplied** and drag **SM_Castle_Column** and **SM_CastleStructure** multiple times in the scene in **Room 7**.  We will use these as backrounds that will show us behind thes glass.

![open up Basic Materials 2 and pupulate room 7.](images/addPropsRoom7.png)

![](../images/line2.png)

##### `Step 2.`\|`UE5MAT`|:small_blue_diamond: :small_blue_diamond: 

Go to **Materials | Master** and press the <kbd>+ Add</kbd> button.  Create a new **Material** called `M_Glass`.

![add m_glass material](images/addMGlass.png)

![](../images/line2.png)

##### `Step 3.`\|`UE5MAT`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Add a **Vector 3 Parameter** called `Glass Color`.  Set the **Group** to `Base Color` and **Sort Priority** to `0`.

![add vector 3 parameter glass color](images/addBaseColor.png)

![](../images/line2.png)

##### `Step 4.`\|`UE5MAT`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Select **M_Glass** and change the **Shading Model** to `Translucent`.  We want it to be glass so we have to see through it. Set **Two Sided** to `true`.

![translucent shading model](images/shadingModel.png)

![](../images/line2.png)

##### `Step 5.`\|`UE5MAT`| :small_orange_diamond:

Select a light blue color and connect the white pin in **Glass Color** to the **Base Color** pin.

![make color light blue connect glass color pin](images/lightBlueGlass.png)

![](../images/line2.png)

##### `Step 6.`\|`UE5MAT`| :small_orange_diamond: :small_blue_diamond:

Add a **Scalar Parameter** called `Opacity` and set the **Default Value** to `0.3` and the **Slider Max** to `1`.  We cannot have an opacity that is less than 0 or greater than one.

![set default value to .3](images/opacityScalarParameter.png)

![](../images/line2.png)

##### `Step 7.`\|`UE5MAT`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

Create another **Scalar Parameter** and call it `Refraction`.  Set it to `.1`.  Make a comment around the **Opacity** and **Refraction** nodes with comment `Surface Properties`.  The highlight the base color node and press the <kbd>C</kbd> button and nake the comment `Base Color`.  Change the colors to separate the comments.

Notice that a value of `.1` turns the sphere into a wide angle lens.

![set scalar paramter refractoin to .1](images/point1ScalarRefaction.png)

![](../images/line2.png)

##### `Step 8.`\|`UE5MAT`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

If you set the **Refraction | Default Value** to `2.0`, notice that we get a magnifying effect.

![2 magnifies](images/TwoRefraction.png)

![](../images/line2.png)

##### `Step 9.`\|`UE5MAT`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Set **Opacity** to **Group** `SurfaceProperties` and **Sort Priority** `0`.  Set **Refraction** to **Group** `SurfaceProperties` and **Sort Priority** `1`.

![set priorities](images/GroupSort.png)

![](../images/line2.png)

##### `Step 10.`\|`UE5MAT`| :large_blue_diamond:

Go to **Materials | Master** and right click on **M_Glass** and select **Create Material Instance**.  Call this instance `MI_GlassBasic` and move to the **Materials | Surface** folder.

![create mi_glassbasic as instance of mi_glass](images/miGlassBasic.png)

![](../images/line2.png)

##### `Step 11.`\|`UE5MAT`| :large_blue_diamond: :small_blue_diamond: 

Drag from **Mesh | Supplied | SM_MatPreviewMesh_02** into the scene. Rotate it to face forward.

![drag material ball in scene](images/addMatBall.png)

![](../images/line2.png)


##### `Step 12.`\|`UE5MAT`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: 

![alt_text](images/addMIGlassBasic.png)

![](../images/line2.png)

##### `Step 13.`\|`UE5MAT`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 

![alt_text](images/changeLightingMode.png)

![](../images/line2.png)

##### `Step 14.`\|`UE5MAT`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 

![alt_text](images/changeRoughMet.png)

![](../images/line2.png)

##### `Step 15.`\|`UE5MAT`| :large_blue_diamond: :small_orange_diamond: 

![alt_text](images/fresnelLerp.png)

![](../images/line2.png)

##### `Step 16.`\|`UE5MAT`| :large_blue_diamond: :small_orange_diamond:   :small_blue_diamond: 

![alt_text](images/hookUPFresnellLerp.png)

![](../images/line2.png)

##### `Step 17.`\|`UE5MAT`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

![alt_text](images/lessopaqueWhiter.png)

![](../images/line2.png)

##### `Step 18.`\|`UE5MAT`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

![alt_text](images/centerRefract.png)

![](../images/line2.png)

##### `Step 19.`\|`UE5MAT`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

![alt_text](images/miBasicTextTitle.png)

![](../images/line2.png)

##### `Step 20.`\|`UE5MAT`| :large_blue_diamond: :large_blue_diamond:

![alt_text](images/addFrenelExpScalarParam.png)

![](../images/line2.png)

##### `Step 21.`\|`UE5MAT`| :large_blue_diamond: :large_blue_diamond: :small_blue_diamond:

![alt_text](images/.png)


![](../images/line.png)

<!-- <img src="https://via.placeholder.com/1000x100/45D7CA/000000/?text=Next Up - Refraction and Fresnel II"> -->
![next up next tile](images/banner.png)

![](../images/line.png)

| [previous](../decals-ii/README.md#user-content-decals-ii)| [home](../README.md#user-content-ue5-intro-to-materials) | [next](../refract-ii/README.md#user-content-refraction-and-fresnel-ii)|
|---|---|---|
