# Sensehub Stack
This repository contains all of the non-standard ros packages needed to run the SWAMP sensor pipeline. To clone with the necessary sub-modules, use:

```bash
git clone --recurse-submodules https://github.com/Herschenglime/sensehub_stack # or use ssh clone if needed
```

To compile everything after cloning, run the following (with ROS2 headers sourced):
```bash
colcon build --symlink-install
```

## Point-LIO Bag Processing Launch

Use `sensehub_bringup`'s `point_lio_bag_processing.launch.py` to:
- launch Point-LIO with `use_sim_time:=true`
- publish identity transform `unilidar_lidar -> body`
- record a new output bag with sim time
- play an input bag with `--clock`
- shut down about 1 second after playback completes

### Arguments
- `input_bag` (required): input bag path, absolute or relative to `<workspace>/bags`
- `output_bag_name` (optional, default: `point_lio_processed`): output bag directory name in `<workspace>/bags`
- `overwrite_output_bag` (optional, default: `false`): if `true`, removes existing output bag path first

### Recorded topics
- `/image_raw`
- `/camera_info`
- `/cloud_registered_body`
- `/tf`
- `/tf_static`

### Example usage
From the workspace root (`sensor_pipeline_ws`):

```bash
ros2 launch sensehub_bringup point_lio_bag_processing.launch.py \
	input_bag:=ippd_lab_2 \
	output_bag_name:=ippd_lab_2_point_lio \
	overwrite_output_bag:=true
```

Or with an absolute input bag path:

```bash
ros2 launch sensehub_bringup point_lio_bag_processing.launch.py \
	input_bag:=/home/team/workspaces/isaac_ros-dev/sensor_pipeline_ws/bags/ippd_lab_2
```
