# Load-Shedding-Traffic-Light-Negotiation

This project involved adapting the existing MATLAB Traffic Light Negotiation with Unreal Engine Visualization model to suit South African conditions, particularly accounting for Load Shedding events. In South Africa, during periods of no electricity, traffic lights function as four-way stops. For simplicity in this project, the traffic lights were simulated as stop signs.

The primary challenge faced was replicating the Load Shedding scenario within Unreal Engine. This setup deactivated all traffic lights, rendering them without any color indication. To address this, the vehicle's programming focused on identifying the stop line and halting at the required distance. Detection of the stop line was achieved using image processing techniques. Initially, the image was cropped to display only the bottom half, minimizing errors in subsequent processes like Hough Transform for identifying horizontal lines. The cropped image underwent conversion to grayscale, noise reduction via a Gaussian filter, and subsequent edge detection. The Hough Transform was then applied to the edge-detected image, filtering lines based on angle and distance criteria.

Perception-based detection utilized a YOLOv2 detector specially trained to recognize all four traffic light states: Green, Yellow, Red, and Load Shedding (No State). Upon identifying the traffic light state, the appropriate logic was implemented to guide the vehicle in either halting at the intersection or proceeding through it. This involved leveraging the detected states to determine the vehicle's response accurately.


In summary, the project successfully identifies the load shedding traffic light state and detects the intersection's stop line. When encountering load shedding conditions, the vehicle stops at the intersection and treats it as a stop street, proceeding cautiously. Additionally, the scenario can be switched to normal conditions, allowing the vehicle to dynamically decide whether to stop or continue over the intersection based on the detected traffic light states, replicating real-world driving behavior. 


How to run: 

All files needed to run the project can be found on this One drive link. Download the two files. 
1. Open the TLNUnreal folder, click the TLNUnreal folder, Testbench, and then open the simulink model TrafficLightDecisionLogic.slx.
2. Once the Simulink model opens you need to change the file location of the YOLOv2 detector and the Unreal engine scene. This is done by opening the sensors environment sun model, double click on the Simulation 3D Scene configuration block and change the file path to where you save the AutoVrtlEnv.uproject in the AutoVert folder. This is the Unreal Engine scene which displays the load shedding conditions. If you want to test normal conditions change this block to US City Block.
3. Change the detector location to where you saved the detectorYOLO2.mat. It should be in TLNUnreal, No state.
