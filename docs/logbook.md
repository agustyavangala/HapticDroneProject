## 2026-11-25 (Wed)

**Goal:** Build the frame, set up the telemetry radio and GPS, and install the parts into the drone.

**Done:**
- Created the GitHub repo `drone-contact-force` (license: MIT)
- Built the airframe (Holybrox650)
- Calibrated the accelerometer (MissionPlanner - pass )
- Set up the telemetry radio (915 MHz, baud rate 57600 , link confirmed with ground station: yes)
- Set up the GPS 

**Evening session: real telemetry link**
- Mission Planner is connected to the real Pixhawk 6X (ArduPilot) through the 915 MHz telemetry radio pair
- Ground-side radio: COM5, 57600 baud
- Props off, bench only. No commands sent from my own code; read-only logging.

**Connection string for my own code (real link):**
- `mavutil.mavlink_connection("COM5", baud=57600)`
- Only one program can hold COM5, so Mission Planner must be disconnected first, or I connect to its MAVLink mirror port instead (port: ____)

**Simulator (SITL) status:**
- Launched from Mission Planner Simulation tab: yes/no
- 

**Measurements (fill in after running the script):**
- Expectation recorded before measuring: well below the 50 Hz assumed in the architecture document, because 57600 baud is shared with Mission Planner's telemetry

**Plan changes (ArduPilot instead of PX4):**
- GUIDED mode replaces offboard mode
- ArduPilot SITL replaces `make px4_sitl gz_x500`
- PX4's 2 Hz offboard rule won't apply; I'll measure what ArduPilot does when the setpoint stream stops
- Research Plan wording needs updating, and I need to tell my mentor

**Next:** Write rig/mavlink_bridge.py, log 60 s of position to CSV on the real link, then repeat on SITL and compare the two rates.

**Not done:**
- Installing the remaining parts into the drone (carried over to next session)

**What broke / what I learned:**
- Learned about power distribution boards
- different functions within the pixhawk controller
- how the telemetry radio communicates.
- Started thinking about how the haptic controler 

**Numbers:**
- Accelerometer calibration: ____
- Radio link: signal strength / packet loss ____
- GPS: satellite count ____, HDOP ____

**Next:** Install the remaining parts, then continue with the plan (PX4 SITL, then reading vehicle state into a CSV).
