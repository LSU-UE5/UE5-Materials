![](../images/line3.png)

### Solid Material II

<sub>[previous](../solid-material/README.md#user-content-solid-material) • [home](../README.md#user-content-ue5-intro-to-materials) • [next](../)</sub>

![](../images/line3.png)

<img src="https://via.placeholder.com/1000x4/45D7CA/45D7CA" alt="drawing" height="4px"/>

Now lets use material functions and instances with this master material to make it scalable and reusable.

<br>

---


##### `Step 1.`\|`UE5MAT`|:small_blue_diamond:

Now we don't want our master material to have a recognizable texture in it.  We want those to be assigned in the material instance.  So we will create one white and a normal map that is small.  Now for textures to look good the engine uses a technique called [Mip Mapping](https://en.wikipedia.org/wiki/Mipmap) to make the textures look good.  This is making sure that instead of scaling the texture in real time for every object, it prescales the textures and picks the closest side needed by the renderer on that one frame.

The mip map holds sizes from 1 pixel upwards.  So if a texture is 512 by 512, the mip map will contain the 512, 256, 128, 64, 32, 16, 8, 4, 2, 1 pixel sizes.  It would be combined to one texture sheet like the example from Wikipedia shown.

![mip map texture](images/MipMap_Example_STS101.jpg)

![](../images/line2.png)

##### `Step 2.`\|`UE5MAT`|:small_blue_diamond: :small_blue_diamond: 

Now if we open up **T_WildGrass_BCH** you can see we have 13 mip levels. You can switch between them to see how they look and you can see the display size being updated.  Now since it is power of 2 it is able to simply average pixel groups to get a high quality reduction.

https://user-images.githubusercontent.com/5504953/185605473-400a3d46-2334-4baa-a807-489c72a35d90.mp4

![](../images/line2.png)

##### `Step 3.`\|`UE5MAT`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

So what happens if we have a texture that is not square.  Lets look.  Download [T_BadTexture.png](../Assets/T_BadTexture.png).  Drag and drop it in the **Texture | Surfaces** folder. Open it up.  Now look that there is only one mip level.  This is because the texture is 45 x 45 pixels.  A texture to work properly needs to be a power of two.  It needs to be 1, 2, 4, 8, 16, 32, 64, 128, 256, 512, 1024, 2048, 4096, or 8192 (if your video card can support it).  Now both axis don't need to be the same so you can have a texture that is 2048 x 256, this will mip properly.

![bad mip levels](images/oneMipLev.png)

![](../images/line2.png)

##### `Step 4.`\|`UE5MAT`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

OK, so lets create a new small texture in photoshop that we will use as stand ins for our master material.  Make it `32` pixels square with a **White** background. Press the **Create** button.

![create a new blank material](images/newMat.png)

![](../images/line2.png)

##### `Step 5.`\|`UE5MAT`| :small_orange_diamond:

*Press* the **File | Save As** and call it `T_BaseWhite_BC`. Select **png** as our file format and press the <kbd>Save</kbd> button.

![save as t_basewhite_bc](images/saveAsPNG.png)

![](../images/line2.png)

##### `Step 6.`\|`UE5MAT`| :small_orange_diamond: :small_blue_diamond:

Now click on the foreground color swatch and lets make a neutral normal map (all normals perpendicular) which is 50% **RG** and 100% **B**. So set **R** & **G** to `127` and **B** to `255`.

![neutral normal map](images/neutralNormal.png)

![](../images/line2.png)

##### `Step 7.`\|`UE5MAT`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

Now select the fill tool and fill the white square with this neutral normal map color.  Press **File | Save As** and call it `N_Base_N` as type `.png`.  Press the <kbd>Save</kbd> button.

![save normal map version](images/tbaseNormal.png)

![](../images/line2.png)

##### `Step 8.`\|`UE5MAT`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Drag the two textures you just exported from photoshop into the **Textures** folder.

![drag to textures in folder](images/dragToTextures.png)

![](../images/line2.png)

##### `Step 9.`\|`UE5MAT`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Open up both textures and make sure they have mip levels and that the normal is recognized and uses **Normal** compression.  

![confirm both textures](images/checkTexture.png)

![](../images/line2.png)

##### `Step 10.`\|`UE5MAT`| :large_blue_diamond:

Open up **M_SolidTexture** and delete all of the texture nodes.  We will replace them with a material function.

![delete all nodes in M_SolidTexture](images/deleteStext.png)

![](../images/line2.png)

##### `Step 11.`\|`UE5MAT`| :large_blue_diamond: :small_blue_diamond: 

Select the **MaterialFunction** folder and press the <kbd>+ Add</kbd> button and select **Material | Material Function**.  Call this material function `MF_Texture`.

![create material function MF_Texture](images/mf_texturecreate.png)

![](../images/line2.png)


##### `Step 12.`\|`UE5MAT`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: 

Open up **MF_Texture**> Drag **T_BaseWhite_BC** and **T_Base_N** into the graph of **MF_Texture**.

![drag two textures to MF_Texture graph](images/dragTToMat.png)

![](../images/line2.png)

##### `Step 13.`\|`UE5MAT`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 

![alt_text](images/outputBC.png)

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

| [previous](../solid-material/README.md#user-content-solid-material)| [home](../README.md#user-content-ue5-intro-to-materials) | [next](../)|
|---|---|---|
