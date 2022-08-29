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

![output brick surface](images/bridgeSettings.png)

![](../images/line2.png)

##### `Step 5.`\|`UE5MAT`| :small_orange_diamond:

![alt_text](images/bringInTextures.png)

![](../images/line2.png)

##### `Step 6.`\|`UE5MAT`| :small_orange_diamond: :small_blue_diamond:

![alt_text](images/agreeToLink.png)

![](../images/line2.png)

##### `Step 7.`\|`UE5MAT`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

![alt_text](images/orderTextures.png)

![](../images/line2.png)

##### `Step 8.`\|`UE5MAT`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

![alt_text](images/addMetalic.png)

![](../images/line2.png)

##### `Step 9.`\|`UE5MAT`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

![alt_text](images/spaceAlphaMerge.png)

![](../images/line2.png)

##### `Step 10.`\|`UE5MAT`| :large_blue_diamond:

![alt_text](images/ConnectPins.png)

![](../images/line2.png)

##### `Step 11.`\|`UE5MAT`| :large_blue_diamond: :small_blue_diamond: 

![alt_text](images/addOutput.png)

![](../images/line2.png)


##### `Step 12.`\|`UE5MAT`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: 

![alt_text](images/bcH.png)

![](../images/line2.png)

##### `Step 13.`\|`UE5MAT`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 

![alt_text](images/outputN.png)

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
