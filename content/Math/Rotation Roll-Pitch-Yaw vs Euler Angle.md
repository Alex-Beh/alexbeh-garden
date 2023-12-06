
![[rollpitchyaw_to_euler.png]]
- **Euler angles** refer to the angles in a sequence of rotations in a **body-fixed frame**.
![[euler.png]]
![[euler-illustration.png]]

- **Roll-Pitch-Yaw** angles as a sequence of rotations relative to the **space frame**.
![[roll-pitch-yaw-illustration.png]]

## Code
```c++

Eigen::AngleAxisd rotation_x = Eigen::AngleAxisd(-0.5 * M_PI, Eigen::Vector3d::UnitX());

Eigen::AngleAxisd rotation_y = Eigen::AngleAxisd(0.5 * M_PI, Eigen::Vector3d::UnitY());

cout << "[FIXED/EULER] Rotation: " << endl
<< std::setprecision(2) << rotation_y.matrix() * rotation_x.matrix() << endl;

cout << "[roll-pitch-yaw] Rotation: " << endl
<< std::setprecision(2) << rotation_x.matrix() * rotation_y.matrix() << endl;
```

https://web.mit.edu/2.05/www/Handout/HO2.PDF

https://math.stackexchange.com/a/1681118/1133515