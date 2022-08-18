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

We also want to sort the order of the ouput pins with **Output Base Color | Sort Priority** leave at `0`, **Output Specular | Sort Priority** to `2` and finally **Roughness | Sort** priority to `3`




https://user-images.githubusercontent.com/5504953/185414628-327fe3e2-1c58-4f3d-b698-114df14cfb67.mp4

![](../images/line2.png)

##### `Step 2.`\|`UE5MAT`|:small_blue_diamond: :small_blue_diamond: 

https://user-images.githubusercontent.com/5504953/185414701-cfad61ad-609a-4522-b394-90e9fb4daf3a.mp4

![](../images/line2.png)

##### `Step 3.`\|`UE5MAT`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

https://user-images.githubusercontent.com/5504953/185414884-4da5bd0d-55e2-4120-a074-4c5d062b7ccb.mp4

![](../images/line2.png)

##### `Step 4.`\|`UE5MAT`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

https://user-images.githubusercontent.com/5504953/185414976-940b6f61-a481-4d12-b9b0-8bd480753100.mp4

![](../images/line2.png)

##### `Step 5.`\|`UE5MAT`| :small_orange_diamond:

![alt_text](images/.png)

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

| [previous](../tile-texture/README.md#user-content-basic-material)| [home](../README.md#user-content-ue5-intro-to-materials) | [next](../)|
|---|---|---|
