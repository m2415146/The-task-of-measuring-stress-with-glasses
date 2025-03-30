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

now we are creating another smaller rectangle to simulate the lenses. we compare both rectangles

https://github.com/user-attachments/assets/5b38e8a9-af89-45bc-a1f5-b6ebb71bb165

We also model a rectangle for the bridge of the nose.

![Screenshot_217](https://github.com/user-attachments/assets/7689ee48-5d4f-444d-860b-862885a2fc95)

using the Geometry/fill commands, we select the points where the edges are rounded.

![Screenshot_218](https://github.com/user-attachments/assets/a670472d-5f15-4a07-9db0-a51f2ee54c97)

combine the shapes using the Geometry/union commands, then remove the intersection in the bridge of the nose using Geometry/delete entities

![Screenshot_220](https://github.com/user-attachments/assets/b3cbd887-8234-4f5e-ae61-8d6f93287703)

then, also using the fill command, round off the edge of the bridge of the nose.

![Screenshot_221](https://github.com/user-attachments/assets/d5a15977-b18e-42d1-a8f0-97e4b9479c8d)

using the Geometry/copy and Geometry/mirror commands, we mirror our model to get the shape of the rim. I selected the X-axis offset coordinates for the mirrored part manually so as not to have to compare them.

![Screenshot_222](https://github.com/user-attachments/assets/2ed5abaf-b7e0-4be0-b258-ec4d1d74063f)

add 2 dots to indicate the arches.

![Screenshot_223](https://github.com/user-attachments/assets/c41861a7-d1a4-4581-96a6-a9f697dcc991)

using the Geometry/union commands, we will combine the 2 parts of our model into 1

![Screenshot_224](https://github.com/user-attachments/assets/3d56e500-7c3a-47a0-afe9-7d59fa9e51a4)

now, using add material, we will add the material for the frame.

![Screenshot_225](https://github.com/user-attachments/assets/9260b90d-4a51-45a2-9faf-85ff09566598)

let's choose the parts for which we will use the monel alloy 400 material.

![Screenshot_226](https://github.com/user-attachments/assets/b6c124c6-0ab2-4778-a0a6-fbd0d8b3c1bb)

When trying to add the lens material specified in task - Cr-39, the application library provides only optical properties. we are not satisfied with this, because we need physical parameters - Young's modulus, density and Poisson's ratio. since there is no such data in the library, we will add the properties manually.

![Screenshot_227](https://github.com/user-attachments/assets/f8c356ae-e323-4c05-add1-3cfca6787507)

to find out the numbers needed to complete the task, I used the DeepSeek neural network.

![Screenshot_229](https://github.com/user-attachments/assets/2b323df4-a4b3-4223-aa93-b86e3e731791)

adding parameters to the material/blank material (pre-selecting the lenses)

![Screenshot_228](https://github.com/user-attachments/assets/7dd60bfa-59a0-44a2-aaeb-92c22a762fb5)

in the Solid Mechanics field, select the thickness of the frame and lenses. let the thickness of the frame be equal to the thickness of the lenses. for some reason, the program outputs units of measurement in meters here, although we previously set centimeters.

![Screenshot_230](https://github.com/user-attachments/assets/67c6d7a1-2a49-4d27-9598-0d74bdd98986)

we select the fixed part - the right arm of the glasses through Solid Mechanics/fixed constraint

![Screenshot_231](https://github.com/user-attachments/assets/9149604c-5ebc-4b9f-af46-202829bc30fe)

now we select the load: Solid mechanics/boundary load, set the load value along the Y axis (since it is applied vertically) and change the force parameters to total force, since we want to find out the pressure not specifically on this area, but on the entire model.

![Screenshot_232](https://github.com/user-attachments/assets/a328d114-57f0-4df8-8a80-085a8c43935c)

in the Mesh field, select free triangles, as input parameters - entire geometry (since we want to measure the entire model) and quality - extremely fine/ build

![Screenshot_233](https://github.com/user-attachments/assets/cfdac8c8-61a9-4be2-89e2-cde2ada311d6)

in the Study/stationary field, select Computer selected for the study product

![Screenshot_234](https://github.com/user-attachments/assets/c2fb99f9-576e-4812-b00d-8b09c20456c6)

despite the obvious success of the computer simulation, I was confused by the overly pronounced deformation of the rim. in real life, with a load of 3 Newtons, we are unlikely to notice this on real glasses. Let's try to make changes so that the simulation result looks close to life.

in the STress/solid/deformations field, we estimate the scale factor, which acts as a multiplier for our load. it turns out to be huge

![Screenshot_235](https://github.com/user-attachments/assets/d91777c2-cc98-4a1b-a907-7740f74cf1e1)

let's change it to a value of 1/press plot

![Screenshot_236](https://github.com/user-attachments/assets/3c32b23a-b625-4039-ba15-b8c97aa99c24)

now we don't see such an incredible deformation - most likely it would be the same in life, while we clearly see in the image the places where stress is distributed.

























































