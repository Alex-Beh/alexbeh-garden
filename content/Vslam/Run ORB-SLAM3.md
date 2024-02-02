Supported camera model
- PinHole
- KannalaBrandt8
- [ORB-SLAM3源码阅读笔记4：ORB-SLAM3中的相机模型与特征提取、匹配](https://zhaoxuhui.top/blog/2021/08/01/orb-slam3-note-4-camera-model-and-feature-extraction.html)

Parameter

- Camera.bf: 双目相机baseline和相机焦距的乘积，即bf=b*f。单位为mm。必须为float类型
- ThDepth: 相机的有效深度，必须是float类型
- Tbc: Transformation from camera 0 to body-frame (imu)
- Stereo Rectification: Only if you need to pre-rectify the images.
	- LEFT.height
	- LEFT.width
	- LEFT.D
	- LEFT.K
	- LEFT.R
	- LEFT.Rf
	- LEFT.P



https://zhaoxuhui.top/blog/2023/11/16/stereo-inertial-configuration-and-stereo-rectification-in-orb-slam3.html

