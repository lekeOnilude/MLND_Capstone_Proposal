# Capstone Project Proposal

Gbemileke Onilude

March 18th, 2018

## Proposal

Robots Navigation and Recognition of Environment

## Domain Background

Robots are the future, their futuristic applications are limitless from autonomous vehicles to space exploration. Even though their history can be traced back to the ancient world, we have not yet scratched the surface when it comes to their potential. For years engineers have always faced a problem when it comes to helping a robot navigate its environment. Robot navigation means the robot’s ability to determine its own position in its frame of reference and then to plan a path toward some goal location [(Wikipedia)](https://en.wikipedia.org/wiki/Robot_navigation)

Vision-based navigation is on the top front of research and implementation when it comes to robotic navigation but there are some instances where its implementation can be limited. That is where an inertial measurement unit comes into play, though they are been around for a while, their usefulness cannot be ignored. An inertial measurement unit (IMU) is an electronic device that measures and reports a body's specific force, angular rate, and sometimes the magnetic field surrounding the body, using a combination of accelerometers and gyroscopes, sometimes also magnetometers. IMUs are typically used to manoeuvre aircraft, including unmanned aerial vehicles (UAVs), among many others, and spacecraft, including satellites and landers. Recent developments allow for the production of IMU-enabled GPS devices. An IMU allows a GPS receiver to work when GPS-signals are unavailable, such as in tunnels, inside buildings, or when electronic interference is present.

## Problem Statement

A blind man wearing a shoe can still tell if the floor he is working on is slippery, sandy or concrete based on his speed and orientation, but for a robot this is one major source of problem, if a robot cannot identify the nature of the ground in which it navigated, it might have problems when it comes to the necessary speed and forces need to move through its environment. It might use so much force where little is require and little where much is needed. While some robots are require to change the shape of their tyres just to be able to navigate this terrain effectively, but without knowledge of their terrain, this could be a major problem.

## Datasets and Input.

The dataset was gotten from an IMU sensor attached to the robot, the robot was then driven around different surface terrain (nine-floor types). The input data collected, covering 10 sensor channels and 128 measurements per times series. The 10 sensor channels are: orientation_X, orientation_Y, orientation_Z, orientation_W, angular_velocity_X, angular_velocity_Y, angular_velocity_Z, linear_acceleration_X, linear_acceleration_Y, linear_acceleration_Z. it also has

-	row_id: The ID for this row.
-	series_id: ID number for the measurement series. Foreign key to y_train/sample_submission.
-	measurement_number: Measurement number within the series.

The 10 sensor channel would be used to track the velocity and the acceleration of the robot has it moves through this different terrain and the dataset id gotten from [Kaggle](https://www.kaggle.com/c/career-con-2019/data)

## Solution Statement

Using a classification algorithm, I should be able to classify the kind of terrain the robot is moving on base on the velocity and the orientation of the robot over a 128 measurement per time series.

## Benchmark Model

The benchmark used was gotten from this Kaggle [user](https://www.kaggle.com/theoviel/deep-learning-starter) who has an accuracy of 0.6381 in the testing dataset. He makes use of a Recurrent Neural Network. Firstly he divided the state set into train and testing, drop the 'row_id' "series_id" and "measurement_number" column, encode the output values and created an input neural network of shape (128, 10), two hidden layers and an output layer of size nine. The optimizer used was ‘adam’

## Evaluation Metrics

The accuracy in which the model identifies the terrain is the most import factor in other to determine if the classification algorithm is effective for this particular problem or if some hyperparameter tuning will be required. The predicted output is compared to the test targeted output and then the accuracy of the algorithm is display

## Project Design

The project design would be design into two stages:

1.	Pre-processing
2.	Modelling

In the pre-processing stage, the data could be check for any missing value, depending on the situation, the rows would be drop or the values replaced by the closest row value to it. Also, normalisation would also be performed on the dataset so has to scale it and avoid some column having more effect on the prediction.

The algorithm to be used is LSTM (Long short-term memory), it would have an input shape of (128, 10) and an output shape of (9) for the nice different fool types. The other hyper-parameter would be tuned as the project progresses
