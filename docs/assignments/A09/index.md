# A9 – Pulleys

## Choice of Parameters
For this project, we are given a choice for Rotational Speed, the Center to Center Distance between the pulleys, and the Belt Tension. Because I like to use extremes for worst case scenarios, I went with 2000 rpm, 6 inches, and 6 lbf respectively

## Belt Design
### Setup
First, we had to find the cross sectional area of the belt as well a the outer circumference of the belt that is wrapped around the two pulleys. To do so, I need to find the forces on both the tight and loose sides of the belt while assuming there is no slippage. This is done with a mix of statics and dynamics. Lastly, any belt that I need to chose must be made out of polyurethane rubber, which has a yield strength of 471 psi.

### Calculations
<img width="3603" height="10423" alt="image" src="https://github.com/user-attachments/assets/bb3d3a0c-b4f5-40d2-9fec-5927887e4299" />

### The Selection and its Issues
In the end, I decided belt 9462T58. Since my result was a strange .305 inches, they do not have that diameter available with the closet being .3125 inches (must be above to stay within factor of safety). Additionally, no .3125 in, premade belt is too close to the outer diameter end result I calculated. However, there is a one "made to order" belt that can hit 23.5 inches, even better, it works with the 3 inch diameter pulley. Even though the belt is a little small, after recalculating the safety factor, with the same setup and force values I calculate, I found it reached about 3.14. Possibly, this .14 extra factor of safety can compensate for extra tension caused by the belt being slightly shorter than it should be. Not nowing how to calculate that, I will just accept this as true at face value.

## Shaft's Diameter Design
### Setup
Next, I need to use the material properties of 1060 hardened steel to find the minimum diameter of the shafts used for the pulleys. This is done by using the applied torque to calculate the minimum cross section area. One issue I ran into is that I could not find a data sheet with shear yield strength to calculate this with. Luckily, steel of this kind has an equation than can estimate the shear yield strength using its normal yield strength. For this project I used [this data sheet](https://www.matweb.com/search/DataSheet.aspx?MatGUID=fe7b3b4ca8894c8398ab9063e89ec0b7&ckck=1) for these calculations, however, it seems that this type of steel can have drastically different data depending on the diameter used when hardening. Further testing would be needed.
### Calculations 
<img width="3406" height="6131" alt="image" src="https://github.com/user-attachments/assets/9e43ab74-9dee-465b-a520-d2f881441a83" />

### Result
As a result, I found the minimum diameter allowed for the shaft is .1645 inches. This should be relatively alarming on a surface level, how can the pulley diameter be about 18 times the size of the shaft? Well, 12 lbf is not really a large amount of force, especially for hardened steel. 

## Journal Bearing Design
### Setup
Next, I need to find the material that will to design the journal bearing for the shaft. To do so, I need to determine the pressure, the linear velocity, and the PV rating and see how they match up with the sintered metal or non metallic Table for journal bearing in the Machinery’s Handbook. From there, it seems to be up in the air on how to design the rest of the bearing since no fit classification was given and we were not told to chose from a list of given journal bearings. For that reason, I will use Mc-Masters site to see what could work. To start, in case a metal journal bearing is needed, they usually come at a small .25 inch length. For that reason, I will use that as my length.

### Calculations
<img width="3535" height="9968" alt="image" src="https://github.com/user-attachments/assets/7bbd3085-affe-4a94-9a29-2ea8c9f19746" />

### Results
In the end, I was able to chose between bronze, iron, and other metals for the journal bearing. Instead of choosing the material immediately initially, I decided to base it off what materials used in Mc-Masters products might realistic be made and sold. Since my shaft diameter was rather strange, I chose the closest diameters above and below .1645 inches. Immediately, it was shown that bronze was the only option, so I decided on bronze. For the next step of the project, I needed and outer diameter to use for calculating and designing parts of the frame I need to make. For that reason, I chose an outer diameter that both closest shaft diameters options had. This further game me a more realistic idea on what sizing of journal bearings I could make. This gave me .252 inches as a outer diameter.

## Design of Frame
### Setup
Lastly, we were asked to use "engineering analysis to design a frame which supports the pulley system." The problem is that this part was left incredibly vague, but after talking with others, I decided that I would design my frame around a material with an excellent strength-to-weight vs cost ratio. To keep the actual math and design simple, I used a simple 2-force, straight bracket. 
### General Design
I decided to build my frame design and equation around the journal bracket. Since this gave me the thickness and minimum height. I only needed to calculate the extra height needed for the stress concentrations around the hole. To find the right height, I only need to find my desired material
<img width="3441" height="2835" alt="image" src="https://github.com/user-attachments/assets/dc256fc1-71fa-4a93-b1f8-56afc4cba075" />

### What Materials to Chose From
As I learned in manufacturing systems (and reminded by other students), Ashby plots are used to compare different properties (and costs) of a material to find effective materials for specific needs. One problem is that finding charts for strength-to-weight vs cost ratios are hard to come by. However, I did find [this British site](https://simulations4all.com/simulations/material-selection-ashby-chart) that gives several highly interactive Ashby plots to make finding materials significantly easier. I am able to select different kinds of materials and directly compare a couple when I click on them. It even allows me to export a file giving the list properties of my selected materials. What is great is that it gives a yield stress vs cost per kg (though in British pounds) chart. I quickly realized that shuffling through all the materials to find the exactly PEFECT material could take a long time. So, I decided I would focus on lowest cost per kg materials. This gave me Cast Iron, two types of carbon steel, spruce wood, and pine wood. So I exported the materials to a file. However, as will be seen in a minute, just because something is low cost, does not mean it will be low weight as seen in the yield strength vs density chart.


<img width="1605" height="1231" alt="image" src="https://github.com/user-attachments/assets/fb275c99-5fa9-4064-8acc-bedf460f37e4" />


<img width="1761" height="1373" alt="image" src="https://github.com/user-attachments/assets/4d1ad6db-ee90-42a1-9708-d6106f21bb72" />


<img width="2021" height="423" alt="image" src="https://github.com/user-attachments/assets/40bb4c92-b370-4f4d-95fd-f6ab2b8c19ee" />

### Taking the Easy Way Out
At this point, I was going to make an excel sheet to relate the properties together to find the best material that fits my ratio, however, at this point I feel I have done way more than what was necessary. For the sake of my time, I decided to make ChatGPT to going through the file and give me a data sheet that calculates it for me. In the end, it seems that Spruce is the best fit. This makes sense, even though steel is far stronger than wood and the steel selected cost the same per kg to make, steal is also significantly more denser then wood. Essentially, the wood punches more for for its weight and  that it actually also leads to it costing less to make. 


<img width="1619" height="1131" alt="image" src="https://github.com/user-attachments/assets/95006cd8-849f-4619-a554-7fdd816e4abd" />


### Finishing the Design and Final Cost
Now given the choice of material, I plugged in its yield strength to find the final additional height to be.... extremely small. Actually, way too small to the point that hitting it just slightly wrong might break it. But that is okay, even though I might raise the height to an actually acceptable size (.15 inches per side), the cost of it does not really matter because this setup with the wood is extremely cheap. After finishing my model, I found that the weight was only .0141 lb and that the cost for one of these, based on the data, was not even worth one cent!
<img width="3488" height="5271" alt="image" src="https://github.com/user-attachments/assets/46eb6293-733a-4f8b-96cc-3687bfb67999" />

## Lessons Learned
In the end, I learned how friction between a rope and a fixed pulley can be used to create mechanical advantage. By designing the pulley system this way, I was able to support a load while applying very little force to the opposite end of the rope.
