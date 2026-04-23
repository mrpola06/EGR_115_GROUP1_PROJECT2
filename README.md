# Orbital Distance or Velocity Calculator - EGR115: Group 1
## Group Members
Odin Ebert, Griffin Heil, Hunter Logan, Maccabee Menig, Aiden Murphrey, Isabel Scalia

## Overview Of The Project
This MATLAB project is an Orbital Distance or Orbital Velocity Calculator that models basic orbital mechanics around a chosen celestial body assuming a circular orbit. The program allows users to choose from preset planetary values or a custom planetary body by inputting mass and radius, then select whether they want to solve for the orbital velocity or orbital distanceUsing these inputs, the code uses basic gravity equations to calculate gravitational acceleration, orbital velocity, orbital radius, and orbital period. 

The code is structured into four main components: an input section that handles planet selection, user validation, and physics-based parameter setup; a loop section that generates datasets for visualization; a plotting section that produces a 3D visualization of the planet and the orbiting object’s trajectory; and a function section that contains reusable physics equations for gravitational acceleration, orbital distance, orbital period, and parametric orbit coordinates. 

## Features
This code has the ability to compute:
- Orbital velocity: The velocity of the orbiting object
- Orbital distance: The distance of orbiting object from the surface of the planet

To do this the code takes these user inputs:
- Mass of the Planet
- Radius of the planet

Then a menue opens up asking if the user would like to provide either:
1. Distance away from the surface
2. Orbiting Velocity

The code takes this data and creates a 3d plot of the orbiting object and its path around the chosen planet.

## Project Components
The Orbital distance or Velocity calculator is composed of one MATLAB file with 4 defined sections.

### Input Section
1. Provide the user with a list of preset planet values
2. Allows for custom user values if they choose to do a custom planet
3. Displays an error if the users custom values do not work with code
4. Prompts the user to choose which quantity to provide: orbital radius or velocity
5. Validates the user’s selection from the menu
6. If radius is chosen, takes input, converts it to distance from the center, and validates it
7. If velocity is chosen, takes and validates the velocity input
8. Uses physics functions to compute gravitational acceleration, orbital period, and the missing variable (velocity or radius) based on the user’s choice.

### Loop Section
1. Builds a dataset for plotting

### Plotting Section
1. Make a 3D visual of the chosen planet
2. Make a 3D visual of the orbiting object
3. Track the path of the orbiting object

### Function Section
1. Gravitational Acceleration
2. Ideal Distance
3. Orbital Period
4. X Orbit Values
5. Y Orbit Values
6. Z Orbit Values

## Example Code Output

I WILL ADD ONCE THE CODE IS 100% DONE

## Physics Connection

### Newton’s law of gravitation (used for surface gravity):
g = \frac{GM}{r^2}
### Orbital velocity (circular orbit):
v = \sqrt{\frac{GM}{r}}
### Orbital radius from velocity:
r = \frac{GM}{v^2}
### Orbital period (Kepler’s 3rd law form):
T = 2\pi \sqrt{\frac{r^3}{GM}}
### Circular orbit parametric equations:
x = r\cos(t)
y = r\sin(t)
z = 0

### Variable Definitions
G = Gravitational Constant
M = mass of central body (chosen planet)
v  = orbital velocity
r = orbital radius (distance from center of planet)
g = Gravitational acceleration at distance r
T = Orbital Period (time for one full orbit)
t = time/ angle variable for plotting


