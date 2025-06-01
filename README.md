# AUV_ROS
 source /usr/share/gazebo/setup.sh <br>
source /opt/ros/humble/setup.bash<br>
cd Desktop/<br>
cd test/<br>
source install/setup.bash<br>
ros2 launch uuv_gazebo_worlds ocean_waves.launch(for launching world) <br>
ros2 launch uuv_descriptions upload_rexrov_default.launch.py mode:=default x:=0 y:=0 z:=-20 namespace:=rexrov gazebo_namespace:="''" (for launching bot) <br>
ros2 launch uuv_control_cascaded_pid joy_velocity.launch uuv_name:=rexrov model_name:=rexrov (for starting acceleration_control and thruster_manager) <br>
ros2 run uuv_teleop vehicle_keyboard_teleop.py --ros-args -r output:=/rexrov/cmd_vel (for publishing cmd_vel) <br>
python3 src/odom.py (to publish odom) <br>
 ros2 launch uuv_control_cascaded_pid vel.launch uuv_name:=rexrov model_name:=rexrov (velocity_control.py) <br>
