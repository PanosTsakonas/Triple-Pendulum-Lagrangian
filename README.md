# Triple Pendulum Lagrangian

This code solves the triple pendulum Lagrangian of a system with 4 Degrees of Freedom (3 in flexion/extension and 1 in abduction). A spherical coordinate system attached at the origin of the 
Metacarpophalangeal (MCP) joint is used and the flexion/extension movement corresponds to the elevation angle and the abduction movement to the azimuthal angle.
Each joint has its own local reference system. If someone desires to see the total flexion angle from the origin then for the total angle you simply need to add all the previous angles to the one 
you are looking.

To solve the system the elevation angle in this code is the complementary angle of the normal definition of the elevation angle. This is chosen so that when the digits are in full extension then 
all the angles are 0 and not 90 degrees.

The digits are assumed to be rigid cylinders with constant desnity of $\rho=1.1 g/cm^3$ 

The moment of inertial of a cylinder about its center of mass is $$I_{com}= m* (R^2/4 + L^2/12)$$ where R and L are the radius and length of the cylinder respectively.

The mass of a cylinder is calculated from the density formula as

$$ m=\rho \pi R^2 L  $$

The center of mass for each cylinder is located at $L/2$ away from the rotating joint

# Deriving the equations

Let subscript 1,2,3 denote the proximal middle and distal phalanges. Let $$\theta_i ,\phi$$ denote the flexion/extension angle of subscript $i$ and the abduction angle respectively.

Then the equation of the spherical coordinates for the system are:

$$ z_1= -L_1*sin(\theta_1)/2 $$

$$ xy_1= -L_1*cos(\theta_1)/2$$

$$ z_2= -(L_1 *sin(\theta_1) +L_2 *sin(\theta_2)/2)$$

$$ xy_2= -(L_1 *cos(\theta_1)+L_2 *cos(\theta_2)/2)$$

$$ z_3= -(L_1 *sin(\theta_1) +L_2 *sin(\theta_2)+L_3 *sin(\theta_3)/2) $$

$$ xy_3= -(L_1 *cos(\theta_1)+L_2 *cos(\theta_2)+L_3 *cos(\theta_3)/2)$$


$$ x_1= xy_1*cos(\phi) $$

$$ y_1= xy_1*sin(\phi) $$


$$ x_2= xy_2*cos(\phi) $$

$$ y_2= xy_2*sin(\phi) $$


$$ x_3= xy_3*cos(\phi) $$

$$ y_3= xy_3*sin(\phi) $$

Then the Kinetic energy of the system is:

$$ $$

$$ K= 1/2 \sum_{i} m_i *[(\dot z_i)^2+ (\dot x_i)^2 + (\dot y_i)^2 + I_{com,i} *[ (\dot \theta_i)^2 +(\dot \phi)^2 cos(\theta_i)^2]]$$

$$ $$

The first part of the kinetic energy corresponds to the parallel axis theorem that will shift the moment of inertia from the midpoint towards the rotating joint.

The potential energy of the system is

$$ $$

$$V= \sum_{i} [m_i *g *z_i  +1/2 K_i (\theta_i -\theta_{eq,i})^2] +1/2 K_a (\phi-\phi_{eq})^2$$

$$ $$

where $K_i, \theta_{eq,i}$ correspond to the spring constant of the passive moment generated at each joint and the equilibrium angle where the total spring efect is 0.


# Lagrangian equation

Now that both the Kinetic and Potential energies are determined the Lagrangian equation is:

$$ $$ 

$$ L = K-V$$

$$ $$

![Lagrangian](https://user-images.githubusercontent.com/64256997/188129462-b028a90e-f311-4fbc-8034-4ceaf6bdd5a3.jpg)







# Rayleigh dissipation function

The damper effect of the passive moment is introduced into the Lagrangian as a Rayleigh dissipation function

$$ $$ 

$$ R=1/2 \sum_{i} [b_i \dot \theta_i ^2] +1/2 b_a \dot \phi^2 $$

$$ $$

where $b_i$ is the torsional damper constant.

# Euler-Lagrange equations

The equations of motion for each generalised coordinate are obtained from the following equation

$$ $$

$$ d/dt [(\partial L /\partial \dot q_i)] -\partial  L / \partial q_i +\partial R / \partial \dot q_i = Q_i $$

$$ $$


# Derivation of Equations

This script shows the Lagrangian derivation and also the respective equations of motion. It is meant as a guide to verify the Lagrangian matrix. In it the $I_i$ corresponds to the moment of inertia about the centre of mass.

# Digit Lagrangian

This is the main script. It solves the Euler-Lagrange equations of the triple pendulum for some user defined initial conditions. The individual lengths and radii have to be given in millimeters. Some spring and damper constants are given but these can be changed if needed. The equilibrium angles can also be changed to experimentally measured ones. There are also user defined inputs, that can be given that must be functions of time. Running the script, plots the resulting angles and angular velocities that have been calculated from numerically solving the equations of motion. A parametric plot that displays the circumduction movement is also there to visualise the circular motion of the digits. Lastly, excel files with the numerical solutions in rads are created, the change in the abduction moment for the given motion, and the theoretically calculated moments of inertia for the flexion moment, the theoretical calculations for the masses and the abduction moment of inertia when the finger is in extension (i.e. all flexion angles are 0). Lastly, an animation of the resulting motion in flexion/extension is shown. 
