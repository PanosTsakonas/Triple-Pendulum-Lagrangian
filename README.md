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

$$ z_1= L_1*sin(\theta_1)/2 $$

$$ xy_1= L_1*cos(\theta_1)/2$$

$$ z_2= L_1*sin(\theta_1) +L_2*sin(\theta_2)/2$$

$$ xy_2= L_1*cos(\theta_1)+L_2*cos(\theta_2)/2$$

$$ z_3= L_1*sin(\theta_1) +L_2*sin(\theta_2)+L_3*sin(\theta_3)/2 $$

$$ xy_3= L_1*cos(\theta_1)+L_2*cos(\theta_2)+L_3*cos(\theta_3)/2$$


$$ x_1= xy_1*cos(\phi) $$

$$ y_1= xy_1*sin(\phi) $$


$$ x_2= xy_2*cos(\phi) $$

$$ y_2= xy_2*sin(\phi) $$


$$ x_3= xy_3*cos(\phi) $$

$$ y_3= xy_3*sin(\phi) $$

Then the Kinetic energy of the system is:

$$ $$

$$ K= 1/2 \sum m_i *[(\dot z_i)^2+ (\dot x_i)^2 + (\dot y_i)^2 + I_{com,i} *[ (\dot \theta_i)^2 +(\dot \phi)^2 cos(\theta_i)^2]]$$

$$ $$

The first part of the kinetic energy corresponds to the parallel axis theorem that will shift the moment of inertia from the midpoint towards the rotating joint.

The potential energy of the system is

$$ $$

$$V= \sum [m_i *g*z_i +1/2 K_i (\theta_i -\theta_{eq,i})^2]$$

$$ $$

where $K_i, \theta_{eq,i}$ correspond to the spring constant of the passive moment generated at each joint and the equilibrium angle where the total spring efect is 0.


# Lagrangian equation

Now that both the Kinetic and Potential energies are determined the Lagrangian equation is:

$$ $$ 

$$ L = K-V$$

$$ L= [1/2,1/2,1/2][■(𝑚_1 ((𝑅_1^2)/4+(𝐿_1^2)/3),&0,&0@𝑚_2 𝐿_1^2,&𝑚_2 ((𝑅_2^2)/4+(𝐿_2^2)/3),&0@𝑚_3 𝐿_1^2,&𝑚_3 𝐿_2^2,&𝑚_3 ((𝑅_3^2)/4+(𝐿_3^2)/3))][■((θ_1^2 ) ̇+(𝜙^2 ) ̇ cos^2⁡(𝜃_1 )  @(θ_2^2 ) ̇+(𝜙^2 ) ̇ cos^2⁡(𝜃_2 )@(θ_3^2 ) ̇+(𝜙^2 ) ̇ cos^2⁡(𝜃_3 ) )]+[■((𝑚_2/2+𝑚_3 ) 𝐿_1 𝐿_2,&𝑚_3/2 𝐿_1 𝐿_3,&𝑚_3/2 𝐿_2 𝐿_3 )][■((𝜃_1 ) ̇(𝜃_2 ) ̇cos(θ_1−θ_2 )+(𝜙^2 ) ̇ cos⁡(𝜃_1 )  cos⁡(𝜃_2 )@(𝜃_1 ) ̇(𝜃_3 ) ̇cos(θ_1−θ_3 )+(𝜙^2 ) ̇ cos⁡(𝜃_1 )  cos⁡(𝜃_3 )@(𝜃_2 ) ̇(𝜃_3 ) ̇cos(θ_2−θ_3 )+(𝜙^2 ) ̇ cos⁡(𝜃_3 )  cos⁡(𝜃_2 ) )]−[𝑚_1 𝑔,𝑚_2 𝑔,𝑚_3 𝑔][■(𝐿_1/2  sin⁡(𝜃_1 )@𝐿_1  sin⁡(𝜃_1 )+𝐿_2/2  sin⁡(𝜃_2 )@𝐿_1  sin⁡(𝜃_1 )+𝐿_2  sin⁡(𝜃_2 )+𝐿_3/2  sin⁡(𝜃_3 ) )]−[𝐾_1/2,𝐾_2/2,𝐾_3/2,𝐾_𝑎/2][■((𝜃_1−𝜃_(𝑒𝑞,1) )^2@(𝜃_2−𝜃_(𝑒𝑞,2) )^2@(𝜃_3−𝜃_(𝑒𝑞,3) )^2@(𝜙−𝜙_𝑒𝑞 )^2 )]$$


$$ $$

# Rayleigh dissipation function

The damper effect of the passive moment is introduced into the Lagrangian as a Rayleigh dissipation function

$$ $$ 

$$ R=1/2 \sum b_i \dot \theta_i ^2 $$

$$ $$

where $b_i$ is the torsional damper constant.

# Euler-Lagrange equations

The equations of motion for each generalised coordinate are obtained from the following equation

$$ $$

$$ d/dt [(\partial L /\partial \dot q_i)] -\partial  L / \partial q_i +\partial R / \partial \dot q_i = Q_i $$

$$ $$

