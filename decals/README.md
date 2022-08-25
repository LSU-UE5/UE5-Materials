![](../images/line3.png)

### Decals

<sub>[previous](../two-sided-ii/README.md#user-content-two-sided-material-ii) • [home](../README.md#user-content-ue4-intro-to-materials) • [next](../refract/README.md#user-content-refraction-and-fresnel)</sub>

![](../images/line3.png)

We can also change materials dynamically by using decals.  These can be placed over existing materials and cover mesh and uv boundaries. So you can add graphiti to a wall made up of diverse meshes with multiple UVs.  This does require transparencies so it will not work on nanite meshes.

<br>

---


##### `Step 1.`\|`UE5MAT`|:small_blue_diamond:

Lets start by moving the **Player Start** actor to the front of room 6.

![move player start](images/movePlayerStart.png)

![](../images/line2.png)

##### `Step 2.`\|`UE5MAT`|:small_blue_diamond: :small_blue_diamond: 

Right click on the double sided poster in Room 5 and select **Browse to Asset**.  Rename it to `SM_Plane` and move it to the **Basic Geometry** folder.

![rename plane to SM_Plane and put in Basic Geometry folder](images/basicPlane.png)

![](../images/line2.png)

##### `Step 3.`\|`UE5MAT`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Add the **SM_Plane** to Room 6 on the ground.

![add plane to room 6](images/AddPlaneToGround.png)

![](../images/line2.png)

##### `Step 4.`\|`UE5MAT`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Lift the plane up and press the <kbd>End</kbd> key to get it to the ground.  Now when a plane is on top of a plane you will get **Z Fighting** which looks awefull.  So lets go to the **Location | Z** and raise it by `.05` units. Raise it more if it doesn't stop the z fighting on your computer.

https://user-images.githubusercontent.com/5504953/186781596-83d5dffb-dd49-4215-9db1-0c7efdb178f7.mp4

![](../images/line2.png)

##### `Step 5.`\|`UE5MAT`| :small_orange_diamond:


Now press the <kbd>Alt</kbd> while moving the plane to duplicate it 15 times.  This gives us an area with two 8 by 8 rows.

https://user-images.githubusercontent.com/5504953/186781926-c1532920-c8eb-4808-8df1-8e05fe725a24.mp4


![](../images/line2.png)

##### `Step 6.`\|`UE5MAT`| :small_orange_diamond: :small_blue_diamond:

The bump looks backwards so the normal map did not get recognized. Open up **T_BloodSplatter_N.tga** and take a look.

![bump is backwards](images/BackwardsNormals.jpg)

![](../images/line2.png)

##### `Step 7.`\|`UE5MAT`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

Now change the **Compression Settings** to `Normalmap (CXT5, GC5 on DX11)`.  Also flip the normal map's bump by checking the box next to **Flip Green Channel**.

![bump is backwards](images/FlipGreenCompress.jpg)

![](../images/line2.png)

##### `Step 8.`\|`UE5MAT`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Open up the **M_BloodSplatter_Decal** Material. Change the **Material Domain** in the **Details** panel from **Surface** to **Deferred Decal**.

![change material domain of to deferred decal](images/image_232.jpg)

![](../images/line2.png)

##### `Step 9.`\|`UE5MAT`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Make sure the project is set to allow **DBuffer** rendering.  Open up **Settings | Project Settings | Rendering** and look for **DBuffer Decals** and make sure the item is selected (`true`).

![turn on DBuffer Decals in project settings](images/DbufferOn.jpg)


![](../images/line2.png)

##### `Step 10.`\|`UE5MAT`| :large_blue_diamond:

Now for us to be able to preview the decals our previewer needs to be set up correctly.  Open up any static mesh and make sure that **Preview Scene Settings** are set to show both **Show Environment** and **Show Floor**.  Without these we will not see the decal in the previewer.

![set show environment and show floor in static mesh previewer](images/SetPreviewer.jpg)


![](../images/line2.png)

##### `Step 11.`\|`UE5MAT`| :large_blue_diamond: :small_blue_diamond: 

Make sure  the **Blend Mode** is set to **Translucent**. Change the **Decal Blend Mode** to `DBuffer Transluicent Color, Normal, Roughness`.

![change blend mode to translucent decal blend to dbuffer translucent](images/DecalBlendMode.jpg)


![](../images/line2.png)


##### `Step 12.`\|`UE5MAT`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: 

Add two new **Texture Sample** nodes to the material graph.  Assign the Diffuse material to one and the Normal map to the other. Connect them to the appropriate nodes. Look in the top left corner and see the problem. Our background shows through.  The alpha channel is not working. What do we do?

![add two texture sample nodes and apply materials](images/AlphaIgnored.jpg)


![](../images/line2.png)

##### `Step 13.`\|`UE5MAT`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 

There is an alpha channel in the texture so we connect this channel to opacity and voila, black gone. Now press the <kbd>Apply</kbd> button.

![connect alpha channel to opacity](images/AttachAlpha.jpg)

![](../images/line2.png)

##### `Step 14.`\|`UE5MAT`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 

You do not need to do the following as I have already done this for you.  I just wanted to show how to add an Alpha to a file.  Now photoshop doesn't automatically create this 4th Alpha channel for you.  The checkerboard that we think of as an alpha is not a true alpha channel.  Try and save a photoshop file with transparency in a **TGA** format.

![save file in photoshop](images/image_236.jpg)

![](../images/line2.png)

##### `Step 15.`\|`UE5MAT`| :large_blue_diamond: :small_orange_diamond: 

Now press Command (Cntrl on PC) Left Click on the Thumnail to add to select the image.  You should see the marching ants around all opaque pixels.

![select alpha channel](images/image_237.jpg)

![](../images/line2.png)

##### `Step 16.`\|`UE5MAT`| :large_blue_diamond: :small_orange_diamond:   :small_blue_diamond: 

Now go into the **Channels** tab and press the **Save Channel As Selection** button.

![save channel as selecton in channels](images/image_238.jpg)

This adds a channel called **Alpha1** and looks like a photoshop mask.

![add alpha channel to channels](images/image_239.jpg)

![](../images/line2.png)

##### `Step 17.`\|`UE5MAT`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

Add a background layer at the bottom and make sure it is pure black (0,  0, 0 RGB). Now you can save the image as a **TGA** with an alpha.

![add pure black background layer and with tga and alpha turned on](images/image_240.jpg)

![](../images/line2.png)

##### `Step 18.`\|`UE5MAT`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

You can confirm that this channel imported correctly by double clicking the **T_BloodSplatter_DandA** and pressing the **View** drop down and turning all channels off except for Alpha.  You see that you get a channel where white is opaque and black is transparent.

![confirm alpha](images/image_241.jpg)

![](../images/line2.png)

##### `Step 19.`\|`UE5MAT`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Let's go back to the game. You do not need to place this material on a mesh you can apply it to any existing mesh on the level and it will be added on top.  It will create a **Decal** actor in the **World Outliner**.  Just drag the **M_BloodSplatter_Decal** into the level and place next to the shiny wall. Now we do not apply it to a plane, we add the decal to an existing geometry even if it is not flat.  If the decal doesn't show up it is because that the purple arrow on the Decal points towards the surface that you want the decal to be on.  

![apply decal and place on wall](images/DropMatInLevel.jpg)

If the purple arrow points to the wrong location rotate it to point to the surface you want the decal on. Position it so the green box overlaps the wall geometry.

![rotate so purple arrow faces the wall](images/rotateOnPlane.jpg)


![](../images/line2.png)

##### `Step 20.`\|`UE5MAT`| :large_blue_diamond: :large_blue_diamond:

Adjust the scale of the **Decal** actor so the green box is not too deep.  If it is it will show up on both sides of the wall.  If this was a dynamic blood splatter we would just want it on one side. In my case it is scaling the **X** axis down.

![make adjustments to be in right position](images/RescaleXAxis.jpg)

![](../images/line2.png)

##### `Step 21.`\|`UE5MAT`| :large_blue_diamond: :large_blue_diamond: :small_blue_diamond:

Now play the game and look at the decal and make sure nothing bleeds ot the other side of the wall.

https://user-images.githubusercontent.com/5504953/131252525-2d8a7e3e-2f4e-4b9f-b598-e0b119b479e0.mp4

![](../images/line2.png)

##### `Step 22.`\|`UE5MAT`| :large_blue_diamond: :large_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Drop another blood material onto the carpet.  Rotate, position and scale it appropiately.

![add blood to carpet](images/image_247.jpg)

![](../images/line2.png)

##### `Step 23.`\|`UE5MAT`| :large_blue_diamond: :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Play the game and enjoy your decals! Double check that everything is OK.  I forgot to put the two actors in the **Room 5** folder in **World Outliner**.  My blood was also upside down with it dripping upwards which is wrong.  I rotated and repositioned the decal.  

https://user-images.githubusercontent.com/5504953/131253121-26f751dd-6575-409a-9aaa-0be22e15063f.mp4

![](../images/line2.png)

##### `Step 24.`\|`UE5MAT`| :large_blue_diamond: :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Press **Save All** and update Github by **committing** and **pushing** all the changes made.

![save, commit and push to gitnub](images/image_249.jpg)

![](../images/line2.png)

![](../images/line.png)

<!-- <img src="https://via.placeholder.com/1000x100/45D7CA/000000/?text=Next Up - Refraction and Fresnel"> -->
![next up next tile](images/banner.png)

![](../images/line.png)

| [previous](../two-sided-ii/README.md#user-content-two-sided-material-ii)| [home](../README.md#user-content-ue4-intro-to-materials) | [next](../refract/README.md#user-content-refraction-and-fresnel)|
|---|---|---|
