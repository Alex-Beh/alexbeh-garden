Colcon build
Other useful arguments for colcon build:
--packages-up-to builds the package you want, plus all its dependencies, but not the whole workspace (saves time)
--symlink-install saves you from having to rebuild every time you tweak python scripts
--event-handlers console_direct+ shows console output while building (can otherwise be found in the log directory)

The colcon build --packages-select <name-of-pkg> command to only build the selected package and the colcon build --packages-up-to <name-of-pkg> to build the selected package and ALL its dependencies but it will still rebuild things like rclcpp, fastrtps and co...
--packages-select　# 指定package
--packages-up-to # 构建指定package以及递归构建所有依赖
