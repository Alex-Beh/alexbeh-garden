Stereo Rectification
- Reproject image planes onto a common plane parallel to the line between camera centers
- Need two homographies (3x3 transform), one for each input image reprojection
- Steps
  1. Rotate the right camera by R (aligns camera coordinate system orientation only)
  2. Rotate (rectify) the left camera so that the epipole is at infinity
  3. Rotate (rectify) the right camera so that the epipole is at infinity 
  4. Adjust the scale
![[Pasted image 20240130145230.png]]
![[Pasted image 20240130144746.png]]
![[Pasted image 20240130144828.png]]
![[Pasted image 20240130144941.png]]

![[Pasted image 20240130144057.png]]

![[Pasted image 20240130145120.png]]

https://www.cs.cmu.edu/~16385/s17/Slides/13.1_Stereo_Rectification.pdf