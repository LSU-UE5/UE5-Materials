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

Open up **T_WildGrass.N**.  The `_N` stands for normal map.  This uses the RGB channel.  We do not pack a texture in the **Alpha** channel as masks and textures use different compression. This compression is special compression for normals.  When we compress a normal texture we are cheating on details the eye has a hard time picking up.  We are saving space by fooling the human eye.  In normal maps, these are not pixels but each value represents a vector for the angle that light bounces off.  So the compression technique is different (and probably more lossless). Most of the time Unreal will select a normal map compression but if it doesn't change the **Compression Settings** to `Normalmap`.

![normal compression](images/normalMapCompression.png)

![](../images/line2.png)

##### `Step 6.`\|`UE5MAT`| :small_orange_diamond: :small_blue_diamond:

Open up **T_WildGrass_MSRAO**.  `_MSRAO` stands for Metallic (packed in R), Specular (packed in S), Roughness (packed in R), and Ambient Occlusion (packed in AO). Notice that the metallic and specular are solid black.  That means there is no metallic or specularity in the grass.  There are textures though for roughness and for ambient occlusion. "_For example, the interior of a tube is typically more occluded (and hence darker) than the exposed outer surfaces, and becomes darker the deeper inside the tube one goes._". So in the top picture is the scene. The middle is the ambient occlusion map and the bottom photo is the render including ambient occlusion.  So you get better definition of darker areas and the scene is higher contrast and more realistic.

![msrao packed](images/tpackingh.png)

![](../images/line2.png)

##### `Step 7.`\|`UE5MAT`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

[Ambient Occlusion](https://en.wikipedia.org/wiki/Ambient_occlusion) is a single channel grayscale to help the renderer calculate how an area is exposed to ambient light. 

![alt_text](images/AmbientOcclusion_German.jpg)

* image from Wikipedia

![](../images/line2.png)

##### `Step 8.`\|`UE5MAT`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Go to the **Materials | Master** folder and press the <kbd>+ Add</kbd> button.  Select a new **Material** and call it `M_SolidTexture`.

![create M_SolidTexture material](images/solidTextMat.png)

![](../images/line2.png)

##### `Step 9.`\|`UE5MAT`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Open up **M_SolidTexture**.  Open up the **Content Drawer** (cntrl space bar) and drag the three textures you added to the **Textures | Surfaces** folder onto the graph.

![add three textures to msolidtexture](images/dragThreeText.png)

![](../images/line2.png)

##### `Step 10.`\|`UE5MAT`| :large_blue_diamond:

Now select the texture sample with **T_WildGrass_BCH** and select the **RGB** pin at the top and drag it to **Base Color** in the material node.  Now it is very important not to select the RGBA as we do not have a translucency in this material.  We are packing a heigh map in the alpha channel and don't want it poluting the base color. Press the <kbd>Apply</kbd> button.

![attach _bch texture to base color](images/attachBaseColor.png)

![](../images/line2.png)

##### `Step 11.`\|`UE5MAT`| :large_blue_diamond: :small_blue_diamond: 

Duplicate a ball/text pair from room 1 and drag it into room 2 (you can hold alt while both objects are selected). 

![dupe ball and text in room 2](images/dupeBall.png)

![](../images/line2.png)


##### `Step 12.`\|`UE5MAT`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: 

Select the text in Room 2 and change it to **M_SolidTexture**. Now you notice that without the other masks that this doesn't look anything like wild grass.  Lets change that.

![change text to m_solidtexture](images/changeMSolid.png)

![](../images/line2.png)

##### `Step 13.`\|`UE5MAT`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 

Assign to **Material | Element 0** the **M_SolidTexture** material. 

![assign solid texture material](images/materialGrass.png)

![](../images/line2.png)

##### `Step 14.`\|`UE5MAT`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 

Now select the normal map texture, **T_WildGrass_N**.  Double check that the **Sampler Type** is set to `Normal`.  Connect the **RGB** pin to the **Normal** pin in the material.  Press the <kbd>Apply</kbd> button. Now you can see that there is more detail.  It is still too shiny and the roughness and specular are wrong.

![add normal map to material](images/normalMapText.png)

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
