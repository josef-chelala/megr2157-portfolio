# A8 – Gears

## Design of the shafts
### Input Shaft
<img width="2944" height="7915" alt="In Shaft Math" src="https://github.com/user-attachments/assets/b41c3e5a-fbbe-4e4d-b570-58231bf1dc7d" />
### Output Shaft
<img width="2920" height="6055" alt="Out Shaft Math" src="https://github.com/user-attachments/assets/f279d515-eb75-434c-ab0b-5e004cdb39bc" />

## Design Journal Bearings
### Output Bearings
#### Issues
In the “Mechanical Power Transmission Systems: Tutorial Gears” paper given as part of this assigment, I noticed that a dual gear train in a gear box with an input and output should look like the below.

<img width="1039" height="529" alt="image" src="https://github.com/user-attachments/assets/7696d576-dd04-4d61-b744-75f96dd3c9a8" />

In order to get a general understanding of how to follow this build, I made a quick mock up of the approach I was going to take and found major issues on how to cleanly achieve a simple gear box. Using only the gears given and only choosing from the list of journey bearings of the given manufacturing website, I realized there is a major issue in sizing for the output side of the gearbox. Either the length of the shaft is too short, the length of the hub is too long, or the minimum length of the manufacturers journey bearings were very limited. For a basic gear box, it is much easier to keep the journey bearing at an equal distance apart from the center of the teeth of the gear so that the reaction force split between them are equal. However, the length of the hub of the output gear is .25 inches which is two times the thickness of the gear, plus the smallest length is .25 inches for the manufacturers' journal bearings. Ignoring clearances, since one journal bearing must take into account the additional hub length, it at a minimum must be .25 inch + .125inch / 2 = .3125 inches away from the center of the teeth. To make them equal distances away from the center of the teeth, that is additional .3125 inches away. Lastly, is to included the lengths of the bearings, which gives a total (without clearances) of the gears and bearings taking up a length of 1.125 inches, longer than the shaft itself. The easiest solution is to just increase the length of the shaft, but the assignment limits this. Because I love making my life complicated for no reason, I decided that I would trying bringing both journals as close to the gear as possible and to try and base my calculations off the offset difference between them. To make my life easier, after finding which bearing will have the highest reaction moment/force, I decided to just use the same calculated bearing from that result on each side of the output shaft. 
#### Setup and Assumptions
For my setup, I decided to use the smallest possible length of the output journal bearings which is .25 inches. Next, to decided on the gap between the bearings, I had to use ChatGPT to give me a realistic estimate for the smallest possible gap between them since it seems there are a lot of factors to take into considerations that I simply do not know enough about (thermo and the weirdness of the gear shape) and additionally the Machinery's Handbook does not discuss it. After discussing with it, it gave me a very rough guess of about .015 inches. For the sake of time I stuck with it. The reason for trying to minimize these lengths is to squeeze as much length as possible for the output shaft's section that is sticking out of the gear box. Lastly, I am assuming that reaction force of each bearing is at the center of its length. 

#### Finding the Force
<img width="3680" height="13771" alt="OutPut Bear 1" src="https://github.com/user-attachments/assets/339e14a1-f116-42a8-95f7-fd32f0c42030" />

#### Finding the Material
In the end, I landed on either Acetal or Nylon
<img width="2253" height="11340" alt="image" src="https://github.com/user-attachments/assets/910a9127-76c8-483a-81ed-1e6089fdc4ca" />




#### Thickness of Output Bearings
There are several crucial bits of information that are left out to be able to get an accurate thickness of the bearings. We are not given a factor of safety, nor are we told how exactly to find the thickness nor diameter. I spent 2 hours going through the machinery's handbook and it just completely skips over this. I will just assume that I need to reuse the bearing stress equation along with the chart's 1000 psi limit load capacity as the max stress to find the thickness. In the end, the clearance was the deciding factor since it gave me only one option based on the given parameters, which gave me Nylon

<img width="2292" height="8953" alt="image" src="https://github.com/user-attachments/assets/ec693f09-5f3e-44be-a6c1-3c5619069a28" />


### Input Bearings
#### Setup
On website, for a .125 in shaft, the minimum length for a workable bearing is 1/8th on an inch. I will chose this to maximize the ability to simply split the force in half for each bearing and the length of the shaft sticking out of the gear box. To use a less extreme and realistic clearance gap between the gears and bearings, I decided on 1/16 in. 

#### Solving for the Material
In the end, I was forced to chose Bronze since it had the smallest length for the diameter of the shaft so I could minimize the amount of choking of the shaft.
<img width="3435" height="16048" alt="image" src="https://github.com/user-attachments/assets/3c2d64fd-9ea3-418b-a422-0344fd2bcf62" />

#### Thickness
This, of course has the same issues as the Output Bearing thickness. This time I used Bronze's 4500 psi load capacity
<img width="2052" height="6674" alt="image" src="https://github.com/user-attachments/assets/723624e8-8977-4866-844a-9808ef48aa31" />



## The Gear Box

### Sketch

### Creating the Input Shaft
To create the input shaft, I simply made rod of a .125 in diameter and 1 in length as asked for us to do.
<img width="1287" height="939" alt="image" src="https://github.com/user-attachments/assets/016e47ae-a692-47e2-a16b-c382d7af4960" />


### Creating the Output Shaft
To create the output shaft, I simply made rod of a .25in diameter and 1 in length as asked for us to do.
<img width="1509" height="1127" alt="image" src="https://github.com/user-attachments/assets/069d9f15-9f2e-4fe8-a70a-9f844446f750" />

### Creating the Input
#### Making Everything Concentric
After creating an assembly, I inserted all components I chosen for the Input section of the gear box. I started creating the input by making everything concentric with the input shaft.
<img width="1761" height="887" alt="image" src="https://github.com/user-attachments/assets/4ae89545-3e0a-4789-a88f-25542cdc7cd3" />
#### Spacing Them Out
##### Setup
Next, I made one of the bearings flush with one end of the shaft. In this case, it is the bearing on the side of the hub of the gear, and mated the interior distance between the two with a distance mate. Then I made a plane at the center of the Pinion gear. Lastly, I did another distance mate between the interior distance between the other bearing and gear.
<img width="1453" height="893" alt="image" src="https://github.com/user-attachments/assets/7bc5095a-8f4d-42e7-839f-b4c3306844a0" />
##### Applying the Distances
To start, I stated before that I wanted there to be a 1/16 inch clearance gap between the closest bearing to the hub. So I simply just have to change that mate distance to .02 inches. Secondly, I wanted to make sure the that the bearing pair were equal ways apart from the center of the gear. To do that I must make the other distance mate be the thickness of the hub (.19 in) plus the clearance gap plus half the gears thickness (.0625 in) to get .2725 in gap from the plane I made earlier.
<img width="1731" height="855" alt="image" src="https://github.com/user-attachments/assets/4f35275f-86af-4d90-80be-6efeedf8d676" />

### Creating the Output
#### Making Everything Concentric
In the same assembly, I did the same as earlier and made all parts of the output concentric
<img width="1533" height="991" alt="image" src="https://github.com/user-attachments/assets/837860c9-fe77-4980-8756-e37142aeb57d" />
#### Spacing Them Out
This is easier to set up. I decided before to simply have the bearings be .015 inches away from the sides of the gear. So this time I just immediately set the distances between them. The big difference this time, is that I needed to make sure the non-hub side of the gear's bearing to be flush with the output shaft. This will be made clear in a second. As clearly seen below, it seems that part of the shaft that needs to stick out is greatly choked.
<img width="1277" height="1091" alt="image" src="https://github.com/user-attachments/assets/02b4323b-ad8a-4d53-aa9f-9541bde16bda" />
### Aligning the Input and Output
#### Aligning the Centers of the Gears
To start, I created a center plane for the large gear and then mated it to the other gears center plane I made earlier.
<img width="1687" height="1087" alt="image" src="https://github.com/user-attachments/assets/d994096c-87cd-4d11-ad01-7801c0cdccdc" />
#### Center to Center Distance
##### Calculation
Using the textbook's given gear equations, I found an easy way to correctly distance the axes between the two. I Found the center to center to be .6875 inches.
<img width="1631" height="1515" alt="image" src="https://github.com/user-attachments/assets/9a2dfd29-c4c8-4621-86aa-3613a4200686" />
##### Applying the Distance
Luckily, the gears from the website came with center axes premade, so I simply just mated the distance between them.
<img width="1193" height="793" alt="image" src="https://github.com/user-attachments/assets/b9a7d421-2c98-4359-989c-3de2ce9ac2df" />

#### Aligning the Mesh
##### Setup
Usually, the hardest part of putting gears together is correctly interlocking the teeth with one another. However, the gear models came premade with axes that actually correctly align them with one another to get a 20 degree pressure angle. For each gear, I create a plane that was aligned among their respective center axis and the given perfectly placed pitched axis.
<img width="1699" height="1121" alt="image" src="https://github.com/user-attachments/assets/58c3870a-81ac-4ea1-8f36-c9106a911298" />

##### Aligning
All I had to do was just coincident mate the planes and they are perfectly aligned.
<img width="2071" height="1367" alt="image" src="https://github.com/user-attachments/assets/5f2ae00a-3786-4081-a7f9-37386356adad" />

### Creating the Gearbox
I decided for my approach, that I actually would just create the part with in the assembly.
#### Outline of Both Sides with Traces Bearings
<img width="1139" height="1159" alt="image" src="https://github.com/user-attachments/assets/bad46fd0-eb4a-4ba6-a072-34392e9a6d27" />
<img width="1431" height="929" alt="image" src="https://github.com/user-attachments/assets/5eff11bd-c655-474f-a014-b1b0b6325399" />
<img width="1253" height="833" alt="image" src="https://github.com/user-attachments/assets/63ec6141-0699-4ec8-aa19-9bb1457f7a0a" />

#### Adding the Flaps
<img width="945" height="1075" alt="image" src="https://github.com/user-attachments/assets/a1014c7e-42b3-4b99-99d7-14b425934ffa" />
<img width="895" height="941" alt="image" src="https://github.com/user-attachments/assets/0e9df003-0232-436a-b5ba-79177257a24a" />

#### Adding the Screw and Nut Hole
<img width="809" height="877" alt="image" src="https://github.com/user-attachments/assets/5f73bad1-aa64-4b58-a49d-e8e3f98b7c1a" />
<img width="1181" height="1221" alt="image" src="https://github.com/user-attachments/assets/61fa5cf8-c467-499b-9a0c-fc76c171ce0d" />




