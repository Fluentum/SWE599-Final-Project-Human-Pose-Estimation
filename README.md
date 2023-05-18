![image](https://github.com/Fluentum/SWE599-Final-Project-Human-Pose-Estimation/assets/115422651/646cf384-0b8f-41de-802d-33b5d94b4d57)

## SWE 599 - Human Pose Estimation

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

## How to install

1. Install Python
Recommended Python versions are 3.7 to 3.10 - 64 bit version.

For direct download, please use this link:
https://www.python.org/downloads/

2. Install Git

For direct download, please use this link:
https://git-scm.com/downloads

3. Install C++ Redistributable (For Python 3.8, not required for Python 3.7)

For direct download, please use this link:
https://aka.ms/vs/17/release/vc_redist.x64.exe

4. Install the Notebooks

After installing Python 3 and Git, run each step below using Command Prompt (cmd.exe), not PowerShell. Note: If OpenVINO is installed globally, please do not run any of these commands in a terminal where setupvars.bat is sourced.

5. Create a Virtual Environment (if you have not installed openvino-dev)

python -m venv <write_your_venv_name_to_here>

6. Activate the Environment

<write_your_venv_name_to_here>\Scripts\activate

7. Clone the Repository
Note: Using the --depth=1 option for git clone reduces download size.

git clone --depth=1 https://github.com/Fluentum/SWE599-Final-Project-Human-Pose-Estimation.git
cd openvino_notebooks

8. Install the Packages
9.
This step installs OpenVINO and dependencies like Jupyter Lab. First, upgrade pip to the latest version. Then, install the required dependencies.

python -m pip install --upgrade pip wheel setuptools
pip install -r requirements.txt

9. Launch the Notebook!

jupyter notebook Human-Pose-Estimation-for-SWE599.ipynb
