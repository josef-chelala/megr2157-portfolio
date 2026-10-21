# A7 – FEA on Bracket

## Main Choices
SolidWorks and SolidWorks Simulation will be the programs used.  

## First Outer Loop
### Weight of the Bracket
The initial iteration of the bracket is found to be 1.087 pounds. This was found by selecting "Mass Properties" under the Evaluate tab. I also adjusted its settings to give a high accuracy calculation of weight as well as change the units of mass to pounds.
<img width="2049" height="1299" alt="image" src="https://github.com/user-attachments/assets/1a37a85f-7158-4476-85f1-09d64c90e471" />
<img width="1745" height="1657" alt="image" src="https://github.com/user-attachments/assets/eb230bae-c3bf-43d5-9c91-cc227696acbc" />

### Shared Preprocessing
The only changes in the preprocessing for every outer loop's second and third inner loop from their respective first inner loop are the mesh density settings, for that reason I will not repeat the loading and constraints sections for each second and third outer loops. Actually, each outer loops first inner loop will be seen to be essential the same as one another. The preprocessing choices are basically the same throughout all outer loops due to how I made edits. For that reason I will give the main, detailed explanations for the process of preprocessing used for every section in the very this very first inner loop. Afterwards, I will give a lite summary and show a gif of the process for each first inner loop.
#### Loading
##### Setting Up the Application Area
In order to apply the load to the bracket correctly, the distributed force needs to be applied to the top half of the cylinder (called Element A in A5). To do so, I created a plane tangent to the top of the cylinder. Then I created a sketch that outlined the top half of the cylinder
<img width="1981" height="1337" alt="image" src="https://github.com/user-attachments/assets/88aa5e0a-545e-49a7-b91d-94a9c04928b7" />
##### Creating the Application Area
In order to create the applied force area using the sketch that was just made, the split line tool will be used. In this case, I will use the sketch to project a "cut" onto the cylinder. In this situation, the cut doesn't affect the simulation and just makes it possible to apply the force more accurately. 

{Inner_Loop_One-1.gif here}

##### Applying the Load
Creating the load is a multistep process. In SolidWorks, the first step is to choose the "Force" option under "External Load Advisor" at the top of the screen in SolidWorks Simulation. Next, I chose the newly created area I made as the area where the force will be applied. Then, I selected the "Selected Direction" option instead of the "Normal" option. Normal would make the force be constantly applied towards the center of the cylinder, this is incorrect. Since the two sides of the strap wrapped around the cylinder are being pulled straight down, most of the forces being applied in ever little piece of the selected area actually pointing down as well. To emulate this with Selected Direction, I selected the previously made plane, changed the unit system to IPS, chose the perpendicular to plane direction for the force, and then reversed the direction since it was facing the long way. This setup the force to be applied in the right way and direction. Lastly, I changed the applied load to 800 lbf and hit the green checkmark to finish the load section.

{Inner_Loop_One-2.gif Here}

#### Constraints
SolidWorks Simulation requires constraints in all xyz directions in order to even run a simulation. While Elements E and D will show constraints in two directions, that still leaves one left (the "forward/backward" direction). Since the bracket is attached to the beam via a fit, I decided that I would add a constraint of this last direction to all parts of the bracket that would be in direct contact with the rigid I beam once the force is applied (which ends up being just E and D). Furthermore, I will be selecting which elements act as fixtures based on how they would stop from being moved if the load at element A were to increase in lbf over time. Since the I beam is considered rigid its considered fixed, this would mean that the bracket would overall move downward once a great enough force to overcome the material's properties was applied due to how elastic displacement works. The material in contact with the fixed point has no displacement, while the free end does. As seen in elements D, it also stops it from moving inward towards the center of the bracket.

##### At the E "Elements"
As a quick note, there are two types of element in this project, one type are the elements from A5 that designate parts of the bracket, the other are the number of "pieces" of the mesh that will be made later. When I designate it with a letter, it means the prior. Moving on to Element E. As shown in the sketch, Element E is where the main force fight exchange between the bracket and rigid I beam occur according to statics and solid mechanics. The I beam in contact with element E completely blocks the bracket from moving in the main downward direction caused by the force. In reality, this section is way more complicated, however, based on simple physics this is generally how the section of the bracket works. For that reason, a upward fixture is the perfect place for this element. Additionally, as I have stated before, any part of the bracket that would be in continuous contact of the beam I will also treat as a forward/backward fixture, therefore element E will have this.
<img width="4130" height="2807" alt="image" src="https://github.com/user-attachments/assets/34a0520c-431c-4215-93af-13c24de2abff" />

###### Adding the E Fixtures
To add the fixture, I selected "Advanced Fixtures" under the "Fixture Advisor" tree at the stop of the screen. Then in the blue box which defines what surfaces are fixtures, I clicked the first E element surface that would be in contact with the beam. Next, I clicked the pink box which defines a "plane", that will be used to define the directions of the fixture, and selected the same surface I just clicked. Back to the blue box, I also selected the equivalent surface for the other E element since they share the same setup for the fixture. After scrolling down the fixture menu, I selected the "Normal to Plane" button which adds elements Es' vertical fixtures and the "Along Plane Direction 2" which adds the fixture for forward and back. With that, both Element Es are now constrained. 

{Inner_Loop_One-3.gif Here}

##### At the D "Elements"
The interaction between element D and the rigid beam is not as obvious. The interaction between the two is mostly the I beam reacting to the bending of D caused by the forces at element E (obviously the original force at element A as well) since they are offset from D. While not the full picture and not fully accurate, this causes the I beam to fight back against Ds bending with reactive "moments". The beam has essentially blocked the sides of element D in contact with the beam to overall not be able to move "left and right", translating to the entire bracket to essential treat these parts of element D like a fixture in the left and right direction. The types of fixtures that can be added in SolidWorks is very limited, I would try to add a more accurate fixture that would follow the actual phenomenon happening here, but I will just treat their fixture type like with element E. Lastly, same as element E, D will also be in constant contact with the I beam. Therefore I will also give it a fixture in the forward/backward direction.
<img width="4179" height="2717" alt="image" src="https://github.com/user-attachments/assets/8bac6968-a2a3-4be8-8132-deba09647eee" />

###### Adding the D Fixture
The setup for fixtures at D are basically the same as what was done for the E elements. With the only difference being that the surfaces of the D elements in contact with the I beam will used for the fixture and plane. Seen below.

{Inner_Loop_One-4.gif Here}

##### What About the Other Surfaces in Contact With the Beam?
When inspecting the contact between element C and the vertical sides of both elements E with the rigid I beam it appears they are in a different situation. It can be noticed that as an increase of loads are applied at A, they will likely move the beam during displacment (or fracturing) in a direction that would not cause meaningful contact with the beam and these sections of the element. Those surfaces of E would actually just move, if at all, away from the I beam since E would bend outward and away from the beam if an extreme enough force was applied or would just simply break off from the rest of the bracket. For element C, once a force overpowers the material, element C would move downward. Furthermore, this would mean that they do not have continuous contact with the beam. For these reasons, I will not treat these surfaces as fixtures.
<img width="4450" height="2423" alt="image" src="https://github.com/user-attachments/assets/daa352c6-ddbe-4b0f-919c-617e179331de" />


### First Inner Loop
#### Mesh Preprocessing
##### Creation of the Mesh
Creating a mesh in SolidWorks Simulation is very straight forward. To create it, at the bottom of the property manager in the bottom left side of the screen, right click on "Mesh". Then click on "Create Mesh" in the list of the popup, this takes you to the mesh parameters screen. The mesh density section decides on how many elements (quality of the mesh) that will be used, with coarse being the lowest amount of elements and fine having the highest amount of elements. For this assignment, I will use coarse for the first inner loop, the middle for the second, and fine if a third is necessary. Since this is a first inner loop, I set it to coarse. With that selected, one just has to hit the green checkmark and the program will create the mesh. After some time, the mesh of the model made up of triangle will pop up

{Inner_Loop_One-5.gif Here}

##### Number of Elements in a Mesh
To find the number of elements in a mesh, it starts again by right clicking on "Mesh" at the bottom left of the screen and then clicking on "Details" in the pop up. This will show a table of different stats and information of the created mesh. The row labeled "Total Elements" is what is needed. For this mesh in particular, it has 1,352 elements.

{Inner_Loop_One-6.gif Here}

#### Computation
In SolidWorks, running the study that will give the needed the results is literally a press of the button. To run it, you just have to click "Run This Study" at the top of the screen. Then the program will run, taking time based on how dense the mesh is
<img width="1699" height="1655" alt="image" src="https://github.com/user-attachments/assets/dc617d6d-529d-47ac-a409-054d8200572a" />

#### Data Interpretation
##### Adjusting the Units and Displaying the Max
By default, after a study is run, SolidWorks gives the FEA results for stress and displacement. The only changes that need to be made to these are the units for this project since it gives SI units by default. The process is the exact same for ever result section. Using this stress results as an example, to change the units and show the max stress, the first step is to right click on the "Stress" results found at the bottom left of the screen and click on "Edit Definitions" found in the pop up. In the menu that pops up and under display, the unit of measurement can be changed. Since the max yield stress for steel is 36,300 psi and general the max stresses will be in the thousands of psi, I decided to change the unit to ksi to make it more readable. Afterwards click on the chart options tab, there is a check box to make the results display the max stress on the model itself. Lastly, I like to change how the data is displayed by clicking on the unit display selection box (default at scientific) at the bottom left to floating and under that I change the number of decimal places to 4. That makes data way more digestible. Finally, one just needs to click on the green checkmark. This process is the same for other type of data results, except with a different type of units and changing the unit display to general. For displacement I changed it to inches as an example.

{Inner_Loop_One-8.gif Here}

##### Max Stress
The results were expected to be bad, but it came out worse then expected. The max stress was 558,468 psi (55.8468 ksi). Unsurprisingly, the worst stresses were located at center of element B near the point where it connects with element A.
<img width="1287" height="1347" alt="image" src="https://github.com/user-attachments/assets/bc7a1dc8-f535-4ad8-a4a6-dcdd88cbfca7" />

##### Max Displacement
Unsurprisingly, the max displacement was also bad. The results show a max displacement of .030718 inches at the bottom tip of element A.
<img width="1225" height="1449" alt="image" src="https://github.com/user-attachments/assets/565cfeaa-6824-4620-aba2-f8a96037e7d4" />

##### Safety Factor
###### Adding the Safety Factor Results
SolidWorks does not add the Safety Factor results by default. To do so, right click the where it says "Results" at the bottom left of the screen and select "Define Factor of Safety Plot" in the popup, then just hit the checkmark button. I also changed the chart display to show the results in floating instead of scientific notation for easier readability

{Inner_Loop_One-9.gif Here}

###### Results
The results for the factor of safety seems to look insanely bad, but it really is not completely awful. The max factor of safety actually displays parts of the model that are furthest away from max displacement and yield stress. In reality, the min is what is being looked for. In this case, the results show the worst factor of safety to be .649 found near the same place as the max stress. 















