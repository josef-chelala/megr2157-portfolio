# A7 – FEA on Bracket

## Main Choices
SolidWorks and SolidWorks Simulation will be the programs used. The preprocessing choices are basically the same throughout all loops due to how I made edits. For that reason I will give the main, detailed explanations for the preprocessing of every section in the very first inner loop.

## First Outer Loop
### Preprocessing
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
#
