# 介绍
* `路径规划`: 路径规划是指寻找从起点到终点最佳路线的过程，关键在于如何高效地避开障碍物并优化特定的路径指标（如距离、时间或能量消耗）。经典路径规划方法包括图搜索算法，如Dijkstra算法和A*算法；基于采样的方法，如RRT算法，RRT*算法；基于进化的方法，如遗传算法、模拟退火方法。
* `路径跟踪`: 路径跟踪是指通过控制车辆、机器人或其他移动实体的转向和速度，使其能够精确地沿着预设或规划好的路径进行行驶或移动。主要目的是最小化移动实体与参考路径之间的横向距离和航向误差，确保移动实体能够稳定、准确地沿着预设路径移动。

这个库提供了“路径规划”算法中JPS算法、RRT*算法和DWA算法的实现，以及“路径跟踪”算法中的PID算法、MPC算法的实现。

#文件说明
文件结构如下所示

```
├─gif
├─examples
│ ├─simulation_global.mlx
│ ├─simulation_local.mlx
├─global_planner
│ ├─graph_search
│ | ├─a_star.m
│ | ├─d_star.m
│ | ├─dijkstra.m
│ | ├─jps.m
│ ├─sample_search
│ | ├─rrt_star.m
├─local_planner
│ ├─dwa_plan.m
│ ├─pid_plan.m
│ ├─mpc_plan.m
└─utils
```

路径规划和路径跟踪算法实现在文件夹“global_planner”和“local_planner”中。

## 算法运行
若要运行某个算法模拟，请打开`examples/simulation_global.mlx `或`examples/simulation_local.mlx '并选择算法和地图模式（静态和动态），例如

```matlab
clear all; clc;

% load environment
load("gridmap_20x20_scene1.mat");
map_size = size(grid_map);
G = 1;

% simulation mode
mode = "static";
% mode = "dynamic";

% start and goal
start = [3, 2];
goal = [18, 29];
% goal = [12, 16];

% planner
% graph search
% planner_name = "a_star";
% planner_name = "dijkstra";
% planner_name = "jps";
% planner_name = "d_star";

% sample search
planner_name = "rrt_star";
```



## 算法结果
算法结果保存在 `gif` 文件夹中。
