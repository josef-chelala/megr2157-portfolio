# A11 – Motor Selection

## Motor Selection: EthanKing

A motor was selected based on the torque and speed requirements of the lead screw design. The motor was evaluated to ensure it could handle the maximum axial load of 2 kN throughout the required speed range of 1–50 mm/min.

### Selected Motor
[McMaster-Carr Motor – Part #6627T117](https://www.mcmaster.com/6627T117/)

### Motor Specifications
<img width="549" height="627" alt="Screenshot 2026-11-18 213807" src="https://github.com/user-attachments/assets/5ad1d1ad-fd25-4863-abd6-6a44c9d44b32" />
<img width="998" height="590" alt="Screenshot 2026-11-18 213609" src="https://github.com/user-attachments/assets/af09bf8a-0fd9-43d2-a646-6a0933621549" />

### Torque Verification
- Maximum Required Torque: **2.93 N·m (2.161 lb-ft)**

The selected motor was checked to ensure it provides sufficient output torque throughout the required operating speed range.

### Speed-Torque Curve
The motor's speed-torque curve is included below to demonstrate its available torque at different operating speeds.
<img width="553" height="418" alt="Screenshot 2026-11-18 213218" src="https://github.com/user-attachments/assets/6582c5c2-5e98-4599-8ec8-37cb4d2821a4" />

### Conclusion
The selected motor satisfies the torque and speed requirements of the lead screw design.

## Motor Mount Bracket Design

A motor mount bracket was designed to securely attach the selected motor to the tester frame. The bracket uses the motor's existing mounting hole pattern and a four-hole pattern to secure it to the top of the frame.

The design maintains alignment with the lead screw, allows access for assembly and maintenance, and provides sufficient strength to withstand operational torque and reaction forces.
<img width="367" height="721" alt="Screenshot 2026-11-18 214437" src="https://github.com/user-attachments/assets/3e2e1b65-8dc8-4593-b7f9-7b6fef2ba038" />


### Final Design
The final motor mount bracket was modeled in CAD using the calculated thickness and mounting hole locations.
<img width="768" height="702" alt="Screenshot 2026-11-18 214206" src="https://github.com/user-attachments/assets/6498a137-c0d8-4689-97c8-bd4a1658fbde" />
<img width="882" height="877" alt="Screenshot 2026-11-18 214222" src="https://github.com/user-attachments/assets/d29f70c8-5029-4927-82c4-fea0d338e8d7" />

## Coupler Design

A coupler was selected to connect the motor shaft to the lead screw. Torsional shear stress analysis was used to determine the required coupler dimensions and ensure it can safely transmit the maximum operating torque.

### Selected Coupling
[McMaster-Carr Coupling – Part #6412K14](https://www.mcmaster.com/6412K14/)

## Coupler Design
<img width="487" height="382" alt="image" src="https://github.com/user-attachments/assets/3d2b4a90-9af9-42c7-b052-a2e07377df40" />

### Final Design

The selected coupling was evaluated using torsional shear stress analysis to ensure it could safely transmit the required torque.
<img width="499" height="381" alt="Screenshot 2026-11-18 214849" src="https://github.com/user-attachments/assets/e87ceac4-ef4f-4295-8405-1c359631ba9d" />
<img width="999" height="627" alt="Screenshot 2026-11-18 214858" src="https://github.com/user-attachments/assets/9ce43187-2074-4b38-a60b-136227ea4ff8" />
<img width="544" height="132" alt="Screenshot 2026-11-18 214907" src="https://github.com/user-attachments/assets/dd16c823-e106-4a38-90e8-097fe2aaf99d" />















## Analyze and Design a Frame (Josef Chelala)
### Calculations
#### Analyze the Affected Twist by the Motors
First, to find the reactive transverse forces that will affect the vertical frames. Looking from the top, only the torques caused by the motors will be in affect. 


<img width="4724" height="4554" alt="image" src="https://github.com/user-attachments/assets/2c2c4cd9-2a44-4c57-ab5b-b0626b42bc5a" />

As seen, there will only be a small force acting on each section, this is because the reactive forces are at the end meaning that most of the reactive torque to combat the motors will rely on the length of the top frame. This only gives a low 1.525 lbf force. This is incredibly low, so even simple aluminum 40 series brackets at each end can easily handle the low force.

#### Calculating the Vertical Reactive Force
Next, since the leadscrews will each create a 1kN downward force, it is important to calculate the compressive forces that the top frame will act upon the side frames. As shown, these compressive forces are the same and are just 1kN at each end.

<img width="4724" height="4554" alt="image" src="https://github.com/user-attachments/assets/1fdfd9e9-8102-4b22-ac7a-fb29fd0a25f0" />


### Selecting the Bracket
#### Limitations
Using our previously selected beams from A10, the brackets that can be chosen are greatly restricted. Using the given Aluminum Top Frame, I was limited to a size less than 38.1mm in width (since the top bracket is the limiting size), and in 41.275mm in length, with 8.128mm for the slot width.


<img width="1953" height="1999" alt="image17" src="https://github.com/user-attachments/assets/98a97479-73c5-45ed-a326-faf39cfe55e5" />


#### Choice Between Brackets

The found dimensions limited our selection down between two brackets. Due to the low loads, either can work but the more expensive bracket can likely handle more bending and forces due to being gusseted. As shown earlier, the forces and torques are not enormous, so the cheaper option is more than enough. For that reason we will use [the 5JRP7 bracket made of Aluminium with no gusset](https://www.grainger.com/product/80-20-Inside-Corner-Bracket-Inside-5JRP7).


<img width="1976" height="1818" alt="image6" src="https://github.com/user-attachments/assets/719c7b80-79a2-45ff-aad1-fbb99a667e07" />














### Top Frame FEA
First, is to do an FEA on the top 40 series frame of 17 inches.
#### Model Setup
##### Fixtures Caused By Bracket and Vertical Frame

First, I split the surface of the top frame in contact with the vertical frames and the brackets. Then I added fixtures to those sections. Where I split the surface of the contact area where the top and vertical frames connected, I only placed vertical fixtures. Although not perfectly accurate, I then placed regular fixtures where the top frame interacts with the bracket.  


<img width="1869" height="893" alt="image12" src="https://github.com/user-attachments/assets/3743b6f9-a6e3-4b6d-b24e-a44e87280f9c" />



<img width="1225" height="921" alt="image7" src="https://github.com/user-attachments/assets/935a8fdc-2360-4156-85c7-7d1fd310f32c" />



##### Torque and Forces Caused by the Lead Screw
Then, I added torques caused by the lead screw and motors. Which we found to be 2.16 lb-ft or 25.932 lb-in


<img width="1999" height="1165" alt="image16" src="https://github.com/user-attachments/assets/7436e3fb-1cc1-4607-bf99-5bcf7374de79" />



Finally, I added the 1kN vertical forces to each screw hole.


<img width="1747" height="1263" alt="image14" src="https://github.com/user-attachments/assets/f3620af6-1991-4e33-8a54-d92f109bae9d" />

##### Final Setup
This leaves the final end result for the simulation as:


<img width="1519" height="765" alt="image26" src="https://github.com/user-attachments/assets/7e4cdaf2-9cd9-4632-b110-48bb7b29cef9" />


#### Meshing
Throughout the project I set the mesh to the center setting


<img width="375" height="593" alt="image" src="https://github.com/user-attachments/assets/d669664f-f22a-4871-b804-b7b139866a42" />


#### Results

##### Von Mises Stress

###### Max Stress
The heaviest stress of 20.159 ksi is located around the screw holes, with very small pockets of major stress surrounding it. It should be kept in mind that this is possibly inaccurate. It must be taken in consideration possible additional support from the lead screw itself, or just simply the inaccuracy of the torque and force applications. 


<img width="1839" height="959" alt="image25" src="https://github.com/user-attachments/assets/03ae1802-8331-4da8-a3a5-8a9184a1d599" />


<img width="1911" height="949" alt="image2" src="https://github.com/user-attachments/assets/14422ff0-2f6c-433f-b4f4-1062b255a43d" />



###### Just How Bad is the Stress?
With a yield strength of roughly 27.992 ksi and the factor of safety of, this is brought down to 6.998 ksi. Limiting the shown stress to show only above the max absolute stress shows that it is highly concentrated, found only near the lead screw hole and the line between the bracket connection and the top frame. The latter of which is nearly imperceivable. This is good news, that means this can easily be fixed with some additional support like a brace.


<img width="1999" height="845" alt="image10" src="https://github.com/user-attachments/assets/3e5e600c-c2fb-4fe3-b953-7f7c687886b0" />



###### Load Path
As seen in the above pictures, the main load paths are focused at the screw holes. This is likely because of the limitations of Solidworks Simulation itself, where it is had to add a realistic fixture that the Leadscrews, or motor mount would add. So it appears that the top frame is being punched by forces at the holes.


##### Vertical Deflection
###### Max Deflection
As seen below, all major deflection occurs at the lead screw holes with slight deflection in between them along the frame. Specifically, the max deflection is located at one specific screw hole with a deflection of .001616 inches. This makes sense because this is where the most concentrated linear 1kN forces occur with additional forces caused by the torque to further distort the area. Even then, it is not at all significant and is incredibly small. To bring a comparison, the average thickness of a piece of hair is 0.003 inches thick, the max deflection is half of that.


<img width="1864" height="1233" alt="image11" src="https://github.com/user-attachments/assets/084068f5-86be-43ec-9358-967c60f383c8" />


<img width="861" height="905" alt="image20" src="https://github.com/user-attachments/assets/3bb83d1e-fbfb-46e9-bdfa-ede350e94617" />



Limiting the displacement to about the thickness of the thinnest piece of hair a person has shows the displacement is again located at the screw hole alone, nowhere else comes close. Displacement is by no means a major issue despite dual forces and dual torques being applied.


<img width="1667" height="1219" alt="image9" src="https://github.com/user-attachments/assets/f395f223-f6e9-429d-9967-1ecbd3d3ef2e" />


###### Any Twisting or Warping Tendencies?
In the above observed displacement FEA, all displacements are greatly exaggerated to make things more observable. In this viewing, it appears that the frame is acting the same as a Four-point flexural test, where there is little to no displacements at the supports, with most of the bending at the center. Weirdly, even with extreme exaggeration, it appears as though there is no twisting. In real life, this is all completely unnoticeable, only at the most extreme where the leadscrews are is the thickness of hairs displacement visible to the eye. Everywhere else the human eye will not even be able to notice.

##### Factor of Safety
###### Smallest Factor of Safety
At first glance, it may seem as though that the factor of safety throughout the frame is horrid, however, this is far from the case.


<img width="1999" height="766" alt="image13" src="https://github.com/user-attachments/assets/a7019a6d-c302-4dba-859d-fc6111c25fd4" />


When limiting to showing only sections of the frame below the 4 factor of safety, it is clear that only small parts of the frame are actually below it. With a tiny, tiny piece having the smallest factor of safety of 1.386. As said before with the stress section, this means an easy fix can be applied after assembly if this is actualy a concern worth worrying about.


<img width="1999" height="656" alt="image8" src="https://github.com/user-attachments/assets/77697bb8-a93d-48cb-9852-10b18992e2ab" />



<img width="1143" height="1275" alt="image22" src="https://github.com/user-attachments/assets/1e64bd5e-e2c0-4206-be27-8b7b11c1dd94" />



#### Optimization Pass
##### Small Changes Make a Big Difference
Since it seems that only small parts of the frame are facing issues with the factor of safety. When looking at the chart from earlier, it seems some of the issues are caused by indents in the manufactured frame near the screw hole. Possibly, welding these little gaps can act as a retainer to help decrease the local stress.


<img width="1001" height="843" alt="image3" src="https://github.com/user-attachments/assets/82ce4204-c6e0-43cb-91ad-5418dc5899e7" />


<img width="1967" height="1085" alt="image" src="https://github.com/user-attachments/assets/aae9331d-1c18-47b7-8d8b-a2ec5a0212cb" />


##### Final Results

###### Factor of Safety/Stresses

These minor and easy to apply changes completely fixed the issues and no stresses go below the factor of safety as seen below. Now it is located at another indent. It seems that some of the indentations are the main problem with this part of the frame. It maybe in our best interest to customly make some top frames that decrease them for increased strength.


<img width="1843" height="1031" alt="image" src="https://github.com/user-attachments/assets/30ebeab1-7ff0-48f7-8e9e-54aa1d1b729f" />

###### Displacement

Furthermore, the already small displacement increased further, although not by much. Furthermore, it seemed to stay in same general area.


<img width="1219" height="1079" alt="image" src="https://github.com/user-attachments/assets/95ba6127-7e2f-44db-938b-6154e1b83474" />























### Vertical Frame FEA
Next is to use the 40 series vertical frames I was given.
#### Model Setup
##### Fixtures Connecting the Vertical Beam to the Base Beam
I set the fixtures to the whole bottom of the side frame since it will be in full contact with the base frame.


<img width="1359" height="1127" alt="image28" src="https://github.com/user-attachments/assets/bc84545e-1d23-4a80-905a-bf1ea5a452b5" />



##### Forces Caused By Bracket and Top Frame



Before starting, I first split the area where the bracket gets in contact with the vertical frame.


<img width="887" height="1271" alt="image5" src="https://github.com/user-attachments/assets/31de0f8e-fd1b-4a7d-bae3-7db47a5556ed" />


Then I split the section where the top and side frames come in contact.


<img width="1637" height="871" alt="image19" src="https://github.com/user-attachments/assets/505c3c23-e34e-496b-a2d0-5a9c58b9b5c7" />



Once completed, I placed the transverse force of 1.525 lbf found earlier to the contact area with the bracket. Then I applied the compression force caused by the top beam within the contact area between them. 


<img width="1343" height="903" alt="image24" src="https://github.com/user-attachments/assets/17669866-20d7-4762-8da5-4e9cfd325002" />


#### Results

##### Von Mises Stress

###### Max Stress

As seen below, it is quickly noticeable that the forces applied to the side beam are not significant. The maximum stress does not come close to the yield strength of the frame. This is unsurprising, because the top frame experienced far more stress and moments than the side frames. Furthermore, any forces transferred from the top frame to the sides is split in two for each side. As shown and will be shown, this side frame is overkill. For the side frames, the max stress is 2.516 ksi located at the center of where the top frame and side frame connect. 



<img width="1001" height="1161" alt="image18" src="https://github.com/user-attachments/assets/60ff1665-78ea-453b-920c-fcbf46a7df6c" />


###### Load Path
It seems that the load path is located where the max stress is. Directly down the center. This makes sense because the top frame is not taking the whole space where they connect. So all the force is focused at the contact point

##### Vertical Deflection
###### Max Deflection

This is where it becomes clear that this frame is extremely overkill. With even less displacement then the top frame, if that was even possible, the max is .0003796 inches. Completely unnoticeable. It is located are the tri connection point between the top frame, side frame, and the bracket. This makes sense because there is a twisting moment happening there as well as the compressive and transverse force.


<img width="629" height="1439" alt="image23" src="https://github.com/user-attachments/assets/38dc8f3e-d006-4b93-96b1-b079c6f5a356" />

###### Any Twisting or Warping Tendencies?
In the same way as the top frame, the forces are just not significant enough to cause any serious twisting or warping. It is like a person trying to twist a steel beam, it simply does nothing. The exaggerated representation seen in the above image is just not a correct. There is simply nothing happening. A fraction of a thin piece of hair is the displacement

##### Factor of Safety
###### Smallest Factor of Safety
Following in the same exact pattern as the stresses and displacement. The minimum factory of safety is a whopping 11.124, almost triple the 4 we were hoping for. Since the FoS is interlocked with the max stress, it is located in the same place.

<img width="615" height="1311" alt="image21" src="https://github.com/user-attachments/assets/beb7ee30-7d50-473e-9b87-61ecb9cce66a" />


#### Optimization Pass by Cutting the Cost Greatly
##### Factor of Safety
###### A Miracle?
Due to the max stresses and the displacement being extremely small, I decided to reselect the side beam my group mate chose. This time, I selected one with half the width with everything else being the same. After reapplying the exact same forces and fixtures, I found something rather surprising with the factor of safety (which is basically the same result with the Von Misses Stress since they are interconnected). The minimum factor of safety actually tripled further! Now located at the fixture. How is this possible?


<img width="1365" height="1245" alt="image" src="https://github.com/user-attachments/assets/3079a7f9-d4c5-4057-b31f-14521b0fd31b" />


###### How did this happen?

With great confusion on how the stresses and factor of safety significantly improved, I went back and investigated the original side beams. When limiting the sections of the original side frames to the smallest factor of safety of the new side frame, it turns out the max stresses were occurring in the curved sections of the original. Likely, if those were flat, the max stresses and factor of safety would have been greatly decreased more than the new side frames. 


<img width="1457" height="1151" alt="image4" src="https://github.com/user-attachments/assets/cbf340cc-8fcb-4749-917d-be2c25e989f6" />


##### Displacement

Now when focusing on displacement, it did increase:



<img width="549" height="1097" alt="image1" src="https://github.com/user-attachments/assets/0a4a3aef-0505-4587-ac76-56db0d2e4912" />




The displacement change was less surprising. With less width to fight against the transverse force, the displacement did increase to .00176 inches. Now, the displacement is similar to the top frame with a hair’s length displacement. Meaning, displacement is again not something that needs to be worried about. 
#### End Result
In the end, it seems that the original side frames were incredibly overkill and were wasting money for no reason. In terms of stress, it was technically the worse choice without fixing it.




## Lessons Learned

In the end, we learned to run siulations for a 

## Files 

### Simulation Files
The simulation files can be found here
