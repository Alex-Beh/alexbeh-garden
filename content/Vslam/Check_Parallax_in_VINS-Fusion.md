- Explaination about function [compensatedParallax2()](https://github.com/HKUST-Aerial-Robotics/VINS-Fusion/blob/be55a937a57436548ddfb1bd324bc1e9a9e828e0/vins_estimator/src/estimator/feature_manager.cpp#L530) in VINS-Fusion
- To check whether frame $i$ is keyframe by checking whether the parallax between frame $i-1$ and frame $i-2$ is larger than certain threshold
- And it is keyframe, then marginalization_flag is MARGIN_OLD. Else MARGIN_SECOND_NEW
	为了维持窗口大小，需要去除旧的帧添加新的帧，也就是边缘化 Marginalization。到底是删去最旧的帧（MARGIN_OLD）还是删去刚刚进来窗口倒数第二帧(MARGIN_SECOND_NEW)，就需要对当前帧与之前帧进行视差比较，如果是当前帧变化很小，就会删去倒数第二帧，如果变化很大，就删去最旧的帧。


## Code
Second Last Frame & Last Frame
```c++
const FeaturePerFrame &frame_i = it_per_id.feature_per_frame[frame_count - 2 - it_per_id.start_frame];// 倒数第三帧
const FeaturePerFrame &frame_j = it_per_id.feature_per_frame[frame_count - 1 - it_per_id.start_frame];// 倒数第二帧
```
Feature point
```c++
//因为特征点都是归一化之后的点，所以深度都为1，这里没有去除深度，下边去除深度，效果一样。
Vector3d p_j = frame_j.point;  double u_j = p_j(0);  double v_j = p_j(1);

Vector3d p_i = frame_i.point; 
double dep_i = p_i(2);
double u_i = p_i(0) / dep_i;
double v_i = p_i(1) / dep_i;
```

Calculate Parallax

```
double parallax = u_i - u_j, dv = v_i - v_j;
```



