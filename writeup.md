# **PID Controller** 

## Writeup by Ernesto Cañibano

### This is the writeup associated with the fourth project of the Term 2, of the Self-driving Car Nanodegree


---

### Reflection

### 1. Describe the effect of the P, I, D component of the PID algorithm in the implementation.


* **Proportional component Kp.**

  Proportional controller only receives as input the current cross-track error (CTE). 
  The ouput of the controller is the steering angle of the car to try to correcto the CTE. 
  In this way the controller tries to keep the car in a reference trajectory.
  
  In the following videos, it can be observed the effect of the proportional term in the trajectory of the car.
  In both of them the components derivative and integral has been canceled (**Kd = 0**, **Ki = 0**).
  *  [**Kp = 1.0**](videos/kp=1.0_ki=0.0_kd=0.0.mp4) With a big value of the proportional the car responses very fast
  to try to correct the CTE, but the overshooting produces a big oscillation effect even before to reach the first turn. 
  *  [**kp = 0.01**](videos/kp=0.01_ki=0.0_kd=0.0.mp4) If proportional component is too small, the car doesn't oscillate
  too much on the straight part of the track, but it is unable to keep the car on the track as soon the first turn arrives.
 
  The main problem of the proportional controller is the overshooting which generates an oscillation in the trajectory
  of the vehicle. It is not possible to keep the car on track only with the proportional component.

* **Derivative component Kd.**  

  Derivative controller receives as inputs the current value of the CTE and the value of the CTE in a previous time
  interval. This means that the output of the controller is proporitonal to the rate of change of the CTE. If the CTE
  remains constat the derivative componente won't have any effect in the vehicle trajectory.
  
  In this [**video**](videos/kp=0.0_ki=0.0_kd=5.0.mp4) the proportional and integral components have been cancelled
  and the derivative term setted to 5.0. It can be observed how the car barely reacts to the CTE error on the straigh
  part of the track and gradually aproaches to edge of the track. This is effect is due at the low rate of change of the CTE.
  
  The derivative controller cannot be used alone, it has to be used in conjuction with the proportional controller
  to reduce the oscillation of this one.
  
  In this [**video**](videos/kp=0.15_ki=0.0_kd=2.75.mp4) the integral component has been cancelled and proportional 
  and derivative setted to 0.15 and 2.75.


* **Integral component Ki.**

  Integral controller receives as input the sum of all previous CTE values. Its function is correct systematic bias 
  errors. 
  
  This is the [**result**](videos/kp=0.15_ki=0.001_kd=2.75.mp4) of adding the integral component to the previous
  PD controller. The value of the the integral component is lower than proportional and derivative components because
  acts over an acumulative error. The effect of setting a big integral value is that the car tends to go straight in
  the turns.
   

### 2. Describe how hyperparameters have been choosen

  I decided to tune the hyperparameters manually because I tried to adjust them automatically but every time the car
left the track I had to restart the simulator.

  
  
  



