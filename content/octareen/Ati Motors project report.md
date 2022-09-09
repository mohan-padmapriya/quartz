## References
- [2D Map quality evaulation metrics, 2017](https://arxiv.org/pdf/1708.02354.pdf)
- [Benchmarking of 2D slam algs](http://www.acro.be/downloadvrij/Benchmark_2D_SLAM.pdf)
- [Mapping performance comparison of 2D SLAM algorithms based on different sensor combinations, 2021](https://iopscience.iop.org/article/10.1088/1742-6596/2024/1/012056/pdf)
- [3D lidar map comparison, 2019](https://www.aia-polytech.be/wp-content/uploads/2021/01/EvaluationAndComparisonOf3DLidarBasedSLAMAlgorithms.pdf)


-------------------
**Areas:**
- [[Occupancy grids]], [[SLAM]]

**Project:**
*Part 1 -*
Build maps using various data sets using the basic slam.ipynb code provided. Analyse and understand them. 
>- *Do they start and end at the same point? What does this indicate?*
>- *True to the actual, physical surroundings?*
> -*Are there any double walls? How is this corrected?**
> - (accuracy?) bigger the grid cells, less accurate, is this a factor? the blurred walls

*Part 2* -
Build maps using Dr. Krishna's code and compare the algorithms.

> *What metrics do you use to compare the algorithms?*
> 1. *The accuaracy, or size of grid cell?*
> 2. *perturb the pose and the alg should account for the pertubation?*

------------------------


## Look up
- nearest neighbours
- smoothness
- perturbation
- dx, dy, dtheta



## Introduction
- SLAM algorithms 
- [[Occupancy grids]]
- LiDAR

## Implementation

































------------------------------
## Problems and ideas

# Yelli Ideas

…

### Problems

1. Ghosting in the map 
    1. Some features in the map get duplicated due to errors in localization.
2. Loop closure issues
    1. When the path taken contains a loop, we often find loop closure issues, resulting in ghosting.
3. Noisy poses (waviness/kinks)
    1. Some waviness is expected because of the noisy input (lidar frame).
    2. Larger noise is possible in longitudinal direction because of lack of transverse features.
4. Limitation of high Z-slice
    1. We are using a high z-slice to avoid transient objects (e.g. people, trolleys, other bots)
    2. Because of this and geometry, we are unable to use nearby features (e.g. a pillar next tp the mule is ignored because the beams hit it at a lower height than the z-slice)
5. Points at larger distance are less likely to match because of 
    1. Small errors in roll/pitch change the Z significantly
    2. Lidar noise may be higher at higher ranges
6. Initial search may be unstable for small offsets because of lack of features.
    1. Ghosting or repeating features in the map could cause localisation to jump for some small changes in the pose.

### Possible Fixes - Short Term

1. Optimising to find and fix loop closure issues
    1. Works in notebook
    2. TBD: make this code work in production scripts, using CUDA, etc.
2. Use different search spaces for turns and straights?
3. Apply roll/pitch correction and ego-motion correction to lidar frame
4. Lenient matching of farther points
    1. Apply higher weights to matches based on the range
    2. Use a neighbourhood match instead of an exact match, the size of the neighbourhood increasing with range.
    3. `(range**0.25)+1` gives weights from 1 to 3 for range 0-15m
5. Remove transient objects from map with offline processing
6. Map update to update sections of the map
7. Handle bad sensor data
    1. lidar frames (missing sectors) - done
    2. IMU data - done
    3. wheel encoders - done

### Possible Fixes - Long Term

1. Full 3D mapping
    1. Constructing and using a full 3D map has its own difficulties, but it allows us to do map cleaning using ray-tracing etc. 
    2. We could also convert back to a 2D map after cleaning,  etc.
2. Removing dynamic objects enables us to get rid of the strict z-slice limitation.
    1. Using object tracking
    2. 
3. Semantic/feature matching
    1. If we could identify features such as walls, corners, pillars, etc. it would help to avoid bad localization (e.g. when we match an inside wall with an outside wall, or a human to a pillar.
4. Tiled maps, sub-maps 
    1. To restrict matches to objects that one can see
    2. To allow different parameters such as grid size, for different sections of the map
5. GPS etc. for outdoor?



