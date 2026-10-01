# A6 – Bracket Drawing

## Bracket Parametric Design
### SolidWorks Equations
For this project, I used SolidWorks equations to parametrically design this bracket. First, I added all necessary date to start with, and then I added the equations needed to solve each question add additional data when need. I found a way to make "if" statements in SolidWorks Equations, so I had the ability to make stress or deflections automatically overtake the dimension if after solving one was bigger than another. I only did it for Section A, however, because deflections will not be the deciding factor for literal steel at these small dimensions. Lastly, since the way the sections were split up cut off some dimensions between C and D as well as C and E, I decided to make one last dimension that added the thicknesses of C and E to D to make modeling easier.
![Inserted Picture](Pictures/1.png)

### Creating Section A
#### Sketching
To start, I simply created a circle at the central axis of all 3 planes and set the diameter to the calculate result for section A's diameter
![Inserted Picture](Pictures/2.png)
#### Extrusion
Then, I simply extruded it to my chosen general length variable. This is where I realized I had made a mistake in the last lab. The problem is that Section B will choke the length of Section A, meaning that the Uline Strap would not be able to fit. This can be fixed with slight changes to the math, but I do not have time to fix this and it really does not matter.
![Inserted Picture](Pictures/3.png)
### Creating Section B
#### Sketching
I simple created a sketch on one of the flat sides of Section A. From there, I simply created a rectangle across the horizontal diameter (meaning its dimension in this direction is the same as the diameter) and plugged in its variable that combines my 1 inch length I chose with the radius of section A to get my desired length I created my equations based on.
![Inserted Picture](Pictures/4.png)
#### Extrusion
Then I simply extruded it by the variable of the thickness I solved for this part. Notice how it chokes section A a bit.
![Inserted Picture](Pictures/5.png)
### Creating Section C
#### Sketching
Starting the sketch on top of Section B, I simply created a rectangle that made the height be the general length, made the midpoint of the rectangle line up with the line of symmetry of the rest of the bracket, and made its width the calculation of the given "a" and "b" parameters.
![Inserted Picture](Pictures/6.png)
#### Extrusion
Then I simply extruded it by the calculated thickness variable for section C
![Inserted Picture](Pictures/7.png)
### Creating Section D
#### Sketching
As stated before, I made an additional variable that combined the height of the section with the thickness of C and E. Because of that, I started the sketch at the bottom of section C. Since the based shared the same general length and D was directly connected to C, all I had to do was use the thickness variable I had calculated.
![Inserted Picture](Pictures/8.png)
#### Extrusion
Then I simply extruded its length by the additional variable I created.
![Inserted Picture](Pictures/9.png)
### Creating Section E
#### Sketch
Sketch, since the elongated section D already included the thickness of E, I simply started the sketch on the top of D. Then I made the sketch for E on C's edge. Since they shared the same base, I simply dimensioned its length to "b". 
![Inserted Picture](Pictures/10.png)
#### Extrusion
Then I extruded DOWNWARDS its thickness to correctly align it with D.
![Inserted Picture](Pictures/11.png)
### Mirror to Completion
Since the bracket is symmetrically on one axis, I simply had to just mirror Sections D and E to finish the model. You need to go on my github to see this gif
![Inserted Picture](Pictures/12.gif)

## Drawing
Below is the finished drawing of the bracket. Keep in mind that last minute adjustments were made to make sure that the correct fit dimensions were shown. I recommend right clicking the image and opening it in a new tab.
![Inserted Picture](Pictures/Bracket.PNG)

## Reflections 
One thing I learned is that it is actually appropriate in engineering drawing standards to only have to dimension one half of a symmetrical section of a part. Furthermore, if one shape/dimension passes the line of symmetry, you can dimension that entire specific area instead of only doing half of it. This was useful in the top view of my drawing because "a" having a range of dimensions meant that it could make dimensioning tolerances more difficult if I had cut it in half at the line of symmetry. 

<br>

Another thing I learned is that a vast majority of the class, including myself, completely misunderstood the setup of the last lab and this one. A vast majority of people interpreted "a", "b", and "c" were the dimensions we were to build with, however that was the "shaft" portion and we were supposed to figure out the hole portion. I figured this out in the last two hours I worked on this project. I think that things should be made clearer for the next time. However, I feel I have a much better understanding on how to use the book to figure out fits. 

<br>

The last thing I learned is that I need to find a way to make sure files back up correctly because I lost hours of work after SolidWorks crashed and again later when my computer crashed

<br>

As discussed in my Parametric Equations section, I added both stress and deflection equations to solve for the diameter of section A. I used multiple user set variables that would plug into those equations. I then set an if statement that would set the diameter of the section to one of the two equations that gave a bigger diameter. Now, this bracket is very small and is made out of steel, so it is of no surprise that it would take significant "lengths" for deflection to even be needed to be considered. So I only used stress and obiously that if statement would constant have stress winning.


## Link
### Parametric Equations for Link
Below is the parameters and equations I used to make the link. Notice that I built the width of the rectangle along the bigger, 1 inch diameter. This is because it has the smallest cross sectional area at the horizonal 1 inch diameter in the entire link. The normal stresses have to calculate at this point, or else the part will not be at the desired factor of safety. Furthermore, I made the thickness of the link smaller than the chocked section A length, or it would not have full connection with the bracket. Lastly, I used the RC2 fits for the hole connected to section A in order to get a running fit.
![Inserted Picture](Pictures/link-1.png)
### Creation of the General Shape of the Link
I simply made a rectangle, then created arcs that connected to each edge of the rectangle. Since the base and diameter of the arcs were the same, I just had to make the rectangles base equal to the diameter, plus make its length the center to center of the arcs. Then I extruded it to my chosen .25 in thickness.
![Inserted Picture](Pictures/link-2.png)
![Inserted Picture](Pictures/link-3.png)
### Cutting the Holes 
Since the arcs would be concentric to the milled holes, I simply just had to make the circles line up concentrically and set them to their respective diameter variables (didn't matter which was which). Then I simply extrude cut them through the link.
![Inserted Picture](Pictures/link-4.png)
![Inserted Picture](Pictures/link-5.png)
### Finished Link
Simply created and calculated.


![Inserted Picture](Pictures/link-6.png)
### Drawing of the Link
Again, I recommend right clicking the image and opening it in a new tab.

![Inserted Picture](Pictures/Link.PNG)

## Link Reflection
After this lab, I feel I finally understood how to work with fits. While with the bracket we only worked with one object we created, I was able to learn how to make section A from the bracket I made work with a fit in the link I created. Last week I was unable to do so, however, after some more detailed reading of the book it finally clicked. One thing that I found interesting buck quickly understood is that as a hole/shaft diameter increases, so does the range of the tolerances. The reason is that errors in manufacturing have a higher chance of happening as size increases and this effect is additive. However, as I have (briefly) read, this isn't necessarily terrible because the increase in size and tolerance are not linearly proportional. So as dimensions increase, tolerance increase but at a slower rate. Meaning tolerances get easier as size increases.

The differing fits requirements shown through the ranges of tolerance show how tightly packed and therefore how much movement is allowable between a hole and shaft in a fit.

## Total Time
Sadly, this project took me about 10 to 11 hours. The reason is that I had crashes twice that wiped hours of work, and I had to redo and learn the fit sections in order to have better dimensioned drawings

## Downloadable Models and Drawings
[You can download this zip that contains all models, drawings, and a high quality PNG of the drawings here
](https://drive.google.com/file/d/1-VW4ssBY_MYy0DHqNoc7_N2lLkJi6o4Z/view?usp=sharing)





