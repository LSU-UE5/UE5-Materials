![](../images/line3.png)
### Emissive Material

<sub>[previous](../translucent/README.md#user-content-masks-opacity--translucent-ii) • [home](../README.md#user-content-ue4-intro-to-materials) • [next](../illumination-ii/README.md#user-content-emissive-material-ii)</sub>

![](../images/line3.png)

Now for some objects in the game, they will also be a light source.  Think of the sun, a lamp, a TV set etc...  So our materials can handle light blooms and glow to create the illusion that it is illumiating in game.  We will create a new master material and material function to handle this extra mask that will be used to indicate what part of the model will emit light.

<br>

---

##### `Step 1.`\|`UE5MAT`|:small_blue_diamond:

Now Unreal defaults to having **Auto Exposure** set so that it always is brighter in dark areas (increases the exposure automatically in dark areas).  We want dark to be dark so open up **Project Settings** and turn **Auto Exposure** `off`.

![add spotlight as child of lamp in scene](images/autoOff.png)

![](../images/line2.png)

##### `Step 2.`\|`UE5MAT`|:small_blue_diamond: :small_blue_diamond: 

Lets also make sure it is off all the time by opening up BP_Player_Character and select the **First Person Camera** component. Set **MinEV100** and **MaxEV100** to `0`.

![add spotlight as child of lamp in scene](images/ev0.png)

![](../images/line2.png)

##### `Step 3.`\|`UE5MAT`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

We will be using a spotlight which will have a glow on the lightbulb as well as a light placed in it.  Create a new folder called `Props` inside the **Textures** folder. We need to download **[T_Spotlight_BCE.png](../Assets/T_Spotlight_BCE.png)**, **[T_Spotlight_N.png](../Assets/T_Spotlight_N.png)** and **[T_Spotlight_MSRAO.png](../Assets/T_Spotlight_MSRAO.png)**. Drag them into the textures folder. Double check that the engine recognized the normal map of **T_Spotlight_N** and is using normal map image compression.

![add five SpotlightModel textures to game](images/tSpotlightT.png)

![](../images/line2.png)

##### `Step 4.`\|`UE5MAT`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Open up all the textures and make sure they are correct.  They should all have mip levels.  Ensure that the **Normal Map** has **NormalMap** compressoin and change the **MSRAO** to **Masks** compression. Now we are texture packing the **Emissive** mask in the alpha channel of the **Base Color** texture. Remember, in the emissive mask white glows the most and black has no glow.

![add five SpotlightModel textures to game](images/checkTextures.png)

![](../images/line2.png)

##### `Step 5.`\|`UE5MAT`| :small_orange_diamond:

Create a new folder in **Meshes** called `Props`. Drag the **[SM_Spotlight.fbx](../Assets/SM_Spotlight.fbx)** into the **Meshes | Props** folder.  The emissive channel works on nanite models and we need to create a collision volume for these models.  Also, do not create a default material. Press the <kbd>Import All</kbd> button.

![import splotlightmodel fbx](images/importSpotlight.png)

![](../images/line2.png)

##### `Step 6.`\|`UE5MAT`| :small_orange_diamond: :small_blue_diamond:

Go to the **Materials | Master** folder and right click on **M_Basic** and select **Create Material Instance**. Call this new material instance `MI_BrushedSteel`. Move it to the **Material | Surfaces** folder.

![create new material m_brushedsteel](images/createMIBrushedSteel.png)

![](../images/line2.png)

##### `Step 7.`\|`UE5MAT`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

Open up **MI_BrushedSteel** Add change the **Base Color** from white to  `.913`, `.921` and `.915` as the RGB values. Change **Metalic** to `1.0`, **Specular** to `0.3` and **Roughness** to `0.4`.

![add constant vector with near white color and set surface properties](images/steelSettigns.png)

![](../images/line2.png)

##### `Step 8.`\|`UE5MAT`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Double click the **SM_SpotlightBracket** static mesh. Assign the material you just created **MI_BrushedSteel**.

![add mi_brushedsteel to spotlight bracket](images/assignToBracket.png)

![](../images/line2.png)

##### `Step 9.`\|`UE5MAT`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

![duplicate mf_texture for an emmisive material function](images/EmissiveMSRAO.png)

![](../images/line2.png)

##### `Step 10.`\|`UE5MAT`| :large_blue_diamond:



![add m_brushedsteel to SM_Spotlight_bracket](images/ConnectToEmissive.png)

![](../images/line2.png)

##### `Step 11.`\|`UE5MAT`| :large_blue_diamond: :small_blue_diamond: 

![adjust priotities](images/switchParamEm.png)

![](../images/line2.png)

##### `Step 12.`\|`UE5MAT`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: 

![adjust priotities](images/emissiveScalar.png)

![](../images/line2.png)

##### `Step 13.`\|`UE5MAT`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 

![create mi_spotlight and move to props folder](images/testScalar.png)

![](../images/line2.png)

##### `Step 14.`\|`UE5MAT`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 



![create mi_spotlight and move to props folder](images/matInstanceEm.png)

![](../images/line2.png)

##### `Step 15.`\|`UE5MAT`| :large_blue_diamond: :small_orange_diamond: 

![add lamp to scene and point light at wall](images/setUpLamp.png)

![](../images/line2.png)

##### `Step 16.`\|`UE5MAT`| :large_blue_diamond: :small_orange_diamond:   :small_blue_diamond: 



![make lamp a chile of bracket](images/assignLampMat.png)

![](../images/line2.png)

##### `Step 17.`\|`UE5MAT`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

![add color and tint parameter to emissive channel](images/createLampBP.png)

![](../images/line2.png)

##### `Step 18.`\|`UE5MAT`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:


![add ceiling to room 4](images/addComponentsLampBracket.png)

![](../images/line2.png)

##### `Step 19.`\|`UE5MAT`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

![add cube to room](images/dragFirstLightInRoom.png)

![](../images/line2.png)

##### `Step 20.`\|`UE5MAT`| :large_blue_diamond: :large_blue_diamond:

Now move the **Player Start** actor and rotate it so you start at the center of room 4.

![rotate player start](images/adjustPlayerStart.png)

![](../images/line2.png)

##### `Step 21.`\|`UE5MAT`| :large_blue_diamond: :large_blue_diamond: :small_blue_diamond:

*Press* the <kbd>Play</kbd> button and notice that you do not see the glow at a distance.  It clips in as you get closer to it.  Now this might be acceptable if this was a TV set but this is a stage light.  We don't want to crank it up so bright so it creates a spotlight but the color will always be white and it clips in.  In the next page we will fix this.

https://user-images.githubusercontent.com/5504953/186129871-384ce94a-6ec9-4c99-8917-d8bc12526a53.mp4

![](../images/line.png)

<!-- <img src="https://via.placeholder.com/1000x100/45D7CA/000000/?text=Next Up - Emissive Material II"> -->
![next up next tile](images/banner.png)

![](../images/line.png)

| [previous](../translucent/README.md#user-content-masks-opacity--translucent-ii)| [home](../README.md#user-content-ue4-intro-to-materials) | [next](../illumination-ii/README.md#user-content-emissive-material-ii)|
|---|---|---|
