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


##### Torque and Forces Caused by the Lead Screw
Next, I added torques caused by the lead screw and motors. Which we found to be 2.16 lbf-ft or 25.932 lb-in


Finally, I added the 




