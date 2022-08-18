![](../images/line3.png)

### Solid Material

<sub>[previous](../basic-iii/README.md#user-content-basic-material-iii) • [home](../README.md#user-content-ue5-intro-to-materials) • [next](../)</sub>

![](../images/line3.png)

<img src="https://via.placeholder.com/1000x4/45D7CA/45D7CA" alt="drawing" height="4px"/>

So last chapter we looked at blending two solid colors on a model.  Now we can also control the color pixel by pixel on the UV's of the model.  So we can use texture maps and we will add another node we have not used yet.  The ambient occlusion node helps with lighting in the darker more shadowed parts of a model.

<br>

---


##### `Step 1.`\|`UE5MAT`|:small_blue_diamond:

Now we need to download some textures.  Download [T_WildGrass_BCH.png](../Assets/T_WildGrass_BCH.png), [T_WildGrass_N.png](../Assets/T_WildGrass_N.png) and [T_WildGrass_MSRAO.png](../Assets/T_WildGrass_MSRAO.png) to use in our game.

![download three textures](images/downloadThree.png)

![](../images/line2.png)

##### `Step 2.`\|`UE5MAT`|:small_blue_diamond: :small_blue_diamond: 

Create a new folders in **Textures** called `Surfaces`.  Drag and drop the three textures above you downloaded.

![download three textures in new surfaces folder](images/grabSurfaces.png)

![](../images/line2.png)

##### `Step 3.`\|`UE5MAT`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Double click and open **T_WildGrass.BCH**.  Now it will look strange with all of the channels including **Alpha** picked.  This is because we are channel packing.  Lets check that **sRGB** is on and it is using **Default Compression**.  This is what we want for our base color.  Most textures that are not in HDR are using sRGB color space. If yours are not then change it.

![wild grass bch file](images/baseAndHeight.png)

![](../images/line2.png)

##### `Step 4.`\|`UE5MAT`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

We are texture packing and if you select the **R,G,B** channels you will see the green grass texture.  If you select just the **A** alpha channel you will get a height map.  So in our naming of **T_WildGrass.BCH**, the BCH stands for Base Color & Height.

![packed maps](images/baseHeightSeperate.png)

![](../images/line2.png)

##### `Step 5.`\|`UE5MAT`| :small_orange_diamond:

Open up **T_WildGrass.N**.  The `_N` stands for normal map.  This uses the RGB channel.  We do not pack a texture in the **Alpha** channel as masks and textures use different compression. This compression is special compression for normals.  When we compress a normal texture we are cheating on details the eye has a hard time picking up.  We are saving space by fooling the human eye.  In normal maps, these are not pixels but each value represents a vector for the angle that light bounces off.  So the compression technique is different (and probably more lossless).

![normal compression](images/normalMapCompression.png)

![](../images/line2.png)

##### `Step 6.`\|`UE5MAT`| :small_orange_diamond: :small_blue_diamond:

![alt_text](images/.png)

![](../images/line2.png)

##### `Step 7.`\|`UE5MAT`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

![alt_text](images/.png)

![](../images/line2.png)

##### `Step 8.`\|`UE5MAT`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

![alt_text](images/.png)

![](../images/line2.png)

##### `Step 9.`\|`UE5MAT`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

![alt_text](images/.png)

![](../images/line2.png)

##### `Step 10.`\|`UE5MAT`| :large_blue_diamond:

![alt_text](images/.png)

![](../images/line2.png)

##### `Step 11.`\|`UE5MAT`| :large_blue_diamond: :small_blue_diamond: 

![alt_text](images/.png)

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

| [previous](../basic-iii/README.md#user-content-basic-material-iii)| [home](../README.md#user-content-ue5-intro-to-materials) | [next](../)|
|---|---|---|
