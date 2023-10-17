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

Open up all the textures and make sure they are correct.  They should all have mip levels.  Ensure that the **Normal Map** has **NormalMap** compression and change the **MSRAO** to **Masks** compression. Now we are texture packing the **Emissive** mask in the alpha channel of the **Base Color** texture. Remember, in the emissive mask white glows the most and black has no glow.

![add five SpotlightModel textures to game](images/checkTextures.png)

![](../images/line2.png)

##### `Step 5.`\|`UE5MAT`| :small_orange_diamond:

Create a new folder in **Meshes** called `Props`. Drag the **[SM_Spotlight.fbx](../Assets/SM_Spotlight.fbx)** into the **Meshes | Props** folder.  The emissive channel works on nanite models and we need to create a collision volume for these models.  Set **Skeletal Mesh** to `false` (that is for characters) and set **Material Import Method** to `Do Not Create Material`. Press the <kbd>Import All</kbd> button.

![import splotlightmodel fbx](images/importSpotlight.png)

![](../images/line2.png)

##### `Step 6.`\|`UE5MAT`| :small_orange_diamond: :small_blue_diamond:

Go to the **Materials | Master** folder and right click on **M_Basic** and select **Create Material Instance**. Call this new material instance `MI_BrushedSteel`. Move it to the **MaterialInstances** folder.

![create new material m_brushedsteel](images/createMIBrushedSteel.png)

![](../images/line2.png)

##### `Step 7.`\|`UE5MAT`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

Open up **MI_BrushedSteel** Add change the **Base Color** from white to  `.913`, `.921` and `.915` as the RGB values. Change **Metalic** to `1.0`, **Specular** to `0.3` and **Roughness** to `0.4`. This will clamp the camera's aperature range in case this gets 

![add constant vector with near white color and set surface properties](images/steelSettigns.png)

![](../images/line2.png)

##### `Step 8.`\|`UE5MAT`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Double click the **SM_SpotlightBracket** static mesh. Assign the material you just created **MI_BrushedSteel**.

![add mi_brushedsteel to spotlight bracket](images/assignToBracket.png)

![](../images/line2.png)

##### `Step 9.`\|`UE5MAT`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

*Right click* and duplicate **Materials | MasterMaterial | M_Opaque_MSRAO** and create a new master material called `M_Emissive_MSRAO`.  It will be identical to the **Opaque** one except the alpha channel in the base color will go to emissive color portion of the node.  

Emissive means that this part of the material will act like a light source.  Think of a cel phone, computer monitor, LED sign etc...

Basecause we are using the base color Alpha channel, means we will lose transparency.  You could also just add a new material function with a new set of masks or highjack one like the metalic mask as well.  It is up to you on how you want to pack your masks and which ones are more important.

![duplicate mf_texture for an emmisive material function](images/EmissiveMSRAO.png)

![](../images/line2.png)

##### `Step 10.`\|`UE5MAT`| :large_blue_diamond:

Open up **M_Emissive_MSRAO** and disconnect the pin going from **Alpha** and **Opacity Mask** and instead connect it to the **Emissive Color** pin.

![add m_brushedsteel to SM_Spotlight_bracket](images/ConnectToEmissive.png)

![](../images/line2.png)

##### `Step 11.`\|`UE5MAT`| :large_blue_diamond: :small_blue_diamond: 

Now we can edit our base texture material function to switch between using the alpha for emissive or for just a regular alpha.  Open up **MF_BaseTexture** and add a **StaticSwitchParameter** node and call it `ScaleEmissive`.  Set it to **Group** `Base Color` and **Sort Priority** to `2`.

![adjust priotities](images/switchParamEm.png)

![](../images/line2.png)

##### `Step 12.`\|`UE5MAT`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: 

Add a **Scalar Parameter** node and call it **Emissive Scalar**. Set it to **Group** `Base Color` and **Sort Priority** to `3``. Add another **Multiply** node and send the **Emissive Scalar** pin to the new **Multiply B** node. Highjack the **Base Color | A** pin and send it to the top of the **Multiply** node.  Send the output to the **ScaleEmissive? | True** pin.  Send the output of the **ScaleEmissive?** node to the **UseBaseColorAlpha? | True** pin.  

We put this switch before because if you select no alpha channel then you will not get an emissive node and the false pin will only send the static switch with `1` and ignore all the other nodes before it.

![adjust priotities](images/emissiveScalar.png)

![](../images/line2.png)

##### `Step 13.`\|`UE5MAT`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 

Now open up **M_Emissive_MSRAO** and select the **MF_BaseTexture** node.  Make sure that **ScaleEmissive** and **UseBaseColorAlpha** are set to `true`.  Now the emissive color is one of the few channels that can take a value that is greater than `1`.  This adjusts how bright the object is.  A TV screen is a lot less emissive than a light bulb.  So play with values and see how the shader changes.  Leave the default value at `10`.

![create mi_spotlight and move to props folder](images/testScalar.png)

![](../images/line2.png)

##### `Step 14.`\|`UE5MAT`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 

*Right click* on **Materials | Master | M_Emissive_MSRAO** and select **Create Material Instance** and call it `MI_Spotlight_Lamp`.  Ove it to the **Materials | Material Instances** folder.

![create mi_spotlight and move to props folder](images/matInstanceEm.png)

![](../images/line2.png)

##### `Step 15.`\|`UE5MAT`| :large_blue_diamond: :small_orange_diamond: 
 
 Open it up and assign **T_Spotlight_BCE**, **T_Spotlight_N** and **T_Spotlight_MSRAO** to the the appropriate texture slot in the material instance. Make sure that **USeBaseColorAlpha?** and **ScaleEmissive?** are set to `true`.

![add lamp to scene and point light at wall](images/setUpLamp.png)

![](../images/line2.png)

##### `Step 16.`\|`UE5MAT`| :large_blue_diamond: :small_orange_diamond:   :small_blue_diamond: 

Assign `MI_Spotlight_Lamp` to **SM_Spotlight_Lamp**'s **Material Slots | Element 0**. Notice that the mask in teh texture isolates the inside of the lamp as an emissive area.  So the outside does not glow as the emissive part of that UV is black. 

![make lamp a chile of bracket](images/assignLampMat.png)

![](../images/line2.png)

##### `Step 17.`\|`UE5MAT`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

We want to populate the lamp in the area.  It is easiest to combine both meshes into a single object. Go to the **Blueprints** and *right click* and add a new **Blueprint** of type **Actor**.  Call it `BP_Spotlight_Lamp`.

![add color and tint parameter to emissive channel](images/createLampBP.png)

![](../images/line2.png)

##### `Step 18.`\|`UE5MAT`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Now make add two **Static Mesh Components** by pressing the **+ Add** button.  Call the first `Lamp Bracket` and the second `Lamp`.  Assign the **SM_Spotlight_Bracket** and **MI_Brushed Steel** to the **Lamp Bracket** component.  Add **SM_Spotlight_Lamp** and **MI_Spotlight_Lamp** to the **Lamp** component.  

Now since the objects are attached in real life - if we move or rotate the bracket the lamp moves.  Now the lamp can rotate in one axis without moving the bracket.  So we need to make the **Lamp** a *child* of the **Lamp Bracket** - that means the lamp will inherit the transfrom from the bracket.

![add ceiling to room 4](images/addComponentsLampBracket.png)

![](../images/line2.png)

##### `Step 19.`\|`UE5MAT`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Lets see what that inheritance means.  Select the bracket and rotate and move the bracket and notice that the lamp moves and rotates with it.  But if you do the same thing to the lamp it moves and rotates independently.

https://github.com/LSU-UE5/UE5-Materials/assets/5504953/fb30be73-8e63-41d1-85fe-8b25b085a11f

![](../images/line2.png)

##### `Step 20.`\|`UE5MAT`| :large_blue_diamond: :large_blue_diamond:

Drag an instance of **BP_Spotlight_Lamp** into the room.  Notice that the emissive does actually light a little bit. But it is not acting as a specific type of light source.  Since this is a light and not just a glowing screen we need to add an actual light. 

![add cube to room](images/dragFirstLightInRoom.png)


![](../images/line2.png)

##### `Step 21.`\|`UE5MAT`| :large_blue_diamond: :large_blue_diamond: :small_blue_diamond:

In the blueprint add a **Directional Light** component to be the child of **Lamp**.  This means the light will move when both the bracket and lamp move. Rotate it so it matches the direction of the lamp and move the light so it is not inside the model (otherwise the light will not work as it will be clipped inside the model like a light inside an opaque box). 
![rotate player start](images/dragFirstLightInRoom.png)


![](../images/line.png)

<!-- <img src="https://via.placeholder.com/1000x100/45D7CA/000000/?text=Next Up - Emissive Material II"> -->
![next up next tile](images/banner.png)

![](../images/line.png)

| [previous](../translucent/README.md#user-content-masks-opacity--translucent-ii)| [home](../README.md#user-content-ue4-intro-to-materials) | [next](../illumination-ii/README.md#user-content-emissive-material-ii)|
|---|---|---|
