## Code Completion

https://medium.com/@junbs95/code-completion-and-debugging-for-ros2-in-vscode-a4ede900d979

## Debugger

You need to have a .vscode folder with the following configuration
- c_cpp_properties.json

- settings.json

- launch.json

  - This file contains debugger settings and helps to specify command-line arguments for debugging.
  - You will mostly use this file for executing launch files with the debugger.

- tasks.json

  To run the ```colcon``` command from VSCode, you need to create the file ```tasks.json``` within the .vscode folder and populate it with the following content:

![[Pasted image 20240202131953.png]]

### Note
1. When you start debugging, if your breakpoints aren't bound (solid red circle) or they are not being hit, you may need to enable debug symbols during compilation.
	```
	add_compile_options(-g)
	```
	Link: [My breakpoints aren't being hit](https://code.visualstudio.com/docs/cpp/faq-cpp#_my-breakpoints-arent-being-hit)

2. 

### Reference

1. [VSCode Debugging](https://code.visualstudio.com/docs/editor/debugging)
2. [ROS 2 and VSCode](https://picknik.ai/vscode/docker/ros2/2024/01/23/ROS2-and-VSCode.html#debugging-tests)
3. [Unlocking Enhanced Development Experience: Creating Custom Configurations for VS Code Extensions](https://www.theroboticsspace.com/blog/VS-Code-ROS-Configurations/)
4. 