Below are specifications for my system that needs to be integrated with crisp gym

## Leader (left) robot topics
The follower arm is under the `left` namespace, and should not have an active gripper.

/left/cartesian_impedance_controller/transition_event
/left/current_pose
/left/current_twist
/left/dynamic_joint_states
/left/franka/joint_states
/left/franka_gripper/joint_states
/left/gravity_compensation/transition_event
/left/gripper/gripper_position_controller/commands
/left/gripper/joint_states
/left/joint_impedance_controller/transition_event
/left/joint_state_broadcaster/transition_event
/left/joint_states
/left/joint_trajectory_controller/controller_state
/left/joint_trajectory_controller/joint_trajectory
/left/joint_trajectory_controller/state
/left/joint_trajectory_controller/transition_event
/left/pose_broadcaster/transition_event
/left/robot_description
/left/target_joint
/left/target_pose
/left/target_stiffness
/left/target_wrench
/left/twist_broadcaster/transition_event

## Follower (right) robot topics
The follower arm is under the `right` namespace, and is equipped with 
a franka gripper hand with a wrapper that takes continuous commands from 0 to 1
on the /right/gripper/gripper_position_controller/commands topic.

/right/cartesian_impedance_controller/transition_event
/right/current_pose
/right/current_twist
/right/dynamic_joint_states
/right/franka/joint_states
/right/franka_gripper/joint_states
/right/gravity_compensation/transition_event
/right/gripper/gripper_position_controller/commands
/right/gripper/joint_states
/right/joint_impedance_controller/transition_event
/right/joint_state_broadcaster/transition_event
/right/joint_states
/right/joint_trajectory_controller/controller_state
/right/joint_trajectory_controller/joint_trajectory
/right/joint_trajectory_controller/state
/right/joint_trajectory_controller/transition_event
/right/pose_broadcaster/transition_event
/right/robot_description
/right/target_joint
/right/target_pose
/right/target_stiffness
/right/target_wrench
/right/twist_broadcaster/transition_event

## Cameras
There are two realsense cameras running: base, and wrist.

/camera/base/color/image_raw
/camera/base/color/metadata
/camera/base/extrinsics/depth_to_color
/camera/base/color/camera_info

Example info message from the base camera:
---
header:
  stamp:
    sec: 1779148703
    nanosec: 303508057
  frame_id: base_color_optical_frame
height: 720
width: 1280
distortion_model: plumb_bob
d:
- 0.0
- 0.0
- 0.0
- 0.0
- 0.0
k:
- 909.464599609375
- 0.0
- 648.4688720703125
- 0.0
- 909.1887817382812
- 371.5376281738281
- 0.0
- 0.0
- 1.0
r:
- 1.0
- 0.0
- 0.0
- 0.0
- 1.0
- 0.0
- 0.0
- 0.0
- 1.0
p:
- 909.464599609375
- 0.0
- 648.4688720703125
- 0.0
- 0.0
- 909.1887817382812
- 371.5376281738281
- 0.0
- 0.0
- 0.0
- 1.0
- 0.0
binning_x: 0
binning_y: 0
roi:
  x_offset: 0
  y_offset: 0
  height: 0
  width: 0
  do_rectify: false
---

/camera/wrist/color/camera_info
/camera/wrist/color/image_raw
/camera/wrist/color/metadata
/camera/wrist/extrinsics/depth_to_color

Example info message from the wrist camera:
---
header:
  stamp:
    sec: 1779148784
    nanosec: 798334473
  frame_id: wrist_color_optical_frame
height: 480
width: 640
distortion_model: plumb_bob
d:
- 0.0
- 0.0
- 0.0
- 0.0
- 0.0
k:
- 604.2595825195312
- 0.0
- 320.8122253417969
- 0.0
- 604.0947875976562
- 256.8160400390625
- 0.0
- 0.0
- 1.0
r:
- 1.0
- 0.0
- 0.0
- 0.0
- 1.0
- 0.0
- 0.0
- 0.0
- 1.0
p:
- 604.2595825195312
- 0.0
- 320.8122253417969
- 0.0
- 0.0
- 604.0947875976562
- 256.8160400390625
- 0.0
- 0.0
- 0.0
- 1.0
- 0.0
binning_x: 0
binning_y: 0
roi:
  x_offset: 0
  y_offset: 0
  height: 0
  width: 0
  do_rectify: false
---

## Sensors
There are no sensors currently.