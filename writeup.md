# **PID Controller** 

## Writeup by Ernesto Cañibano

### This is the writeup associated with the fourth project of the Term 2, of the Self-driving Car Nanodegree


---

### Reflection

### 1. Describe the effect of the P, I, D component of the PID algorithm in the implementation.


* **Proportional component Kp.**

  Proportional controller only receive as input the current cross-track error (CTE). 
  The ouput of the controller is the steering angle of the car to try to correcto the CTE. 
  In this way the controller tries to keep the car in a reference trajectory.
  
  In the following videos, it can be observed the effect of the proportional term in the trajectory of the car.
  In both of them the components derivative and integral has been canceled (**Kd = 0**, **Ki = 0**).
  *  [**Kp = 1.0**](videos/kp=1.0_ki=0.0_kd=0.0.mp4) With a big value of the proportional the car responses very fast
  to try to correct the CTE, but the overshooting produces a big oscillation effect even before to reach the first turn. 
  *  [**kp = 0.01**](videos/kp=0.001_ki=0.0_kd=0.0.mp4) If proportional component is too small, the car doesn't oscillate
  too much on the straight part of the track, but it is unable to keep the car on the track as soon the first turn arrives.
 
  The main problem of the proportional controller is the overshooting which generates an oscillation in the trajectory
  of the vehicle.

* **Derivative component Kd.**  

  First, i used the function **gaussian_blur()** with **kernel_size=3**. After several iterations i found that this value works properly. This value improve the the noise but keeps the lines sufficiently defined.

  After that, the function **canny()** with values: **low_threshold=50** and **high_threshold=200**. I obtained these values performing several iterations and observing the result.

  ![alt text][image3]

* **Integral component Ki.**

  ![alt text][image4]
  

### 2. Describe how hyperparameters have been choosen


The pipeline works fine with all test image and with two test videos.  

With the video **challenge.mp4**, it works too, but it fails when the color of the road is less dark. 

I think the pipeline can fail in some cases such as:
* Another white/yellow marks painted in the road like arrow, letters an signals.
* When the road asphalt is not dark enough.
* When the car approaches to very tight curves.


