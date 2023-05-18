SWE 599 - Human Pose Estimation
This notebook shows the results of SWE 599 - Human Pose Estimation projects final output. Aim was to analyze the pose of an office worker. Notebook outputs 3 values.

Head left/right: Measures if your head is obligue towards your left or right arm.

Shoulder straight: Measures if both your shoulders are parallel to ground.

Head up/down: Measures if your head is tilted towards your front or back.

Those 3 values are displayed either in green or red color. This is like a traffic light. Red means, bad posture whereas green means correct posture.

This study is based on human-pose-estimation-0001 model from (https://github.com/openvinotoolkit/open_model_zoo/tree/master/models/intel/human-pose-estimation-0001) and related OpenVino demo project.

System benefits from OpenVino software, which helps to optimize the performance of various Intel based hardwares while working for calculation of deep learning models. More information can be found on: (https://www.intel.com/content/www/us/en/developer/tools/openvino-toolkit/overview.html).

There are 4 key values.

System accepts an angle upto 5 degrees as a sign of straightness for the shoulders and head left/right.

Head up/down is a little bit more complex. Hence this requires to make an estimation of 3rd dimension from a 2 dimension value. Here is, how it works. System calculates the distance between two eyes and also finds the two eyes' midpoint's coordinates. Than it is calculating the distance from this mid-point to tip of the nose. It is assumed that, if your head is up, and you are facing forward with an almost straight neck, those two values lengths are proportionally observed by web-cam. Almost always user's eyes are observed, if user is facing his/her laptop in the office. On the other hand, if user is not facing forward, but either down or up, due to 2D nature of the system, the distance from tip of the nose to eyes' midpoint becomes smaller or totally lost.

For a smaller bracket use a smaller value, 0 means exact equality.

head_left_right_angle_max = 5 left_shoulder_right_shoulder_angle_max = 5

For a smaller bracket, make those two values closer to each other.

nose_to_eye_min = 0.30 nose_to_eye_max = 0.40 -> Those two values are calibrated according to the laptop, in which the project is developed. Upcoming users, may need to re-calibrate those two values. But then, users will have the chance of getting a 3D feedback from a 2D system.
