# Dubins Path: RSR (Right-Straight-Right)

In an **RSR Dubins path**, the vehicle follows this sequence:

1. **Initial Right Turn:** From the start position, the vehicle turns clockwise in an arc.
2. **Straight Segment:** The vehicle travels in a straight line.
3. **Final Right Turn:** The vehicle completes the path with another clockwise arc to reach the final position and heading.

---

### Input Parameters

- \( p_i = (x_i, y_i), \, \psi_i \) : Initial position and heading.
- \( p_f = (x_f, y_f), \, \psi_f \) : Final position and heading.
- \( \rho \) : Minimum turning radius of the vehicle.

---

### Step-by-Step Path Generation

#### Step 1: Calculate Circle Centers

1. **Start Right Circle Center** \( C_{R_i} \):

   $$
   (x_{R_i}, y_{R_i}) = \left( x_i + \rho \cos(\psi_i), \, y_i - \rho \sin(\psi_i) \right)
   $$

2. **End Right Circle Center** \( C_{R_f} \):

   $$
   (x_{R_f}, y_{R_f}) = \left( x_f + \rho \cos(\psi_f), \, y_f - \rho \sin(\psi_f) \right)
   $$

#### Step 2: Compute the Angle \( \theta \) for the Straight Segment

The angle \( \theta \) of the straight segment, measured between the centers of the two circles, is:

$$
\theta = \frac{\pi}{2} - \arctan\left( \frac{y_{R_f} - y_{R_i}}{x_{R_f} - x_{R_i}} \right)
$$

#### Step 3: Calculate Length of the Straight Segment \( d \)

The length \( d \) of the straight segment connecting \( C_{R_i} \) and \( C_{R_f} \) is given by the Euclidean distance:

$$
d = \sqrt{(x_{R_f} - x_{R_i})^2 + (y_{R_f} - y_{R_i})^2}
$$

---

### Generating the Path Points

#### Segment 1: Initial Right Turn Arc (from \( p_i \) to \( \theta \))

Each point \( p_n = (x_n, y_n) \) on the initial right turn arc is calculated by rotating the initial position \( p_i \) clockwise around the center \( C_{R_i} \):

$$
(x_n, y_n) = \left( x_{R_i} + \rho \sin(\psi_n), \, y_{R_i} + \rho \cos(\psi_n) \right)
$$

Here, \( \psi_n \) starts at \( \psi_i \) and increments by a small angle \( \Delta \psi \) until it reaches \( \theta \).

#### Segment 2: Straight Line Segment

Each point on the straight line segment is calculated by advancing the previous point \( p_{n-1} \) by a step \( \Delta d \) in the direction of \( \theta \):

$$
(x_n, y_n) = \left( x_{n-1} + \Delta d \sin(\theta), \, y_{n-1} + \Delta d \cos(\theta) \right)
$$

#### Segment 3: Final Right Turn Arc (from \( \theta \) to \( \psi_f \))

This segment involves rotating each point clockwise around the center \( C_{R_f} \) until the heading reaches \( \psi_f \). The points are computed as:

$$
(x_n, y_n) = \left( x_{R_f} + \rho \sin(\psi_n), \, y_{R_f} + \rho \cos(\psi_n) \right)
$$

Here, \( \psi_n \) starts at \( \theta \) and increments by \( \Delta \psi \) until it reaches \( \psi_f \).

---

### Summary

1. **Calculate Circle Centers:** Determine the centers for the initial and final right-turn arcs.
2. **Compute Angle \( \theta \):** Find the angle of the straight segment.
3. **Calculate Straight Segment Length \( d \):** Compute the distance for the straight segment.
4. **Generate Points for Each Segment:** Calculate points along the initial arc, straight segment, and final arc.

---

### Notes

- \( \rho \) is the minimum turning radius, which defines how sharp the turns are for the vehicle.
- The path generation involves calculating points along arcs and straight lines to ensure the vehicle can move smoothly from the start to the end point while maintaining a constant minimum turning radius.
