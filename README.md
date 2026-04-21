# Sensehub Stack
This repository contains all of the non-standard ros packages needed to run the SWAMP sensor pipeline. To clone with the necessary sub-modules, use:

```bash
git clone --recurse-submodules https://github.com/Herschenglime/sensehub_stack # or use ssh clone if needed
```

To compile everything after cloning, run the following (with ROS2 headers sourced):
```bash
colcon build --symlink-install
```
