# The-task-of-measuring-stress-with-glasses
this is a training task for COMSOL multiphysics

## Task

It is required to simulate glasses with frames in the COMSOL program, fix one arm, apply a load to the other and measure the stress level in the bridge of the nose. To illustrate, the teacher proposed a scheme.

![Screenshot_212](https://github.com/user-attachments/assets/45520ebb-104e-4f84-a5db-82942724552c)

frame material - Monel alloy 400

lens material - Cr-39

loading lever - 3N

The drawing must be executed in the COmsol program.

## Creating a model

Using a "Model Wizard" we are creating a 2D model. The option with an axymmetric model will not suit us, since the shape does not look like a simple cube or cylinder and we cannot simply extrapolate all the measurements to the volume of the model along one axis.

![Screenshot_213](https://github.com/user-attachments/assets/8a7c6268-9589-4002-88df-9e14a1f5d646)

we select as the physical model SOlid Mechanics, since we are dealing with a solid body. in the general Studies field, select Stationary, since we were not given the duration of the load in the task conditions.

since the physical dimensions of the lens frame are not specified in the task conditions, we will use the following dimensions

![Screenshot_214](https://github.com/user-attachments/assets/b2b9fc90-7b8b-4c45-8cda-a1e3dc9022d7)

In the Sketch field, we select a rectangle to create a model. We pre-change the units of measurement from meters to centimeters

![Screenshot_215](https://github.com/user-attachments/assets/14d2a768-7ce6-428b-902a-6ba19fb6a455)

resize the rectangle by 6.5*5 cm and click build selected

![Screenshot_216](https://github.com/user-attachments/assets/9fa0095f-4d42-4cb8-a9ed-ab1adbcc8a5b)




