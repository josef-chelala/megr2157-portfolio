# A5 – Bracket Design
## Choices
### Choice of Material
[Using this data sheet for astm A36 steel from Matweb](https://www.matweb.com/search/DataSheet.aspx?MatGUID=d1844977c5c8440cb9a3a967f8909c3a), I found that young's modulus was 29,000,000 psi (2.9 * 10^(7) psi) and the yield strength is 36,300 psi. Just looking at the young's modulus tells me that deflection will not be an issue.

### Length 
The Uline Strap given was .75 inches, so I decided that I would use that for almost every "length" used in each section.


## Calculations
### Section A
#### Knowns, Unknowns, and Assumptions
![Inserted Picture](Pictures/1.png)
#### Stress Symbolic Solution
![Inserted Picture](Pictures/2.png)
#### Stress Solution
![Inserted Picture](Pictures/3.png)
#### Stiffness Symbolic Solution
![Inserted Picture](Pictures/4.png)
#### Stiffness Solution
![Inserted Picture](Pictures/5.png)

### Section B
#### Knowns, Unknowns, and Assumptions
![Inserted Picture](Pictures/6.png)
#### Stress Symbolic Solution
![Inserted Picture](Pictures/7.png)
#### Stress Solution
![Inserted Picture](Pictures/8.png)
#### Stiffness Symbolic Solution
![Inserted Picture](Pictures/9.png)
#### Stiffness Solution
![Inserted Picture](Pictures/10.png)

### Given dimensions for the rest of the sections
![Inserted Picture](Pictures/11.png)

### Section C
#### Knowns, Unknowns, and Assumptions
![Inserted Picture](Pictures/12.png)
#### Stress Symbolic Solution
![Inserted Picture](Pictures/13.png)
#### Stress Solution
![Inserted Picture](Pictures/14.png)
#### Stiffness Symbolic Solution
![Inserted Picture](Pictures/15.png)
#### Stiffness Solution
![Inserted Picture](Pictures/16.png)

### Section D
#### Knowns, Unknowns, and Assumptions
![Inserted Picture](Pictures/17.png)
#### Stress Symbolic Solution
![Inserted Picture](Pictures/18.png)
#### Stress Solution
![Inserted Picture](Pictures/19.png)
#### Stiffness Symbolic Solution
![Inserted Picture](Pictures/20.png)
#### Stiffness Solution
![Inserted Picture](Pictures/21.png)

### Section E
#### Knowns, Unknowns, and Assumptions
![Inserted Picture](Pictures/22.png)
#### Stress Symbolic Solution
![Inserted Picture](Pictures/23.png)
#### Stress Solution
![Inserted Picture](Pictures/24.png)
#### Stiffness Symbolic Solution
![Inserted Picture](Pictures/25.png)
#### Stiffness Solution
![Inserted Picture](Pictures/26.png)

## Sketches
These were technically hand drawn, however, I used OneNote and not physical paper. I did draw it though, I used a ruler tool in OneNote
### Stress Sketch
![Inserted Picture](Pictures/27.png)

### Stiffness Sketch
![Inserted Picture](Pictures/28.png)

## Lessons Learned
### Governing Failure Mode
For every single section, stress governed the final dimensions. This is because of Steel's massive modulus of elasticity and the fact that .005 inch deflection is relatively small for steel with these small dimension constraints and choices. For example on the extreme end, the thickness of section D for stress was .1175 inches while the stiffness gave an extremely small .01103 inch thickness. That is nearly a 10 times decrease in thickness.
### Error Propagation
The only "Error" I made was not using the .75 inch strip length (I initially wanted to used 2.5 inches), however, that was not required for us to use. I did go back and redo my calculations to do that. Otherwise, the only value that was consitently used were the forces that was transfer via reactions forces from one section to the next. This was incredible easy to keep track off cause it was always either 1600 lbf or half that. The part that made sure I didn't mess it up were the FBDs.
### Assumption sensitivity
The biggest assumption that is highly questionable is the setup of section E. The fact that Section E lays flat on the Rigid T beam with only the force on the very edge means calculations for it are very unrealistic. What would actually happen if this was the case would lead to a height of that section being "unsolvable" since a height would not matter. In real life, since there are sections connecting D to E, is that there would be curvature from that area that would lead to some bending at section E. Additionally, that would try to pull section E off, but friction through out the bracket connected to the beam that would put some load back on E.


## Link Creation
Since stress governed the final dimensions, I will be using that for this calculations
![Inserted Picture](Pictures/29.png)
