If you have boost installed on your system, CMake is probably looking for it in the wrong place. This may help you:
```
colcon build --symlink-install --cmake-args -DBoost_LIBRARY_DIR_RELEASE=/usr/lib/aarch64-linux-gnu/
```

1. [colcon build error for [point_cloud_perception] packages #4](https://github.com/noshluk2/ros2_learners/issues/4#issuecomment-1426409841)
2. [[compile error] find_package(PCL) finds some but not all boost libraries #5052](https://github.com/PointCloudLibrary/pcl/issues/5052#issuecomment-984042504)
