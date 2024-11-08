# Dubins Path: RSR (Right-Straight-Right)
The Dubins path is a shortest path trajectory for a vehicle that moves with a constant forward velocity and a minimum turning radius constraint, often used in UAV, robotics, and autonomous vehicle navigation. Here, we discuss the **RSR (Right-Straight-Right)** Dubins path, one of the six possible Dubins path types.

## Overview of Dubins Path

Dubins paths are composed of three segments:
1. **Turning Right** or **Turning Left**: Circular arcs at a specified minimum turning radius.
2. **Straight Line**: A linear segment between two circular arcs.

An RSR Dubins path includes two right turns with a straight line in between. This path structure allows a vehicle to travel from an initial position and orientation to a target position and orientation with minimal travel distance, considering the constraint of the minimum turning radius.

## Components of an RSR Path

For an RSR Dubins path, the trajectory includes:
1. **Right Arc Segment** (Initial Turn): The first segment begins with a rightward turn from the starting position and orientation until the vehicle is aligned with the straight line segment.
2. **Straight Line Segment**: After the initial turn, the vehicle travels along a straight line path, bridging the gap between the two circular arcs.
3. **Right Arc Segment** (Final Turn): The final segment completes the path with a second rightward turn, transitioning from the straight segment to the endpoint with the target orientation.

## Calculating the RSR Path

The calculation of an RSR path between two points involves:

### 1. Determining Turn Centers
   - The turn centers are calculated based on the initial and final positions, initial and final headings, and the minimum turning radius.
   - The direction of each turn dictates the offset from the vehicle's position for the turn center (e.g., for a right turn, the center is offset to the right of the vehicle's heading).

### 2. Calculating Straight Line Segment
   - With the turn centers known, a line segment between the two circular arcs is calculated.
   - This line segment represents the straight portion of the path, which joins the two turns at tangent points.

### 3. Constructing the Path Segments
   - Each segment (initial turn, straight line, final turn) is parameterized to generate the trajectory along the RSR path.
   - The initial and final arc segments are circular, while the middle segment is a straight line.

### 4. RSR Path Constraints
   - The radius of each turn is limited to the vehicle’s minimum turning radius, ensuring the path is feasible for vehicles that can’t make sharp turns.
   - The path minimizes the travel distance within this constraint, offering an efficient path from start to end.

## Visualizing the RSR Path

The RSR path can be visualized as a sequence of three segments, connected by tangent points on the two circular arcs. This path type is advantageous because it provides a continuous, smooth path that respects the vehicle’s turning constraints.

---

This theoretical explanation covers the basic understanding and calculation steps for implementing an RSR Dubins path, making it helpful for developers or researchers working on path planning with Dubins curves.
