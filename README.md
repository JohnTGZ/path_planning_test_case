# path_planning_test_case
This repository contains test cases for path planning and trajectory optimization problems.
Currently only one 10m x 10m map `map0` with cylindrical obstacles is provided, which has the following top view:
<img src="pictures/map0_top.png" alt="map0_top" style="width: 500px;"/>

An A* planner is then executed from () to () on the voronoi graph of the map, yielding the following raw A* path:
<img src="pictures/map0_a_star_raw.png" alt="map0_top" style="width: 500px;"/>

After smoothing the raw A* path, we end up with a piecewise linear A* path :
<img src="pictures/map0_a_star_piecewise_linear.png" alt="map0_top" style="width: 500px;"/>

## Important Info
1. Origin of the map `(0.0, 0.0, 0.0)` is in the middle of the map and not at the corners of it. Obstacle positions and A* path points are relative to this origin. 

## Provided files
1. `map0.pcd`: (Not necessary) 10m x 10m point cloud map replete with obstacles.
    - The 3D obstacle map can be visualized with a point cloud viewer using this file.
2. `map0_obstacle_data.json`: JSON file containing the position and attributes of obstacles 
    - Within the `cylinders` field is an array of cylindrical obstacles. 
    - Each obtacle has the attributes `x`, `y`, `radius` and `height`. By iterating through each element in the array, a visualization of the obstacle map can be reconstructed.
    - All units in meters.
3. `map0_a_star_raw.json`: JSON file containing raw A* path 
    - All units in meters.
4. `map0_a_star_piecewise_linear.json`: JSON file containing piecewise linear A* path
    - This path has been processed from the continuous A* path to obtain a piecewise linear path using a simple line of sight check. Resulting in fewer waypoints.
    - All units in meters.

## Reading JSON in MATLAB
Refer to [jsondecode](https://www.mathworks.com/help/matlab/ref/jsondecode.html) library for parsing JSON files in MATLAB.
