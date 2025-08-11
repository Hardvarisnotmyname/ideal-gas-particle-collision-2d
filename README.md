✨ Ultimate Ideal Gas Simulation ✨
This isn't just a simulation; it's a digital petri dish. A high-performance, 2D physics playground built with vanilla JavaScript and WebGL, designed to juggle 100,000+ particles in real-time. 🚀

Forget static textbook diagrams. Here, you control the laws of physics. You can crank up the heat until particles move at blistering speeds, freeze them to absolute zero, and smash them together to witness the beautiful, chaotic results. This is your laboratory for exploring everything from the Ideal Gas Law to emergent phenomena that were never explicitly coded.

🎮 The Playground: An Interactive Sandbox
This simulation is built for experimentation. The controls aren't just settings; they are your tools for discovery.

Control	What it Does	🔬 Experiment Ideas
Total Particles	Sets the particle count from 0 to 100,000.	Crank it to the max to see large-scale structures form. Or, use a low count to track individual particle journeys.
Left/Right Temp	Injects kinetic energy! Sets the initial speed of particles.	Phase Transition: Set one side to 0 (absolute zero!) and the other to max. Open the pipe and watch the frozen "crystal" melt and boil!
Radius	Changes the size of the particles.	How does particle size affect the rate of thermal equilibrium? Make them huge and watch them clog the pipe!
Pipe Height	Adjusts the size of the opening in the central wall.	Slowly open the pipe between a hot and cold box. Can you create a stable temperature gradient?
Substeps	Runs physics multiple times per frame for accuracy.	Low substeps lead to chaos and tunneling. High substeps create a more orderly, classical system. Which do you prefer?
Max Speed	A speed limiter to prevent tunneling.	Dial this down to see how it affects high-energy systems. It's the "realism" knob.
Collision Mode	Switches between SAP (accurate) and Grid (fast).	The Grid mode allows some overlap, creating fascinating 3D-like cluster effects. SAP keeps things clean.
Physics Toggles	Enable Gravity, Friction, Drag, or Pressure.	Turn on Gravity and watch the particles collapse into a "star"! Add Drag to see the system slowly cool and die.
Uncap FPS	Run the simulation as fast as your machine can handle! ⚡	Use this to fast-forward your experiments and see long-term outcomes in seconds.


🤯 Discover Emergent Phenomena
The most beautiful things in this simulation are the ones that weren't explicitly programmed. These are emergent properties—complex patterns arising from simple rules.

Wavefronts & Tunneling: At low substeps and high temperatures, particles can "quantum tunnel" through the central wall. This isn't just a bug; it's a feature! By keeping the pipe closed and heating one side, you can generate a coherent wavefront of high-energy particles that phase through the barrier, creating stunning visual pulses.

Grain Boundaries: Start a simulation with two different temperatures. As the system moves toward equilibrium, you can see faint, shifting lines where the hot and cold regions meet. These are analogous to grain boundaries in polycrystalline materials, where different crystal orientations meet.

Crystallization & Melting: Use the temperature sliders to create a block of "ice" (temp ≈ 0). Introduce a few high-speed "hot" particles and watch them shatter the crystal structure, creating a cascade of collisions in a beautiful melting effect.

🤓 Under the Hood: A Developer's Deep Dive
So, you want to know how the magic happens? Let's get technical.

Architecture: Main Thread vs. Web Workers
The simulation is architected into three decoupled parts: the UI Layer, the Renderer, and the PhysicsModule. While currently running on the main thread for simplicity, the PhysicsModule is self-contained and can be easily offloaded to a Web Worker. This would move the heavy physics calculations off the main thread, keeping the UI perfectly responsive even at 100k particles. It's the next logical step for performance purists.

The Particle Data Structure: A Typed Array Powerhouse
There are no particle class objects here. That would be too slow. Instead, all particle data is stored in a single, massive Float32Array.

[x1, y1, vx1, vy1, r1, g1, b1, radius1, x2, y2, vx2, vy2, ...]

This flat data structure is cache-friendly and perfect for blazingly fast iteration and for uploading directly to the GPU.

Collision Detection: The Great Trade-Off
The Collision Mode switch lets you explore a fundamental trade-off in computational physics.

Sweep and Prune (SAP): Your scalpel хирургический_нож:. This is an O(n log n) algorithm that works by sorting all particles along the x-axis. It then "sweeps" across this sorted list, only checking for collisions between particles whose x-intervals overlap. It's elegant, precise, and avoids most unnecessary checks. This is your go-to for physically accurate-looking results.

Spatial Grid (Hashing): Your sledgehammer 🔨. This O(n) algorithm is brutally effective. It partitions the space into a grid and drops each particle into a cell. Collisions are then only checked between particles in the same cell. It's incredibly fast but can lead to "clumping" and overlaps if particles get too dense in one cell, creating the unique visual artifacts you see in Grid mode.

Rendering: From CPU to GPU
The simulation uses WebGL to achieve 100k particles. It packs the positions, colors, and radii into buffers and uploads them to the GPU. Then, with a single draw call (gl.drawArrays(gl.POINTS, ...)), it tells the GPU to render every single particle. The vertex shader places the particles, and the fragment shader draws them as soft, anti-aliased circles. This is orders of magnitude faster than a traditional 2D canvas arc() loop.

📚 On the Shoulders of Giants
This project was inspired by a long history of computational physics and creative coding. If you find this interesting, you should explore these as well:

Academic Roots: The simulation is a visual representation of the Maxwell-Boltzmann distribution, which describes particle speeds in a gas.

Classic Inspirations: Many of us grew up with "Gas in a Box" Java applets. This project is a modern homage to those early web physics toys.

Modern Sandboxes: Projects like Particle Life and the work of Seb Lague showcase the incredible beauty of emergent systems.

The Coding Train: Daniel Shiffman has inspired countless people to explore creative coding and physics simulations.

🚀 Your Turn to Build!
This project is open-source and built to be tinkered with. Fork it, break it, make it better.

Contribution Ideas:

Implement a Web Worker: Move the PhysicsModule to a separate thread.

Add More Forces: What about electromagnetism? Or custom force fields painted by the user's mouse?

True "Accurate Mode": Implement the full conservation of energy and momentum collision formulas.

Add More Stats: How about tracking momentum, or graphing the distribution of particle speeds?
