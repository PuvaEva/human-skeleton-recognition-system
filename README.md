# human-skeleton-recognition-system

Depth sensor is used to recognize human skeleton in this research. In 2011-2012, a group of mechanical engineering students from the University of Leeds developed a toolkit for LabVIEW named Kinesthesia to allow access to RGB video, depth camera and Skeletal tracking functions of Microsoft Kinect, which was initially developed for medical rehabilitation and surgical tools [59].This Kinesthesia toolkits provides is the “Distance and Displacement between Joints” VI which obtain 20 joint coordinates of the skeleton starting from head until feet as shown in Figure 3.5.

<img width="233" alt="1" src="https://user-images.githubusercontent.com/41656537/81128525-0751c880-8f74-11ea-8d50-a15412c94e8e.PNG"> <img width="280" alt="1b" src="https://user-images.githubusercontent.com/41656537/81128526-091b8c00-8f74-11ea-9913-c5ad55d3079e.PNG">

When the Microsoft Kinect starts operating, the subject to be recognized must stand at a minimum distance of 1.5 meters from the Kinect while holding his or her arms next to waist, because as the arms rise, the shoulder joints and the spine extend in Microsoft Kinect’s perspective thus giving inaccurate data. The subject must stand still for 10 seconds. During this time, 20 joint’s coordinates are obtained.  Figure 3.6 shows the 20 joints and the connections. 

<img width="289" alt="2" src="https://user-images.githubusercontent.com/41656537/81128529-09b42280-8f74-11ea-8e29-d54ec7d1bd81.PNG">
Two adjacent Joints are selected to obtain the X, Y and Z coordinates of each Joint. The extracted sub arrays of Joints 1 and Joint 2 are subtracted from each other, squared, summed and finally the square root is taken as the Euclidean distance algorithm (refer Equation 3.1) implemented. 
<img width="319" alt="3" src="https://user-images.githubusercontent.com/41656537/81128532-0a4cb900-8f74-11ea-938e-3f001584320f.PNG">

By applying this algorithm, it was possible to obtain 19 absolute distances between the 20 joints of each skeleton measurements. These 19 Euclidean distances are the bone distance of the human which are the skeleton information will be used to match the subject’s skeleton information in the real time. The names of the 20, connections of each bone joints and the 19 bones are shown in the Figure 3.7 clearly.

<img width="232" alt="4" src="https://user-images.githubusercontent.com/41656537/81128537-0ae54f80-8f74-11ea-8352-ed037e8b0aa7.PNG">

To increase the system accuracy, the 20 joints and 19 bones measured and calculated for 250 times. The data then are written in a spreadsheet file. After Euclidean (bone) distances calculated, mean for each of 19 bone distances calculated using equations 3.2.


<img width="200" alt="5" src="https://user-images.githubusercontent.com/41656537/81128539-0b7de600-8f74-11ea-97c8-82db21fb0b21.PNG">
The sample skeleton information and the 19 mean Euclidean distances (bone distance) are shown in Table 3.1.

<img width="207" alt="6" src="https://user-images.githubusercontent.com/41656537/81128540-0c167c80-8f74-11ea-98d0-ff1ef0c23290.PNG">


 The data saved as the subject will be registered as user. During the recognition, the 19 mean distance data stored in the file (.csv). As the last step of skeleton identification algorithm, the 19 mean distance will be added and subtracted 0.5 cm in order to create the range value. This range value is created as the real time data always changing as the subject makes small movements. So, this range value will be compared with the 19 real time Euclidean distance of subject to be recognized. The 19 outputs are either logic 1 or logic 0. If the measurement is more the range value, then the logic will be counted as 0. Finally, all of these are summed using “Compound Arithmetic” function and choosing the “Add” option. If the score is equal to or more then 15, then the subject is recognized as the registered user. Figure 3.8 and Appendix B shows the developed skeleton recognition system front panel and block diagram respectively.


<img width="208" alt="7" src="https://user-images.githubusercontent.com/41656537/81128541-0c167c80-8f74-11ea-9449-aa9b36d16a4b.PNG">
