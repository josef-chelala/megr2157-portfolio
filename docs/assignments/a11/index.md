# A11 – Motor Selection





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

##### 


