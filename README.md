# 📚 Reference 

This repo contains the matlab live script files (`.mlx`) that have been introduced in the following conference paper - 
```
@inproceedings{lai2019learning,
  title={A learning-based inverse kinematics solver for a multi-segment continuum robot in robot-independent mapping},
  author={Lai, Jiewen and Huang, Kaicheng and Chu, Henry K},
  booktitle={Proc. IEEE Int. Conf. Robot. Biomim.},
  pages={576--582},
  year={2019},
}
```
The interactive live script helps one to understand better how the code works. It is only for verficaition/proof-of-concept.


## ✔️ What's it about?

- This repo presents a simplified model to represent a multi-segment continuum robot using virtual rigid links. Based on the model, its IK can be solved using a multilayer perceptron (MLP), a class of feedforward neural network (FNN). 
- The transformation between virtual joint space to task space is described using Denavit-Hartenberg (D-H) convention. 
- Using 20,000 established training data for supervised learning, the MLP reaches a mean squared error of 0.022 for a dual-segment continuum robot. 
- The trained MLP is then used to find the joints for different end-effector positions, and the results show a mean relative error of 2.90% can be on the robot configuration. 
- This simplified model and its MLP provide a simple method to evaluate the IK solution of a two-segment continuum robot, which can be further generalized and implemented in multi-segment cases. 

## 👨‍💻 Try it yourself!

`trainNetwork_DH.mlx`: 
- Compute the transformation matrix of a two-segment continuum robot based on the DH prameters (a virtual pseudo-rigid link model)
- Clear
- Based on the DH model, compute ans save the IO relationship between the configuration ($R^4$) and tip cartesian ($R^6$).
- Train MLP, save the network locally as `ik_net.mat`
- Test an show error

`testPerformance.mlx`:
- load `ik_net.mat`
- Use forward kinematics to compute a desired path
- Put the desired path as an input to the trained network -> get inverse output
- Use the inverse as new input, and test it forwardly
- Evaluate the error - you will see something like this (for example)


 ![img](/figHeart.png)


