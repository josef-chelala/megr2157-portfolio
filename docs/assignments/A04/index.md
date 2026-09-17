<img width="5612" height="9846" alt="F1 Deflection" src="https://github.com/user-attachments/assets/ed0d0b4c-08bc-4e3c-9f75-9ba45f040be4" /># A4 – Motor Mount

## Given Resources 

PETG had the highest material properties of the given materials, therefore I decided to use this to try to minimize the sizes of the features. [I will be using the data sheet given as part of the assignment.](https://www.matweb.com/search/DataSheet.aspx?MatGUID=4de1c85bb946406a86c52b688e3810d0&ckck=1) 

Also, the project is heavily dependent of the [design of the motor given to us as part of the assignment as well](https://www.omc-stepperonline.com/brushed-24v-dc-gear-motor-3-6kg-cm-46rpm-w-99-5-1-planetary-gearbox-pa28-28245800-g100). Specifically the size of the shaft and the largest diameter of the motor is essential as well.
<img width="2736" height="961" alt="image" src="https://github.com/user-attachments/assets/dec8c0e4-8c03-417e-93e8-33e781cd6772" />

## General Approach
The only way to solve these problems is to pick reasonable length and then pick a reasonable base or height and solve for the other. Height would be problematic for the shaft in feature 1, plus feature 1 and 2 will share the same base, therefore I chose to solve for height and pick my own base.

## Feature 1
### Knowns and Unknowns
To start, I wrote down every known and unknown that will likely be necessary to use to solve for the cross sectional area of feature via yielding and deflection.
<img width="5302" height="14234" alt="Knows 1" src="https://github.com/user-attachments/assets/30c70685-37a8-4221-aef8-606580b03f2c" />

### Figuring Out Length and Base
Next, in order to solve I had to calculate the lengths I needed to solve these equations. I extensively wrote my explanations in my notes below. Due to lack of time, I decided on 10mm gap. Also decided to give all edges surrounding motor 5mm gaps, to minimize creating as much height as possible



### Deflection
Next, I symbolically solved and then completely solved the deflection for feature 1. The most important component of this part of the problem is that the force is applied PARALLEL not perpendicular to the beam like usual problems. This changes up the equations and how to approach the problem completely. For example, to solve for parts of the beam that does not have any moment or force applied, I had to take the derivative of the 
<img width="5612" height="9846" alt="F1 Deflection" src="https://github.com/user-attachments/assets/91d6bce4-3114-4fcd-9e94-778c49cd68f7" />

### Yield

<img width="4589" height="11197" alt="F2 Yield" src="https://github.com/user-attachments/assets/1180889c-b9a1-422a-9849-0840ba54dce7" />

### Which had the larger height?
Unsurprisingly, deflection increased and the height almost double of yield. The length was just significantly more and plastics are not the greatests for this sort of application.  

## Feature 2
### Knows and Unknowns
<img width="5247" height="12628" alt="Knows 22222222222" src="https://github.com/user-attachments/assets/c6d94906-c61c-423d-8e78-a0910a743274" />

### Figuring Out Length
[This article](https://protoplastics.com/designing-plastic-parts-guide/) says to make screw distances from plastic edges to be 2x the diameter of the screw

<img width="5370" height="14036" alt="f2 LENGTH" src="https://github.com/user-attachments/assets/da0001a8-3166-468d-8a8d-2763d18944de" />

### Deflection
<img width="4846" height="9576" alt="f2_maxDef" src="https://github.com/user-attachments/assets/ac40e448-aff4-4f73-8b95-311ce35a8c48" />

### Yield
<img width="4589" height="11197" alt="F2 Yield" src="https://github.com/user-attachments/assets/57ba8da3-0f2a-4e56-9a29-17ac2fed69fa" />

### Which had a larger height?
Completely unsurprising, the yield had a far larger height than deflection. This is becasue the length that wasn't attached to the wall was incredibly strong. 

## CAD Design
### Drawing

To further this design, I researched some 90 degree motor mounts and [I came across this one](https://www.walmart.com/ip/42-Stepper-Motor-Bracket-Nema17-Mounting-L-Bracket-Mount-Step-Motor-Mount-Holder/5349534311) seen below. It is actually made of ABS plastic, showing this is a realistic idea for additive manufacturing. Not wanting to redesign the entire wall mount, I decided to only keep the triangling looking supports. I am certain this could cause relief to the excessively thick part of feature 1. 
<img width="573" height="573" alt="image" src="https://github.com/user-attachments/assets/b7b6b8dd-df59-4d85-9f46-d9ee259b52ca" />

Also I decided to fillet the section connecting the two features together which should further help against deformation, I decided on 3mm. Leading to my final design:

<img width="2489" height="1419" alt="image" src="https://github.com/user-attachments/assets/123c255c-fb9b-44b3-86af-f1dc1efeb766" />

### Creating the Model

#### Feature 1
##### Parametric Equations
To design feature one, I used these parametric equations in order to make the model
<img width="2553" height="1227" alt="image" src="https://github.com/user-attachments/assets/e61a8a13-0b5d-4548-a48d-1ce8b2e44d2b" />
##### Making the Base
First I made a rectangle, then I applied the calculated base and height for feature 1 into its dimensions
<img width="2712" height="1596" alt="1" src="https://github.com/user-attachments/assets/5fe4c8ac-64f3-4288-a06b-d863276cbafd" />

Then I extruded it given the calculated length
<img width="2712" height="1596" alt="2" src="https://github.com/user-attachments/assets/b7d1aa62-5cbc-4a57-8b85-5900b06ea447" />

##### Adding the Indent
I decided to add the indent from the motor (about 2mm deep and 22mm diameter. I made a dimension that gave the gap between the center of the shaft to the gap. 
<img width="2712" height="1596" alt="3" src="https://github.com/user-attachments/assets/45955c77-b8ff-4217-8177-ede92cd6ff73" />
Then I extrude cut it  2mm deep
<img width="2712" height="1596" alt="4" src="https://github.com/user-attachments/assets/60882392-b654-46f5-903d-c516ca04ae3b" />
I realized I used the wrong diameter so I fixed it afterwards
<img width="1781" height="1349" alt="5" src="https://github.com/user-attachments/assets/90568eac-4e7b-43dc-b346-2f2e60bc6fe3" />
That concludes Feature 1

#### Feature 2 
##### Parametric Equations
To design Feature 2 I used these parametric equations in order to make the model
##### Making the wall base
First I made a rectangle, then I applied the calculated base and height for feature 2 into its dimensions
<img width="2712" height="1596" alt="1" src="https://github.com/user-attachments/assets/6b44fc9a-3e35-4f23-950a-07c990536b58" />
Then I extruded it based on the wall length, ignoring the additional height of feature 1 that I used to solve for Feature 2
<img width="1824" height="1288" alt="2" src="https://github.com/user-attachments/assets/bb001bee-c70f-43b2-bdae-8d5306fa8939" />
##### Adding the Screw Holes
Next, I added the 4 circles to the top of the model, aligned them with one another, and made them equal to one another
<img width="2450" height="1288" alt="3" src="https://github.com/user-attachments/assets/849135d7-70c3-43b2-81d2-a8ea41503fd0" />
Once I finished that, I added all necessary dimensions. I made the holes equal to the given screw diameters. Then I made sure that they were 2x the distance of their diameter away from the edges
<img width="2450" height="1288" alt="4" src="https://github.com/user-attachments/assets/e19d178c-9f2c-4dd6-8c1c-f5ee8b95df26" />
Lastly, I extrude cut to the other side of the model
<img width="2012" height="1288" alt="5" src="https://github.com/user-attachments/assets/93ff525d-3ac1-4224-9389-5ba743c3b1e8" />
##### Adding the Last Additional Length
Remember, that their is also the additional length needed to connect features 1 and 2 together. This is done by simply adding the height that was solved for feature 1.
<img width="2546" height="1548" alt="6" src="https://github.com/user-attachments/assets/44689382-bbf7-4d06-8b6f-ad1259d2241b" />

#### Initial Assembly Setup
##### Adding the Two Features
First, I simply dragged and dropped both features into the assembly
<img width="2546" height="1548" alt="1" src="https://github.com/user-attachments/assets/32aacc36-bffa-4f7e-b7a1-5135d1cc4080" />
Then I mated them together like they are supposed to be 
<img width="2546" height="1548" alt="2" src="https://github.com/user-attachments/assets/c924a39d-6d00-49ce-8bfb-389298478b48" />

##### Creating the Supports
Instead of mathematically solving how to connect the supports, I simply created a sketch in the assembly connecting the tips.
<img width="2546" height="1548" alt="3" src="https://github.com/user-attachments/assets/a94f3b1f-ce5e-4685-9d35-22066460d69c" />
SolidWorks does not allow you to make parts within an assembly, so I simply created a new file then copy and pasted the sketch into the new part
<img width="2546" height="1548" alt="4" src="https://github.com/user-attachments/assets/724ba0ca-cce7-4d0c-9fe0-db1e9b14c179" />
Earlier I decided to make its thickness the size of the bolt size. So I simply extruded it at that thickness.
<img width="2546" height="1548" alt="5" src="https://github.com/user-attachments/assets/809d2226-ac3d-46bf-8449-b0efcf51f317" />

##### The "Final" Assembly
Once created, I added the new support part into the assembly. Then matted it to where I designed it to be. Off screen, I did the same thing again on the other side.
<img width="2546" height="1548" alt="6" src="https://github.com/user-attachments/assets/ae0d0d9a-2c1b-4122-b007-02f28b2f3e94" />
For whatever reason, I could not get the assembly to create a fillet. So I had to find a workaround. To do so, I exported this assembly as a part.
<img width="2546" height="1548" alt="8" src="https://github.com/user-attachments/assets/aab2773c-c4f4-48d6-9975-5ca2f6e9084d" />


#### Actual Final Assembly
##### Merging All Components
To make a fillet, I had to combine all the components. To do so, I opened the new part file, and used the combine feature to merge them together.
<img width="2546" height="1548" alt="9" src="https://github.com/user-attachments/assets/33b6c27e-644d-4a5e-8bf6-2ca317b714ca" />
##### The Final Step
All, I had to do now was add a fillet. I had no time left to research an appropriate fillet radius. So I simply chose 3mm. This completed the Assembly
<img width="2546" height="1548" alt="10" src="https://github.com/user-attachments/assets/160031a5-22ad-4ce9-ba7c-13cfc7774344" />

### The Finished Model
[Here is a picture of the finished model, Followed by all the files I used to create it.](https://drive.google.com/file/d/16o2YxqmDvwLovTEjgNi4sFD1KbKqM24B/view?usp=drive_link)



























In order to add fillet I have to save the assembly as a part. This will lose the equations, so I will give every single part and assembly file attatched.
