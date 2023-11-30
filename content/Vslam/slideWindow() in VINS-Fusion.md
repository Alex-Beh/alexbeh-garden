After [[Check_Parallax_in_VINS-Fusion|check parallax]], we have decided whether to remove the last keyframe or second new keyframe.
## Case 1: marginalization_flag == MARGIN_OLD
#### Step 1: 0,1,2...WINDOW_SIZE——>1,2...WINDOW_SIZE,0
```c++
for (int i = 0; i < WINDOW_SIZE; i++)
{
	Headers[i] = Headers[i + 1];
	Rs[i].swap(Rs[i + 1]);
	Ps[i].swap(Ps[i + 1]);
}
```
#### Step 2: 0,1,2...WINDOW_SIZE>1,2...WINDOW_SIZE,WINDOW_SIZE
```C++
Headers[WINDOW_SIZE] = Headers[WINDOW_SIZE - 1];
Ps[WINDOW_SIZE] = Ps[WINDOW_SIZE - 1];
Rs[WINDOW_SIZE] = Rs[WINDOW_SIZE - 1];
```
#### Remove the very old frame from all_image_frame

#### slideWindowOld()
- f_manager.removeBackShiftDepth()
- f_manager.removeBack()
## Case 2: marginalization_flag == MARGIN_SECOND_NEW
