# Active-Flutter-Supression
This project extends the 2-DOF aeroelasticity flutter model to include an active control system that suppresses flutter above the passive critical speed. Both PID and LQR controllers are designed and compared.
## Background
In passive flutter control, structural stiffness and frequency saperation are used to delay flutter onset. Active flutter suppression instead uses control surfaces such as ailerons to generate corrective aerodynamic forces that oppose growing oscillations. This allows aircraft to operate safely at higher airspeeds than passive design alone would permit.
## System Description
A control surface delflection &delta; generates additional aerodynamic lift and moment:<br>
L_control= &pi;&rho;Vb.&delta; <br>
M_control= -&pi;&rho; $b^2$ V.&delta;/2<br>
The controller measures wing states and computes &delta; to drive oscillations to zero.<br>
PID Controller: It corrects based on pitch angle &theta; and pitch rate &theta;. Gains turned empirically: Kp= 500, Ki= 5, Kd= 10.<br>
LQR Controller: It uses full state feedback from all four states(h,&theta;,h,&theta). Gains are computed by minimising a quadratic cost function balancing state error against control effort. Q= diag(1000,1000,10,10),R=0.1
## Results
Uncontrolled system diverges at approximately t=10 seconds and v= 10 m/s, more than double the passive flutter speed of 4.4 m/s.
PID controller maintains stable response for full 40 second simulation at V= 10 m/s, more than double the passive flutter speed.
LQR controller achieves equivalent supression with mathematically optimal gain selection, demonstrating the advantage of model based control over empirical tuning.
## Tools
MATLAB, Simulink,PID control, LQR optimal control, state-space formulation.
