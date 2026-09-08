# F1Tenth Gym Docker View

F1Tenth (or generic ROS 2, if you want) RViz running inside a Docker container.

## Prerequisites

- Run `xhost local:docker` on the host at least once per boot so the container
  is authorized to open windows on the host X server.

- The car must be running **Fast DDS Discovery Server**. This container is
  configured as a discovery client and will not find any nodes unless the car's
  discovery server is reachable.
- The car's address is specified in the `.env` file as `CAR_ADDR`. The
  `docker-compose.yml` uses this to set `ROS_DISCOVERY_SERVER=${CAR_ADDR}:11811`.

## Opening the RViz configs

The `.rviz` files in `f1tenth_view/` (e.g. `fastsimplex.rviz`,
`gym_bridge.rviz`, `rl_verification.rviz`) can be opened in RViz via
**File -> Open**, then navigating to `/f1tenth_view`.