# CarND-Controls-PID
---
Adam Shan's solution to the PID program.

## Describe the effect each of the P, I, D components had in your implementation.
The P (proportional) is the steer proportional to the CTE (the distance to the basic line). It controls the the intensity of turning. If the P is large, the controller will tends to turning large according to the CTE.

The D (differential), the P-Controller tends to run overshoot again and again. This makes the car runs like a snake. 
With the D term, the car will be always close to the reference trajectory without high oscillation

The I (integral), this term help to offset the influence from the systematic bias.



## Describe how the final hyperparameters were chosen.

First, I choose the P, I, D parameters manually, to make the car can drive on the road at least.
Then, using the Twiddle algorithm to search the best parameters(P, I, D).

The initial (P,I,D) I used is **(0.5, 0.001, 1.5)**, which total_error is about **2686.48** for the next 2000 steps.
I initialize the change rate with 0.1*init_parameter.
The algorithm here is a little different from that in the python PID program
since the car can't put to the the start point again and again. After 71400 steps, the total_error reduce to and the final hyperparameters are
 **P: 0.3345 I: 0.0011011 D: 2.662**
 
I think the total_error will reduce if continue running the TWIDDLE. But it will consume lots of time and this implementation meets the requirements already. 
So I end the TWIDDLE algorithm at step 71400.

File [twiddle_log.txt](twiddle_log.txt) is the detail log of the TWIDDLE algorithm in my implementation. change index 0, 1, 2 denote the change of P, I, D respectively.


 

