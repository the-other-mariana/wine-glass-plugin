# Wine Glass Plugin for 3dsMax

This is a repo that contains the script in MAXScript Language that creates a plugin to automatically and procedurally generate any type of wine glass cup mesh object. You can export the object as .obj, etc.<br />

## Usage

This was made in 3dsMax 2020. <br />

1. Download [this file](https://github.com/the-other-mariana/wine-glass-plugin/blob/master/wine-glass-v3.ms) and store it in your computer.<br />
2. Open 3dsMax. <br />
3. Click on `Scripting` tab. <br />
4. Choose `MAXScript Editor`. <br />
5. On the editor, go to File > Open File > /Downloads/wine-glass-v3.ms, to open the downloaded script from step 1. <br />
6. Type Ctrl + E to run the script. <br />
7. Find the plugin in `Plugins Class` category of meshes. <br />

## Progress & Logic

### 1st Round

First defined 5 essential sections, just as the teapot. Then created a cylinder where each section has N number of `segments`. This is so that if the user inputs `segments = 1` it can still look like the minimum form of a wine glass.<br />

Then just defined each section's radius and interpolated the current radius with the next.<br />

![alt text](https://github.com/the-other-mariana/wine-glass-plugin/blob/master/images/process01.png?raw=true) <br />

### 2nd Round

What I did was simply clean a bit the parameters of heights: I added a spinner for the wine glass body scale and determined all the other section's height with respect to it. Next thing to do is round section 4 (below the body). <br />

![alt text](https://github.com/the-other-mariana/wine-glass-plugin/blob/master/images/process02.png?raw=true) <br />

### 3rd Round

This time I made section 4 (between handle and body) have an option to be curved or simply straight, using spheric coordinates. Separated `Segments` parameter to just apply to sections 2,3 and 5 (bigger sections) and sections 1(foot) and 4(belly) (smaller sections) to have their separate amount of custom sections. <br />

![alt text](https://github.com/the-other-mariana/wine-glass-plugin/blob/master/images/cup03.png?raw=true) <br />

### 4th Round

I made section 4's curve to be calculated automatically (inverse tangent!) and the curve can have a better look even if there are a lot of sections. I also closed the model in top and bottom. Added closure factor slider for the cup's mouth, but erased the angle parameter in the belly curve which didnt really improved the model and now is calculated. <br />

![alt text](https://github.com/the-other-mariana/wine-glass-plugin/blob/master/images/process04.png?raw=true) <br />

### 5th Round

This time I found that smoothing groups in 3dsMax are set according to powers of two: if you want a face in smoothing group 4 (N), you need to write 2^(N-1), that is, an 8. So I set every section to its own sg, except when Belly is on (1), because then it section 5 must have the same sg as section 4 (belly) so that it looks nice.<br />

![alt text](https://github.com/the-other-mariana/wine-glass-plugin/blob/master/images/smoothgroups.png?raw=true) <br />

A picture of probably all final parameters is shown bellow.

![alt text](https://github.com/the-other-mariana/wine-glass-plugin/blob/master/images/process05.png?raw=true) <br />

### Final version

Current script is [this file](https://github.com/the-other-mariana/wine-glass-plugin/blob/master/wine-glass-v3.ms). An example would be the following.<br />

![alt text](https://github.com/the-other-mariana/wine-glass-plugin/blob/master/images/process-final.png?raw=true) <br />

And the smoothing corrected as mentioned. <br />

![alt text](https://github.com/the-other-mariana/wine-glass-plugin/blob/master/images/process-final02.png?raw=true) <br />
