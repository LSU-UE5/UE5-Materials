![](../images/line3.png)

### Export Textures

<sub>[previous](../animation-ii/README.md#user-content-animation-ii) • [home](../README.md#user-content-ue5-intro-to-materials) • [next](../world-alignment/README.md#user-content-world-aligned-materials)</sub>

![](../images/line3.png)

<img src="https://via.placeholder.com/1000x4/45D7CA/45D7CA" alt="drawing" height="4px"/>

All the textures we have used to date that are detailed (not the masks) all come from Quixel.  Lets look at the process so you can also create your own. We will need a brick wall for Room 9, so lets go through the process together.

<br>

---


##### `Step 1.`\|`UE5MAT`|:small_blue_diamond:

You can download from **Quixel** bridge in the editor.  In the same **Place Actors** menu you can select **Bridge** and use your **Epic** login credentials to get free access.  You then can assign our own master material which is cool.  It doesn't export the layers in the same order, and even though there is no metallic or diffuse it is not exporting these layers. We will use a diffent way.

![bridge through editor](images/downloadingBridge.png)

![](../images/line2.png)

##### `Step 2.`\|`UE5MAT`|:small_blue_diamond: :small_blue_diamond: 

You can get a stand alone version of **Quixel Bridge** and then further customize to your likings.  Go to [quixel.com/bridge](https://quixel.com/bridge) and **Download Bridge** and install.  Login with your Epic credentials.

![install quixel bridge](images/downloadBridge.png)

![](../images/line2.png)

##### `Step 3.`\|`UE5MAT`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Open **Quixel Bridge**.

![open quixel bridge](images/launchBridge.png)

![](../images/line2.png)

##### `Step 4.`\|`UE5MAT`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Search for a **Brick** surface.  I liked **Brick Facade**. Set the resolution to `4K Resolution`.  Press the three lines next to it and make sure you are downloading **Albedo** (called Base Color in unreal), **Metalness**, **Roughness**, **Specular**, **Displacement**, **Normal** and **AO**. Now press the <kbd>Download</kbd> button.

![download brick surface](images/bridgeSettings.png)

![](../images/line2.png)

##### `Step 5.`\|`UE5MAT`| :small_orange_diamond:

We will combine the layers in Substance.  Open up **Substance Designer** and select **File | New** and select **Substance graph**.  Call it `T_BrickWall` and press the <kbd>OK</kbd> button. Press **Save All** and save it in the same folder as the graphic files.

Drag the files you just downloaded to the side bar.  They are located in **Documents | Megascans Library | Downloaded | surface | brick_modern_...**.  When you drag them you will select **Link resource(s)...**.  

![drag images to new subsstance graph](images/bringInTextures.png)


![](../images/line2.png)

##### `Step 6.`\|`UE5MAT`| :small_orange_diamond: :small_blue_diamond:

It will show all the files you dragged to link.  Press the <kbd>OK</kbd> button.

![press ok to link files](images/agreeToLink.png)

![](../images/line2.png)

##### `Step 7.`\|`UE5MAT`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

Click on each one and on the right hand side you can see the filename this will tell you which is which.  From top to bottom order the **Albedo**, **Displacement**, **Normal**, **Specular**, **Roughness** and **AO**. Notice there is no metallic.


![arrange order of images](images/orderTextures.png)

![](../images/line2.png)

##### `Step 8.`\|`UE5MAT`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Drag the paintbucket icon to drag a **Uniform Color** node to the chart where **Metallic** should be, under the normal.  Press the <kbd>Grayscale</kbd> button and make sure it is `0` (black - no metal).

![drag uniform color for metallic to chart](images/addMetalic.png)

![](../images/line2.png)

##### `Step 9.`\|`UE5MAT`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

On the open graph press the <kbd>Space Bar</kbd> and select **Alpha Merge**.

![select alpha merge](images/spaceAlphaMerge.png)

![](../images/line2.png)

##### `Step 10.`\|`UE5MAT`| :large_blue_diamond:

Now notice the the three color RBG albedo is orange and the displacement (height) is a mono single channel image and is gray.  Connect them to the same color pins in the **Alpha Merge** node.

![connect to alpha merge node](images/ConnectPins.png)

![](../images/line2.png)

##### `Step 11.`\|`UE5MAT`| :large_blue_diamond: :small_blue_diamond: 

Pull off of the output node from **Alpha Merge** and select **Output** node.

![add output node](images/addOutput.png)

![](../images/line2.png)


##### `Step 12.`\|`UE5MAT`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: 

Change the **Modifier** to `BCH`.  It will use this as the postfix for the texture name.

![add metal uniform color](images/bcH.png)

![](../images/line2.png)

##### `Step 13.`\|`UE5MAT`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 

Add an **Output** node next to the normal texture. Connect the nodes.  Change the **Modifier** to `N`.

![add normal output](images/outputN.png)

![](../images/line2.png)

##### `Step 14.`\|`UE5MAT`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 

![alt_text](images/rgbaMerge.png)

![](../images/line2.png)

##### `Step 15.`\|`UE5MAT`| :large_blue_diamond: :small_orange_diamond: 

![alt_text](images/msrao.png)

![](../images/line2.png)

##### `Step 16.`\|`UE5MAT`| :large_blue_diamond: :small_orange_diamond:   :small_blue_diamond: 

![alt_text](images/exportTextures.png)

![](../images/line2.png)

##### `Step 17.`\|`UE5MAT`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

![alt_text](images/ThreeTextures.png)

![alt_text](images/.png)

![](../images/line.png)

<!-- <img src="https://via.placeholder.com/1000x100/45D7CA/000000/?text=Next Up - World Aligned Materials"> -->
![next up next tile](images/banner.png)

![](../images/line.png)

| [previous](../animation-ii/README.md#user-content-animation-ii)| [home](../README.md#user-content-ue5-intro-to-materials) | [next](../world-alignment/README.md#user-content-world-aligned-materials)|
|---|---|---|
