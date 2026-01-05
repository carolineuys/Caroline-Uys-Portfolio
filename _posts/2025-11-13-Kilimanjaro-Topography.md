---
title: "Mount Kilimanjaro Topography 3D Print"
categories: 
  - blog
  - in-class assignment
date: 2025-11-13
tags: 
  - update
---

# 11/13/2025
Today we printed out 3D mountains that we chose on the website terrain2stl. I chose Mount Kilimanjaro in Tanzania because it is mentioned in a song I really like: Africa by Toto. The coordinates of Mount Kilimanjaro are 3.0674° S, 37.3556° E, but to position the box that determined what would be converted to an STL, I just dragged it over to the moutain's location on the map. The way that the website works is that you select a certain area of land by placing the red box over it, then it takes the topography of that land and converts into an STL file that has the same proportions as real life. The dimensions of the print were 63.5mm x 88.90mm x 25.4mm which I was able to obtain by changing the scaling factors in Bambu. This is what the design looked like in Bambu before printing:
<img width="1083" height="888" alt="Screenshot 2025-11-13 103927" src="https://github.com/user-attachments/assets/95d88d68-61fd-41a0-bfad-209e596bec62" />
This is the final, printed design:
![mountain topography](https://github.com/user-attachments/assets/3a1a7e8b-dc64-404e-b272-d01b8b831dbb)
You can download the 3D printing file here: [Download 3D print file](https://github.com/carolineuys/Caroline-Uys-Portfolio/blob/master/assets/files/Kilimanjaro/UYSterrain-90887%20(1).3mf)
This is the aspire file: [Download UYSterrain-90887 (1).stl.zip](https://github.com/carolineuys/Caroline-Uys-Portfolio/blob/master/assets/files/Kilimanjaro/UYSterrain-90887%20(1).stl.zip)

# 11/20/2025
After successfully printing out the mountains, our next step was to create a toolpath in Aspire that we are going to use with the CNC machine to mill the mountains into wood blocks. This is the workflow for creating the toolpath in Aspire:
## Phase 1: Job Setup & STL Import 
1. This phase is about preparing your workspace and bringing in your 3D model.
2. Create New File: Open Aspire.
  - Define Material:
  - Set the Job Type to Single Slided.
  - Set your Job Size (X, Y) to match your physical stock. The X axis is to the right
    and left of the bed while the Y axis is to the back of the Carvera machine when        looking at the bed.
  - Set your Thickness (Z). This is critical. Your imported STL model's height cannot      be thicker than this value.  [As a general rule, this value should be the height (thickness) of your stock.]
3. Set Zero Origin:
  - Z Zero Position: Material Surface (top) for the Cavera.
  - XY Datum Position: BottomLeft is often easiest when working with a single 3D           model, as it helps you center the component easily.
4. Set Model Resolution:You can set the resolution to High or Very High for best 3D       quality, but the software will run slower. It is okay to leave the resolution at       Standard (fastest).
5. Click OK.

#Import 3D Model:
1. Go to the Modeling tab (the one with the blue/green shapes).
2. Click the "Import a Component or 3D Model" icon (looks like a folder with a blue arrow).
3. Select your .stl file.
4. Orient 3D Model - 
5. Imported 3D Model > Transform 
6. This is the most important step for an STL workflow. A new 3D orientation window will appear.
7. Initial Orientation: Set the Initial Orientation to Top. Leave the Rotation about Z Axis at “0” or change it to move the orientation of your 3D model.
8. Model Size: Adjust the model's Width, Height, or Depth. Use the "Lock" icon, which needs to be unchecked, to change the X, Y, and Z sizes individually to the stock size. Use the appropriate size for your stock.  In our example, the stock is 1”.  [As a general rule, the Z height should be less than or equal to the thickness of your stock for the Carvera.] 
9. Click Apply and then Center Model.
10. Apply Perspectiver along Z: Ignore. Leave it unchecked. Click Position and Import>. 
11. Import 3D Model (.stl file) > Position: 
12. Next, using the slider bar, position the purple horizontal cutting plane at the appropriate depth to maximize the vertical relief of your model while maintaining a reasonable base height of the model. In other words, make sure that your model’s Z height size is slightly below the lowest relief point of your model 
13. Using the view cube in the top right corner of the screen, Click on the FRONT VIEW  to see the view of your model compared to the cut line.
14. Again, using the view cube, adjust the view cube to an isometric view to be able to view your model to be sure you are not cutting away part of the bottom relief like in the image above.
15. Your STL file is now imported as a single 3D "Component" in your Component Tree. You will see it in the 3D view.
# Phase 2: Sizing your Component
1. Now you must position the 3D model towards the top of the stock.
2. Click on the Component tab:
3. Click on the name of your .STL file name to access the Component Properties.You may need to right click on the name of the imported .STL 4. file that is under Level 1 below the Components section. You can also access this by right clicking then selecting the Properties.
4. Click the "Shape Height"  and change the value to 1.0. This will make the Z height of your model more pronounced. Next, Click the "Base Height" and change the value to 0.0. This will raise the height of your imported model in the material so that it is closer to the top of stock
5. Click close.
# Phase 3: Positioning & Creating a Boundary
1. Now you must position the 3D model within your material and tell Aspire the exact area you want to machine.
2. Position the Component:
3. Switch to the Design tab. Now click on the 2D view.
4. Click the Alignment Tool (under Transform Objects). Click the "Center" tool. This will perfectly center your imported model in the material you defined in Phase 1.
5. Click Close
6. Create a Boundary:
7. While on the 2D view  go to the Create Vectors section under Design.
8. Click the " Draw Rectangle" icon. 
9. You will create a rectangle around the boundary of your model. This rectangle will be the size of your stock, such as 2.5” (X) by 3.5” (Y).
10. Why this is crucial: This profile is what you will use to trim your finished product.
# Phase 4: 3D Toolpath Generation (CAM: Computer Aided Manufacturing)
1. This is where you create the actual cutting instructions. For a 3D model, this is almost always a two-part process: a "Roughing" pass and a "Finishing" pass.
2. Switch to the Toolpaths Tab (top right).
3. Select Your Boundary: In the 2D view, click on the 3D model image.
4. Pin the Toolpaths Tab Open using the "pin" icon so it doesn't close.
5. Step 4A: The 3D Roughing Toolpath (Clearing Material)
6. The goal here is to quickly remove the bulk of the "unused" material with a large, strong bit.
7. Click the 3D Roughing Toolpath icon. 
8. Tool: The Material needs to be set to Hardwood. Select a large 25 mm Flute End Mill (3.175 mm) under the Carvera Tools subsection Example Tools. This is also known as 1/8” End Mill. This is set to Tool Number 1 for the ATC.
9. Machining Limit Boundary: Select Model Boundary. This tells Aspire to only machine the area inside the vector you have selected.
10. Machining Allowance: Set a small value (e.g., 0.024"). This leaves a thin "skin" of material for the finishing bit to clean up, preventing it from "chattering" or breaking.
11. Strategy: Choose Z Level (efficient for "stairstepping" down) or 3D Raster (good for flatter models).
12. Name your toolpath (e.g., "3D Rough - 0.25 Endmill or 25 mm Flute End Mill") and click Calculate.
13. Step 4B: The 3D Finishing Toolpath (The Detail Pass)
14. The goal here is to use a small bit to slowly go over the entire model, creating       
the smooth, detailed final surface.
15. Click the 3D Finishing Toolpath icon.  (Your boundary vector should still be selected).
16. Tool: The Material needs to be set to Hardwood. Select a small ⅛” Ball Nose bit. The smaller the bit, the more detail you get, but the longer it takes.This is set to Tool Number 6 for the ATC. 
17. Machining Limit Boundary: Again, select Model Boundary.
18. Raster: A good, all-around strategy. Set the Raster Angle (e.g., 0 degrees) to go back and forth along the X-axis.
19. Offset: Good for models that are circular or oval.
20. Name your toolpath (e.g., "3D Finish - 0.125 Ballnose") and click Calculate.
# Phase 5: 2D Profile Toolpath Generation (CAM)
1. This is where you create the actual cutting instructions. For a 3D model, this is almost always a two-part process: a "Roughing" pass and a "Finishing" pass.
2. Select Your Boundary: In the 2D view, click on the rectangular model profile.
3. Toolpaths: Select the 2D Profile Toolpath. 
4. The 2D Profile Toolpath
5. Click the 2D Roughing Toolpath icon. 
6. Cutting Depths: Make the Star Depth 0 and the Cut Depth 0.5. This tells Aspire to only machine the specific depth.
7. Tool: The Material needs to be set to Hardwood. Select a large 25 mm Flute End Mill (3.175 mm) under the Carvera Tools subsection Example Tools. This is also known as ⅛” End Mill. This is set to Tool Number 1 for the ATC. (see images to right and below) 
8. Machine Vectors: Select On the line and the Direction of climb.
9. Do Separate Last Pass: Ignore it. Leave it unchecked.
10. Add tabs to toolpath: Not Needed.
11. Name your toolpath (e.g., "2D Profile - ⅛” Endmill" or 25 mm Flute End Mill) and click Calculate. (see image below)
# Phase 6: Simulation & Exporting
1. Preview ALL Toolpaths: 
2. This is your most important safety check. Click the Preview all Toolpaths button.
3. Aspire will run a full 3D simulation. First, you'll see the Roughing pass "hog out" the material in steps. Then, you'll see the Finishing pass clean it up. You can preview each file independently, together, etc.
4. Check for errors: Does it look correct? Did you miss any spots? Is the detail what you expected? The images below are examples of the Preview Toolpaths. 
5. Toolpaths Summary: Click on the Toolpaths Summary icon to learn how long your total machining time will take to complete your file.
6. Save Your Project File: While u Go to File > Save As... and save your .crv3d project file. This saves all your work you have completed as an Aspire VCarve file to the computer.
7. Save Your G-Code (Toolpath Files):
8. Click the Save Toolpaths button (floppy disk icon). 
9. This workflow creates Visible toolpaths to one file for your machine.
10. Check Toolpaths: Select "3D Rough," then select "3D Finish", and then select “2D Prolfie”. -> Click Save Toolpath(s).
11. Choose your Machine -> Carvera Desktop CNC Machine.
12. Choose your Post-Processor( the "driver" for your Carvera ATC CNC machine) → Carvera ATC (mm) (*cnc) -> Click Save Toolpath(s). This will save the .gcode  as a .cnc Makera Carvera file to the computer.
13. You will now have the .gcode (or .nc, etc.) file to run at your CNC machine, as a file that will automatically run each toolpath one after another.

# 12/03-05
These past couple of days I have been creating the toolpaths for a cnc machine in Aspire for my Kilimanjaro topography. I had to make three different toolpaths for this design: profile, roughing, and finishing. Roughing is to carve out the majority of the wood and it uses the .8mm corn bit, finishing is for making the design more detailed and is used with a .2mm ball bit, and the profile cut is the final step which is to cut all the way around the design and also uses a .8mm corn bit. I exported the toolpaths from Aspire as a single .cnc file so that it can be put into MakeraCam when it is exported. You can download my file here: [Download toolpaths](https://github.com/carolineuys/Caroline-Uys-Portfolio/blob/master/assets/files/Kilimanjaro/UYSterrain-90887toolpaths.cnc.zip)
This is a picture of what my toolpaths looked like in Aspire:
![kiltoolpathspic](https://github.com/carolineuys/Caroline-Uys-Portfolio/blob/master/assets/images/kiltoolpathspic.png)
# 12/08
Today I milled the topography map on wood by first importing my .cnc file to MakeraCam and then homing the device, offset the bottom left corner of the coordinate axes by 6mm each and then I ran the design. 
Here's a top and side view of the final piece:
![kilfromtop](https://github.com/carolineuys/Caroline-Uys-Portfolio/blob/master/assets/images/kilfromtop.jpg)
![kilfromside](https://github.com/carolineuys/Caroline-Uys-Portfolio/blob/master/assets/images/kilfromside.jpg)
