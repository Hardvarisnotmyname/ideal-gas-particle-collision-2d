

AI Cleaned up Readme

Ultimate Ideal Gas Simulation
A high-performance, vibe-coded particle simulation in HTML/JS aiming for 100,000 particles

Overview
This simulation models two square boxes connected by a variable-width pipe. Each box contains a configurable number of ideal gas particles moving with some velocity. Particles collide elastically with each other and with walls (including the pipe divider), using a Sweep and Prune collision detection algorithm for efficiency.

The design goal:

Handle huge particle counts without degenerating into clumpy or blob-like motion.

Keep collisions realistic and avoid tunneling (or turn tunneling into a creative “feature”).

Offer real-time interactive controls for temperature, particle count, pipe width, and more.

Core Features
Simulation Layout
Two square boxes on a 16:9 canvas.

Pipe in the middle wall — adjustable height.

Pipe toggle — open or close in real time.

Particle Physics
Position, velocity, radius, and mass per particle.

Elastic collisions between particles and walls.

Sweep and Prune collision detection for efficiency.

Speed-based color coding:

Red = hot/fast

Blue = cold/slow

Quantum tunneling effect: At high speeds, particles can slip through closed walls. This is caused by the step size of updates — and can be exploited for fun effects like wavefronts.

Controls
Control	Description
Particles/Box	Number of particles in each box.
Temp Left	Temperature of the left box. Rescales velocities instantly.
Temp Right	Temperature of the right box.
Radius	Particle size (good for low N and visual clarity).
Pipe Height	Height of the connecting pipe.
Reset	Resets simulation with new random particles.
Pause/Resume	Freezes or unfreezes the sim.
Open/Close Pipe	Toggles the divider opening.

Temperature slider notes:

Zero temperature = “frozen” particles.

Re-warming either restores old directions or assigns random new ones.

Live Stats
Left Temp / Right Temp: Derived from RMS velocity.

Total Particles.

Collisions/sec.

FPS.

Graphs
Left Box Temp vs. Time.

Right Box Temp vs. Time.

Auto-adjusting Y-axis for dynamic ranges.

Min, max, and average values displayed.

Room for four graphs (future feature: add long-term and short-term history graphs).

Performance Notes
Collision detection = ~50% CPU time. Naive method is O(n²), but Sweep and Prune reduces this toward O(n log n).

Rendering = ~50% CPU time (all draw calls via 2D canvas).

WebGL could allow higher particle counts — not implemented yet.

Known Issues
Tunneling at high speeds: Can be fixed with smaller update steps, but intentionally left in for now as a “wavefront mode.”

No WebGL acceleration — limited by CPU draw calls.

Possible Future Improvements
Tunneling toggle (strict vs. artistic mode).

More graph options.

Frames-per-collision stat.

WebGL backend.

How It Works
1. Particle Updates & Wall Collisions
Particles are updated in small sub-steps to prevent skipping through walls:
2. Collision Detection (Sweep and Prune)
Sorted along x and only checking nearby particles cuts down checks:
3. Temperature Control
Instantly rescale velocities to match the desired temperature:
4. Graph Drawing with Dynamic Y-Axis
Min/max are computed every frame to adjust scale:
License
MIT — use, modify, break, and vibe freely.

real readme
Ok so this is a particle sim written in html aiming for 100k particles with vibe coding O_O. The idea is there are two boxes connected by a pipe of variable width. 
There are particles in the boxes which are zooming around ie. have some velocity. Particles collide with other particles and dont go thru walls....this part is important and takes a lot of processing or clever pruning
and still we observe the quantum tunneling effect. Its a feature. But there should be a button or switch to turn it off hopefully but rn you can create a non circular wavefront using this bug (pipe is not opened between
hot and cold boxes but fast particles still make it through. Also fast particles are red, slow are blue.....draw calls might get expensive for big number of particles but its pretty. So basically 2 boxes with a pipe in
between and particles, collisions are handled using sweep and prune but faster methods are always better as long as the particles dont become clumpy or bloby.
Above the boxes there is a slider for number or particles, temperature of left box slider (this sets a temp ie particle velocities in the box using a temp speed scaling factor), temp of right box (same, also temps
should go down to zero for the sliders cuz we want to see frozen particles get hit by moving ones and a cascade effect) (also temp sliders update the particle velocities in real time if changed and particles dont freeze
if slider is set to zero and then given a non zero value particles either remember the velocity direction vector or get random velocities assigned, a particle radius slider (optional but good for low n and old people 
and easy collision checkingvisually), a pipe width slider (also optional but why not), reset pause and open pipe buttons, open pipe becomes close pipe when clicked and should be self explanatory,
pause is for pause, reset uses the new particle count from the slider and starts a new sim (randomly arranged particles with random velocities acc to temp). There is also a left box temp and right box temp indicators
which update to indicate the box temps calculated from the particle velocities. After that there is also a total particle counter (can be removed if slider indicated total number of particles instead of particles per
box, a collision/sec reading and a fps reading, maybe we add a frames per collision or collision per frame reading too but idk if that will be that useful really also hard to read cuz reciprocals and stuff, and finally
since the boxes are square and monitors are 16x9, we can fit two boxes with all the readings and sliders on top and still have room on the right for two graphs which show the left box temp and right box temp vs time,
how as one box gets colder the other heats up and stuff. There is space for 4 graphs so maybe in the future there is are two long full history graphs and two dynamic y axis short term graphs. Half the time goes into
collision detection as it can be O(n^2) if checked naively (its closer to O(n) or O(nlogn) with the spruceandprune i think), the other half goes into draw calls but i have had no luck with webgl.
sorry for the text wall this is how i think..
