# Dubins Path: RSR (Right-Straight-Right)
In a **Dubins path**, the vehicle follows this sequence:
1. **Initial Right Turn:** From the start position, the vehicle turns clockwise in an arc.
2. **Straight Segment:** The vehicle travels in a straight line.
3. **Final Right Turn:** The vehicle completes the path with another clockwise arc to reach the final position and heading.

## Input Parameters
- Initial position and heading: **$(x_{i},y_{i}),\psi_{i}$**
- Final position and heading: **$(x_{f},y_{f}),\psi_{f}$**
- Minimum turning radius: **$\rho $**
## Step-by-Step Path Genertaion
1. **Calculate Circle Centers**
- **Start Right Circle Center**
$$
 C_{Ri​​}=(x_{Ri}​​,y_{Ri​​})=(x_{i​}+\rho cos(\psi_{i​}),y_{i​}−\rho sin(\psi_{i​}))
$$
