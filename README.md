# Triple Pendulum Lagrangian

This code solves the triple pendulum Lagrangian of a system with 4 Degrees of Freedom (3 in flexion/extension and 1 in abduction). A spherical coordinate system attached at the origin of the 
Metacarpophalangeal (MCP) joint is used and the flexion/extension movement corresponds to the elevation angle and the abduction movement to the azimuthal angle.
Each joint has its own local reference system. If someone desires to see the total flexion angle from the origin then for the total angle you simply need to add all the previous angles to the one 
you are looking.

To solve the system the elevation angle in this code is the complementary angle of the normal definition of the elevation angle. This is chosen so that when the digits are in full extension then 
all the angles are 0 and not 90 degrees.

The digits are assumed to be rigid cylinders with constant desnity of r=1.1 g/cm^3.

The moment of inertial of a cylinder about its center of mass is Icom= R^2/4 + L^2/12, where R and L are the radius and length of the cylinder respectively.

The center of mass for each cylinder is located at L/2 away from the rotating joint

# Deriving the equations

Let subscript 1,2,3 denote the proximal middle and distal phalanges. 

z1=L1*sin(\theta_1)




