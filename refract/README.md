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

![alt_text](images/addMGlass.png)

![](../images/line2.png)

##### `Step 3.`\|`UE5MAT`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

![alt_text](images/addBaseColor.png)

![](../images/line2.png)

##### `Step 4.`\|`UE5MAT`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

![alt_text](images/shadingModel.png)

![](../images/line2.png)

##### `Step 5.`\|`UE5MAT`| :small_orange_diamond:

![alt_text](images/lightBlueGlass.png)

![](../images/line2.png)

##### `Step 6.`\|`UE5MAT`| :small_orange_diamond: :small_blue_diamond:

![alt_text](images/opacityScalarParameter.png)

![](../images/line2.png)

##### `Step 7.`\|`UE5MAT`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

![alt_text](images/point1ScalarRefaction.png)

![](../images/line2.png)

##### `Step 8.`\|`UE5MAT`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

![alt_text](images/TwoRefraction.png)

![](../images/line2.png)

##### `Step 9.`\|`UE5MAT`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

![alt_text](images/GroupSort.png)

![](../images/line2.png)

##### `Step 10.`\|`UE5MAT`| :large_blue_diamond:

![alt_text](images/miGlassBasic.png)

![](../images/line2.png)

##### `Step 11.`\|`UE5MAT`| :large_blue_diamond: :small_blue_diamond: 

![alt_text](images/addMatBall.png)

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
