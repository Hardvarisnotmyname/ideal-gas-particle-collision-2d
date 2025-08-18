Turn drag on for gravity, the hot early universe did not have planets, slow the sim down to see gravity!!

# Ultimate Ideal Gas Simulation - VC funded project

## 🔬 What's this?

Welcome to an advanced particle physics playground! This simulation lets you explore how thousands of particles behave under different physical forces - from basic collisions to complex phenomena like temperature equilibrium, gravity wells, and even a mini universe.

**Probably For**: STEM students, educators, curious coders, kids fascinated by physics, and anyone who wants to see invisible forces in action!

---
i hate this ai generated garbage readme so here's a screenshot.. just download the html and it should run, fix it yourself if it doesnt, lu bye.
<img width="1912" height="974" alt="image" src="https://github.com/user-attachments/assets/66d0c99c-0f91-490c-bd3e-8fa602767a86" />


## 🚀 Quick Start

1. **Hit Reset** to seed fresh particles
2. **Open the Pipe** to connect the two boxes
3. **Watch the magic** - hot (red) particles mix with cold (blue) ones
4. **Check the graphs** to see temperature equilibrium happen in real-time!

---

## 🎨 Visual Guide

### Particle Colors (Speed-Based)

- **🔵 Blue**: Slow/cold particles (low kinetic energy)
- **🟢 Green**: Medium speed particles
- **🟡 Yellow**: Fast particles
- **🔴 Red**: Very fast/hot particles (high kinetic energy)

The simulation uses HSL color shifting, so you'll see smooth transitions through the entire spectrum as particle speeds change!

---


another nice picture sprinkled in, try to use the settings you see to get the same, hopefully it should work, if not open the config values and spend hours tweaking the constants and magic numbers :D
<img width="1911" height="977" alt="image" src="https://github.com/user-attachments/assets/a47b5537-40c6-4662-ac06-6cd09111431e" />


## 🎛️ Control Panel Guide

### Basic Controls

**Total Particles** (100 - 120,000)

- More particles = more realistic physics but slower performance
- Sweet spot: 10,000 for most experiments
- Use Grid mode for 10,000+ particles with gravity/pressure

**Left/Right Temperature** (0 - 30,000)

- Sets initial particle speeds in each box
- Only affects new particles when you Reset
- Try extreme differences (50 vs 30,000) for dramatic effects!

**Particle Radius** (1-12px)

- Bigger particles = more collisions
- Large radius + few particles = easy to follow individual bounces
- Small radius + many particles = realistic gas behavior

**Pipe Height** (0-100%)

- Controls the opening between boxes
- 0% = completely sealed
- 100% = wide open connection
- Try 1-5% for realistic gas flow effects

### Advanced Physics

**Maxwell's Demon** 👹

- When ON: Only allows fast particles to move left→right
- Demonstrates the famous thermodynamics thought experiment
- **Creates density gradients**: Fast particles accumulate on the right, slow on the left
- **Demon Threshold**: Sets how fast a particle needs to be (1-250)
  - Higher = demon is pickier about "fast" particles
  - Lower = demon lets more particles through

**Collision Modes**

- **SAP Mode**: More accurate physics, better for studying collisions
- **Grid Mode**: Faster performance, creates cool 3D-like effects with large particles

**Force Systems**

- **Gravity**: Particles attract each other (creates clusters/singularities)
- **Pressure**: Particles repel nearby neighbors (realistic gas pressure)
- **Friction**: Energy loss during collisions (particles slow down over time)
- **Drag**: Air resistance effect (fast particles lose more speed)

### Performance Tuning

**Substeps** (1-8)

- Higher = more accurate collision detection
- Lower = better performance
- Reduce if simulation feels laggy

**Max Speed** (5-2500)

- Speed limiter to prevent particles from going too fast
- Lower values = calmer simulation

**Uncap FPS** 🚀

- Progressively increases simulation speed: 60→80→100→120+ FPS
- Watch temperature equilibrium happen in seconds instead of minutes!
- May stress your CPU - use with caution

---

## 🧪 Cool Experiments to Try

### 1. **Temperature Equilibrium Classic**

- Set Left: 20,000, Right: 50
- Open pipe to 2%
- Watch hot particles slowly warm up the cold side
- Observe graphs reaching equilibrium

### 2. **Rocket Nozzle Effect**

- Make left side very hot (25,000+)
- Keep right side cold (50)
- Open pipe just 1%
- See high-pressure gas escaping through small opening

### 3. **Gravity Wells & Clusters**

- Turn on Gravity
- Use Grid mode for performance
- Watch particles form clusters and orbital patterns
- Try with large radius for clearer visualization

### 4. **Collision Physics Demo**

- Set particles to ~500 total
- Increase radius to 8-12
- Use SAP mode for accuracy
- Watch individual particle bounces clearly

### 5. **Maxwell's Demon Paradox**

- Enable Maxwell's Demon
- Set threshold around 50
- Demon "cheats" thermodynamics by sorting particles
- Watch density gradients form - fast particles pile up on the right!
- See if you can break the second law!

### 6. **Density Gradient Study**

- Use Maxwell's Demon with threshold ~100
- Start with equal temperatures on both sides
- Watch particles naturally separate by speed/density
- Perfect demonstration of selective permeability

### 6. **Density Gradient Study**

- Use Maxwell's Demon with threshold ~100
- Start with equal temperatures on both sides
- Watch particles naturally separate by speed/density
- Perfect demonstration of selective permeability

### 7. **Pressure Cooker**

- Small pipe opening (1%)
- High particle count (50,000+)
- Turn on Pressure forces
- Watch realistic gas dynamics

### 8. **Friction & Drag Studies**

- Start with high-energy particles
- Enable Friction and/or Drag
- Watch the system slowly lose energy
- Perfect for studying energy dissipation

---

## ⚡ Performance Guide

### Smooth Performance (60+ FPS)

- **Up to 10,000 particles**: Any settings work well
- **10,000-50,000 particles**: Use Grid mode, avoid Gravity+Pressure
- **50,000+ particles**: Grid mode only, minimal effects

### When Things Get Slow

1. **Switch to Grid mode** (faster than SAP)
2. **Reduce Substeps** to 1-2
3. **Turn off Gravity and Pressure** (most CPU-intensive)
4. **Lower particle count** temporarily
5. **Reduce particle radius**

### For Maximum Speed

- Enable **Uncap FPS** (gradually increases to your display's max refresh rate)
- Use **Grid collision mode**
- Keep **Substeps** at 1-2
- Disable **Gravity** and **Pressure**

---

## 📊 Reading the Data

### Stats Panel

- **FPS**: Rendering frame rate (higher = smoother visuals)
- **Target FPS**: Simulation speed (increases with Uncap FPS)
- **Collisions/sec**: How many particle bounces per second
- **Collision Checks**: CPU work for collision detection
- **Left/Right Box Temp**: Average particle speed in each side

### Temperature Graphs

- **Recent**: Last ~2 minutes of data (good for watching changes)
- **Full**: Complete simulation history (shows long-term trends)
- **Watch for**: Equilibrium (both sides reaching same temperature)

---

## 🎓 Physics Concepts Demonstrated

- **Kinetic Theory of Gases**: Particle motion represents molecular motion
- **Thermodynamic Equilibrium**: Hot and cold sides eventually balance
- **Maxwell-Boltzmann Distribution**: Particle speed distributions
- **Collision Dynamics**: Elastic and inelastic collisions
- **Pressure**: Force from particle collisions with boundaries
- **Phase Transitions**: Watch particles cluster under gravity
- **Energy Conservation**: Total system energy (with friction off)
- **Entropy**: System disorder and the second law of thermodynamics

---

## 💡 Tips & Tricks

### For Educators

- Start students with simple setups (few particles, large radius)
- Use the pause button to discuss what's happening
- Reset graphs when starting new experiments
- Uncap FPS to speed through equilibrium demonstrations

### For Visual Learners

- Large particles (radius 8+) make individual collisions visible
- Extreme temperatures (50 vs 30,000) create dramatic color contrasts
- Grid mode with gravity creates beautiful clustering patterns

### For Performance Testing

- See how many particles your device can handle
- Test different collision modes
- Experiment with all force combinations

---

## 🔧 Troubleshooting

**Simulation running slowly?**

- Reduce particle count or switch to Grid mode
- Turn off Gravity and Pressure for 10,000+ particles
- Lower Substeps to 1-2

**Simulation frozen or hanging?**

- **Reset all settings to defaults** - sometimes extreme combinations cause issues
- Hit Reset button to clear corrupted particle states
- Reload the page if completely stuck

**Particles behaving weirdly?**

- Hit Reset to clear any accumulated errors
- Check if Max Speed is too low
- Make sure Pipe Height isn't at 0% when you want mixing

**Graphs not updating?**

- They update automatically - wait a few seconds
- Hit Reset to clear old data

**Maxwell's Demon not working?**

- Make sure there's actually a speed difference between sides
- Adjust Demon Threshold - try values between 10-100
- The demon works even with pipes closed!

---

## 🌟 Advanced Notes

This simulation uses optimized algorithms to handle thousands of particles in real-time:

- **Spatial partitioning** for efficient collision detection
- **WebGL rendering** when available (falls back to 2D canvas)
- **Adaptive physics stepping** for smooth performance
- **Force approximation** for gravity/pressure calculations

The physics engine separates collision detection (SAP vs Grid) from force calculations, allowing you to mix and match for different effects and performance characteristics.

---

**Have fun exploring the invisible world of particle physics! 🚀**

## 🎯 Push the Limits!

**Don't be afraid to break things!** This simulation is built to handle extreme conditions:

- Crank particles to 120,000 and see what happens
- Turn on ALL forces at once and watch chaos unfold
- Set ridiculous temperatures (30,000 vs 0) and observe the mayhem
- Find the breaking point of your device - where does it start to lag?
- Discover weird edge cases and unexpected behaviors
- **You are only limited by your imagination!**

The best way to learn physics is to push systems beyond their normal operating ranges. Go wild, experiment, and see what fascinating phenomena emerge from the complex interactions of simple rules.

---

*Remember: This is a simplified model - real gases have quantum effects, intermolecular forces, and other complexities not shown here. But the fundamental principles are all accurate!*
