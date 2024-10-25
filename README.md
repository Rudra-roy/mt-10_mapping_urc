# Urc_mapping_sim_mt10
Step:1
Install slam_toolbox
 
sudo apt install ros-humble-slam-toolbox


Step:2 
add the husky_simulation folder into a ros2 workspace src directory

Step:3
colcon build --symlink-install 
build the packages and source the install/setup.bash 

Step:4 
Download the mesh file of urc ground from this link, 
https://drive.google.com/file/d/1BZCTas0r-5BLlgOfmsuB1dWyIGfvT2ze/view?usp=drivesdk

go to the .gazebo folder inside the home. Create a models folder, inside that create a meshes folder and place the downloaded .dae file in that folder


Now, run 

ros2 launch husky_simulator husky_gazebo_launch.py 

This will launch the husky on URC ground. The orientation is reversed, so use the gazebo's rotate tool to rotate the husky model in the correct orientation. 

Now, run
ros2 run teleop_twist_keyboard teleop_twist_keyboard

and drive the model into an approximate level place. 

Step:6 
run, 
ros2 launch slam_toolbox online_async_launch.py slam_params_file:=~/ros2_ws/src/husky_simulation/mapper_params_online_async.yaml use_sime_time:=true


Now, change the fixed frame in Rviz to a map and start driving the model from the keyboard or teleop_joy package. 
