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
Creating the load is a multistep process. In SolidWorks, the first step is to choose the "Force" option under "External Load Advisor" at the top of the screen in SolidWorks Simulation. Next, I chose the newly created area I made as the area where the force will be applied. Then, I selected the "Selected Direction" option instead of the "Normal" option. Normal would make the force be constantly applied towards the center of the cylinder, this is incorrect. Since the two sides of the strap wrapped around the cylinder are being pulled straight down, most of the forces being applied in ever little piece of the selected area actually pointing down as well. Also, I chose 800lbf in A5, but since each side of the strap is pulling it, it is actually 1600lbf that I need to use. To emulate this with Selected Direction, I selected the previously made plane, changed the unit system to IPS, chose the perpendicular to plane direction for the force, and then reversed the direction since it was facing the long way. This setup the force to be applied in the right way and direction.

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

##### Adjusting the Units and Displaying the Max
By default, after a study is run, SolidWorks gives the FEA results for stress and displacement. The only changes that need to be made to these are the units for this project since it gives SI units by default. The process is the exact same for ever result section. Using this stress results as an example, to change the units and show the max stress, the first step is to right click on the "Stress" results found at the bottom left of the screen and click on "Edit Definitions" found in the pop up. In the menu that pops up and under display, the unit of measurement can be changed. Since the max yield stress for steel is 36,300 psi and general the max stresses will be in the thousands of psi, I decided to change the unit to ksi to make it more readable. Afterwards click on the chart options tab, there is a check box to make the results display the max stress on the model itself. Lastly, I like to change how the data is displayed by clicking on the unit display selection box (default at scientific) at the bottom left to floating and under that I change the number of decimal places to 4. That makes data way more digestible. Finally, one just needs to click on the green checkmark. This process is the same for other type of data results, except with a different type of units and changing the unit display to general. For displacement I changed it to inches as an example.

{Inner_Loop_One-8.gif Here}

##### Max Stress
The results were expected to be bad, but it came out far worse then expected. The max stress was 111.6936 ksi (111,693.6 psi). Unsurprisingly, since this is a lever, the worst stresses were located at center of element B near the point where it connects with element A since that is where the lever has the max length before increasing its cross sectional area.
<img width="997" height="1043" alt="image" src="https://github.com/user-attachments/assets/1741ab9d-e6eb-4098-96d1-cbaaef20a5a7" />


##### Max Displacement
Unsurprisingly, the max displacement was also bad. The results show a max displacement of .061437 inches at the bottom tip of element A, this could be slightly noticeable but still far passes what was needed. The location is of no surprise, I am certain it will always be the furthest point from the 
<img width="929" height="1035" alt="image" src="https://github.com/user-attachments/assets/845a54c4-6222-454f-aaf8-83ea15c11d91" />


##### Safety Factor
###### Adding the Safety Factor Results
SolidWorks does not add the Safety Factor results by default. To do so, right click the where it says "Results" at the bottom left of the screen and select "Define Factor of Safety Plot" in the popup, then just hit the checkmark button. I also changed the chart display to show the results in floating instead of scientific notation for easier readability

{Inner_Loop_One-9.gif Here}

###### Results
The results for the factor of safety seems to look insanely bad, but it really is not completely awful. The max factor of safety actually displays parts of the model that are furthest away from max displacement and yield stress. In reality, the min is what is being looked for. In this case, the results show the worst factor of safety to be .325 found near the same place as the max stress. 
<img width="815" height="989" alt="image" src="https://github.com/user-attachments/assets/40ec1aa6-2722-4cc8-b084-8bae375d4e28" />



### Second Inner Loop
#### Mesh Preprocessing
This time, the mesh density dial was moved to the center. After running it, the mesh had 9,293 elements. The meshing setting for each respective 1, 2, and 3 loop will be the same so I will not show this again
<img width="1224" height="1139" alt="image" src="https://github.com/user-attachments/assets/87bd7dd7-e55d-4270-b262-d1cbbc0049a1" />


#### Computation
##### Max Stress
For the second run, it seems that the max stress increased further. Now at 130.1098 ksi and at the same place as in the first run.
<img width="911" height="913" alt="image" src="https://github.com/user-attachments/assets/d5fdf9d8-3d57-43e9-85db-b12e4409f67a" />

##### Max Displacement
Max displacement also seemed to increase further, although less drastically as it is now at 0.064104 inches. Again, found at the same place as the first run.
<img width="879" height="977" alt="image" src="https://github.com/user-attachments/assets/000cc16d-07aa-4b1e-8e33-47a1061e3ee2" />


##### Safety Factor
Lastly, it seems that the factor of safety also got worse as well, now sitting at .279. Again, the location is consistent and also appears where the max stress is located. It seems the two are interlinked, and this should makes sense since the factor of safety is equal to the max stress divided by the yield strength. 
<img width="867" height="915" alt="image" src="https://github.com/user-attachments/assets/a4cead10-fc6b-4d38-a1e9-442c8f7a4464" />


### First and Second Loop Convergence
Now that both the first or second loop are finished, it is time to test the convergence using the equation:
<img width="1148" height="507" alt="ConvergenceEquation" src="https://github.com/user-attachments/assets/17e367a1-2d27-4bc0-ab7a-ef6ada562469" />

#### Example Using Max Stress 
Using stress as an example for the convergence equation, the convergence turned out to be 15.23%.
<img width="2589" height="869" alt="image" src="https://github.com/user-attachments/assets/1ba583c3-ec9d-4462-8d5b-19b7b7ea2ae0" />

#### Using Excel
The calculations are incredibly simple, so having to write these 10+ times is just a waste of time. For that reasons, I will be using an excel sheet to rapidly calculate it from here on out. I will attach the excel file to my assignment as proof. 
<img width="1387" height="281" alt="image" src="https://github.com/user-attachments/assets/e9cb4e25-4b92-43d7-bff4-b5450bdc045a" />


#### Convergence Results
Sadly, it seems that the convergence was not under 7% for both max stress and the factor of safety. This makes sense because the max Stress increased greatly. The professor warned that there could be points that increase drastically on a model that may possibly be an error and does not represent reality so it could be an issue to ignore. However, I do not know how to tell if it is an error and how exactly I can accurately measure "around" it, so I will just run it a third time. Also, the factor of safety and max stress do have the exact same convergence percentage. So my theory that they are directly linked is correct. From this data alone, it seems that increasing the mesh worsens everything. Except, it seems that the displacement did converge. Possibly because the displacement is very small?


### Third Inner Loop
#### Mesh Preprocessing
For the last loop, the mesh density dial was maxed to fine. This resulted in a mesh with a total element count of 66,341. A significant increase! 
<img width="1363" height="1281" alt="image" src="https://github.com/user-attachments/assets/8e376ab6-fa15-4881-8e43-966f045a8d59" />


#### Computation
##### Max Stress
It seems that results do worsen as the mesh gets finer, now the max stress is at 159.8541 ksi. However, something different did occur. Now the max shear stress is located at the two inner corners were element B and C connect, possibly a stress concentration.
<img width="1135" height="1201" alt="image" src="https://github.com/user-attachments/assets/781e96cb-cc78-48eb-b882-941a54f931d7" />


##### Max Displacement
Displacement seemed to show a different pattern, there was only a slight difference from inner loop two with a max displacement of 0.06494 inches. Again, the location was at the further point of the fixed sections.
<img width="869" height="1005" alt="image" src="https://github.com/user-attachments/assets/d0fcd5c6-1e85-48d7-ba9f-623bce18fba2" />



##### Safety Factor
Lastly, as I have learned, that it seems that the factor of safety changed similarly to max stress and at the same exact location. This factor of safety was found to be 0.226828. 
<img width="909" height="977" alt="image" src="https://github.com/user-attachments/assets/dcf9fc70-b7ac-4394-bbaa-42d7b13e420a" />

 

### Second and Third Loop Convergence
Running the convergence calculations through excel showed some interesting patterns. Still, the max stress and factor of safety did not converge, and it actually got worse as things got finer. Surprisingly, for displacement it not only still converges, the percentage actually decreased further. Seems that the convergence percentages between stress and the factor of safety increase while the displacement decrease as the mesh becomes finer.



## Outer Loop One Data Interpertation
### Analysis 
It seems that the biggest problem is that Element A and B seem to create a sort of lever. When the force is applied to A, its creates a moment along the length of B which is more then 1 inch. There are two ways to approach this, drastically decrease the length or to add another element B to the opposite side of the bracket. In the end, I decided to do both. For one, getting rid of the moment should greatly reduce the max stress. For the length, well, the strap given in A5 actually only has a .047" thickness. So a 1 inch gap is absurd. Luckily, I have a parameter for this length and it does not affect the rest of the math and dimensioning, so I can just type in a length for it. 
### Edits
#### Changing the Length
Changing the length was incredibly easy since it was a parametric equation I made. I simply changed the length to 1/8th of an inch and hit enter. 1/8th is about 2.5 times the thickness of the strap, more then enough clearance when it is pulling 
<img width="2407" height="1383" alt="image" src="https://github.com/user-attachments/assets/9066b999-6a80-4abc-ab08-a7c740eb99c0" />

#### Adding an Additional Element A
As stated, I simply need to add another element A to the open end. I ended up just deciding to trace over the entire bracket on the other side and extruded the same amount as the thickness of element A. It should be noted that all edits going forward that I make will not affect the placement of fixtures, forces, and the like to keep things simple.
<img width="813" height="1127" alt="image" src="https://github.com/user-attachments/assets/bacc21fe-33b2-422a-a3fa-8040dbcc9d70" />

<img width="1003" height="1143" alt="image" src="https://github.com/user-attachments/assets/45258631-d329-4c69-8673-d373f518f03a" />















## Second Outer Loop

### Weight
Since I only added material in the first edit, the weight increased to 1.330 pounds.
### First Inner Loop
#### Number of Mesh Elements
With this new design, the number of elements for the coarse mesh is 1,289

#### Computation
##### Max Stress
Whelp, the foresight on my design was incredibly correct. The max stress dropped to a whopping 9.5800 ksi. A massive success in bringing the overall stress below the yield strength. Interestingly, it seems that the max stress is located near the edges of the connections between elements A, B, and C. This is likelt
<img width="1035" height="1009" alt="image" src="https://github.com/user-attachments/assets/b4086849-b4ad-4f94-b270-448acce225da" />

##### Max Displacement
Similarly, displacement decreased greatly. It now sits at 0.000722 inches, essentially imperceivable. Now, it seems I was slightly incorrect in saying that displacement will always happen at the further point. The shading does shows something similar, however, the 1600 lbf force added an additional displacement where it contacts with element A. For that reason, the peak displacement is there
<img width="731" height="1011" alt="image" src="https://github.com/user-attachments/assets/f5f064d6-dcc4-4cee-84ac-3a23e3080876" />



##### Safety Factor
Since the factor of safety follows max stress also decreased and is in the same location as the max stress. It was found to be 3.7849.
<img width="807" height="905" alt="image" src="https://github.com/user-attachments/assets/4f0778ef-3a68-4b3f-ba4b-93a761b2c892" />


### Second Inner Loop
#### Number of Mesh Elements
Now at the center between coarse and fine, this mesh has 8,731 elements

#### Computation
##### Max Stress
Increasing the mesh detail also increased the max stress to 11.9275 ksi. Now, the max stress is near the inner corner connecting element D and E. Likely some sort of concentrated mesh. This might be a difficult one to fix since it seems to be in an area I cannot modify.
<img width="1177" height="1173" alt="image" src="https://github.com/user-attachments/assets/0ba368f7-ddaa-40c4-b025-6d964de0c3b8" />

##### Max Displacement
Again, it seems that the displacement further decreased, now at 0.000747 inches, and still in the same location
<img width="811" height="1077" alt="image" src="https://github.com/user-attachments/assets/921105ad-cb65-488c-9b8b-e4724f8d170d" />

##### Safety Factor
Following the max stresses decrease and location, the Factor of Safety is now at 3.04.
<img width="877" height="877" alt="image" src="https://github.com/user-attachments/assets/5dc3dc3d-e9c1-4409-b0df-5548947521e6" />


### First and Second Loop Convergence
Running these numbers through the excel sheet found similar results (and percentages) to the first outer loop. The max stress and factor of safety convergence percentage is over the threshold while displacement did not go over. Since some did go over, time to run the last inner loop. It should be noted that only the displacement was below the desired design limits, and by a decent margin away from .005 inches. 
<img width="1387" height="287" alt="image" src="https://github.com/user-attachments/assets/9845b47b-002c-4960-8bf0-d3fbbad15ffa" />


### Third Inner Loop
#### Number of Mesh Elements
This mesh came out as 


#### Computation
##### Max Stress
In strange turn of events, the max stress seemed to diverge completely, now sitting at 
##### Max Displacement

##### Safety Factor

###### Where is the bad factor of safety focused?
SolidWorks Simulation has a "Iso Clipping" Tool that allows me to only show sections of the model for a range of data like max stress and the Factor of safety. I decided to see if this issue was localized or spread throughout. It turns out that any factor of safety below the desired 4 is actually highly localized in specific areas. 
<img width="1111" height="1183" alt="image" src="https://github.com/user-attachments/assets/baeb9ded-7123-428e-b0f0-1522ec029cd0" />



### Second and Third Loop Convergence
It is absolutely ludicrous the drastic change in convergence that occurred. The max stress/factor of safety is now double than the first inner loop but in a completely different location and the convergence between the second and third loop is nearly 50%. This is in all honesty a mystery to me. Displacement was more consistent with only around a percentage change.
<img width="2001" height="268" alt="image" src="https://github.com/user-attachments/assets/76e4ee8f-58df-412a-9559-a7f1b2844b0e" />



## Outer Loop Two Data Interpertation
### Analysis 
It seems that all the major stress is mostly located in the inner corners of the bracket that interact with the beam, places that major changes can not be made without making changes to the I beam itself, so it maybe a lost cause trying to fix those areas. I will try adding material on the outside surrounding those corners, but it will likely do nothing. Either this is an issue with the limitations of SolidWorks Simulation since all the fixtures act as if the bracket is literally attached to the beam and so it causes this issue. Or this is actually how it acts in real life. This is likely a mix of both. However, major stress areas around the connects between elements A, B, and C can be fixed. Also, it seems that Elements E and C have a huge excess of unnecessary material. Element E is in no way a surprise, as I pointed out and explained in A5, the setup we were expected to use for element E was nonsensical and meant that figuring out what equation to use was rather difficult. I knew the equation would be significantly off, and this simulation shows this clear as that. For that reason I plan to cut most of it off. Now I just need to figure out how to cut as much material as possible. To do so I used the Iso Clipping tool again to show all stresses above a set amount for me to trace around. I honestly had no idea how much, so I decided on 2 ksi.
<img width="893" height="1223" alt="image" src="https://github.com/user-attachments/assets/ffb60aad-85bb-4c0f-bfed-cc3add30c67f" />

### Edits
#### Getting Rid of the Element A Length
For a reason that will soon be clear, I decided that I will get rid of the length for element A near completely. To do so Just had to go back to the parametric equation and set the length to zero. Well, actually if it is set to zero then the model completely breaks, to bypass it I added a significantly small length that should have no meaningful affect.  
<img width="1953" height="1395" alt="image" src="https://github.com/user-attachments/assets/7ed93c2c-777a-48eb-9c73-785c3d02a122" />






















## Second Outer Loop

### Weight
Since I only added material in the first edit, the weight increased to 1.330 pounds.
### First Inner Loop
#### Number of Mesh Elements



#### Computation
##### Max Stress

##### Max Displacement

##### Safety Factor






### Second Inner Loop
#### Number of Mesh Elements



#### Computation
##### Max Stress

##### Max Displacement

##### Safety Factor


### First and Second Loop Convergence


### Third Inner Loop
#### Number of Mesh Elements



#### Computation
##### Max Stress

##### Max Displacement

##### Safety Factor


### Second and Third Loop Convergence


## Outer Loop Two Data Interpertation
### Analysis 












## Lessons Learned
Math we used is highly inaccurate, however may be a good basis, but so off it is questionably useful
Simulation is useful but flawed, hard to tell if a extreme stress point is real or a strange error

Max Stress and FOS seem to go hand in hand in simulation. Although as mesh increases, these increase, but the opposite for max deflection









