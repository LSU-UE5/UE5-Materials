![](../images/line3.png)

### Basic Material II

<sub>[previous](../tile-texture/README.md#user-content-basic-material) • [home](../README.md#user-content-ue5-intro-to-materials) • [next](../)</sub>

![](../images/line3.png)

<img src="https://via.placeholder.com/1000x4/45D7CA/45D7CA" alt="drawing" height="4px"/>

Lets finish implementing the material function then add a second color with a fresnel.

<br>

---

##### `Step 1.`\|`UE5MAT`|:small_blue_diamond:

Open up **M_Basic**.  Copy and cut all of the nodes in this material.  Open up **MF_BaseColor**.  Cut the 4 nodes into this material function.  Now we will need four outputs to represent base color, metallic, specular and roughness. So add three **Output** nodes to the material.  Name the top one `Base Color`, then `Metallic`, then `Specular` and finally the last one at the bottom `Roughness`. 

To organize these ouptut nodes, we can select all 4 outputs and right click and select **Alignment | Align Left** and **Alignment | Distribute Vertical**.  This will make the node chart neater and easier to read.

Then we connect the pins.  **Roughness** to **Output Roughness**, **Specular** to **Output Specular**, **Metallic** to **Output Metallic** and finally **Base Color** to **Output Base Color**.

Now we want to control what order the pins come up in order in the Material Function.  We want it to match the order that unreal sorts the pins in the material to be consistent.  Go to **Base Color** and set the **Sort Priority** to `0`, **Metallic | Sort Priority** to `1`, **Specular | Sort Priority** to `2` and finally **Roughness | Sort** priority to `3`.  

We also want to sort the order of the ouput pins with **Output Base Color | Sort Priority** leave at `0`, **Output Specular | Sort Priority** to `2` and finally **Roughness | Sort** priority to `3`.

Press the <kbd>Apply</kbd> and <kbd>Save</kbd> buttons to render and save the changes.  Make sure there are no errors.




https://user-images.githubusercontent.com/5504953/185414628-327fe3e2-1c58-4f3d-b698-114df14cfb67.mp4

![](../images/line2.png)

##### `Step 2.`\|`UE5MAT`|:small_blue_diamond: :small_blue_diamond: 

Now open up **M_Basic** again and drag a copy of the **MF_BaseColor** material function into the graph.  Now it is just a matter of connecting the four output pins to the aptly named input pins that are all in the correct order. Press the <kbd>Apply</kbd> and <kbd>Save</kbd> buttons to render and save the changes.  Make sure there are no errors. Now *press* the <kbd>Play</kbd> button in the top menu bar to launch the game. Now it should be exactly the same as it was before we included the material function.  This is exactly what we want!

https://user-images.githubusercontent.com/5504953/185414884-4da5bd0d-55e2-4120-a074-4c5d062b7ccb.mp4

![](../images/line2.png)

##### `Step 3.`\|`UE5MAT`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Now let's create one more material instance called `M_ShinyPlastic`.  Set the **Metallic** and **Roughness** to `0`. Duplicate another material ball and update the title.  Now *press* the <kbd>Play</kbd> button in the top menu bar to launch the game and now you should have three material balls using the same parent material and a material function.

https://user-images.githubusercontent.com/5504953/185414976-940b6f61-a481-4d12-b9b0-8bd480753100.mp4

![](../images/line2.png)

##### `Step 4.`\|`UE5MAT`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Lets add some functionality to our material function.  We will be lerping between two colors using a [fresnel](https://marmoset.co/posts/basic-theory-of-physically-based-rendering/#Fresnel).  This affects the material based on the normal at that point in the model.  We can use this in concert with a linear interpolation node to change colors based on the angle of the object in the scene and give it a colored rim effect.

So lets start there, add a **Linear Interpolate** node to the node graph.

![add lerp to base node](images/addLerp.png)

![](../images/line2.png)

##### `Step 5.`\|`UE5MAT`| :small_orange_diamond:

Now you should have a new node that is abbreviated to **LERP**.

![lerp node in chart](images/addedLerpNode.png)

![](../images/line2.png)

##### `Step 6.`\|`UE5MAT`| :small_orange_diamond: :small_blue_diamond:

Right click on the open graph and select a **Vector Paremeter** node and call it `Outside Color`. Make sure it is solid black.

![alt_text](images/outsideVector.png)

![](../images/line2.png)

##### `Step 7.`\|`UE5MAT`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

Connect **Base Color** to the **A** input pin on the **LERP** node and the output pin from **Output Color** to the **B** side of the **LERP** node.  Connect the outpt of the **LERP** to the **Output Base Color** pin.

![connect lerp node to base color nodes](images/connectLerp.png)

![](../images/line2.png)

##### `Step 8.`\|`UE5MAT`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Now how the *Alpha* pin works on a Lerp node is that a value of `0` will be 100% the **A** pin, and a value of `1` will be 100% of the **B** pin.  Any fractional number between will be a blend of A & B by the fractional amount (so `0.9` would be 90% B pin)l

![lerp change](images/lerpChange.png)

![](../images/line2.png)

##### `Step 9.`\|`UE5MAT`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Now we may not always want to use two colors.  So lets add a switch that lets us turn this on and off.  Right click on the open graph and look for a **StaticSwitchParamete**.  Call it `Two Color?`.  Now when it is false (so NOT two colors) put the output of the **Base Color** to the **False** pin.  And then the output of the
 **Lerp** node to the **True** pin.  Now send the output of teh **Two Color?** node to the **Output Base Color** pin.

![add second color static switch](images/staticSwitch.png)

![](../images/line2.png)

##### `Step 10.`\|`UE5MAT`| :large_blue_diamond:
 
 Now right click on the empty graph and add a **Fresnel** node.  
![add fresnel node](images/addFresnel.png)

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

| [previous](../tile-texture/README.md#user-content-basic-material)| [home](../README.md#user-content-ue5-intro-to-materials) | [next](../)|
|---|---|---|
