## Nonlinear-Model-Predictive-Control-for-Obstacle-Avoidance
An NMPC implementation using casadi framwork in jupyter notebook

**Abstract**:
Obstacle avoidance is a critical component whenever autonomous systems operate in dynamic, cluttered environments. Nonlinear Model Predictive Control (NMPC) is a powerful control technique that enables real-time decision-making and trajectory planning. I propose an NMPC approach for obstacle avoidance implemented with the CasADi framework in this repository. An environment similar to the familiar world for turtlebot3 in ros2 in the presence of 9 parallel obstacles illustrated below is designed. (The reason is that I will apply the same code in ros2 as an ongoing repository.) 

![download (1)](https://github.com/PeymanMawlani1993/Nonlinear-Model-Predictive-Control-for-Obstacle-Avoidance/assets/103693616/75b4c88b-79a2-4c1a-afda-dde4c088cf6c)

As it is shown at the end of description, the norm2 (error) for the implementation is less than 0.1, which illustrates that NMPC effectively addresses the problem of static obstacle avoidance.

**model predictive control**:

Nonlinear Model Predictive Control (NMPC) is an optimized-based control strategy employed in various scientific and engineering domains. Unlike traditional linear control approaches, NMPC accommodates nonlinear system dynamics, making it well-suited for complex and highly nonlinear processes.NMPC formulation, like many other optimization problems, is defined as,

![download2](https://github.com/PeymanMawlani1993/Nonlinear-Model-Predictive-Control-for-Obstacle-Avoidance/assets/103693616/88ba4feb-c5e1-4863-9303-503197fb9a63)


f(x) is objective function over number of horizions (N), here the objective function is defined as below,  

![Screenshot from 2023-08-29 02-47-22](https://github.com/PeymanMawlani1993/Nonlinear-Model-Predictive-Control-for-Obstacle-Avoidance/assets/103693616/1d13676a-03d3-40ac-8ed6-aa771c8ae183)

h(x) are equality constraints, including the nonlinear dynamic model of the robot.

![Screenshot from 2023-08-29 02-46-56](https://github.com/PeymanMawlani1993/Nonlinear-Model-Predictive-Control-for-Obstacle-Avoidance/assets/103693616/669cda3e-4bd4-4ba1-94fa-dcf4efc7d9cf)

g(x) are inequality constraints, obstacle contraints are usually considred in this group of constraints. We assume the environment map is completely provided, and the location of obstacles is predefined. To avoid obstacles, the Euclidian distance between the centre of obstacles and the centre of the robot should be greater than the radius of the obstacle and the robot, plus a predefined safety value. the inequality equation for each obstacle is defiend in the following as, 

![Screenshot from 2023-08-29 03-03-29](https://github.com/PeymanMawlani1993/Nonlinear-Model-Predictive-Control-for-Obstacle-Avoidance/assets/103693616/e2a61ca9-2610-49e0-b2b5-b25e768d463d)

![Screenshot from 2023-08-29 03-03-47](https://github.com/PeymanMawlani1993/Nonlinear-Model-Predictive-Control-for-Obstacle-Avoidance/assets/103693616/2070d666-a656-4673-b07e-9adc68bda1ac)

In each iteration, an objective function is calculated over the horizon and fed to the CASADi solver. Also, the constraints specify the feasible value for optimal values. The whole process can be solved as a multiple-shooting problem (a good recource to learn NMPC: https://www.syscop.de/event/tempo-spring-school).

**Results**:

The CasADi framework provides a versatile and efficient platform for implementing NMPC algorithms. It offers a wide range of numerical optimization tools and supports various programming languages, making it suitable for both rapid prototyping and real-time deployment. The framework's ability to handle nonlinear constraints and differential equations enables the incorporation of complex dynamics and obstacle avoidance constraints into the optimization problem.
To demonstrate the effectiveness of the proposed approach, we conducted extensive simulations in various challenging scenarios. The results show that the NMPC controller using the CasADi framework successfully avoids obstacles while maintaining system performance and stability.

As shown in the following figures. The NMPC efficiently solve the nonlinear optimization in the presence of static obstacles.


![Screenshot from 2023-08-29 03-24-24](https://github.com/PeymanMawlani1993/Nonlinear-Model-Predictive-Control-for-Obstacle-Avoidance/assets/103693616/9622cbcf-959e-4f73-aadc-77eb540d0570) initial pose=[1,0.5,pi] target=[-1.5,-1.5,0]

![Screenshot from 2023-08-29 03-23-30](https://github.com/PeymanMawlani1993/Nonlinear-Model-Predictive-Control-for-Obstacle-Avoidance/assets/103693616/7cb219f1-9999-45c7-a808-c74080891ca6) initial pose=[1,-1.5,pi] target=[-1.5,0.5,0]

![Screenshot from 2023-08-29 03-19-39](https://github.com/PeymanMawlani1993/Nonlinear-Model-Predictive-Control-for-Obstacle-Avoidance/assets/103693616/9ab3d936-9878-42a4-8943-028dadfc0f15) initial pose=[-2,-0.5,0] target=[0.5,2,0]

## What is next?
The following repository will be the exact implementation for the gazebo simulation of the turtlebot3 burger in ros2. 









